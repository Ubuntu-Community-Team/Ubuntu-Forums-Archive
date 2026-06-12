---
title: "Problems with Azureus"
date: 2007-05-01
forum: General Help
---

### Post by blackdevil on 2007-05-01
I'm running Feisty with Beryl and I just installed Azureus. When I run it, the language selection screen comes up for about half a second then it just closes out... Any suggestions? I installed it through synaptic, so it grabbed all the other programs it needs.

---

### Post by taurus on 2007-05-01
Run it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
azureus
```

---

### Post by blackdevil on 2007-05-01
An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaadd054c9f, pid=25068, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9c9f]
#
# An error report file with more information is saved as hs_err_pid25068.log

---

### Post by blackdevil on 2007-05-01
Is that what you needed?

---

### Post by blackdevil on 2007-05-01
anyone? Is this due to 64bit drivers and 32bit versions for firefox??

---

### Post by briansvgs on 2007-05-01
I am having the same problem. I am running xubuntu feisty. I am running azureus 2.50 from the repositories. My error is

[FONT="Courier New"]changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=11699, tid=3084667792
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid11699.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)[/FONT]

I tried running azureus with gksu just to see if it would work, and it does. Because this compromises some of the security of my system, I don't want to run it like this all of the time. When I run it as root, this is the output:

changeLocale: *Default Language* != English (United States). Searching without ountry..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US, using 'English (default)'
DEBUG::Tue May 01 12:26:55 GMT-05:00 2007::com.aelitis.azureus.core.networkmanaer.VirtualChannelSelector::select::272:
  Caught exception on selector.select() op: Operation not permitted
    NonBlockingReadWriteService$1::runSupport::80,AEThread::run::69
java.io.IOException: Operation not permitted
        at sun.nio.ch.EPollArrayWrapper.epollCtl(Native Method)
        at sun.nio.ch.EPollArrayWrapper.updateRegistrations(EPollArrayWrapper.jva:202)
        at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:183)
        at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:65)
        at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:69)
        at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:80)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelecorImpl.select(VirtualChannelSelectorImpl.java:446)
        at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.selec(VirtualChannelSelector.java:272)
        at com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWrteService$1.runSupport(NonBlockingReadWriteService.java:80)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

briansvgs@briansvgs-laptop:~$ gksu azureus
StartSocket: passing startup args to already-running Azureus java process listeing on [127.0.0.1: 6880]

---

### Post by kelvin spratt on 2007-05-01
its a problem with java ihave abandoned the frog for a while till they sort it out allso safe peer has done a runner
the frog is not the frog as we know it

---

### Post by blackdevil on 2007-05-01
I tried GKSU and this is what I got:

changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
  Inconsistent stream length for 'http://192.168.1.1:2869/IGatewayDeviceDescDoc': expected = 3444, actual = 3445
    ResourceDownloaderURLImpl$2::runSupport::319,AEThread::run::69
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b555b3f2301, pid=27322, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# V  [libjvm.so+0x321301]
#
# An error report file with more information is saved as hs_err_pid27322.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


Pretty much the same thing

---

### Post by blackdevil on 2007-05-01
Any suggestions for another p2p bit torrent application than?

---

### Post by blackdevil on 2007-05-01
Okay, I just put on the gcj version and it works now. Hope this helps someone else. Java sucks

---

### Post by stchman on 2007-05-01
> **blackdevil said:**
> I'm running Feisty with Beryl and I just installed Azureus. When I run it, the language selection screen comes up for about half a second then it just closes out... Any suggestions? I installed it through synaptic, so it grabbed all the other programs it needs.

I tried Azureus and all it did was give me problems.  Ktorrent is a better bitorrent client for Ubuntu IMO.

sudo apt-get install ktorrent

You will like it.

---

### Post by blackdevil on 2007-05-01
now I got NAT errors.... something I guess is common with the WRT54G router

---

### Post by blackdevil on 2007-05-01
sweet, Ktorrent works fine. Any recommendations for a good place to get bit-torrents?

---

### Post by stchman on 2007-05-01
> **blackdevil said:**
> sweet, Ktorrent works fine. Any recommendations for a good place to get bit-torrents?


I told you it was better than Azureus.  It is nearly as good as utorrent.

Remember that you need to open up the proper ports on your router (port forwarding).  In the configuration section there will be the ports that ktorrent uses.  Also give your PC that you will be downloading on a static IP and use the openDNS numbers.

I use piratebay.org or torrentspy.com.

---

### Post by ndvsky on 2007-05-01
> **blackdevil said:**
> anyone? Is this due to 64bit drivers and 32bit versions for firefox??

yes to me! I'm using 32bits version for Firefox with Sun Java 32 bits from repositories

The solution:

sudo update-alternatives --config java

and choose the option for 64bits java.

---

### Post by SlackLagg on 2007-05-02
> **blackdevil said:**
> now I got NAT errors.... something I guess is common with the WRT54G router


Did you setup port forwarding ?  ( I have the same router) 

I was having the same Runtime and core dump problem with Azureus. I got it  working again with Sun Java after I used 

```
sudo update-alternatives --config java 
```

and selected the non Sun option. I then restarted Azureus and did a clean exit (via File->Exit . I started getting the core dumps after I did a hard-reset of the machine so I'm sure that screwed up something) 

I then re-ran 
```
sudo update-alternatives --config java 
```

and reselected Sun Java as the option. It seems to work...for now...

[-o<

---

