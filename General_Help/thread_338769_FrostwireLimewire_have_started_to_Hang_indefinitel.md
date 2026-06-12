---
title: "Frostwire/Limewire have started to Hang indefinitely (not a firewall issue)"
date: 2007-01-14
forum: General Help
---

### Post by rishibravo on 2007-01-14
My frostwire and limewire both used to run fine until 2 days back. The applet loads but there is just the starting picture of the frostwire and I never get to see the new window. It seemed to me as a java issue so i used the new jdk (1.6) as well but no use. when I take a stack dump of frostwire this is what I see in the main thread.

***************************************************************************
"main" prio=1 tid=0x0805cba8 nid=0x2e26 runnable [0xbf87d000..0xbf87e538]
        at java.net.Inet6AddressImpl.lookupAllHostAddr(Native Method)
        at java.net.InetAddress$1.lookupAllHostAddr(InetAddress.java:838)
        at java.net.InetAddress.getAddressFromNameService(InetAddress.java:1176)
        at java.net.InetAddress.getLocalHost(InetAddress.java:1305)
        at org.cybergarage.upnp.ssdp.HTTPUSocket.open(HTTPUSocket.java:116)
        - locked <0x88a59240> (a org.cybergarage.upnp.ssdp.SSDPSearchResponseSocket)
        at org.cybergarage.upnp.ssdp.HTTPUSocket.<init>(HTTPUSocket.java:57)
        at org.cybergarage.upnp.ssdp.SSDPSearchResponseSocket.<init>(SSDPSearchResponseSocket.java:37)
        at org.cybergarage.upnp.ssdp.SSDPSearchResponseSocketList.open(SSDPSearchResponseSocketList.java:71)
        at org.cybergarage.upnp.ControlPoint.start(ControlPoint.java:805)
        at org.cybergarage.upnp.ControlPoint.start(ControlPoint.java:849)
        at com.limegroup.gnutella.UPnPManager.start(UPnPManager.java:131)
        - locked <0x88ab0118> (a java.lang.Object)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:193)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)

"VM Thread" prio=1 tid=0x08099698 nid=0x2e27 runnable 

"VM Periodic Task Thread" prio=1 tid=0x080a7ec8 nid=0x2e2d waiting on condition 
***************************************************************************

I thought may be its coming on beryl but the problem is persistent if I am on metacity as well. Limewire and Frostwire both have the exactly same behaviour. The irony is that my other machine with same java version and similar configuration is not giving any issue, so i am a lil confused here :-k 

Has anyone else encountered this problem. :-k

---

### Post by rabid9797 on 2007-01-14
im not a big expert in java, but try this:

[http://ubuntuforums.org/showthread.php?t=278134](http://ubuntuforums.org/showthread.php?t=278134)

---

### Post by rishibravo on 2007-01-15
I figured out the problem. Apparently the problem fixed when i gave a fully qualified host-name (mycomp.xyz.com) . I figured out that the api java.net.InetAddress.getLocalHost
causes a problem if your machine is part of a domain and your hostname is not fully qualified. :-D

---

