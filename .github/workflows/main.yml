name: Windows Free RDP 2026
on:
  workflow_dispatch:

jobs:
  build:
    runs-on: windows-latest
    timeout-minutes: 360
    steps:
      - name: Setup Tailscale Network
        uses: tailscale/github-action@v2
        with:
          authkey: ${{ secrets.TAILSCALE_AUTHKEY }}
      - name: Enable Remote Desktop
        run: |
          Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -value 0
          Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
          net user runneradmin YourPassword2026! /add
          net localgroup administrators runneradmin /add
      - name: Keep Alive Loop
        run: |
          $val = 0
          while ($val -lt 360) {
            Start-Sleep -Seconds 60
            $val++
          }
