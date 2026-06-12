---
title: "Azureus won't start.. (Gutsy)"
date: 2007-11-04
forum: General Help
---

### Post by geo909 on 2007-11-04
Hello everyone,
I'm having this problem:

I downloaded Azureus from Add/Remove programs,
I even restarted my computer but what happens
everytime I try to open Azureus is that I see the splash screen,
a flash from the "Choose your language" window and then
it dissapears.
I tried reinstallation and then remove-->install again
from synaptic but that didn't change anything..

Any ideas, please?!

Thanks in advance!

---

### Post by Pumalite on 2007-11-04
It might be java. I think is better to download it from sourceforge.net and extract it to /home. But better still is to use ktorrent.

---

### Post by por100pre1 on 2007-11-04
Try this (in terminal):

```
mv .azureus .azureus_backup
```

But I think the best solution is to forget Azureus and try Deluge:

```
sudo aptitude install deluge-torrent
```

---

### Post by geo909 on 2007-11-04
I did the "mv" but nothing happened.
By the way, when I try to run in terminal, I get this:

```

geo909@desktop:~$ azureus
DEBUG::Sun Nov 04 16:50:12 GMT+02:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Sun Nov 04 16:50:15 GMT+02:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
DEBUG::Sun Nov 04 16:50:20 GMT+02:00 2007::com.aelitis.azureus.plugins.upnp.UPnPPluginService::checkMapping::221:
  com.aelitis.net.upnp.UPnPException: Invoke of 'urn:schemas-upnp-org:service:WANIPConnection:1#AddPortMapping' fails: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:134)
   at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.addPortMapping(UPnPSSWANConnectionImpl.java:319)
   at com.aelitis.azureus.plugins.upnp.UPnPPluginService.checkMapping(UPnPPluginService.java:189)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.checkState(UPnPPlugin.java:1115)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(UPnPPlugin.java:1004)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(UPnPPlugin.java:939)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:899)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.rootDeviceFound(UPnPPlugin.java:691)
   at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:237)
   at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
   at org.gudy.azureus2.core3.util.ThreadPool$3.runSupport(ThreadPool.java:523)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.io.IOException: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:646)
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:508)
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:98)
   ...13 more

DEBUG::Sun Nov 04 16:50:20 GMT+02:00 2007::com.aelitis.azureus.plugins.upnp.UPnPPluginService::checkMapping::221:
  com.aelitis.net.upnp.UPnPException: Invoke of 'urn:schemas-upnp-org:service:WANIPConnection:1#AddPortMapping' fails: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:134)
   at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.addPortMapping(UPnPSSWANConnectionImpl.java:319)
   at com.aelitis.azureus.plugins.upnp.UPnPPluginService.checkMapping(UPnPPluginService.java:189)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.checkState(UPnPPlugin.java:1115)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(UPnPPlugin.java:1004)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(UPnPPlugin.java:939)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:899)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.rootDeviceFound(UPnPPlugin.java:691)
   at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:237)
   at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
   at org.gudy.azureus2.core3.util.ThreadPool$3.runSupport(ThreadPool.java:523)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.io.IOException: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:646)
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:508)
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:98)
   ...13 more

DEBUG::Sun Nov 04 16:50:21 GMT+02:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl::select::528:
  VirtualChannelSelector: No progress for op 1: listener = class com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$2, count = 10, socket: open = true, connected = true
    VirtualChannelSelector::select::272,NonBlockingReadWriteService$1::runSupport::79,AEThread::run::69


```

 Now, any idea?

---

### Post by JacobRogers on 2007-11-05
> **por100pre1 said:**
> Try this (in terminal):

```
mv .azureus .azureus_backup
```

But I think the best solution is to forget Azureus and try Deluge:

```
sudo aptitude install deluge-torrent
``` 

That first tip worked for me!

---

### Post by JacobRogers on 2007-11-05
I take it back, it didn't really work for me.  It did, but not I'm back to square one.  I'm going to try deluge.

---

