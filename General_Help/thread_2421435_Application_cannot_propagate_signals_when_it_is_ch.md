---
title: "Application cannot propagate signals when it is child of 'dbus.service' (mostly)"
date: 2019-06-21
forum: General Help
---

### Post by tom_tlr on 2019-06-21
Hello,

I have a machine with Ubuntu Bionic Server with MATE desktop from Mint repositories. Don't ask, it's due to limitations at work (admins provide headless and preconfigured Ubuntu, hence server edition; developers install DE of choice). I had a hard time deciding which subforum to post in.

When I start Intellij IDEA from the Mint menu on one machine, there is a notificiation that the [IDE ignores SIGINT]("https://intellij-support.jetbrains.com/hc/en-us/articles/360004770440-The-IDE-ignores-SIGINT-the-Stop-button-in-run-configurations-may-not-work") and hence is not able to stop running projects (e.g. Spring Boot). When I start the IDE from the terminal, there is not such a notification and stopping projects works just fine. I have another machine which is set up the exact same way and the problem does not occur there even if the IDE is started from the menu.

Now, I have found some differences depending whether the IDE was launched from terminal or menu. On the machine, where the SIGINT notifications is shown the IDE belongs to "dbus.service".

```

&#9679; user@1000.service - User Manager for UID 1000
   Loaded: loaded (/lib/systemd/system/user@.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/user@.service.d
           &#9492;&#9472;timeout.conf
   Active: active (running) since Wed 2019-06-19 13:25:29 UTC; 22min ago
 Main PID: 1768 (systemd)
   Status: "Startup finished in 24ms."
    Tasks: 98
   CGroup: /user.slice/user-1000.slice/user@1000.service
           &#9500;&#9472;dbus.service
           &#9474; &#9500;&#9472;1836 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
           &#9474; &#9500;&#9472;1870 /usr/lib/dconf/dconf-service
           &#9474; &#9500;&#9472;1983 /usr/lib/gnome-online-accounts/goa-daemon
           &#9474; &#9500;&#9472;2080 /usr/lib/gnome-online-accounts/goa-identity-service
           &#9474; &#9500;&#9472;2674 /usr/lib/ibus/ibus-portal
           &#9474; &#9500;&#9472;2772 mintmenu
           &#9474; &#9500;&#9472;2774 /usr/lib/mate-panel/wnck-applet
           &#9474; &#9500;&#9472;2777 /usr/lib/mate-panel/clock-applet
           &#9474; &#9500;&#9472;2778 /usr/lib/mate-panel/notification-area-applet
           &#9474; &#9500;&#9472;3269 /bin/sh /opt/idea-IU-191.7479.19/bin/idea.sh %f
           &#9474; &#9500;&#9472;3317 /opt/idea-IU-191.7479.19/jre64/bin/java -classpath /opt/idea-IU-191.7479.19/lib/bootstrap.jar:/opt/idea-IU-191.7479.19/lib/extensions.jar:/opt/idea-IU-191.7479.19/lib/util.jar:/opt/idea-IU-191.7479.19/lib/jdom.jar:/opt/idea-IU-191.7479.19/lib/log4j.jar:/opt/idea-IU-191.7479.19/lib/trove4j.jar:/opt/idea-IU-191.7479.19/lib/jna.jar:/opt/idea-IU-191.7479.19/jre64/lib/tools.jar -Xms128m -Xmx750m -XX:ReservedCodeCacheSize=240m -XX:+UseConcMarkSweepGC -XX:SoftRefLRUPolicyMSPerMB=50 -ea -Dsun.io.useCanonCaches=false -Djava.net.preferIPv4Stack=true -Djdk.http.auth.tunneling.disabledSchemes="" -XX:+HeapDumpOnOutOfMemoryError -XX:-OmitStackTraceInFastThrow -Dawt.useSystemAAFontSettings=lcd -Dsun.java2d.renderer=sun.java2d.marlin.MarlinRenderingEngine -Dsun.tools.attach.tmp.only=true -XX:ErrorFile=/home/user/java_error_in_IDEA_%p.log -XX:HeapDumpPath=/home/user/java_error_in_IDEA.hprof -Didea.paths.selector=IntelliJIdea2019.1 -Djb.vmOptionsFile=/opt/idea-IU-191.7479.19/bin/idea64.vmoptions -Didea.jre.check=true com.intellij.idea.Main %f

```

On the other machine, where this problem does not occur there is no "dbus.service" the IDE belongs to. It's directly beneath this "user.slice" stuff. 

```

&#9679; session-28.scope - Session 28 of user user
   Loaded: loaded (/run/systemd/transient/session-28.scope; transient)
Transient: yes
   Active: active (running) since Fri 2019-06-14 09:20:21 CEST; 5 days ago
    Tasks: 546
   CGroup: /user.slice/user-1004.slice/session-28.scope
           &#9500;&#9472; 4577 mate-session
           &#9500;&#9472; 4601 gnome-keyring-daemon --start
           &#9500;&#9472; 4605 /usr/bin/mate-settings-daemon
           &#9500;&#9472; 4621 marco --composite --replace
           &#9500;&#9472; 4622 mate-panel
           &#9500;&#9472; 4645 caja
           &#9500;&#9472; 4653 mate-screensaver
           &#9500;&#9472; 4658 /usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1
           &#9500;&#9472; 4680 mate-volume-control-applet
           &#9500;&#9472; 4696 /usr/bin/python3 /usr/share/system-config-printer/applet.py
           &#9500;&#9472; 4711 nm-applet
           &#9500;&#9472;25705 /bin/sh /work/software/intellij-2019.1.3/bin/idea.sh
           &#9500;&#9472;25761 /work/software/intellij-2019.1.3/jre64/bin/java -classpath /work/software/intellij-2019.1.3/lib/bootstrap.jar:/work/software/intellij-2019.1.3/lib/extensions.jar:/work/software/intellij-2019.1.3/lib/util.jar:/work/software/intellij-2019.1.3/lib/jdom.jar:/work/software/intellij-2019.1.3/lib/log4j.jar:/work/software/intellij-2019.1.3/lib/trove4j.jar:/work/software/intellij-2019.1.3/lib/jna.jar:/work/software/intellij-2019.1.3/jre64/lib/tools.jar -Xms128m -Xmx750m -XX:ReservedCodeCacheSize=240m -XX:+UseConcMarkSweepGC -XX:SoftRefLRUPolicyMSPerMB=50 -ea -Dsun.io.useCanonCaches=false -Djava.net.preferIPv4Stack=true -Djdk.http.auth.tunneling.disabledSchemes="" -XX:+HeapDumpOnOutOfMemoryError -XX:-OmitStackTraceInFastThrow -Dawt.useSystemAAFontSettings=lcd -Dsun.java2d.renderer=sun.java2d.marlin.MarlinRenderingEngine -Dsun.tools.attach.tmp.only=true -XX:ErrorFile=/home/user/java_error_in_IDEA_%p.log -XX:HeapDumpPath=/home/user/java_error_in_IDEA.hprof -Didea.paths.selector=IntelliJIdea2019.1 -Djb.vmOptionsFile=/work/software/intellij-2019.1.3/bin/idea64.vmoptions -Didea.jre.check=true com.intellij.idea.Main

```
          
It seems to me that this could be the culprit. When the IDE belongs to "dbus.service" its signals are not propagated to running projects and they are unaware of termination request. 

To make things even stranger, I cannot reproduce the SIGINT notification when I run the IDE from the MATE menu on an official Ubuntu MATE (Bionic), although the IDE belongs to "dbus.service". Maybe the DE is better integrated by default. But then I'm still puzzled why it works on the other machine with the server edition + Mint MATE.

What might be the reason that the IDE belongs to "dbus.service" on the first machine but not on the second machine, when the IDE is startet from the menu on both machines? Maybe the first machine misses something to behave like the other machine. Any suggestions?

All the best,
Andi

---

### Post by TheFu on 2019-06-21
Server installs don't include much of the DE cruft that desktops get.  Many things in desktops are added for point-n-click stuff that aren't part of servers.  If you don't have any gnome or qt infrastructure in the server, then all those added dependencies aren't installed.

I wouldn't worry about any of this. It is just a slow, bloated, IDE.
If you want a more integrated feel, then install the desktop from one repo and don't try to make a Frankenstein OS expecting everything to integrate perfectly.

---

