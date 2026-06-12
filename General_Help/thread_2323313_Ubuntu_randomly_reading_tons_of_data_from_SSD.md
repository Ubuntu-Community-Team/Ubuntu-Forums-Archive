---
title: "Ubuntu randomly reading tons of data from SSD"
date: 2016-05-04
forum: General Help
---

### Post by Only1KW on 2016-05-04
Before about 1-2 months ago, for about 6 months, I had an installation of Ubuntu 14.04 running on my desktop without any issues and without needing to reboot.  I was regularly performing upgrades, but not dist-upgrades.  At the end of that 6 months, I performed a dist-upgrade and rebooted.  Since that time, I've barely kept my system up and running for more than a week before it required another reboot (hence the reason I go so long between dist-upgrades if everything seems to be working correctly).

This issue is that, whenever I perform some random, minor action on my system, all of the sudden I will see hundreds of MB (over 500 MB sometimes) of data being read from my SSD every second.  This triggers a slowdown on my system so bad that my mouse cursor slows down noticeably as I move it.  The action can be as simple as opening some simple webpage in a new tab in Chrome.  There isn't some single application that is doing all the reading either.  If I run iotop, I see almost 150 tasks that are reading from the drive, compared to one or two when I'm not seeing this issue, and there isn't one task that sticks out as reading way more data than the rest.  

If I had to guess from the data, it looks like a swap storm is occurring on my system.  This theory is strengthened by the fact that kswapd0 is one of the tasks running.  However, the problem is that, as you can see from my "top" output below, I don't have any swap configured.  I've tried googling this situation and found a few hits, but no one has a good guess on what is actually happening other than there is a kernel bug.  Every time I reboot, I've been performing another dist-upgrade, so if it is a kernel bug, it doesn't seem to have been fixed yet.  A reboot does seem to make the problem go away for a few days, but eventually it comes back and I need to reboot again to make any progress.

Any ideas what may be going wrong, and/or what I can do to mitigate this without a fresh installation?

iotop output snapshot:
```

09:49:13 Total DISK READ :     356.78 M/s | Total DISK WRITE :     539.57 K/s
09:49:13 Actual DISK READ:      79.05 M/s | Actual DISK WRITE:      33.03 K/s
    TIME  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
09:49:13  6654 be/4 username    9.44 M/s    0.00 B/s  0.00 % 91.69 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.81.282110345 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 11921 be/4 username   10.69 M/s    0.00 B/s  0.00 % 91.13 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.27.1206405469 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  6809 be/4 root       12.15 M/s    0.00 B/s  0.00 % 89.61 % python /usr/sbin/iotop -bot --iter=1
09:49:13 13367 be/4 username   32.75 M/s    0.00 B/s  0.00 % 88.14 % plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 32214 true plugin
09:49:13  6753 be/4 username   10.45 M/s    0.00 B/s  0.00 % 86.18 % python3 ./scripts/HwEtmDecoder.py -t hwtraces -b build/product/fpga -o hwtraces
09:49:13  2733 be/4 username   10.15 M/s    0.00 B/s  0.00 % 82.39 % xfce4-orageclock-plugin  3 18874417 xfce4-orageclock-plugin Orage Panel Clock Show time and date?
09:49:13 13159 be/4 username   12.19 M/s    0.00 B/s  0.00 % 81.92 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 31873 be/4 username   23.06 M/s    0.00 B/s  0.00 % 80.92 % chrome --window-depth=24
09:49:13  2858 be/1 username    9.64 M/s    0.00 B/s  0.00 % 80.87 % pulseaudio --start --log-target=syslog [alsa-sink-ALC28]
09:49:13  2869 be/4 username   10.34 M/s    0.00 B/s  0.00 % 80.74 % gnome-terminal
09:49:13 32214 be/4 username    9.03 M/s    0.00 B/s  0.00 % 80.39 % firefox --new-window company-pilot.slack.com
09:49:13 11923 be/4 username   10.44 M/s    0.00 B/s  0.00 % 80.36 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.27.1206405469 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [Compositor]
09:49:13  6667 be/4 username   11.73 M/s    0.00 B/s  0.00 % 67.45 % chrome --window-depth=24 [threaded-ml]
09:49:13  2136 be/4 username   38.76 M/s    0.00 B/s  0.00 % 61.69 % cli /usr/lib/keepass2/KeePass.exe
09:49:13 31933 be/4 username   20.81 M/s    0.00 B/s  0.00 % 60.80 % chrome --type=gpu-process --channel=31873.0.614754111 --window-depth=24 --supports-dual-gpus=false --gpu-driver-bug-workarounds=4,5,19,21,26,34,49,53 --disable-accelerated-video-decode --gpu-vendor-id=0x1002 --gpu-device-id=0x6749 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.3 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  6677 be/4 username    8.03 M/s    0.00 B/s  0.00 % 60.19 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.81.282110345 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [AudioOutputDevi]
09:49:13 16905 be/4 username   20.38 M/s    0.00 B/s  0.00 % 52.57 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  2332 be/4 root       26.22 M/s    0.00 B/s  0.00 % 51.69 % nmbd -D
09:49:13 11955 be/4 username    5.03 M/s    0.00 B/s  0.00 % 50.11 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.29.285707354 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  6652 be/4 username    4.60 M/s    0.00 B/s  0.00 % 34.36 % multi -sr_connect_servicerouter_port 36204
09:49:13   668 be/4 username    3.00 M/s    0.00 B/s  0.00 % 31.79 % mstart -multi
09:49:13 31937 be/4 username    4.11 M/s    0.00 B/s  0.00 % 28.14 % --extension-process --enable-webrtc-hw-h264-encoding --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.1.1704487562 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  1654 be/4 root        4.36 M/s    0.00 B/s  0.00 % 26.19 % X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
09:49:13 16923 be/4 username   15.38 M/s  138.75 K/s  0.00 % 24.65 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  7141 be/4 username    2.16 M/s    0.00 B/s  0.00 % 22.28 % helpview -sr_connect_servicerouter_port 49637
09:49:13 32267 be/4 username    5.98 M/s    0.00 B/s  0.00 % 21.96 % firefox --new-window company-pilot.slack.com [SoftwareVsyncTh]
09:49:13  6653 be/4 username    2.33 M/s    0.00 B/s  0.00 % 19.92 % mpserv ghprobe32839.company.com -sr_client_start_cookie 39 -sr_connect_servicerouter_host 127.0.0.1 -sr_connect_servicerouter_port 42303
09:49:13   106 be/4 root        0.00 B/s  323.74 K/s  0.00 % 16.48 % [kswapd0]
09:49:13  2845 be/1 username    2.55 M/s    0.00 B/s  0.00 % 15.38 % pulseaudio --start --log-target=syslog
09:49:13 32398 be/4 username    2.46 M/s    0.00 B/s  0.00 % 14.80 % firefox --new-window company-pilot.slack.com [DOM Worker]
09:49:13 11839 be/4 username 1336.81 K/s    0.00 B/s  0.00 % 12.85 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.24.1860846613 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13   707 be/4 username  949.20 K/s    0.00 B/s  0.00 %  7.83 % svc_router -connect_servicerouter 40015
09:49:13 27098 be/4 username  757.60 K/s    0.00 B/s  0.00 %  5.50 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 32248 be/4 username  920.57 K/s    0.00 B/s  0.00 %  5.21 % firefox --new-window company-pilot.slack.com [Timer]
09:49:13  3828 be/4 username  121.13 K/s    0.00 B/s  0.00 %  5.16 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.76.398253299 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  6729 be/4 username  125.53 K/s    0.00 B/s  0.00 %  5.15 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.82.1329553586 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 14697 be/4 username  171.78 K/s    0.00 B/s  0.00 %  5.15 % --instant-process --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.48.1718531021 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 31915 be/4 username  777.42 K/s    0.00 B/s  0.00 %  4.22 % chrome --window-depth=24 [CompositorTileW]
09:49:13 31912 be/4 username  561.59 K/s    0.00 B/s  0.00 %  4.21 % chrome --window-depth=24 [Chrome_IOThread]
09:49:13 27274 be/4 username  588.02 K/s    0.00 B/s  0.00 %  4.13 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 27276 be/4 username  473.50 K/s    0.00 B/s  0.00 %  2.83 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13   715 be/4 username  596.83 K/s    0.00 B/s  0.00 %  2.59 % svc_statemgr -sr_connect_servicerouter_port 34853
09:49:13 27094 be/4 username  319.34 K/s    0.00 B/s  0.00 %  2.54 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 27272 be/4 username  251.06 K/s    0.00 B/s  0.00 %  2.37 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  2670 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.29 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 23235 be/4 username   22.02 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 11545 be/4 username   81.49 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28499 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  7391 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24604 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 22756 be/4 username   30.83 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28957 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24645 be/4 username   37.44 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 17343 be/4 username   33.03 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  3177 be/4 username   26.43 K/s    0.00 B/s  0.00 %  2.28 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24124 be/4 username   92.50 K/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  7374 be/4 username   26.43 K/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 13773 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 20062 be/4 username   15.42 K/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  3045 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 23280 be/4 username   33.03 K/s    0.00 B/s  0.00 %  2.27 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 32240 be/4 username  436.06 K/s    0.00 B/s  0.00 %  2.27 % firefox --new-window company-pilot.slack.com [JS Watchdog]
09:49:13 16768 be/4 username  107.91 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 23466 be/4 username    8.81 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 20075 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28965 be/4 username   19.82 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 22996 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28963 be/4 username   15.42 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 12649 be/4 username   79.28 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24211 be/4 username   19.82 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24412 be/4 username   59.46 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 12648 be/4 username   33.03 K/s    0.00 B/s  0.00 %  2.26 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28501 be/4 username   44.05 K/s    0.00 B/s  0.00 %  2.25 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 25851 be/4 username   52.86 K/s    0.00 B/s  0.00 %  2.25 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 11730 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.23 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 23815 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.22 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 11779 be/4 username   15.42 K/s    0.00 B/s  0.00 %  2.22 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 13498 be/4 username   50.65 K/s    0.00 B/s  0.00 %  2.22 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 25016 be/4 username  143.15 K/s    0.00 B/s  0.00 %  2.22 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 15371 be/4 username   19.82 K/s    0.00 B/s  0.00 %  2.18 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28457 be/4 username   83.69 K/s    0.00 B/s  0.00 %  2.16 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 11840 be/4 username  429.45 K/s    0.00 B/s  0.00 %  2.16 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.24.1860846613 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [Chrome_ChildIOT]
09:49:13 13767 be/4 username   13.21 K/s    0.00 B/s  0.00 %  2.15 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  7951 be/4 username  134.34 K/s    0.00 B/s  0.00 %  2.15 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 12629 be/4 username   24.23 K/s    0.00 B/s  0.00 %  2.15 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24112 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.15 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 16521 be/4 username   70.47 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 12641 be/4 username   63.87 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 20248 be/4 username   83.69 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 25856 be/4 username   39.64 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 25841 be/4 username    2.20 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 11619 be/4 username   68.27 K/s    0.00 B/s  0.00 %  2.14 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28469 be/4 username   83.69 K/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 23948 be/4 username   35.24 K/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 28468 be/4 username   92.50 K/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 25860 be/4 username   11.01 K/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13  3258 be/4 username    0.00 B/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 24107 be/4 username  140.95 K/s    0.00 B/s  0.00 %  2.13 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 27096 be/4 username  118.93 K/s    0.00 B/s  0.00 %  2.12 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 26952 be/4 username  145.35 K/s    0.00 B/s  0.00 %  2.10 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 31959 be/4 username  735.58 K/s    0.00 B/s  0.00 %  1.97 % chrome --type=gpu-process --channel=31873.0.614754111 --window-depth=24 --supports-dual-gpus=false --gpu-driver-bug-workarounds=4,5,19,21,26,34,49,53 --disable-accelerated-video-decode --gpu-vendor-id=0x1002 --gpu-device-id=0x6749 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.3 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [Chrome_ChildIOT]
09:49:13  1247 be/4 root     1770.67 K/s    0.00 B/s  0.00 %  1.20 % NetworkManager [gmain]
09:49:13  3101 be/4 username 1931.44 K/s    0.00 B/s  0.00 %  1.16 % zeitgeist-fts [gmain]
09:49:13 11922 be/4 username  290.71 K/s    0.00 B/s  0.00 %  1.00 % --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --channel=31873.27.1206405469 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [Chrome_ChildIOT]
09:49:13  2401 be/4 ntp        61.67 K/s    0.00 B/s  0.00 %  0.66 % ntpd -p /var/run/ntpd.pid -g -u 117:125
09:49:13  2145 be/4 username   77.08 K/s    0.00 B/s  0.00 %  0.56 % cli /usr/lib/keepass2/KeePass.exe
09:49:13 27097 be/4 username    6.61 K/s    0.00 B/s  0.00 %  0.56 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 27095 be/4 username   85.89 K/s    0.00 B/s  0.00 %  0.56 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 27093 be/4 username   81.49 K/s    0.00 B/s  0.00 %  0.56 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13  3947 be/4 username   85.89 K/s    0.00 B/s  0.00 %  0.54 % cli /usr/lib/keepass2/KeePass.exe
09:49:13  2148 be/4 username  198.21 K/s    0.00 B/s  0.00 %  0.52 % cli /usr/lib/keepass2/KeePass.exe
09:49:13  2147 be/4 username  145.35 K/s    0.00 B/s  0.00 %  0.51 % cli /usr/lib/keepass2/KeePass.exe
09:49:13  3033 be/4 username  162.97 K/s    0.00 B/s  0.00 %  0.50 % gnome-terminal [gmain]
09:49:13  2825 be/4 username  405.23 K/s    0.00 B/s  0.00 %  0.49 % zeitgeist-datahub [gmain]
09:49:13  2900 be/4 username  244.46 K/s    0.00 B/s  0.00 %  0.49 % indicator-messages-service [gmain]
09:49:13 16926 be/4 username  169.58 K/s    0.00 B/s  0.00 %  0.45 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13 16935 be/4 username  116.72 K/s    0.00 B/s  0.00 %  0.44 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar [gmain]
09:49:13  6682 be/4 username  784.03 K/s    0.00 B/s  0.00 %  0.42 % svc_python -sr_connect_servicerouter_port 55759
09:49:13  2150 be/4 username    4.40 K/s    0.00 B/s  0.00 %  0.40 % cli /usr/lib/keepass2/KeePass.exe
09:49:13  2151 be/4 username    4.40 K/s    0.00 B/s  0.00 %  0.39 % cli /usr/lib/keepass2/KeePass.exe
09:49:13 13399 be/4 username  118.93 K/s    0.00 B/s  0.00 %  0.39 % plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 32214 true plugin
09:49:13 13400 be/4 username   48.45 K/s    0.00 B/s  0.00 %  0.38 % plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 32214 true plugin
09:49:13 16916 be/4 username  114.52 K/s    0.00 B/s  0.00 %  0.22 % java -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar -os linux -ws gtk -arch x86_64 -showsplash /usr/lib/eclipse//plugins/org.eclipse.platform_3.8.1.dist/splash.bmp -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist/eclipse_1503.so -startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar --launcher.overrideVmargs -exitdata 300006 -vm /usr/bin/java -vmargs -Xms40m -Xmx384m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
09:49:13   249 be/3 root        0.00 B/s   70.47 K/s  0.00 %  0.16 % [jbd2/sda5-8]
09:49:13 13160 be/4 username   11.01 K/s    0.00 B/s  0.00 %  0.08 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd [Chrome_ChildIOT]
09:49:13 32234 be/4 username   13.21 K/s    0.00 B/s  0.00 %  0.06 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 27275 be/4 username    0.00 B/s    0.00 B/s  0.00 %  0.06 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 32230 be/4 username   13.21 K/s    0.00 B/s  0.00 %  0.06 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 27271 be/4 username    8.81 K/s    0.00 B/s  0.00 %  0.06 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 27273 be/4 username    0.00 B/s    0.00 B/s  0.00 %  0.06 % chrome --type=ppapi --channel=31873.30.1950151072 --ppapi-flash-args --lang=en-US --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 13403 be/4 username   35.24 K/s    0.00 B/s  0.00 %  0.04 % plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 32214 true plugin
09:49:13 13404 be/4 username   15.42 K/s    0.00 B/s  0.00 %  0.04 % plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 32214 true plugin
09:49:13 32232 be/4 username   13.21 K/s    0.00 B/s  0.00 %  0.04 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 32226 be/4 username    6.61 K/s    0.00 B/s  0.00 %  0.03 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 32233 be/4 username    4.40 K/s    0.00 B/s  0.00 %  0.02 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 32225 be/4 username    4.40 K/s    0.00 B/s  0.00 %  0.02 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13  1810 be/4 rtkit      33.03 K/s    0.00 B/s  0.00 %  0.02 % rtkit-daemon
09:49:13 32228 be/4 username    2.20 K/s    0.00 B/s  0.00 %  0.02 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 32238 be/4 username    2.20 K/s    0.00 B/s  0.00 %  0.02 % firefox --new-window company-pilot.slack.com [JS Helper]
09:49:13 31948 be/4 username    2.20 K/s    0.00 B/s  0.00 %  0.01 % chrome --type=gpu-process --channel=31873.0.614754111 --window-depth=24 --supports-dual-gpus=false --gpu-driver-bug-workarounds=4,5,19,21,26,34,49,53 --disable-accelerated-video-decode --gpu-vendor-id=0x1002 --gpu-device-id=0x6749 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.3 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
09:49:13 32231 be/4 username    2.20 K/s    0.00 B/s  0.00 %  0.01 % firefox --new-window company-pilot.slack.com [JS Helper]

```

top output snapshot:
```
top - 09:49:13 up 8 days, 21:13,  4 users,  load average: 20.67, 8.50, 3.42Tasks: 307 total,   3 running, 304 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.9 us,  0.4 sy,  0.0 ni, 97.5 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16343916 total, 15857276 used,   486640 free,     2216 buffers
KiB Swap:        0 total,        0 used,        0 free. 11125544 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 6753 username  20   0  461084 427956   1216 R 100.0  2.6   7:53.46 python3
31933 username  20   0  537984  72296   7496 R  70.1  0.4   1:06.98 chrome
 6654 username  20   0  950968  93208   7404 S  63.7  0.6   0:37.78 chrome
31873 username  20   0 1145524  91804  13472 S  25.5  0.6   6:29.25 chrome
32214 username  20   0 1541128 303084   6876 D  12.7  1.9  68:16.59 firefox
   18 root      20   0       0      0      0 S   6.4  0.0   0:12.93 rcuos/10
 1654 root      20   0  365376 153200  44904 S   6.4  0.9  80:02.51 Xorg
13159 username  20   0  639804  59520   2596 S   6.4  0.4  99:44.80 chrome
16904 username  20   0 7345388 562788   1696 S   6.4  3.4 280:37.75 java
    1 root      20   0   34024   2684    752 S   0.0  0.0   0:01.94 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.09 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:02.25 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   3:12.36 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   1:12.73 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:46.08 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   2:11.97 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   1:01.23 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   1:13.24 rcuos/4
   13 root      20   0       0      0      0 S   0.0  0.0   1:15.88 rcuos/5
   14 root      20   0       0      0      0 S   0.0  0.0   0:12.70 rcuos/6
   15 root      20   0       0      0      0 S   0.0  0.0   0:11.90 rcuos/7
   16 root      20   0       0      0      0 S   0.0  0.0   0:13.87 rcuos/8
   17 root      20   0       0      0      0 S   0.0  0.0   0:14.83 rcuos/9
   19 root      20   0       0      0      0 S   0.0  0.0   0:11.79 rcuos/11
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   25 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/4
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/5
   27 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/6
   28 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/7
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/8
   30 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/9
   31 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/10
   32 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/11
   33 root      rt   0       0      0      0 S   0.0  0.0   0:01.06 migration/0
   34 root      rt   0       0      0      0 S   0.0  0.0   0:03.37 watchdog/0
   35 root      rt   0       0      0      0 S   0.0  0.0   0:03.33 watchdog/1
   36 root      rt   0       0      0      0 S   0.0  0.0   0:00.92 migration/1
   37 root      20   0       0      0      0 S   0.0  0.0   0:01.14 ksoftirqd/1
   39 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H
   40 root      rt   0       0      0      0 S   0.0  0.0   0:03.13 watchdog/2
   41 root      rt   0       0      0      0 S   0.0  0.0   0:00.93 migration/2
   42 root      20   0       0      0      0 S   0.0  0.0   0:03.20 ksoftirqd/2
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H
   45 root      rt   0       0      0      0 S   0.0  0.0   0:03.10 watchdog/3
   46 root      rt   0       0      0      0 S   0.0  0.0   0:00.66 migration/3
   47 root      20   0       0      0      0 S   0.0  0.0   0:02.41 ksoftirqd/3
   49 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H
   50 root      rt   0       0      0      0 S   0.0  0.0   0:03.15 watchdog/4
   51 root      rt   0       0      0      0 S   0.0  0.0   0:00.91 migration/4
   52 root      20   0       0      0      0 S   0.0  0.0   0:03.25 ksoftirqd/4
   54 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/4:0H
   55 root      rt   0       0      0      0 S   0.0  0.0   0:03.15 watchdog/5
   56 root      rt   0       0      0      0 S   0.0  0.0   0:00.61 migration/5
   57 root      20   0       0      0      0 S   0.0  0.0   0:02.54 ksoftirqd/5
   59 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/5:0H
   60 root      rt   0       0      0      0 S   0.0  0.0   0:02.96 watchdog/6
   61 root      rt   0       0      0      0 S   0.0  0.0   0:00.43 migration/6
   62 root      20   0       0      0      0 S   0.0  0.0   0:00.33 ksoftirqd/6
   64 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/6:0H
   65 root      rt   0       0      0      0 S   0.0  0.0   0:03.02 watchdog/7
   66 root      rt   0       0      0      0 S   0.0  0.0   0:00.58 migration/7
   67 root      20   0       0      0      0 S   0.0  0.0   0:00.35 ksoftirqd/7
   69 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/7:0H
   70 root      rt   0       0      0      0 S   0.0  0.0   0:03.09 watchdog/8
   71 root      rt   0       0      0      0 S   0.0  0.0   0:00.49 migration/8
   72 root      20   0       0      0      0 S   0.0  0.0   0:00.30 ksoftirqd/8
   74 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/8:0H
   75 root      rt   0       0      0      0 S   0.0  0.0   0:03.00 watchdog/9
   76 root      rt   0       0      0      0 S   0.0  0.0   0:00.41 migration/9
   77 root      20   0       0      0      0 S   0.0  0.0   0:00.27 ksoftirqd/9
   79 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/9:0H
   80 root      rt   0       0      0      0 S   0.0  0.0   0:03.05 watchdog/10
   81 root      rt   0       0      0      0 S   0.0  0.0   0:00.45 migration/10
   82 root      20   0       0      0      0 S   0.0  0.0   0:00.29 ksoftirqd/10
   84 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/10:0H
   85 root      rt   0       0      0      0 S   0.0  0.0   0:03.05 watchdog/11
   86 root      rt   0       0      0      0 S   0.0  0.0   0:00.32 migration/11
   87 root      20   0       0      0      0 S   0.0  0.0   0:00.28 ksoftirqd/11
   89 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/11:0H
   90 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   91 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   92 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   93 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   94 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   95 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   97 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   99 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
  100 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khubd
  101 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
  102 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
  105 root      20   0       0      0      0 S   0.0  0.0   0:00.74 khungtaskd
  106 root      20   0       0      0      0 S   0.0  0.0   6:10.88 kswapd0
  107 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 vmstat
  108 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
  109 root      39  19       0      0      0 S   0.0  0.0   0:23.96 khugepaged
  110 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_mark
  111 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
  112 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
  124 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
  126 root      20   0       0      0      0 S   0.0  0.0   0:24.16 kworker/11:1
  147 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
  148 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_manager
  214 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  215 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  217 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  218 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  219 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  220 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_4
  221 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_5
  222 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_6
  249 root      20   0       0      0      0 S   0.0  0.0   0:29.24 jbd2/sda5-8
  250 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  294 root      20   0   33148    900    372 S   0.0  0.0   0:00.26 mountall
  390 root      20   0   19604    692    260 S   0.0  0.0   0:00.28 upstart-udev-br
  400 root      20   0   51740   1512    620 S   0.0  0.0   0:00.09 systemd-udevd
  494 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/81-mei_me
  496 root       0 -20       0      0      0 S   0.0  0.0   0:00.04 kworker/u25:1
  526 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 edac-poller
  635 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ttm_swap
  650 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
  662 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-clean
  668 username  20   0   24300   4916    228 S   0.0  0.0   3:04.07 mstart
  707 username  20   0   15820   3376      0 S   0.0  0.0   1:11.37 svc_router
  715 username  20   0   14328   9620      0 S   0.0  0.1   0:30.91 svc_statemgr
  791 root      20   0   23420    656    372 S   0.0  0.0   0:01.34 rpcbind
  862 statd     20   0   21540   1096    636 S   0.0  0.0   0:00.00 rpc.statd
  867 root      20   0   15388    436     80 S   0.0  0.0   0:00.27 upstart-socket-
  882 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio1
  917 root      20   0       0      0      0 S   0.0  0.0   0:00.07 jbd2/sdb2-8
  918 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  941 root      20   0  316716   3084    808 S   0.0  0.0   0:04.71 smbd
  942 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 rpciod
  958 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 nfsiod
  970 message+  20   0   40024   1564    392 S   0.0  0.0   0:03.15 dbus-daemon
 1016 root      20   0   23476    300     88 S   0.0  0.0   0:00.00 rpc.idmapd
 1066 root      20   0  308744   2268     96 S   0.0  0.0   0:00.00 smbd
 1077 root      20   0   19292    636    360 S   0.0  0.0   0:00.00 bluetoothd
 1100 root      20   0  316716   2612    336 S   0.0  0.0   0:02.85 smbd
 1105 root      20   0   43536   1144    752 S   0.0  0.0   0:00.01 systemd-logind
 1114 root      10 -10       0      0      0 S   0.0  0.0   0:00.00 krfcommd
 1190 syslog    20   0  255840   3852    708 S   0.0  0.0   0:01.04 rsyslogd
 1214 root      20   0  345012   2128    460 S   0.0  0.0   0:18.07 NetworkManager
 1230 avahi     20   0   32472    988    544 S   0.0  0.0   0:26.61 avahi-daemon
 1236 avahi     20   0   32220    332     76 S   0.0  0.0   0:00.00 avahi-daemon
 1259 root      20   0  281032   2524    568 S   0.0  0.0   0:00.37 polkitd
 1304 root      20   0   15404    484    192 S   0.0  0.0   0:00.25 upstart-file-br
 1352 root      20   0   20012    828    676 S   0.0  0.0   0:00.00 getty
 1356 root      20   0   20012    840    676 S   0.0  0.0   0:00.00 getty
 1363 root      20   0   20012    836    676 S   0.0  0.0   0:00.00 getty
 1364 root      20   0   20012    840    676 S   0.0  0.0   0:00.00 getty
 1367 root      20   0   20012    824    676 S   0.0  0.0   0:00.00 getty
 1403 root      20   0   61376   1324    648 S   0.0  0.0   0:00.00 sshd
 1426 root      20   0   23652    852    592 S   0.0  0.0   0:00.86 cron
 1451 root      20   0   19188    624    376 S   0.0  0.0   1:10.42 irqbalance
 1458 kernoops  20   0   37140    484    148 S   0.0  0.0   0:22.25 kerneloops
 1484 root      20   0   75488   1624    668 S   0.0  0.0   0:00.04 cups-browsed
 1503 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 iprt
 1515 root      20   0    4364    668    476 S   0.0  0.0   0:07.94 acpid
 1541 xrdp      20   0   19392    540     92 S   0.0  0.0   0:00.00 xrdp
 1543 root      20   0   31908    664    260 S   0.0  0.0   0:00.00 xrdp-sesman
 1627 root      20   0   20012    832    676 S   0.0  0.0   0:00.00 getty
 1642 root      20   0  351624   1556    692 S   0.0  0.0   0:00.02 lightdm
 1657 root      20   0  287468   1600    560 S   0.0  0.0   0:00.79 accounts-daemon
 1679 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1753 root      20   0  180996   1456    544 S   0.0  0.0   0:00.02 lightdm
 1795 root      20   0  304908   1396    348 S   0.0  0.0   0:00.13 upowerd
 1808 rtkit     21   1  168912    832    600 S   0.0  0.0   0:10.05 rtkit-daemon
 2083 root      20   0   10228   2892    592 S   0.0  0.0   0:00.69 dhclient
 2096 nobody    20   0   35220    984    724 S   0.0  0.0   0:05.86 dnsmasq
 2136 username  20   0 1208432  59560    916 S   0.0  0.4  25:49.71 cli
 2249 root      20   0  278160   2476    556 S   0.0  0.0   0:09.27 winbindd
 2309 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cifsiod
 2315 root      20   0       0      0      0 S   0.0  0.0   0:07.72 cifsd
 2316 root      20   0       0      0      0 S   0.0  0.0   0:07.63 cifsd
 2320 root      20   0       0      0      0 S   0.0  0.0   0:22.98 cifsd
 2324 root      20   0       0      0      0 S   0.0  0.0   0:07.70 cifsd
 2332 root      20   0  231440   2084    448 S   0.0  0.0   2:44.15 nmbd
 2336 root      20   0  278292   2100    152 S   0.0  0.0   0:02.20 winbindd
 2401 ntp       20   0   33508   1308    700 S   0.0  0.0   0:36.59 ntpd
 2489 username  20   0  452656   1068     88 S   0.0  0.0   0:00.25 gnome-keyring-d
 2498 username  20   0   40048   1632    796 S   0.0  0.0   0:00.34 init
 2584 username  20   0   40124   1752    348 S   0.0  0.0   0:01.56 dbus-daemon
 2594 username  20   0   22296    632    420 S   0.0  0.0   0:00.09 upstart-event-b
 2624 username  20   0   30780    516    208 S   0.0  0.0   0:00.02 upstart-file-br
 2626 username  20   0   22304    400    180 S   0.0  0.0   0:00.32 upstart-dbus-br
 2632 username  20   0   22304    380    156 S   0.0  0.0   0:00.23 upstart-dbus-br
 2635 username  20   0  393764  50884    396 S   0.0  0.3  12:07.10 ibus-daemon
 2648 username  20   0  196768   1076    432 S   0.0  0.0   0:00.13 gvfsd
 2653 username  20   0  345660    824    100 S   0.0  0.0   0:00.01 gvfsd-fuse
 2654 username  20   0    4440    596    488 S   0.0  0.0   0:00.00 sh
 2671 username  20   0  280876   3148    428 S   0.0  0.0   0:00.02 ibus-dconf
 2673 username  20   0  484808  27028    392 S   0.0  0.2   1:44.86 ibus-ui-gtk3
 2675 username  20   0  366156   2708    516 S   0.0  0.0   0:02.91 ibus-x11
 2677 username  20   0  403540   6396    560 S   0.0  0.0   0:16.70 xfce4-session
 2683 username  20   0  337516   1048    448 S   0.0  0.0   0:00.00 at-spi-bus-laun
 2687 username  20   0   39244   1124    680 S   0.0  0.0   0:00.50 dbus-daemon
 2690 username  20   0  124912   1188    592 S   0.0  0.0   0:02.47 at-spi2-registr
 2701 username  20   0   39452    928    452 S   0.0  0.0   0:00.32 xfconfd
 2705 username  20   0   10620    332      0 S   0.0  0.0   0:00.00 ssh-agent
 2706 username  20   0  473284   6588   1912 S   0.0  0.0   0:48.29 xfwm4
 2714 username  20   0  205148   3276    272 S   0.0  0.0   1:29.10 ibus-engine-sim
 2718 username  20   0  698700   9724   2108 S   0.0  0.1   0:05.64 Thunar
 2721 username  20   0  726504  14588   1524 S   0.0  0.1   2:08.80 xfce4-panel
 2727 username  20   0  791028  91540  33052 S   0.0  0.6   0:34.74 xfdesktop
 2728 username  20   0  337168   2864    448 S   0.0  0.0   0:02.29 xfsettingsd
 2732 username  20   0  561716   6260    684 S   0.0  0.0   0:01.86 panel-15-indica
 2733 username  20   0  280844   4176   2252 S   0.0  0.0   8:12.40 xfce4-oragecloc
 2744 username  20   0  263792   1064    552 S   0.0  0.0   0:00.00 indicator-bluet
 2748 username  20   0  300888   1916    344 S   0.0  0.0   0:00.97 polkit-gnome-au
 2751 username  20   0  476096   3972    660 S   0.0  0.0   0:01.52 update-notifier
 2760 username  20   0 1090432   6924    472 S   0.0  0.0   0:13.07 zeitgeist-datah
 2762 username  20   0  286784   1564    448 S   0.0  0.0   0:00.09 indicator-appli
 2767 username  20   0   70624   1648    728 S   0.0  0.0   0:29.93 xscreensaver
 2772 username  20   0  632424   5324    588 S   0.0  0.0   0:01.12 nm-applet
 2780 username  20   0  348860   1736    636 S   0.0  0.0   0:00.45 zeitgeist-daemo
 2781 username  20   0  352552  17848    780 S   0.0  0.1   0:14.92 quicktile.py
 2784 username  20   0  220720  11992    804 S   0.0  0.1   0:01.05 applet.py
 2786 username  20   0  278604   3276    620 S   0.0  0.0   0:00.00 indicator-power
 2794 username  20   0  252164   5084    484 S   0.0  0.0   0:11.39 zeitgeist-fts
 2827 username  20   0  913448   2804    504 S   0.0  0.0   0:05.55 gvfs-udisks2-vo
 2829 username  20   0   11408    540    444 S   0.0  0.0   0:00.00 cat
 2832 root      20   0  437028   5392    724 S   0.0  0.0   1:12.25 udisksd
 2838 username  20   0   15936    764    628 S   0.0  0.0   0:00.00 grep
 2845 username   9 -11  578896   4612   2148 S   0.0  0.0 215:09.92 pulseaudio
 2865 username  20   0  319360   3368    496 S   0.0  0.0   0:01.18 notify-osd
 2869 username  20   0  703496  13892   2480 S   0.0  0.1   4:04.35 gnome-terminal
 2873 username  20   0  303792   2108    564 S   0.0  0.0   0:00.00 xfce4-volumed
 2875 username  20   0  318600   2072    416 S   0.0  0.0   0:00.19 xfce4-power-man
 2890 username  20   0   31364   1236    736 S   0.0  0.0   0:00.01 init
 2893 username  20   0  353220   1516    580 S   0.0  0.0   0:11.65 indicator-messa
 2901 username  20   0   58260   2360    744 S   0.0  0.0   0:00.98 gconfd-2
 2905 username  20   0  553272   2384    632 S   0.0  0.0   0:00.28 indicator-sound
 2906 username  20   0  893884   3564    420 S   0.0  0.0   0:00.04 indicator-sessi
 3035 username  20   0   14820    736    576 S   0.0  0.0   0:00.00 gnome-pty-helpe
 3036 username  20   0   29004   5244    988 S   0.0  0.0   0:01.96 bash
 3060 username  20   0  200272    996    364 S   0.0  0.0   0:00.04 gvfs-mtp-volume
 3064 username  20   0  285964   2832     76 S   0.0  0.0   0:00.04 gvfs-afc-volume
 3069 username  20   0  212436   1376    552 S   0.0  0.0   0:00.04 gvfs-gphoto2-vo
 3078 username  20   0  359588   1352    212 S   0.0  0.0   0:00.14 gvfsd-trash
 3542 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/5:0
 3560 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:2
 3654 root      20   0       0      0      0 S   0.0  0.0   0:06.76 kworker/0:2
 3765 username  20   0   61812   9816    600 S   0.0  0.1   0:05.98 vncviewer
 3828 username  20   0  789348  22288    968 S   0.0  0.1   0:23.63 chrome
 4268 username  20   0  270376   1188    600 S   0.0  0.0   0:00.00 gvfsd-burn
 4883 root       0 -20   17720   5452   3508 S   0.0  0.0   0:02.02 atop
 5943 username  20   0   28952   3192    592 S   0.0  0.0   0:03.31 flit
 6200 root      20   0   77040   2008    720 S   0.0  0.0   0:00.01 cupsd
 6240 root      20   0       0      0      0 S   0.0  0.0   0:03.09 kworker/7:2
 6591 root      20   0       0      0      0 S   0.0  0.0   0:00.07 kworker/u24:2
 6607 root      20   0       0      0      0 S   0.0  0.0   0:00.14 kworker/u24:1
 6652 username  20   0   67424  43356    488 S   0.0  0.3   0:04.12 multi
 6653 username  20   0   23376  12508    168 S   0.0  0.1   0:01.94 mpserv
 6682 username  20   0   34948   6572      0 S   0.0  0.0   0:00.28 svc_python
 6729 username  20   0  897352  76292   4272 S   0.0  0.5   0:04.68 chrome
 6781 root      20   0       0      0      0 S   0.0  0.0   0:58.61 kworker/4:2
 6784 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u24:0
 6802 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u24:3
 6813 username  20   0   29140   1500   1064 R   0.0  0.0   0:00.00 top
 6814 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/5:1
 7129 root      20   0       0      0      0 S   0.0  0.0   1:03.27 kworker/5:2
 7141 username  20   0   21004   2812    192 S   0.0  0.0   2:44.12 helpview
 7480 username  20   0  305208   1324    272 S   0.0  0.0   0:00.00 gvfsd-http
 9191 root      20   0       0      0      0 S   0.0  0.0   0:05.45 kworker/0:0
 9303 username  20   0 2071812  34080   3640 S   0.0  0.2   0:18.02 retext
 9889 root      20   0       0      0      0 S   0.0  0.0   0:09.64 kworker/3:3
 9994 username  20   0  124704   1412    616 S   0.0  0.0   0:00.01 gvfsd-metadata
10399 username  20   0   27808   3944    900 S   0.0  0.0   0:00.20 bash
11761 username  20   0   28916   5260   1096 S   0.0  0.0   0:01.73 bash
11839 username  20   0  870712  56976   2168 S   0.0  0.3   1:10.69 chrome
11920 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/10:2
11955 username  20   0  836052  48932   4528 S   0.0  0.3   1:56.64 chrome
13242 root      20   0       0      0      0 S   0.0  0.0   0:06.52 kworker/1:2
13367 username  20   0  590016  46124   1892 S   0.0  0.3  14:05.90 plugin-containe
13438 username  20   0  745308 115656   1612 S   0.0  0.7   0:13.46 gvim
13567 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/4:1
13607 root      20   0       0      0      0 S   0.0  0.0   0:02.30 kworker/10:0
14697 username  20   0  851904  43564   1792 S   0.0  0.3   0:17.89 chrome
14702 username  20   0  924632  24856   1864 S   0.0  0.2   1:10.32 gedit
15590 root      20   0       0      0      0 S   0.0  0.0   0:05.68 kworker/6:0
16836 username  20   0   11408    396    300 S   0.0  0.0   0:00.00 cat
16837 username  20   0   11408    364    264 S   0.0  0.0   0:00.00 cat
16883 username  20   0   17720    788    632 S   0.0  0.0   0:00.00 eclipse
18735 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/7:1
19968 root      20   0       0      0      0 S   0.0  0.0   0:14.57 kworker/9:2
20585 root      20   0       0      0      0 S   0.0  0.0   0:22.02 kworker/8:2
21547 username  20   0  178304   3136    336 S   0.0  0.0   0:00.22 dconf-service
24244 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/11:2
25438 username  20   0  285928   6560   1124 S   0.0  0.0   0:02.04 orage
29665 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0
29805 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/8:0
31043 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/9:1
31095 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u25:0
31421 root      20   0       0      0      0 S   0.0  0.0   0:11.56 kworker/2:1
31867 root      20   0       0      0      0 S   0.0  0.0   0:01.27 kworker/1:0
31880 username  20   0   11408    512    416 S   0.0  0.0   0:00.00 cat
31881 username  20   0   11408    504    408 S   0.0  0.0   0:00.00 cat
31887 username  20   0  349364   8916    864 S   0.0  0.1   0:00.02 chrome
31888 username  20   0  133100   1960    660 S   0.0  0.0   0:00.00 nacl_helper
31891 username  20   0  349364   8228    160 S   0.0  0.1   0:00.08 chrome
31937 username  20   0  789540  24348    760 S   0.0  0.1   0:44.09 chrome
32413 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/6:1
```

---

### Post by Only1KW on 2016-05-11
On advice from a coworker, I tried adding a swap file to my system.  That seems to have helped.  Unfortunately, that still points to some sort of kernel issue where it worked 6 months ago with the same workload and amount of installed memory but can no longer work without a swap partition/file in it's current state.  This has the unfortunate effect of causing me to lose almost 10% of my SSD capacity and who knows how much of its life due to the significantly increased number of writes occurring on the drive.  Hopefully this will be fixed in some future version of the kernel.

---

### Post by howefield on 2016-05-12
Are you using an application now that you didn't previously ?

Could just as easily be a rogue application as a kernel issue.

If it is the kernel to blame, chances are something will be recorded in /var/logs.

---

### Post by Bucky Ball on 2016-05-12
You don't need the /swap on the SSD. You can put it anywhere. Do you have a hard drive in the machine also? It also should be using nowhere near 10% of your drive, unless your SSD is 20Gb. 

Your /swap doesn't need to be any larger than 2Gb unless you are hibernating. As you ran 14.04 for six months with no /swap, I'm presuming you are not.

If you have a hard drive, try putting the /swap on that (you'll need to point the /swap entry in fstab to the new /swap UUID on the hard drive) and see if that makes any improvement.

Puzzled as to why the /swap is necessary to solve the problem, though, which leads me to think the problem goes deeper than that.

---

### Post by Only1KW on 2016-05-12
Like I said earlier, my workload is exactly the same as before.  

I don't see how one rogue application can trigger 30+ processes on my system to simultaneously start reading from my drive.  That seems like only the Kernel should have the authority to be able to influence that.

---

### Post by Only1KW on 2016-05-12
I don't have an HDD.  I have an SSD and remote network storage, which I don't trust to use with the swap.  My SSD is marketed as 200 GB, but in reality is closer to 185 GB.  I created a 16 GB swap file to match the 16 GB of RAM in my system as everything I've read recommends that the swap file be at least as big as the physical RAM size.

---

### Post by Bucky Ball on 2016-05-12
> **Only1KW said:**
> I created a 16 GB swap file to match the 16 GB of RAM in my system as everything I've read recommends that the swap file be at least as big as the physical RAM size.

Unless you're hibernating, totally unnecessary. You were running 14.04 fine without one at all, correct? Others do also and I have only ever used 2Gb. I'm using a machine with 16Gb of RAM now and a 2Gb /swap.

But we digress and best not to drift too far away from your original problem and land in the stuff of another thread ... ;)

---

