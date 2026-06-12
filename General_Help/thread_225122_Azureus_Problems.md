---
title: "Azureus Problems"
date: 2006-07-29
forum: General Help
---

### Post by Beamerboy on 2006-07-29
I couldn't get Azureus to work in 64bit Dapper, but I recently switched back to 32bit Dapper and never expected any problems.  But...

I launch Azureus, the splash screen opens, the splash screen closes and I am left with just those annoying message boxes in the bottom right corner of the screen. (Don't worry I know how to get rid of them ;))

The only thing I can see in the error log is:

```

[2907 07:03:52] DEBUG::Sat Jul 29 07:03:52 GMT 2006::com.aelitis.azureus.plugins.upnp.UPnPPluginService::checkMapping::223:
[2907 07:03:52]   com.aelitis.net.upnp.UPnPException: Invoke of 'urn:schemas-upnp-org:service:WANPPPConnection:1#AddPortMapping' fails: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:134)
   at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.addPortMapping(UPnPSSWANConnectionImpl.java:295)
   at com.aelitis.azureus.plugins.upnp.UPnPPluginService.checkMapping(UPnPPluginService.java:195)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.checkState(UPnPPlugin.java:705)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(UPnPPlugin.java:598)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(UPnPPlugin.java:554)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:516)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:518)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:518)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin$7.rootDeviceFound(UPnPPlugin.java:334)
   at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:230)
   at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
   at org.gudy.azureus2.core3.util.ThreadPool$threadPoolWorker$1.runSupport(ThreadPool.java:412)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.io.IOException: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:589)
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:452)
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:98)
   ...13 more

```

So I am not overly sure where to go from here.  According to Synaptic I am running Azureus 2.4.0.2-0ubuntu2 (which from what I can see from sourceforge is the latest release) and I have Sun JRE 1.5.0-06-1 (which is also apparantly the latest version and is the version suggested on Azureus Sourceforge page).

So anyone come across this before and managed to fix it?

Thanks

BeamerBoy

---

### Post by JerMe on 2006-07-29
I fixed it by installing Wine 0.9.17 and uTorrent 1.6  ;)

[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)

---

### Post by Beamerboy on 2006-07-29
> **JerMe said:**
> I fixed it by installing Wine 0.9.17 and uTorrent 1.6  ;)

[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)


Well I also run win2k3 in a virtual machine so I could just run it in that, but I would rather run it natively.

---

### Post by Beamerboy on 2006-07-29
OK the problem was despite installing Sun's JRE Ubuntu doesn't use it by default.  I had to do the following command:

sudo update-alternatives --config java

And select 3 from the list returned.

Everything is working now.

---

