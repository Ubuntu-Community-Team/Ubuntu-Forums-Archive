---
title: "Azureus not working properly"
date: 2007-04-25
forum: General Help
---

### Post by Dearhell on 2007-04-25
I have installed azureus on Feisty Fawn, I have ports stuff properly configured, Azureus displays that my NAT is OK and my DHT working

The problem it's that Azureus starts downloading and then usually stops, also there is no upload rate. 

In Windows XP Azureus still works fine

---

### Post by Dearhell on 2007-04-25
I have installed java6 and when I type on the terminal java --version it says that it's 1.4.2

---

### Post by paridoth on 2007-04-25
i belive im getting a similar problem, i installed the gcj version if that matters, this is a clean fiest install, my edgy ran azureus perfectly, my azureus is working on an off, usually off, then sporaticly downloading, then stopping as soon as it started, this is on multiple trackers, so i know its not the torrent, its azureus/fiesty

here is some output when i run azureus, if it helps

```
paridoth@paridoth-desktop:~$ azureus
DEBUG::Wed Apr 25 11:57:32 GMT-07:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::-1:
  No SSL provider available
    SESecurityManager::initialise::-1,ConfigurationChecker::setSystemProperties::-1,ConfigurationManager::initialise::-1,ConfigurationManager::getInstance::-1,LoggerImpl::init::-1,Logger::<clinit>::-1,Class::initializeClass::-1,Logger::isEnabled::-1,StartServer::<init>::-1,Main::<init>::-1,Main::main::-1
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Wed Apr 25 11:57:33 GMT-07:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::-1:
  No SSL provider available
    SESecurityManager::initialise::-1,CryptoManagerImpl::<init>::-1,CryptoManagerImpl::getSingleton::-1,CryptoManagerFactory::getSingleton::-1,AzureusCoreImpl::<init>::-1,AzureusCoreImpl::create::-1,AzureusCoreFactory::create::-1,Main::<init>::-1,Main::main::-1
java.lang.Exception: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
   at org.gnu.glib.GObject.printStackTrace(glib0.4.jar.so)
DEBUG::Wed Apr 25 11:57:43 GMT-07:00 2007::com.aelitis.azureus.plugins.upnp.UPnPPluginService::checkMapping::-1:
  com.aelitis.net.upnp.UPnPException: Invoke of 'urn:schemas-upnp-org:service:WANIPConnection:1#AddPortMapping' fails: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(Azureus2.jar.so)
   at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.addPortMapping(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPluginService.checkMapping(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.checkState(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(Azureus2.jar.so)
   at com.aelitis.azureus.plugins.upnp.UPnPPlugin.rootDeviceFound(Azureus2.jar.so)
   at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(Azureus2.jar.so)
   at org.gudy.azureus2.core3.util.AERunnable.run(Azureus2.jar.so)
   at org.gudy.azureus2.core3.util.ThreadPool$3.runSupport(Azureus2.jar.so)
   at org.gudy.azureus2.core3.util.AEThread.run(Azureus2.jar.so)
Caused by: java.io.IOException: HTTP request failed:HTTP/1.1 500 Internal Server Error
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(Azureus2.jar.so)
   at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(Azureus2.jar.so)
   at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(Azureus2.jar.so)
   ...13 more
DEBUG::Wed Apr 25 11:59:19 GMT-07:00 2007::org.gudy.azureus2.core3.peer.util.PeerIdentityManager::removeIdentity::-1:
  id not present: id=2D4243303037302D8919D048532D7A62DDAB35DA
    PEPeerTransportProtocol::performClose::-1,PEPeerTransportProtocol::closeConnection::-1,PEPeerControlImpl::closeAndRemovePeer::-1,PEPeerControlImpl::checkSeeds::-1,PEPeerControlImpl::schedule::-1,PeerControlSchedulerImpl$instanceWrapper::schedule::-1,PeerControlSchedulerImpl::schedule::-1,PeerControlSchedulerImpl$1::runSupport::-1,AEThread::run::-1
DEBUG::Wed Apr 25 11:59:19 GMT-07:00 2007::org.gudy.azureus2.core3.peer.util.PeerIdentityManager::removeIdentity::-1:
  id not present: id=2D5554313730422D9284B4C2B8132A6DD5BFC301
    PEPeerTransportProtocol::performClose::-1,PEPeerTransportProtocol::closeConnection::-1,PEPeerControlImpl::closeAndRemovePeer::-1,PEPeerControlImpl::checkSeeds::-1,PEPeerControlImpl::schedule::-1,PeerControlSchedulerImpl$instanceWrapper::schedule::-1,PeerControlSchedulerImpl::schedule::-1,PeerControlSchedulerImpl$1::runSupport::-1,AEThread::run::-1
DEBUG::Wed Apr 25 12:00:46 GMT-07:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl::select::-1:
  VirtualChannelSelector: No progress for op 1: listener = class com.aelitis.azureus.core.networkmanager.impl.tcp.TCPTransportHelper$1, count = 10, socket: open = true, connected = true
    VirtualChannelSelector::select::-1,TCPNetworkManager::readSelectorLoop::-1,TCPNetworkManager::access$0::-1,TCPNetworkManager$2::runSupport::-1,AEThread::run::-1


```

---

### Post by mungy on 2007-04-25
> **Dearhell said:**
> I have installed java6 and when I type on the terminal java --version it says that it's 1.4.2

```
sudo update-alternatives --config java
```

Run that in a terminal and select java6. It worked for me.

If you have port forwarding from your router you don't need to have UPnP selected in plug-ins -> options.

It is worth checking to see if your router is set up correctly.

---

### Post by paridoth on 2007-04-25
i changed it to 6 and now it crashes as soon as the azureus mainwindow loads with this in terminal
```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=11122, tid=3084626832
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid11122.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

P.S. it works fine if i put it back to java-GCJ where it was at =/

---

### Post by Dearhell on 2007-04-26
> **mungy said:**
> ```
sudo update-alternatives --config java
```

Run that in a terminal and select java6. It worked for me.

If you have port forwarding from your router you don't need to have UPnP selected in plug-ins -> options.

It is worth checking to see if your router is set up correctly.

It seems that select java6 with that command fixed my problem, thx

---

### Post by paridoth on 2007-04-26
i uninstalled azureus with synaptic, then used automatix to install it and its working fine now, also sais its using java 1.6 in help about, thanks

---

### Post by asipi on 2007-04-26
as an alternative try Ktorrent, not so feature rich like azureus but more smoother run in fact it is native cpu-code not java...

---

### Post by kelvin spratt on 2007-04-26
i've used the blue from for a long time both on windows and linux the frog is a bit temperamental it does not like change at the last update it went strange on my system after java updated  since then ive used ktorrent and have been shocked at its speed i will try the frog after its next update as i have similer problems on windows
but worse as it reboots windows every 20 mins i think its java causing the problem but as allways bugs do not effect all computers

---

### Post by mungy on 2007-04-26
> **paridoth said:**
> i changed it to 6 and now it crashes as soon as the azureus mainwindow loads with this in terminal
```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=11122, tid=3084626832
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid11122.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

P.S. it works fine if i put it back to java-GCJ where it was at =/

go into your .azureus folder and delete any log files and the logs folder. that should get it to start

---

### Post by xjas05 on 2007-04-27
thanks mungy, that just fixed my problem too :)

---

### Post by Dearhell on 2007-04-28
I have to delete logs folder everytime I start azureus

---

### Post by mungy on 2007-04-28
> **Dearhell said:**
> I have to delete logs folder everytime I start azureus

when i close azureus i always stop all transfers and wait a few seconds until they are all stopped, then I select exit from the file menu.

I do this because azureus doesn't like being just switched off. I used to have the same problems you have until i change how i closed it down. Perhaps that will help you too.

---

### Post by dhanwada on 2007-04-28
Thanks for all who posted usefull tips.

I tried most of those, but could not solve the problem. 

I installed and switched to [COLOR="Red"]java5[/COLOR] and started azureus. That seems to have solved my issues.

I have been using Ubuntu for abt a week now ... and I love it ... especially the community ... I get most of my issues resolved browing thru these forums....

Keep up the great work people.

---

### Post by ignignokt00 on 2007-09-03
> **mungy said:**
> go into your .azureus folder and delete any log files and the logs folder. that should get it to start

worked for me, now i can use java6, thanks.

---

