---
title: "Can't Install Prey"
date: 2016-04-28
forum: General Help
---

### Post by alex517 on 2016-04-28
[https://preyproject.com/download](https://preyproject.com/download)

The file I'm trying to install: prey_1.5.0_i386.deb
My OS: Ubuntu 14.04.3 LTS

I don't have much time to play around and I'm not experienced with Linux, so I'm hoping it's a quick fix. If I installed it on WINE (assuming that install would work), would Prey still work as it should? It's for tracking stolen or missing computers.

When I try to install it, I get:
Error: Cannot install 'scrot:i386'

This is the Lintian output tab:

```
E: prey: unstripped-binary-or-object usr/lib/prey/versions/1.5.0/bin/nodeE: prey: embedded-library usr/lib/prey/versions/1.5.0/bin/node: openssl
E: prey: embedded-library usr/lib/prey/versions/1.5.0/bin/node: zlib
W: prey: hardening-no-relro usr/lib/prey/versions/1.5.0/bin/node
W: prey: wrong-name-for-changelog-of-native-package usr/share/doc/prey/changelog.Debian.gz
W: prey: syntax-error-in-debian-changelog line 4 "found eof where expected more change data or trailer"
W: prey: control-file-is-empty conffiles
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/bin/node 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/bin/prey 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/alarm.mp3 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/modem.mp3 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/ring.mp3 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/siren.mp3 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/alert/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alert/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/alert/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/alert/linux/flash.py 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/filebrowser/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/filebrowser/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/lib/ 0750 != 0755
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/lib/bg-lock.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/lib/bg-lock.png 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/linux/prey-lock 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/linux/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/linux/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/runner.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/windows.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/wipe.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/cli.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/commands.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/common.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/default.options 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/helpers.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/hooks.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugin.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/parser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/processors.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/test/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/test/plugin_test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/completer.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/help.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/accounts.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/devices.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/errors.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/keys.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/logger.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/push.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/request.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/authorize_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/device_link_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_with_proxy_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_without_proxy_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/signup_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/bus.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/test/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/test/index_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/test/test_server.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/prompt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/sender.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/setup.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/test/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/test/main_load.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/test/setup.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/reports-to-inbox/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/reports-to-inbox/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/reports-to-inbox/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/retry-failed-reports/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/retry-failed-reports/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/retry-failed-reports/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/test/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/test/trigger_spec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/files/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/files/finder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/files/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/linux/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/strategies.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/ia32/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/ia32/NodeRT_Windows_Devices_Geolocation.node 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/x64/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/x64/NodeRT_Windows_Devices_Geolocation.node 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/NodeRT_Windows_Devices_Geolocation.d.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/NodeRT_Windows_Devices_Geolocation.d.ts 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/main.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/ramcheck.vbs 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/network/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/network/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/network/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/network/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/network/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/windows.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/linux/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/system/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/system/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/linux/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/reports.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/reports/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/reports/load.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/reports/specs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/reports/status.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/reports/stolen.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/transports.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/transports/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/transports/http/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/transports/http/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/transports/smtp/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/transports/smtp/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/connection/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/connection/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/lib/latlng.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/test_latlng.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/network/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/network/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/triggers/power/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/triggers/power/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/updater.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/agent/utils/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/utils/logo.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/utils/pidfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/agent/utils/storage.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/common.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/account.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/cli.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/gui/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/gui/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/linux/prey-config.glade 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/linux/prey-config.py 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/ 0750 != 0755
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/agent.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/agent.bmp 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/ 0750 != 0755
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/check.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/check.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/connect.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/connect.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/settings.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/settings.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.bmp
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.bmp 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-agent-48.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-agent-48.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text-shadow.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text-shadow.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text.png 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey.ico 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey.png 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/install.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/log.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/plugins.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/settings.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/shared/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/keys.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/log.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/messages.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/panel.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/plugin_manager.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/shared/version_manager.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/tasks/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/daemon.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/windows.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/prey_user.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/tasks/utils/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/tasks/utils/create_user.sh 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/conf/utils/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/utils/cp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/utils/operetta.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/utils/run.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/utils/run_synced.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/conf/versions.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/exceptions.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/package.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/plugins.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/system/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/system/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/system/linux/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/system/linux/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/system/linux/paths.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/system/paths.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/lib/system/utils/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/lib/system/utils/runner.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/license.txt 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/async/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/async/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/async/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/async/component.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/async/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/async/lib/async.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/async/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/bin/buckle 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/bin/decompress-zip 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/download-test-assets.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/decompress-zip.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/extractors.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/file-details.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/signatures.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/structures.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/lib/vars.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/perf/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/perf/loop.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/perf/small.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/graceful-fs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/polyfills.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/mkpath.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/bin/nopt.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/lib/nopt.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/CONTRIBUTING.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/abbrev.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/CONTRIBUTING.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/benchmark/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/benchmark/compare-with-callbacks.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/benchmark/scenarios.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/q.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/queue.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/bin/touch.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/bin/nopt.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/lib/nopt.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/CONTRIBUTING.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/abbrev.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/touch.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/buckle/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/campfire/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/README.markdown 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire/message.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire/room.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/campfire/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/chela/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/chela/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/bin/chela 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/get-uid-gid.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/uid-number.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/chela/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/clean-exit/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/clean-exit/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/clean-exit/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/colors/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/ReadMe.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/colors.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/colors/themes/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/themes/winston-dark.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/colors/themes/winston-light.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/commander/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/commander/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/commander/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/commander/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/commander/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/lib/connect.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/lib/proto.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/bower.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/debug.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/connect/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/dialog/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/dialog/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/dialog/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/dialog/bin/dialog.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/dialog/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/dialog/msgbox.vbs 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/dialog/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/lib/gateway.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/lib/ssdp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/lib/utils.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/bin/needle 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/auth.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/decoder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/multipart.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/needle.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/parsers.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/querystring.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/Changelog.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/internal.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/streams.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/83.coffee 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/CONTRIBUTING.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/Config.xml 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/Depp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/att.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/canon.xml 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/incompat.coffee 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/incompat2.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/bom.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/processors.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/xml2js.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/AUTHORS 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/LICENSE-W3C.html 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/lib/sax.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLAttribute.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLBuilder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLCData.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLComment.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDAttList.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDElement.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDEntity.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDNotation.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDeclaration.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDocType.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLElement.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLNode.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLProcessingInstruction.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLRaw.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLStringifier.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLText.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/chunk.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/compact.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/difference.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/drop.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropRightWhile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropWhile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/fill.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/findIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/findLastIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/first.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/flatten.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/flattenDeep.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/head.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/indexOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/initial.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/intersection.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/last.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/lastIndexOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/object.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/pull.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/pullAt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/remove.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/rest.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/slice.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/sortedIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/sortedLastIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/tail.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/take.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeRightWhile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeWhile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/union.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/uniq.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/unique.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/unzip.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/without.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/xor.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/zip.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/zipObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/chain.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/commit.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/lodash.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/plant.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/reverse.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/run.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/tap.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/thru.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/toJSON.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/toString.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/value.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/valueOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperChain.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperCommit.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperPlant.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperReverse.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperToString.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperValue.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/all.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/any.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/at.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/collect.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/contains.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/countBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/detect.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/each.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/eachRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/every.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/filter.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/find.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/findLast.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/findWhere.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/foldl.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/foldr.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/forEach.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/forEachRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/groupBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/include.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/includes.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/indexBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/inject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/invoke.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/map.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/max.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/min.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/partition.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/pluck.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reduce.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reduceRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sample.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/select.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/shuffle.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/size.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/some.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sortBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sortByAll.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/where.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/date.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/date/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/date/now.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/after.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/ary.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/backflow.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/before.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bind.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bindAll.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bindKey.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/compose.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/curry.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/curryRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/debounce.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/defer.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/delay.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/flow.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/flowRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/memoize.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/negate.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/once.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/partial.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/partialRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/rearg.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/spread.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/throttle.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/wrap.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/LazyWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/LodashWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/MapCache.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/SetCache.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayCopy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEach.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEachRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEvery.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayFilter.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMap.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMax.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMin.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayReduce.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayReduceRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arraySome.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/assignDefaults.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/assignOwnDefaults.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseAssign.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseAt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseBindAll.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCallback.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseClone.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCompareAscending.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCopy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCreate.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseDelay.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseDifference.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEach.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEachRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEvery.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFill.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFilter.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFind.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFlatten.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFor.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForIn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForOwn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForOwnRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFunctions.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIndexOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseInvoke.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsEqual.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsEqualDeep.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsFunction.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsMatch.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseLodash.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMap.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMatches.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMatchesProperty.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMerge.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMergeDeep.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseProperty.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/basePullAt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseRandom.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseReduce.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSetData.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSlice.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSome.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSortBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseToString.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseUniq.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseValues.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseWrapperValue.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/binaryIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/binaryIndexBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/bindCallback.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/bufferClone.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/cacheIndexOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/cachePush.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charAtCallback.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charsLeftIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charsRightIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/compareAscending.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/compareMultipleAscending.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/composeArgs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/composeArgsRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createAggregator.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createAssigner.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createBindWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCache.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCompounder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCtorWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createExtremum.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createHybridWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createPad.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createPartialWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createWrapper.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/deburrLetter.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalArrays.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalByTag.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalObjects.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/escapeHtmlChar.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/escapeStringChar.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/extremumBy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/getData.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/getView.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/indexOfNaN.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneArray.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneByTag.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isBindable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isIterateeCall.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isLength.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isObjectLike.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isSpace.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isStrictComparable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyClone.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyReverse.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyValue.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapDelete.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapGet.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapHas.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapSet.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mergeData.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/metaMap.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/pickByArray.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/pickByCallback.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reEscape.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reEvaluate.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reInterpolate.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reorder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/replaceHolders.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/setData.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/shimIsPlainObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/shimKeys.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/sortedUniq.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/toIterable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/toObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/trimmedLeftIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/trimmedRightIndex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/unescapeHtmlChar.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/wrapperClone.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/clone.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/cloneDeep.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isArguments.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isArray.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isBoolean.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isDate.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isElement.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isEmpty.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isEqual.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isError.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isFinite.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isFunction.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isMatch.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNaN.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNative.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNull.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNumber.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isPlainObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isRegExp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isString.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isTypedArray.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isUndefined.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/toArray.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/toPlainObject.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number/inRange.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number/random.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/assign.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/create.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/defaults.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/extend.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/findKey.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/findLastKey.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forIn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forInRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forOwn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forOwnRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/functions.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/has.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/invert.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/keys.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/keysIn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/mapValues.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/merge.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/methods.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/omit.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/pairs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/pick.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/result.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/transform.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/values.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/valuesIn.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/camelCase.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/capitalize.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/deburr.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/endsWith.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/escape.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/escapeRegExp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/kebabCase.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/pad.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/padLeft.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/padRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/parseInt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/repeat.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/snakeCase.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/startCase.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/startsWith.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/template.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/templateSettings.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trim.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trimLeft.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trimRight.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trunc.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/unescape.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/words.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/support.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/attempt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/callback.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/constant.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/identity.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/iteratee.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/matches.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/matchesProperty.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/mixin.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/noop.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/property.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/propertyOf.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/range.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/times.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/uniqueId.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/text.coffee 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/text.xml 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/x.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/entry/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/firewall/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/darwin.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/win32.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/which.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/firewall/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/lib/html.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/lib/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/charset.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/encoding.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/language.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/mediaType.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/negotiator.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/public/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/folder.css 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/folder.html 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/ 0750 != 0755
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_3gp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_3gp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_7z.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_7z.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension__page.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension__page.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aac.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aac.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ace.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ace.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ai.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ai.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aif.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aif.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aiff.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aiff.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_amr.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_amr.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_avi.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_avi.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bat.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bat.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bin.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bin.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bmp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bmp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bup.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bup.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_c.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_c.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cab.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cab.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cbr.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cbr.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cda.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cda.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdl.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdl.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdr.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdr.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_chm.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_chm.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_code.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_code.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cpp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cpp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_css.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_css.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dat.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dat.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_divx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_divx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dll.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dll.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dmg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dmg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_doc.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_doc.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dotx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dotx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dss.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dss.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dvf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dvf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dwg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dwg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dxf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dxf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eml.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eml.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eps.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eps.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_exe.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_exe.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_fla.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_fla.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_flv.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_flv.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gif.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gif.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gz.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gz.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_h.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_h.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hpp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hpp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hqx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hqx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_htm.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_htm.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_html.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_html.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ics.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ics.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ifo.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ifo.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_indd.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_indd.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_iso.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_iso.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jar.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jar.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_java.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_java.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpeg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpeg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_js.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_js.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_key.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_key.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_less.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_less.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_lnk.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_lnk.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_log.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_log.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4a.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4a.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4b.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4b.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4p.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4p.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4v.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4v.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mcd.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mcd.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mdb.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mdb.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mid.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mid.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mov.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mov.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp2.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp2.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp3.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp3.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp4.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp4.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpeg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpeg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_msi.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_msi.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mswmm.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mswmm.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ods.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ods.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odt.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odt.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ogg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ogg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_otp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_otp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ots.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ots.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ott.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ott.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pdf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pdf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_php.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_php.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_png.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_png.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pps.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pps.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ppt.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ppt.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ps.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ps.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_psd.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_psd.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pst.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pst.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ptb.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ptb.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pub.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pub.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_py.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_py.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbb.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbb.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbw.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbw.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qt.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qt.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qxd.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qxd.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ram.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ram.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rar.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rar.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rb.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rb.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rm.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rm.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rmvb.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rmvb.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rtf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rtf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sass.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sass.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_scss.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_scss.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sea.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sea.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ses.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ses.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sh.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sh.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sit.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sit.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sitx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sitx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sql.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sql.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ss.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ss.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_svg.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_svg.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_swf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_swf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tga.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tga.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tgz.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tgz.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_thm.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_thm.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tif.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tif.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tiff.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tiff.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tmp.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tmp.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_torrent.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_torrent.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ttf.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ttf.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_txt.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_txt.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vcd.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vcd.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vob.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vob.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wav.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wav.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wma.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wma.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wmv.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wmv.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wps.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wps.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xls.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xls.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xlsx.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xlsx.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xml.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xml.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xpi.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xpi.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_yml.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_yml.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_zip.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_zip.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/folder.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/folder.png 0750
W: prey: image-file-in-usr-lib usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/page_white.png
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/page_white.png 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/folder/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/getset/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/foo 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/getset/lib/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/file.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/memory.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/utils/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/utils/parser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/lib/helpers.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/getset/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/fs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/graceful-fs.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/polyfills.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/bin/linus 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/os.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/whenever/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/whenever/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/whenever/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/linus/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/memorize/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/memorize/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/memorize/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/memorize/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/mime/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/mime.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/mime/types/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/types/mime.types 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/mime/types/node.types 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/debug.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/lib/debug.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/bin/needle 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/auth.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/cookies.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/decoder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/multipart.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/needle.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/parsers.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/lib/querystring.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/Changelog.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/internal.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/streams.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/needle/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/bin/network 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/lib/darwin.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/lib/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/lib/win32.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/bin/needle 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/auth.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/decoder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/multipart.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/needle.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/parsers.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/querystring.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/Changelog.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/internal.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/streams.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/network/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/src/addressparser.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/LICENSE.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/duplex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/float.patch 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_duplex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_passthrough.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_readable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_transform.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_writable.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/float.patch 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/lib/util.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/util.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/inherits.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/inherits_browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/build/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/build/build.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/passthrough.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/readable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/transform.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/writable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/duplex.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_duplex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_passthrough.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_readable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_transform.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_writable.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/float.patch 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/lib/util.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/util.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/inherits.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/inherits_browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/build/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/build/build.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/passthrough.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/readable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/transform.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/writable.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/LICENCE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/immutable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/mutable.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/through2.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/readme.markdown 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/lib/libbase64.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/lib/libqp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/src/buildmail.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/LICENCE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/LICENSE.APACHE2 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/LICENSE.MIT 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/readme.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/readme.markdown 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/Changelog.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/dbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/dbcs-data.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/internal.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-codec.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-data-generated.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-data.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/big5-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp936.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp949.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp950.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/eucjp.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/gbk-added.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/shiftjis.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/utf16.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/utf7.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/extend-node.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/streams.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/lib/libbase64.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/lib/libqp.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/charset.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/libmime.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/mimetypes.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/src/data-stream.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/src/smtp-connection.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/src/direct-transport.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/src/message-queue.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/services.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/Gruntfile.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/src/data-stream.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/src/smtp-connection.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/src/smtp-transport.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/nodemailer/src/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/src/compiler.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/nodemailer/src/nodemailer.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/ocelot/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/ocelot/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/ocelot/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/ocelot/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/ocelot/runner.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/ocelot/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/petit/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/petit/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/petit/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/petit/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/qs/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/CHANGELOG.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/CONTRIBUTING.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/qs/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/lib/parse.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/lib/stringify.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/lib/utils.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/qs/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/random-ua/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/scopes/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/scopes/scope_settings.xml 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/workspace.xml 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/random-ua/random_ua.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/remover/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/remover/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/remover/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/remover/bin/remover 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/remover/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/remover/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/reply/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/reply/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/reply/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/reply/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/bin.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/common.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/glob.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/inflight.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/wrappy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/inherits.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/inherits_browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/benchmark.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/minimatch.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/wrappy.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/once.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/sync.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/rimraf/rimraf.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/bin/satan 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/builder.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/helpers.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/systemd.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/sysvinit.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/upstart.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/distro.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/template.systemd 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/template.sysvinit 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/template.upstart 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/which.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/nssm.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/service.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/bin/linus 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/os.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/whenever/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/whenever/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/whenever/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/Readme.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/bin/minstache 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/lib/commander.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/satan/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/scrambler/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/scrambler/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/scrambler/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/scrambler/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/semver/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/semver/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/bin/semver 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/semver.browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/semver.browser.js.gz 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/semver.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/semver.min.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/semver/semver.min.js.gz 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/Makefile 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/bower.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/browser.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/component.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/debug.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/node.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/History.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/Readme.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/buffer-concat.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/callsite-tostring.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc1.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16_ccitt.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16_modbus.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc24.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc32.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc8.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc8_1wire.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/create.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/hex.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/build/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/build/build.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/build/test.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/cli.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/mime.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/types.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/HISTORY.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/serve-static/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/sudoer/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/sudoer/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/sudoer/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/sudoer/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/sudoer/lib/which.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/sudoer/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/sudoer/test.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/triggers/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/linux.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/mac.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/windows.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/triggers/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/tuna/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/tuna/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/tuna/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/tuna/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/underscore/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore-min.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore-min.map 0750
W: prey: embedded-javascript-library usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore.js
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/whenever/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/whenever/README.md 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/whenever/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/whenever/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/which/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/which/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/which/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/which/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/which/bin/which 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/which/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/which/which.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/wink/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/wink/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/wink/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/README.md 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/bin/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/bin/winssh 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/lib/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/lib/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/lib/utils.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/index.js 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/ 0750 != 0755
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/LICENSE 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/readme.markdown 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/README.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/readme.markdown 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/winssh/package.json 0750
W: prey: non-standard-dir-perm usr/lib/prey/versions/1.5.0/node_modules/wmic/ 0750 != 0755
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/wmic/index.js 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/node_modules/wmic/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/package.json 0750
W: prey: executable-is-not-world-readable usr/lib/prey/versions/1.5.0/prey.conf.default 0750
E: prey: executable-in-usr-share-doc usr/share/doc/prey/CHANGES.gz 0750
W: prey: executable-is-not-world-readable usr/share/doc/prey/CHANGES.gz 0750
E: prey: executable-in-usr-share-doc usr/share/doc/prey/changelog.Debian.gz 0750
W: prey: executable-is-not-world-readable usr/share/doc/prey/changelog.Debian.gz 0750
E: prey: executable-in-usr-share-doc usr/share/doc/prey/copyright 0750
W: prey: executable-is-not-world-readable usr/share/doc/prey/copyright 0750
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/runner.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/lib/system/utils/runner.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/buckle/bin/buckle #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/bin/decompress-zip #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/bin/nopt.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/bin/nopt.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/chela/bin/chela #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/dialog/bin/dialog.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/bin/needle #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/linus/bin/linus #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/needle/bin/needle #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/network/bin/network #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/bin/needle #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/ocelot/test.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/remover/bin/remover #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/rimraf/bin.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/satan/bin/satan #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/bin/linus #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/bin/minstache #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/semver/bin/semver #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/cli.js #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/which/bin/which #!node
W: prey: unusual-interpreter usr/lib/prey/versions/1.5.0/node_modules/winssh/bin/winssh #!node
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/sudoer/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16_ccitt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/files/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/extend-node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/templateSettings.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/memoize.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/os.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/filter.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/padRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/bus.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_psd.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFunctions.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/mimetypes.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trim.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_exe.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reorder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/plugin_manager.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapHas.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/escapeStringChar.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/upstart.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/readme.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/multipart.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/system/paths.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/readme.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mergeData.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/sortedIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMax.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/buffer-concat.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/sudoer/lib/which.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalByTag.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/wrappy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_chm.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/toPlainObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/keys.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sitx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_zip.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/passthrough.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/types/mime.types
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/types.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/default.options
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/groupBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/logger.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/composeArgs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/debounce.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/defaults.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/reply/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isArguments.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/readable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/utils/cp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/inherits_browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/unzip.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/lib/latlng.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/mutable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeWhile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperReverse.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pdf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCtorWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_js.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/wrapperClone.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_h.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/prey.conf.default
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/parseInt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/tuna/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapSet.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayReduceRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isArray.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rmvb.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdl.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperPlant.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDNotation.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/CONTRIBUTING.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/utils/pidfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/once.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/foldr.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/getData.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/prey_user.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/text.xml
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/random_ua.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/systemd.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/xml2js.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/src/smtp-connection.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text-shadow.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isFunction.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/win32.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/which/which.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/transform.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForOwn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeRightWhile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/internal.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/before.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/minimatch.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reInterpolate.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/foldl.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sortBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSome.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/MapCache.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpeg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/test_latlng.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gz.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDocType.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/cloneDeep.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseAt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/os.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/querystring.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/map.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rm.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/lib/darwin.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/functions.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/callsite-tostring.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/endsWith.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/findWhere.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/streams.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/flattenDeep.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_doc.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/cookies.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/benchmark/scenarios.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qt.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/utils/logo.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/remove.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/Changelog.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/system/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/perf/small.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/startsWith.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMatchesProperty.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/where.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/ReadMe.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMatches.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/prompt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/clean-exit/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/wmic/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/times.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/defer.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/tap.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire/room.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNative.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/sortedUniq.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/querystring.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/system/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp949.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseProperty.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseRandom.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/NodeRT_Windows_Devices_Geolocation.d.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/build/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/countBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp950.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/cachePush.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_key.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/filebrowser/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/siren.mp3
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/install.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/lib/libbase64.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/folder.html
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/mapValues.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/dbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/lib/nopt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/signup_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isEqual.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/identity.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/commander/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/lib/libbase64.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/wipe.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/Config.xml
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/incompat.coffee
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/Changelog.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/date.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/abbrev.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/incompat2.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_swf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/themes/winston-light.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/template.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLStringifier.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/whenever/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/after.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mdb.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/wmic/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/deburr.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/retry-failed-reports/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/scrambler/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCallback.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4p.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hpp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/src/message-queue.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bmp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/eucjp.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/startCase.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/ramcheck.vbs
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/inherits.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/request.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/network/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rb.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/takeRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isLength.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseDelay.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/common.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/findLastIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_html.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sample.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/olduser.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aif.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/curryRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_duplex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/text.coffee
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/snakeCase.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/bom.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/completer.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number/inRange.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/transports.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/inherits.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/build/build.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/src/buildmail.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/inject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/date/now.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/agent.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/memorize/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_3gp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/min.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/collect.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseToString.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLNode.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/valuesIn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/commander/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dll.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/drop.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mswmm.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc1.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/which/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/src/nodemailer.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/zip.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNull.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/passthrough.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ics.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/system/linux/paths.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayReduce.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/LICENCE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/attempt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseLodash.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/log.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/lib/sax.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/needle.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/camelCase.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cbr.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/binaryIndexBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/debug.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/pairs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/keys.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/ring.mp3
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/unique.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/colors.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/scopes/scope_settings.xml
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/bindCallback.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/max.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ots.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/indexOfNaN.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/once.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cdr.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isSpace.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/range.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/merge.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/duplex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isUndefined.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/distro.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayFilter.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xml.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/lib/win32.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperValue.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/getos/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4b.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/reports/load.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/setData.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/uid-number.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sh.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/build/build.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/eachRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-terminal/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbw.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/sudoer/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/tail.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/whenever/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/updater.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_passthrough.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arraySome.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/partition.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/cli.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalObjects.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/clone.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/head.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isElement.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEach.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperCommit.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_thm.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aac.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wav.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseAssign.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/shimIsPlainObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/AUTHORS
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/throttle.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc24.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForIn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-data-generated.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/shuffle.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/utils/run.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/needle.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/reverse.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/constant.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xpi.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bat.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_lnk.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/whenever/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/dialog/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/iteratee.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropRightWhile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bup.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vob.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/package.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_bin.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/linux/prey-config.glade
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/decoder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFill.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseValues.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cpp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMerge.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/build/build.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMap.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/themes/winston-dark.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/messages.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/dialog/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_svg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFlatten.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/pickByCallback.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rar.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/node_modules/wrappy/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/pull.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_divx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/commit.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/lib/vars.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dvf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore-min.map
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/files/finder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/tuna/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ifo.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sql.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/utils/operetta.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isIterateeCall.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_amr.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/glob.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/some.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_readable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/needle.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eps.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ram.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/petit/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/LICENSE
W: prey: executable-not-elf-or-script usr/share/doc/prey/CHANGES.gz
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/dialog/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/rearg.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qbb.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/whenever/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/forEachRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLBuilder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/auth.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/create.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/geofence/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/page_white.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/support.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/sync.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLText.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/polyfills.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/test/main_load.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/utils/run_synced.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_with_proxy_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/template.systemd
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isBindable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/readme.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/ary.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/utf7.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNumber.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/callback.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIndexOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/connection/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/pad.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/CONTRIBUTING.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/extend.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseBindAll.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mid.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLAttribute.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/propertyOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_vcd.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/LICENSE.APACHE2
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/indexOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/main.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/select.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/getView.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/streams.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/thru.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/hex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/LazyWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_hqx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/indexBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_scss.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/wrap.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/util.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pst.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc32.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/Changelog.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSortBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/services.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/compose.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/charset.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/parsers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reduce.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tga.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4v.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_passthrough.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/benchmark.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_less.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/composeArgsRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tmp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/querystring.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/lib/html.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/lib/processors.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/contains.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/readme.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/file.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jar.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/utils/parser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/get-uid-gid.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/push.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/daemon.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/panel.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/test/test_server.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/LICENSE-W3C.html
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_php.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/common.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/settings.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createPad.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/utf16.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/flowRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/invoke.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEvery.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isFinite.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/ocelot/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/lib/utils.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCompareAscending.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc16_modbus.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/number/random.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/async/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/package.json
W: prey: executable-not-elf-or-script usr/share/doc/prey/changelog.Debian.gz
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/dropWhile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/sortByAll.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/hooks.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_py.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/foo
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/invert.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/includes.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/findKey.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseMergeDeep.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_rtf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/CONTRIBUTING.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/reports-to-inbox/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/multipart.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/helpers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/backends/sysvinit.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/zipObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/take.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tgz.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_transform.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ptb.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/modem.mp3
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/float.patch
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libbase64/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperToString.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dss.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/chain.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/download-test-assets.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/unescapeHtmlChar.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pub.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/partialRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/escapeRegExp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_qxd.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/matchesProperty.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/immutable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/tuna/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wmv.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/lib/ssdp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bindAll.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseDifference.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/bufferClone.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isPlainObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/log.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/petit/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dmg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/sender.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/petit/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/charset.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/lib/libqp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMin.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseForOwnRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_odt.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/remover/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dotx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/fresh/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/file-details.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mcd.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/xor.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/launchd/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/lock/lib/bg-lock.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/valueOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/strategies.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forInRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/curry.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/version_manager.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/remote-desktop/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/capitalize.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/gb18030-ranges.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/sortedLastIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/connect.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsEqualDeep.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/accounts.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/semver.min.js.gz
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/debug.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_aiff.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createHybridWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/remover/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/LICENSE.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/async/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xls.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/cacheIndexOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/secure.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/value.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wps.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_fla.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/lib/compat/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/findIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/semver.browser.js.gz
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ss.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore-min.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cda.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/screenshot/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEachRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/types/node.types
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/ocelot/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/all.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLRaw.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/basePullAt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isEmpty.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/lib/util.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ttf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/x64/NodeRT_Windows_Devices_Geolocation.node
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc8.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reEscape.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/lodash.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reduceRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/union.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/device_link_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/create.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isTypedArray.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/cp936.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_7z.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_java.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/memorize/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/include.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/lib/parse.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ps.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/which/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dwg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_iso.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/sax/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/repeat.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/each.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/buffers/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugin.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/big5-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/long-polling/test/index_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/commander/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey.ico
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/at.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createAggregator.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/auth.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_eml.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/commands.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isBoolean.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/transform.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/negate.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/inherits/inherits_browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/size.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/att.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/sudoer/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dxf.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/assign.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/LICENCE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/parser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/libqp/lib/libqp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/LICENSE.MIT
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/string_decoder/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/uniqueId.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/node_modules/ee-first/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/src/direct-transport.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/graceful-fs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/pickByArray.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/toArray.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_log.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/commander/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/rest.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alert/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/concat-map/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/batch/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/lib/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSlice.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/run.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/check.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseInvoke.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/scrambler/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCache.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/decoder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_writable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/devices.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_m4a.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/queue.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/bower.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/parsers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFor.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/through2.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/noop.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mpg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/through/readme.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/reports/specs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isObjectLike.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/partial.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/shimKeys.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/bower.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/underscore.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/os/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/parseurl/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/nssm.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/has.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/internal.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ott.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/remover/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/kebabCase.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bind.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/findLastKey.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/lib/darwin.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/dbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/lib/crc8_1wire.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_xlsx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/result.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/signatures.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/memorize/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDAttList.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_transform.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_txt.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/graceful-fs/graceful-fs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/unescape.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/Changelog.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/wrappy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/node_modules/keypress/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/mkpath.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/trimmedLeftIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/plugins.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/pick.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/wink/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/src/smtp-connection.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/compareAscending.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/canon.xml
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charsRightIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/every.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/metaMap.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inherits/inherits_browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/assignOwnDefaults.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFilter.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/without.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/pluck.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_c.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ses.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/async/lib/async.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/rimraf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/triggers/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/async/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tiff.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/transports/http/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/connections/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/win32/service.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/intersection.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isRegExp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_torrent.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseFind.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/debug/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/ms/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp4.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/gbk-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/keysIn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/processors.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/escape.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/matches.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyReverse.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/forEach.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapGet.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_jpeg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/parseurl/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/hardware/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isMatch.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/flow.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_wma.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/fill.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/test/setup.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_indd.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/mixin.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/setup.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/template.upstart
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_gif.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/wink/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createCompounder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/polyfills.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/83.coffee
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/clean-exit/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/network/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createBindWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/folder.css
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charsLeftIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-agent-48.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/reject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sass.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_png.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/utf16.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneByTag.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trimLeft.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_htm.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/structures.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp2.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_dat.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/mime.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/sbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/lib/utils.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsEqual.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_readable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/omit.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/object.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/find.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_yml.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createAssigner.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/inherits.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseReduce.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEach.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/scrambler/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/compact.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_flv.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/wipe/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/depd/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/reports-to-inbox/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_css.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayEachRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_pps.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/CONTRIBUTING.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/node_modules/balanced-match/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/language.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/isarray/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/builder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-codec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/nodemailer-wellknown/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/findLast.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/folder.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/email.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/whenever/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/CHANGELOG.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_otp.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/nopt/node_modules/abbrev/abbrev.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/node_modules/traverse/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseUniq.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isString.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/q.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/hyperquest/node_modules/duplexer/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_code.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/wifi.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLComment.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forIn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/network/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/lib/connect.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isDate.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/words.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/src/smtp-transport.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/lib/_stream_duplex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trimRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/account.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/escape-html/Makefile
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/retry-failed-reports/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/toIterable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/delay.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/test/trigger_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/settings.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ace.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/graceful-fs/fs.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/utils-merge/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/any.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/minimist/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/wrapperChain.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/replaceHolders.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_avi.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/last.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/node_modules/wrappy/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mov.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/bin/ia32/NodeRT_Windows_Devices_Geolocation.node
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/bin/touch.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/async/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/uniq.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/memorize/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/src/addressparser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/campfire/test/plugin_test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayMap.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/.idea/workspace.xml
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseClone.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/destroy/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/inherits/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/inflight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/range-parser/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/lib/stringify.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/src/libmime.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/node_modules/ms/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/lib/debug.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/writable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/internal.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/padLeft.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/compareMultipleAscending.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/core-util-is/float.patch
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/lib/helpers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/src/compiler.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/x.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isNaN.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyClone.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseEvery.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/cli.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/mime.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ppt.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forOwnRight.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/utils-merge/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/touch.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/dialog/msgbox.vbs
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/node_modules/uid-number/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/arrayCopy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/string_decoder/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/collection/detect.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/shiftjis.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sea.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_mp3.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/webcam/linux/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/node_modules/chainsaw/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/mime/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/slice.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/streams.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/assignDefaults.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/linus/node_modules/whenever/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/decompress-zip.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/bandwidth/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/common.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/mediaType.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/reports/status.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/extremumBy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/lib/campfire/message.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDeclaration.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/memorize/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/shiftjis.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/lib/commander.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/controlpanel.bmp
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/shared/keys.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/system.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/system/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/writable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/winssh/node_modules/optimist/node_modules/wordwrap/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/reply/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/tasks/os/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/semver.browser.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/sbcs-data-generated.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp936.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/difference.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/semver.min.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/backflow.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/lib/alarm.mp3
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseSetData.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/semver/semver.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/ocelot/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/lastIndexOf.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/random-ua/LICENSE
W: prey: executable-not-elf-or-script usr/share/doc/prey/copyright
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/chunk.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/request_without_proxy_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsMatch.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/deburrLetter.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/triggers/power/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/on-finished/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libbase64/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/values.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension__page.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/node_modules/crc/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/toObject.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/node_modules/abbrev/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/lib/auth.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createExtremum.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/transports/smtp/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCopy.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/versions.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/pullAt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/methods.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/inflight/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/getos/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/dbcs-data.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_asx.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/initial.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/processes/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/debug/History.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/util.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/lib/utils.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDEntity.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/charAtCallback.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/lib/gateway.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/lib/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/LodashWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/lang/isError.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/utils/storage.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/equalArrays.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/lib/_stream_writable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/firewall/node_modules/spawnx/which.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/once/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/prey-text.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLCData.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_sit.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/lib/extend-node.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_msi.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/delay.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/forOwn.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ai.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/SetCache.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/indicators/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/utility/property.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/Depp.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/lib/proto.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/minstache/node_modules/commander/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp949.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/xtend/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nat-pmp/node_modules/debug/debug.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/bindKey.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/encodings/utf7.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/underscore/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/first.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/license.txt
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/cp950.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-smtp-transport/node_modules/smtp-connection/src/data-stream.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/array/flatten.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/user.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/etag/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/console/help.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/duplex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/actions/alarm/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/node_modules/isarray/component.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/binary/perf/loop.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/errors.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_tif.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/lib/extractors.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/lazyValue.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/lib/util.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/nodemailer-direct-transport/node_modules/smtp-connection/src/data-stream.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/node_modules/core-util-is/float.patch
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/decoder.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseCreate.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/exceptions.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/chela/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/reports.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/reports/stolen.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/libqp/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/campfire/README.markdown
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLProcessingInstruction.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/node_modules/iconv-lite/lib/streams.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/isStrictComparable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/node_modules/ee-first/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/needle/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/control-panel/api/test/authorize_spec.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/pixmaps/conf/newuser.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/internal.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLElement.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/colors/test.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/mkpath/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/lib/parsers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/Gruntfile.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/encoding.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/reEvaluate.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/plugins.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/encodings/tables/big5-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ods.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/node_modules/negotiator/lib/negotiator.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/needle/node_modules/iconv-lite/encodings/tables/eucjp.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/through2/node_modules/readable-stream/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/send/node_modules/mime/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/network/mac.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/getset/lib/backends/memory.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/triggers/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/serve-static/node_modules/escape-html/Readme.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/whenever/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/CONTRIBUTING.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/geo/win32/windows.devices.geolocation/lib/NodeRT_Windows_Devices_Geolocation.d.ts
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/plugins/url-trigger/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/toJSON.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_ogg.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/qs/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/escapeHtmlChar.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseWrapperValue.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/toString.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/lib/XMLDTDElement.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/sudoer/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/q/benchmark/compare-with-callbacks.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/addressparser/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/node_modules/linus/node_modules/whenever/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/lan/windows.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/folder/public/mime/file_extension_cab.png
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/satan/lib/linux/which.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/helpers.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/buckle/node_modules/decompress-zip/node_modules/touch/node_modules/nopt/lib/nopt.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/baseIsFunction.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/connect/node_modules/finalhandler/node_modules/on-finished/HISTORY.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/createPartialWrapper.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/function/spread.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/rimraf/node_modules/glob/node_modules/minimatch/node_modules/brace-expansion/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/mapDelete.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/buildmail/node_modules/hyperquest/node_modules/duplexer2/node_modules/readable-stream/readable.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/which/README.md
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/conf/gui/index.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/lib/agent/providers/network/linux.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/object/transform.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/initCloneArray.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/node_modules/iconv-lite/LICENSE
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/reply/package.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/nodemailer/node_modules/libmime/node_modules/iconv-lite/encodings/tables/gbk-added.json
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/chain/plant.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/network/node_modules/needle/lib/multipart.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/trimmedRightIndex.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/string/trunc.js
W: prey: executable-not-elf-or-script usr/lib/prey/versions/1.5.0/node_modules/entry/node_modules/xml2js/node_modules/xmlbuilder/node_modules/lodash/internal/binaryIndex.js
W: prey: possibly-insecure-handling-of-tmp-files-in-maintainer-script postinst:15


Lintian finished with exit status 1
```

Is that everything that's needed?

Thanks for any help.

---

### Post by Frogs Hair on 2016-04-28
Are you running 32 bit or 64 ? If 64 that package won't work. If dual booting you can install from Windows. The 64 bit package Prey for Linux would have to be compiled 

 ```
uname -a
``` If you see x86_64 in the output you have 64 bit

---

### Post by alex517 on 2016-04-28
Thanks. I don't know how to run that command, but my Kernel version says x86_64. I'm not dual booting either.

If I can't run Prey, is there anything similar for Linux that's easy to install and use?

---

### Post by Dennis N on 2016-04-28
> **alex517 said:**
> Thanks. I don't know how to run that command, but my Kernel version says x86_64. I'm not dual booting either.

If I can't run Prey, is there anything similar for Linux that's easy to install and use?

You can run 32-bit applications on 64-bit Ubuntu -- I run 32-bit games on my 64-bit Xubuntu. You just need to install the necessary 32-bit libraries. First, enable installation of 32-bit packages:

[FONT=Courier New]sudo dpkg --add-architecture i386[/FONT]

I followed the suggestions for Ubuntu 13.04 and later in the following link, and installed all their suggested packages:

[https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system](https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system)

I installed mine with Synaptic, because it is easy to filter for 32-bit packages with the "architecture" button on the left. All of them end with :i386

If those are not enough to get the program going, there are ways to find what other packages are needed from the error messages when you try to start them from the terminal.

---

### Post by RobGoss on 2016-04-28
Hello and welcome, You might be able to download Prey from the Ubuntu Center as stated from this page
[https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu](https://preyproject.com/blog/2011/04/its-official-prey-is-now-on-ubuntu)

I never use this app so I don't much about it good luck, Oh and I did check to see if it was available and it was

---

### Post by Dennis N on 2016-04-28
Yes, its in the repositories and that is the best way to install it. The same package for both 32-bit and 64-bit OS:

[http://packages.ubuntu.com/trusty/prey](http://packages.ubuntu.com/trusty/prey)

Good luck.

---

### Post by alex517 on 2016-04-28
> **Dennis N said:**
> You can run 32-bit applications on 64-bit Ubuntu -- I run 32-bit games on my 64-bit Xubuntu. You just need to install the necessary 32-bit libraries. First, enable installation of 32-bit packages:

[FONT=Courier New]sudo dpkg --add-architecture i386[/FONT]

I followed the suggestions for Ubuntu 13.04 and later in the following link, and installed all their suggested packages:

[https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system](https://support.humblebundle.com/hc/en-us/articles/202759400-Installing-32-bit-libs-on-a-64-bit-Linux-system)

I installed mine with Synaptic, because it is easy to filter for 32-bit packages with the "architecture" button on the left. All of them end with :i386

If those are not enough to get the program going, there are ways to find what other packages are needed from the error messages when you try to start them from the terminal.


> **Dennis N said:**
> Yes, its in the repositories and that is the best way to install it. The same package for both 32-bit and 64-bit OS:

[http://packages.ubuntu.com/trusty/prey](http://packages.ubuntu.com/trusty/prey)

Good luck.

Thanks - I've managed to install it using Synaptic, but how do I open the software? It's not in any of the software menus, but it's listed as installed in Synaptic.

And if I try the "Installing 32-bit libs on a 64-bit Linux system" link, at step 1 I get:
E: Unable to locate package ia320libs

---

### Post by Dennis N on 2016-04-28
> **alex517 said:**
> Thanks - I've managed to install it using Synaptic, but how do I open the software? It's not in any of the software menus, but it's listed as installed in Synaptic.

And if I try the "Installing 32-bit libs on a 64-bit Linux system" link, at step 1 I get:
E: Unable to locate package ia320libs

ia32-libs is in the section about 12.04. ia32-libs is no longer available. The part that should be followed would be the part just below that that refers to Ubuntu 13.04 (and later). But none of that post is relevant now, unless you plan to install some 32-bit software that is NOT in the Ubuntu repositories. 

Since you are Using Ubuntu, search for "Prey" in the Dash and I think it should find it. Start it from the icon that shows up in the Dash.

---

### Post by Dennis N on 2016-04-28
Did you see the information here on how to use it? You need to set up an account, if you haven't. That may be where you configure it. Otherwise, it just runs in the background on your device, I think, probably autostarts when you start the device. waiting to hear from headquarters to take a photo or do the other things it does.

[http://help.preyproject.com/article/185-overview-what-is-prey](http://help.preyproject.com/article/185-overview-what-is-prey)

---

### Post by alex517 on 2016-05-12
> **Dennis N said:**
> ia32-libs is in the section about 12.04. ia32-libs is no longer available. The part that should be followed would be the part just below that that refers to Ubuntu 13.04 (and later). But none of that post is relevant now, unless you plan to install some 32-bit software that is NOT in the Ubuntu repositories. 

Since you are Using Ubuntu, search for "Prey" in the Dash and I think it should find it. Start it from the icon that shows up in the Dash.

Is that the Software Center? It doesn't appear when I search there.

> **Dennis N said:**
> Did you see the information here on how to use it? You need to set up an account, if you haven't. That may be where you configure it. Otherwise, it just runs in the background on your device, I think, probably autostarts when you start the device. waiting to hear from headquarters to take a photo or do the other things it does.

[http://help.preyproject.com/article/185-overview-what-is-prey](http://help.preyproject.com/article/185-overview-what-is-prey)

I have an account, but it doesn't detect Prey on my device. If I try and install the Linux version from [https://panel.preyproject.com/devices](https://panel.preyproject.com/devices) when I'm logged in, I get an error message saying that an older version was found on a software channel, and it's best to use this as it's more likely to be supported for my device.

---

