---
title: "Azureus - closes on open"
date: 2006-12-06
forum: General Help
---

### Post by Drezliok on 2006-12-06
I was curious as to why it did this and desided to try running it in a terminal to see what happens.


```
drezliok@TuxEater:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Wed Dec 06 11:31:31 EST 2006::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::92:
    IncomingSocketChannelManager::start::299,IncomingSocketChannelManager::<init>::110,TCPNetworkManager::<init>::111,TCPNetworkManager::<clinit>::41,NetworkManager::getMinMssSize::151,ByteBucket::ensureByteBucketMinBurstRate::150,ByteBucket::<init>::63,ByteBucket::<init>::49,TransferProcessor::<init>::60,NetworkManager::<init>::124,NetworkManager::<clinit>::50,AzureusCoreImpl::<init>::177,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:299)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:110)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:111)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:41)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:151)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:60)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:177)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:92)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
[COLOR="Blue"]DEBUG::Wed Dec 06 11:31:31 EST 2006::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::start::93:
  java.net.BindException: Address already in use
        at sun.nio.ch.Net.bind(Native Method)
        at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:119)
        at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:59)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.start(VirtualBlockingServerChannelSelector.java:79)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.start(IncomingSocketChannelManager.java:299)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.IncomingSocketChannelManager.<init>(IncomingSocketChannelManager.java:110)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<init>(TCPNetworkManager.java:111)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPNetworkManager.<clinit>(TCPNetworkManager.java:41)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.getMinMssSize(NetworkManager.java:151)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.ensureByteBucketMinBurstRate(ByteBucket.java:150)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:63)
        at com.aelitis.azureus.core.networkmanager.impl.ByteBucket.<init>(ByteBucket.java:49)
        at com.aelitis.azureus.core.networkmanager.impl.TransferProcessor.<init>(TransferProcessor.java:60)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(NetworkManager.java:124)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(NetworkManager.java:50)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:177)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:92)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

DEBUG::Wed Dec 06 11:31:31 EST 2006::com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl::receiveLoop::286:
  java.net.BindException: Address already in use
        at java.net.PlainDatagramSocketImpl.bind0(Native Method)
        at java.net.PlainDatagramSocketImpl.bind(PlainDatagramSocketImpl.java:82)
        at java.net.DatagramSocket.bind(DatagramSocket.java:368)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:210)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:261)
        at java.net.DatagramSocket.<init>(DatagramSocket.java:234)
        at com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl.receiveLoop(PRUDPPacketHandlerImpl.java:187)
        at com.aelitis.net.udp.uc.impl.PRUDPPacketHandlerImpl$1.runSupport(PRUDPPacketHandlerImpl.java:107)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0692d02, pid=5800, tid=3085137584
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid5800.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)[/color]

```

I highlighted what I think is the problem is but I'm new to useing the terminal this way so I don't really know what to look for. So I copy pasted the whole thing.

I'm Using Xubuntu right now, I have a p4 2.66ghz. I noticed it did not run smooth at all on Ubuntu. First day it ran fine, infact better than fine. but after shutting the system down and going to bed it will close itself out. I tried using the gcj version but it ran slower and couldn't connect right.

---

### Post by bscbrit on 2006-12-06
I'm not sure that I can help but I'm also not sure I understand what I am reading.  Are you running Azureus using a VM?  Is your version of Xubuntu being run this way?  If so, does it work when it is run as a normal program?  I'll try to help when I can understand what is happening.  I am running Azureus as I type this and it seems to run fine.  I suspect, therefore, that this is something to do with your configuration rather than the program itself but, of course, I could be wrong again!

---

### Post by Drezliok on 2006-12-06
I'm am trying to use Azureus with out the nativly compiled gcj version. I want it to use Sun Java instead. The non-free stuff.

I am using Xubuntu Edgy Eft 6.10.

There are 2 packages for Azureus, One that is standerd and another that is natively compiled code for use by gij.

I want to use the standard. Why? It downloads faster, but seems unstable. I'm trying to find out if I need to change settings to get it to work right.

Right now I am using Azureus-gcj because it works, BUT it's slow as ever for downloading. I was downloading at 15k per torrent. not I am downloading at 3k per torrent. That much performance loss for just using a differing package.

---

### Post by Drezliok on 2006-12-06
Nevermind. I'm going to switch to deluge for now. It's not as feature heavy and doesn't do all of what I want but maybe future versions will work better.

Or when I have al;ot of time I'll learn how to compile it myself.

---

### Post by bscbrit on 2006-12-07
Azureus takes quite a while to get up to speed, and it will also depend on how many other peers are available for you to download from.  It will also be limited to your ISP connection speed.  I'm managing downloads of 150 -200 kbs! I'm also using 6.10 and azureus so the software is certainly capable of working.  Perhaps we should spend some time looking at your configuration?

---

### Post by Get_Ya_Wicked_On on 2006-12-10
I'm having the exact same problem, on a mildly configured Ubuntu.

It worked just fine for about the first 4 days I had it.

And it just started doing that "close-on-start" deal. 

It happens with my Totem movie player, as well on occasion.

```


# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=6553, tid=3084531376
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6553.log


```

That is when I'm under AIGLX using Beryl

```


# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=6739, tid=3084797616
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  0x00000000
#
# An error report file with more information is saved as hs_err_pid6739.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#


```

This is when I'm using AIGLX, (yep, you guessed it), when NOT using Beryl.

---

### Post by matt_risi on 2006-12-10
Yeah the same's happened to me, I just got pissed off and switched to Deluge. Not as pretty as Azureus though, they really had the right idea with that little gem.

---

### Post by Get_Ya_Wicked_On on 2006-12-10
[http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)

Well, there's a solution...

---

### Post by desimo on 2006-12-11
Thanks Wicked, I had the exact same problems as described above (azureus with non-free java crashes on startup), and then I did one of these:
```

sudo apt-get --purge remove azureus

```
Reinstalled following instructions above, and now it's working just as it was before.

---

### Post by gkokaisel on 2007-03-12
removing it worked for me, but noth from the terminal. I had to go to the synaptic package manager and select complete removal option and then I had to reinstall it from there too. The add/remove programs thingamajigger didn't work out so well.

---

