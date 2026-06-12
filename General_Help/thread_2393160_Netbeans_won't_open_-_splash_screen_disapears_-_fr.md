---
title: "Netbeans won't open - splash screen disapears - fresh install 18.04"
date: 2018-05-30
forum: General Help
---

### Post by chrisbay90 on 2018-05-30
Hello,

I have a fresh install of Ubuntu 18.04 desktop. I have updated Ubuntu and then installed netbeans - the system is 100% fresh otherwise.

The splash screen for netbeans appears for about 5 seconds and then silently disappears. The problem persists after a reboot as well as an uninstall and purge then reinstall.

Running the command "netbeans" from the terminal reveals nothing especially telling:


```

WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.netbeans.ProxyURLStreamHandlerFactory (file:/usr/share/netbeans/platform18/lib/boot.jar) to field java.net.URL.handler
WARNING: Please consider reporting this to the maintainers of org.netbeans.ProxyURLStreamHandlerFactory
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release

```

Flashes prior to the splashscreen apearing. The splash screen then comes up for 5 seconds, silently disapears and the command then silently concludes.

The log at ~/.netbeans/8.1/var/log reveals little telling info either.

```

>Log Session: Wednesday, May 30, 2018 at 10:02:29 PM Australian Eastern Standard Time
>System Info: 
  Product Version         = NetBeans IDE 8.1 (Build 20180221-debian-8.1)
  Operating System        = Linux version 4.15.0-22-generic running on amd64
  Java; VM; Vendor        = 10.0.1; OpenJDK 64-Bit Server VM 10.0.1+10-Ubuntu-3ubuntu1; Oracle Corporation
  Runtime                 = OpenJDK Runtime Environment 10.0.1+10-Ubuntu-3ubuntu1
  Java Home               = /usr/lib/jvm/java-11-openjdk-amd64
  System Locale; Encoding = en_AU (nb); UTF-8
  Home Directory          = /home/user
  Current Directory       = /home/user
  User Directory          = /home/user/.netbeans/8.1
  Cache Directory         = /home/user/.cache/netbeans/8.1
  Installation            = /usr/share/netbeans/8.1/nb
                            /usr/share/netbeans/8.1/ide
                            /usr/share/netbeans/8.1/java
                            /usr/share/netbeans/8.1/apisupport
                            /usr/share/netbeans/8.1/harness
                            /usr/share/netbeans/8.1/platform
  Boot & Ext. Classpath   = 
  Application Classpath   = /usr/share/java/jcodings.jar:/usr/share/netbeans/8.1/platform/lib/boot.jar:/usr/share/netbeans/8.1/platform/lib/org-openide-modules.jar:/usr/share/netbeans/8.1/platform/lib/org-openide-util.jar:/usr/share/netbeans/8.1/platform/lib/org-openide-util-lookup.jar:/usr/share/netbeans/8.1/platform/lib/org-openide-util-ui.jar
  Startup Classpath       = /usr/share/netbeans/8.1/platform/core/core-base.jar:/usr/share/netbeans/8.1/platform/core/core.jar:/usr/share/netbeans/8.1/platform/core/org-openide-filesystems.jar:/usr/share/netbeans/8.1/platform/core/org-openide-filesystems-compat8.jar:/usr/share/netbeans/8.1/platform/core/asm-all-5.0.1.jar:/usr/share/netbeans/8.1/platform/core/org-netbeans-libs-asm.jar:/usr/share/netbeans/8.1/nb/core/org-netbeans-upgrader.jar:/usr/share/netbeans/8.1/nb/core/locale/core_nb.jar
-------------------------------------------------------------------------------
java.lang.SecurityException: setContextClassLoader
    at java.base/jdk.internal.misc.InnocuousThread.setContextClassLoader(InnocuousThread.java:116)
    at org.netbeans.ModuleManager.updateContextClassLoaders(Unknown Source)
    at org.netbeans.ModuleManager.<init>(Unknown Source)
    at org.netbeans.core.startup.ModuleSystem.<init>(Unknown Source)
    at org.netbeans.core.startup.Main.getModuleSystem(Unknown Source)
INFO [null]: Last record repeated again.
    at org.netbeans.core.startup.Main.start(Unknown Source)
    at org.netbeans.core.startup.TopThreadGroup.run(Unknown Source)
    at java.base/java.lang.Thread.run(Thread.java:844)


```

Bit of a head scratcher. Has anyone experienced this before?

---

### Post by molf2 on 2018-07-16
There's a workaround here: [https://askubuntu.com/questions/1032030/netbeans-does-not-start-on-fresh-ubuntu-18-04-installation](https://askubuntu.com/questions/1032030/netbeans-does-not-start-on-fresh-ubuntu-18-04-installation)

And a bug has (sort of) been raised here: 
[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/1760907](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/1760907)

---

