---
title: "Azureus: From Bad to Worse"
date: 2006-10-10
forum: General Help
---

### Post by keithjr on 2006-10-10
After reinstalling ubuntu dapper, I went about the seemingly inocuous task of isntalling azureus and setting it up as I had it before.  All I did to accomplish this end was grabbing the azureus package from synaptic and installing it, along with several prerequisite packages.  

I now have the following noticable things going wrong with Azureus, simply from a stock apt install...
[LIST=1]
[*]No notification icon, even though X-ing the window doesn't exit the 
client.
[*]The Window List entry has no icon.  Pointless, but maybe the sign of deeper problem...?
[*]Those already-annoying-to-the-point-of-madness pop-up warning and error messages now will not respond to being clicked, so to get rid of them Azureus needs to be shut down.
[*]The tabs in the azureus window don't have any X to close them in the GUI
[*]Attempts to open a torrent file directly from Nautilus will result in a "Cannot Open: not a file" error, even though manually adding them withing Azureus works
[/LIST]

Here's some of the sample output that I get if I run azureus in console.  It's mostly garbage to me...

```

DEBUG::Tue Oct 10 23:08:29 EDT 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::141:
  No SSL provider available
    SESecurityManager::initialise::53,ConfigurationChecker::setSystemProperties::141,ConfigurationManager::initialise::140,ConfigurationManager::getInstance::73,LoggerImpl::init::90,Logger::<clinit>::50,Class::initializeClass::-1,StartServer::<init>::69,Main::<init>::56,Main::main::163
DEBUG::Tue Oct 10 23:08:29 EDT 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::ensureStoreExists::410:
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(libgcj.so.7)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(SESecurityManagerImpl.java:379)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise(SESecurityManagerImpl.java:151)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise(SESecurityManager.java:53)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties(ConfigurationChecker.java:141)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise(ConfigurationManager.java:140)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:73)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init(LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit>(Logger.java:50)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.gudy.azureus2.ui.swt.StartServer.<init>(StartServer.java:69)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:163)

DEBUG::Tue Oct 10 23:08:29 EDT 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::ensureStoreExists::410:
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance(libgcj.so.7)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(SESecurityManagerImpl.java:379)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise(SESecurityManagerImpl.java:153)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise(SESecurityManager.java:53)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties(ConfigurationChecker.java:141)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise(ConfigurationManager.java:140)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance(ConfigurationManager.java:73)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init(LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit>(Logger.java:50)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.gudy.azureus2.ui.swt.StartServer.<init>(StartServer.java:69)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:163)

DEBUG::Tue Oct 10 23:09:58 EDT 2006::com.aelitis.azureus.core.networkmanager.VirtualChannelSelector::select::272:
  Caught exception on selector.select() op: 52
    ReadController::readSelectorLoop::77,ReadController::access$0::74,ReadController$1::runSupport::54,AEThread::run::69
java.lang.ArrayIndexOutOfBoundsException: 52
   at gnu.java.nio.SelectorImpl.getFDsAsArray(libgcj.so.7)
   at gnu.java.nio.SelectorImpl.select(libgcj.so.7)
   at com.aelitis.azureus.core.networkmanager.impl.VirtualChannelSelectorImpl.select(VirtualChannelSelectorImpl.java:423)
   at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.select(VirtualChannelSelector.java:272)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController.readSelectorLoop(ReadController.java:77)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController.access$0(ReadController.java:74)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController$1.runSupport(ReadController.java:54)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
DEBUG::Tue Oct 10 23:13:27 EDT 2006::com.aelitis.azureus.plugins.upnp.UPnPPlugin$6::log::305:
  org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://168.122.223.218:2869/upnphost/udhisapi.dll?content=uuid:cad2d845-1b91-4fd6-8101-a48b15e23247':java.net.ConnectException: Connection refused
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.net.ConnectException: Connection refused
   at gnu.java.net.PlainSocketImpl.connect(libgcj.so.7)
   at java.net.Socket.connect(libgcj.so.7)
   at java.net.Socket.connect(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPConnection.getSocket(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPConnection.getOutputStream(libgcj.so.7)
   at gnu.java.net.protocol.http.Request.dispatch(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPURLConnection.connect(libgcj.so.7)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:449)
   ...2 more

DEBUG::Tue Oct 10 23:13:28 EDT 2006::com.aelitis.azureus.plugins.upnp.UPnPPlugin$6::log::306:
  org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://168.122.223.218:2869/upnphost/udhisapi.dll?content=uuid:cad2d845-1b91-4fd6-8101-a48b15e23247':java.net.ConnectException: Connection refused
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.net.ConnectException: Connection refused
   at gnu.java.net.PlainSocketImpl.connect(libgcj.so.7)
   at java.net.Socket.connect(libgcj.so.7)
   at java.net.Socket.connect(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPConnection.getSocket(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPConnection.getOutputStream(libgcj.so.7)
   at gnu.java.net.protocol.http.Request.dispatch(libgcj.so.7)
   at gnu.java.net.protocol.http.HTTPURLConnection.connect(libgcj.so.7)
   at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:449)

```

I'm reporting this mostly because I'm confounded (tried re-installing azureus but that didn't change anything, might be a problem with a required package???).  But, also, since all I did was install via synaptic, theoretically other people should be seeing problems like this if they are starting from scratch.  


It is bad enough that azureus is so inefficient and user-hostile, but these problems make it downright worthless as a client.  Shame it's the only decent GUI-based one around.  I'm almost willing to try to get uTorrent running in wine just to get around this...

---

### Post by NeoLithium on 2006-10-10
Check out [here]("http://azureus.sourceforge.net/index_CVS.php"), download the new .jar file, and follow the instructions to replace it.  Gets Azureus working nice and smoothly.

---

### Post by keithjr on 2006-10-11
That worked crazily well... What's wrong with the package in the ubuntu repos?  I tried apt-get twice which surely must have replaced the Azureus2.jar file.

Either way, thanks!

---

### Post by Anduu on 2006-10-11
The version of azureus in the repos is older than dirt :(

---

### Post by keithjr on 2006-10-12
> **Anduu said:**
> The version of azureus in the repos is older than dirt :(

That actually makes less sense, since the package was working a few weeks ago before I reformatted and reinstalled ubuntu.  

Either way, the beta I just got has serious connectivity problems, every now and then it'll randomly say the port is firewalled even though it worked moments before.  And occasionally all transfer speeds will simply go to zero even though it shows MANY established connections in the swarm and reports NAT OK.  

I'll keep fiddling with it.

---

### Post by Anduu on 2006-10-12
> **keithjr said:**
> That actually makes less sense, since the package was working a few weeks ago before I reformatted and reinstalled ubuntu.  

Either way, the beta I just got has serious connectivity problems, every now and then it'll randomly say the port is firewalled even though it worked moments before.  And occasionally all transfer speeds will simply go to zero even though it shows MANY established connections in the swarm and reports NAT OK.  

I'll keep fiddling with it.

It makes total sense to me considering I had problems with the repo version and since installing the latest version it has been smooth sailing.

I would look for other causes...

---

### Post by keithjr on 2006-10-15
Even with the latest STABLE version, I still can't get above dialup-era download speeds and non-zero upload.  Oddly enough, it's pretty much the same scene with other the Bittorrent clients (and by other I mean BitTornado and the GNOME default).  Is there some wierd obscure firewall that the default dapper install throws on there but a breezy-to-dapper upgrade wouldn't solve?    I don't have a router and I don't have any bandwidth problems outside of bittorrent.  Altering ports doesn't seem to have any effect and that's about all I can do.


I am migrating back to windows if I can't solve this.  It's unacceptable.

---

### Post by keithjr on 2006-10-15
I migrated to 2.5.0.0 manually by replacing the .jar file, and now if I try to open the Options menu, Azureus crashes.  Running via console, I get this output:

```

Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.swt.views.configsections.ConfigSectionSharing
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.gudy.azureus2.ui.swt.views.ConfigView.initialize(ConfigView.java:264)
   at org.gudy.azureus2.ui.swt.Tab.<init>(Tab.java:184)
   at org.gudy.azureus2.ui.swt.Tab.<init>(Tab.java:93)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.showConfig(MainWindow.java:1297)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.showConfig(MainWindow.java:1312)
   at org.gudy.azureus2.ui.swt.mainwindow.UIFunctionsImpl.showConfig(UIFunctionsImpl.java:152)
   at org.gudy.azureus2.ui.swt.mainwindow.MainMenu$13.handleEvent(MainMenu.java:357)
   at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:62)
   at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1023)
   at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:2853)
   at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2572)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:113)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Caused by: java.lang.VerifyError: verification failed at PC 4 in org.gudy.azureus2.ui.swt.views.configsections.ConfigSectionSharing:<init>(()I): incompatible return type
   at java.lang.Class.initializeClass(libgcj.so.7)

```

](*,)  ](*,)  ](*,)  ](*,)  ](*,)



What's most odd is that the main problem ALL the bit torrent clients are having is that, even with torrents with at many as 5000+ seeders, they won't connect to more than a few of them at any given time.  Usually about 5-10 active connection, in a swarm of 5000!  I just saw the connection speed shoot up to 500kbps but that was all from ONE peer, so bandwidth is NOT an issue.  Why can't I get more connections??

---

