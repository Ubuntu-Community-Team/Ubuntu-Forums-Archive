---
title: "azureus keeps crashing"
date: 2007-09-12
forum: General Help
---

### Post by Chymera on 2007-09-12
So, the thing is my azureus closes itself spontaneously; no error message, no nothing, i don't need to click the close button, i dont even need to be at the computer, and poof, it's gone!

What an easy way to close azureus, don't you think? Now turning it back on is a completely different story. I can't just click the launcher under apps, because that will exit azureus about 1 sec after the program starts. While azureus may have spared me the trouble of getting an error message when it crashed, it did create some log files, apparently dedicated only to the connaisseurs, which it seamlessly hid under home>.azureus>logs.

Now, if i delete those logs i get it up and running again, untill the next time it decides it's time to close...

Any ideas how to fix this permanently?

---

### Post by prince_niceguy on 2007-09-12
start azureus from terminal and post the error here. that shoudl give some starting point to fix this permanently

---

### Post by Chymera on 2007-09-12
you mean to paste the log? i told you, i dont get an error message.

---

### Post by prince_niceguy on 2007-09-13
can you post what is the part of the error log??

that should help...

---

### Post by thesnarky1 on 2007-09-14
This just started happening to me as well. I keep fairly up to date on all new package updates that need to be installed, and I recall that Azureus worked just fine last week, or the week before. I patched today (and once last week) and all of a sudden Azureus is crashing. I've tossed my error logs up onto my website, with hopes that this'll help you solve it. Running from a console produces the following output:
```
snarky@Blade:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4846172, pid=11714, tid=3084688272
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid11714.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

The error logs can be found [here]("http://thesnarky.com/html/azureus/")

Thanks for the help!

---

### Post by hadeshorn on 2007-09-14
My azureus crashes as well. Log here

hades@wolverine:~$ azureus
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'

Segmentation fault (core dumped)

---

### Post by thesnarky1 on 2007-09-14
Figure I'll add as much info as possible. I had installed classpath-tools the day before to get access to javap. I removed it, and Azureus kept crashing. I thought it might be a config issue, so I removed it, apt-get installed it again, kept crashing. Deleting the config file/.azureus directory let Azureus stay open long enough to run the config wizard, before crashing as soon as the main window came up. Hope this helps!

---

### Post by Chymera on 2007-09-14
> [1409 19:48:12] Alert:1:UPnP: Mapping 'Incoming Peer Data Port (UDP/59137)' has been reserved by '10.10.2.62' - please select a different port
[1409 19:48:12] Alert:1:UPnP: Mapping 'UDP Tracker Client Port (UDP/59137)' has been reserved by '10.10.2.62' - please select a different port
[1409 19:48:12] Alert:1:UPnP: Mapping 'Incoming Peer Data Port (TCP/59137)' has been reserved by '10.10.2.62' - please select a different port
[1409 19:48:12] Alert:1:UPnP: Mapping 'Distributed DB (UDP/59137)' has been reserved by '10.10.2.62' - please select a different port
comes with the name alerts_1.log

and>  [1409 19:39:48] DEBUG::Fri Sep 14 19:39:48 EEST 2007  Data Missing /media/sdb1/Torrentz/livecd-amd64-installer-2007.0
[1409 19:39:48] DEBUG::Fri Sep 14 19:39:48 EEST 2007  Data Missing /media/sdb1/Torrentz/SabayonLinux-x86_64-3.4e.iso
comes under debug_1.log

---

### Post by Chymera on 2007-09-15
anyone?

---

### Post by Chymera on 2007-09-15
woah, seems the error logs vary from one occasion to the next

> [1609 01:53:14] DEBUG::Sun Sep 16 01:53:14 EEST 2007::com.aelitis.azureus.plugins.upnp.UPnPPlugin$9::log::504:
[1609 01:53:14]   org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://86.107.182.210:2869/upnphost/udhisapi.dll?content=uuid:013ee4cc-bc71-4ba2-8676-8cd74fc9e19d':java.net.NoRouteToHostException: No route to host
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
	at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.net.NoRouteToHostException: No route to host
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
	at java.net.Socket.connect(Socket.java:519)
	at sun.net.NetworkClient.doConnect(NetworkClient.java:155)
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:382](www.http.HttpClient.openServer(HttpClient.java:382))
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:509](www.http.HttpClient.openServer(HttpClient.java:509))
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:231)
	at sun.net.[www.http.HttpClient.New(HttpClient.java:304](www.http.HttpClient.New(HttpClient.java:304))
	at sun.net.[www.http.HttpClient.New(HttpClient.java:316](www.http.HttpClient.New(HttpClient.java:316))
	at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:817](www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:817))
	at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:769](www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:769))
	at sun.net.[www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:694](www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:694))
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:447)
	... 2 more

[1609 01:53:14] DEBUG::Sun Sep 16 01:53:14 EEST 2007::com.aelitis.azureus.plugins.upnp.UPnPPlugin$9::log::504:
[1609 01:53:14]   com.aelitis.net.upnp.UPnPException: Root device location 'http://86.107.182.210:2869/upnphost/udhisapi.dll?content=uuid:013ee4cc-bc71-4ba2-8676-8cd74fc9e19d' - data read failed
	at com.aelitis.net.upnp.impl.UPnPImpl.downloadXML(UPnPImpl.java:481)
	at com.aelitis.net.upnp.impl.device.UPnPRootDeviceImpl.<init>(UPnPRootDeviceImpl.java:95)
	at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:220)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at org.gudy.azureus2.core3.util.ThreadPool$3.runSupport(ThreadPool.java:523)
	at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://86.107.182.210:2869/upnphost/udhisapi.dll?content=uuid:013ee4cc-bc71-4ba2-8676-8cd74fc9e19d':java.net.NoRouteToHostException: No route to host
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
	... 1 more
Caused by: java.net.NoRouteToHostException: No route to host
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
	at java.net.Socket.connect(Socket.java:519)
	at sun.net.NetworkClient.doConnect(NetworkClient.java:155)
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:382](www.http.HttpClient.openServer(HttpClient.java:382))
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:509](www.http.HttpClient.openServer(HttpClient.java:509))
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:231)
	at sun.net.[www.http.HttpClient.New(HttpClient.java:304](www.http.HttpClient.New(HttpClient.java:304))
	at sun.net.[www.http.HttpClient.New(HttpClient.java:316](www.http.HttpClient.New(HttpClient.java:316))
	at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:817](www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:817))
	at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:769](www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:769))
	at sun.net.[www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:694](www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:694))
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:447)
	... 2 more
and this is called debug_1.log

---

### Post by prince_niceguy on 2007-09-15
which java version you are using ... you can get that witht he following command

java --version

in the terminal.

if it is 1.6 see if you can get hold of 1.4 or 1.5 java from sun's website and then install the same... and change the azureus start up script to point java to the location which you installed...

---

### Post by dannyboy74 on 2007-09-16
Me too have similar kind of problem but different error output. :(
I checked my Java in terminal and I have 1.6.0
How do I do all the things you just described?  Some specific steps to do all those things would help.

---

### Post by mojoman on 2007-09-16
I managed to get around this by unistalling some java version and installing another, but I don't remember which. The thing is, after an upgrade the problems just reapperaed. It's a shame because I really like Azureus but I gave up and switched to Deluge. Earlier on I had tried some other p2p clients but I didn't take to them but I must say that Deluge does it for me. It isn't in the repositories but can be downloaded _[here]("http://deluge-torrent.org/downloads")_

---

### Post by JBAlaska on 2007-09-16
deluge does seem to be a nice client, however many private sites only allow the mainstream clients.

I'm using Azureus with java version 1.5 with absolutely no problems, maybe stick with that runtime version and don't upgrade is the short term fix.

---

### Post by Chymera on 2007-09-16
you mean delete a newer version for the sake of an older one :-/ is it a compatibility issue? if so shouldnt we expect azuresu to get updated?

---

### Post by Earthwormzim on 2007-09-16
Every once in a while, my Azureus does the same thing.  I've found that it tends to happen after it gets closed forcefully, such that it doesn't have time to save it's current state (some file gets corrupted, I guess).

I have found a way to fix this, although it's a bit annoying.  At least it will prevent you from having to re-install it, though.

Just delete the entire ".azureus" folder inside your home/[username] directory.  The only problem now, is that Azureus will think that you have not set up anything....so you'll wind up having to go through your initial setup again.  

As far as resuming your torrents go...in that ".azureus" folder that you just deleted, there is a folder called "torrents".  Locate each torrent, and open them again in Azureus...if you save it to the same place you saved it to in the first place, it will resume from where it left off.

Let me know if this works out for any of you!

---

### Post by prince_niceguy on 2007-09-16
No you do not need to delete the current java version. Just download the java 1.5 from website (java.sun.com). When you install it will just create a directory in your home folder or folder where you run from.

Use that directory in the azureus script. find the line.

JAVA_PROGRAM_DIR="paht to java home/bin" directory.

---

### Post by amadeus266 on 2007-09-17
I have jre versions 1.4, 1.5, and 1.6 installed. before deleting the .azureus folder it shows the splash screen then when it displays the main screen for about 2 seconds and closes. after deleting the .azureus folder, it shows the splash screen, goes to the setup screen and closes before I get a chance to see everything on the screen. I never had problems with ti before regardless which version of jre I had installed.

---

### Post by dannyboy74 on 2007-09-17
I got help in another thread just do this in terminal and re-install Azureus it's basically what EarthWormZim said but with less explaining.

```
mv .azureus .azureus_backup
```

---

### Post by anoolio on 2007-09-18
Mine crashes as well. Used to run okay the first time I installed it but ever since re-start, its up for 1 second and poof its gone.  Here's the terminal error message: PLEASE HELP!

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=6913, tid=3084766096
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6913.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

---

### Post by throntax on 2007-09-18
I have just had the same problem, and googled it a bit. It seems quite a few people have the same problem at the moment! I found another forum:

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/71220](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/71220)

Where deleting the log files works, strangely, so rather than just delete the whole .azureus directory, just delete the logs. It has the same effect as what EarthWormZim
says, only you don't have to stuff around finding torrents afterwards...

```
rm -Rf ~/.azureus/logs/*
```

Worked for me, but no closer to actually understanding what went wrong...

---

### Post by Earthwormzim on 2007-09-18
Ah!!!  I figured I didn't have to go THAT far (deleting the whole folder)...but I was just too lazy to figure out what files were causing the crash.

---

### Post by throntax on 2007-09-19
Yeah, thank the guys on the other forum for that! Azureus actually crashed again, with a different error, after a reboot, but deleting the logs worked again. I'm going to see if going to tools -> options -> Logging and checking the box to disable logging has any effect...

---

### Post by Chymera on 2007-09-19
well? will you tell us?

---

### Post by zilebune on 2007-09-19
Hey, you guys - for me it turned out that this goes deeper than deleting the logs:

Having Azureus halted in the middle of a download, I rebooted and deleted the logs hoping that this would fix it. Below are the first two attempts of runing the program after reboot.

Could you please help with this issue, because my java skills ~0.

> root@boo:~# cd /home/boo/.azureus/
[email]root@boo:~/.azur[/email]eus# rm *.log
[email]root@boo:~/.azur[/email]eus# azureus 
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4851172, pid=5685, tid=3084250000
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid5685.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted
[email]root@boo:~/.azur[/email]eus# azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x000001fc, pid=5746, tid=3084585872
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  0x000001fc
#
# An error report file with more information is saved as hs_err_pid5746.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted
[email]root@boo:~/.azur[/email]eus#

Running Ubuntu 7.04 with Azureus updated from apt archive [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty

---

### Post by zilebune on 2007-09-19
SOLVED, please check this link -> [https://launchpad.net/ubuntu/+source/azureus/+bug/95183](https://launchpad.net/ubuntu/+source/azureus/+bug/95183)

> 
A workaround has been suggested in the german ubuntu forum ([http://forum.ubuntuusers.de/viewtopic.php?p=427193#427193):](http://forum.ubuntuusers.de/viewtopic.php?p=427193#427193):)

 * Download the original Azureus package from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) (version 2.5.0.4 atm).
 * Replace the file /usr/share/java/Azureus2.jar with the same file from the original package.


---

### Post by anoolio on 2007-09-22
thank you zilebune for this fix. just one (again, am very new to this) question, when I try to replace the file as you suggest, the system doesn't give me permission, even though I am the only user and have set up my Ubuntu account. How do I get around that?

---

### Post by zilebune on 2007-09-23
> **anoolio said:**
> thank you zilebune for this fix. just one (again, am very new to this) question, when I try to replace the file as you suggest, the system doesn't give me permission, even though I am the only user and have set up my Ubuntu account. How do I get around that?

Hi,

You have to precede the command with 'sudo' like this:

```

sudo /new/address/azureus.jar /old/address/azureus.jar

```

Then it will ask for you password and that's it!
It's a security thing implemented by default in Ubuntu so you don't mess up your system using the root account. Find out more with 'man sudo'.

---

### Post by anoolio on 2007-09-23
THANKS MUCH, mate... this did the trick and is working fine....!!

---

### Post by defe007 on 2007-11-01
> **zilebune said:**
> SOLVED, please check this link -> [https://launchpad.net/ubuntu/+source/azureus/+bug/95183](https://launchpad.net/ubuntu/+source/azureus/+bug/95183)

Yeap, this worked for me also.  Thanks for the help!

---

### Post by bengoza on 2007-11-02
> **Earthwormzim said:**
> Every once in a while, my Azureus does the same thing.  I've found that it tends to happen after it gets closed forcefully, such that it doesn't have time to save it's current state (some file gets corrupted, I guess).

I have found a way to fix this, although it's a bit annoying.  At least it will prevent you from having to re-install it, though.

Just delete the entire ".azureus" folder inside your home/[username] directory.  The only problem now, is that Azureus will think that you have not set up anything....so you'll wind up having to go through your initial setup again.  

As far as resuming your torrents go...in that ".azureus" folder that you just deleted, there is a folder called "torrents".  Locate each torrent, and open them again in Azureus...if you save it to the same place you saved it to in the first place, it will resume from where it left off.

Let me know if this works out for any of you!

Yes! This worked for me. I might stick with Deluge though if Azureus is going to keep pulling this crap. Side note: I'm using version 2.5.0.0, and one of the things I tried to do to fix this was download the new one (it's attached to something called Vuze now) off sourceforge and I kept getting a "Not Found" error when I clicked the link. It's probably not related, but I thought maybe it's worth mentioning. Anybody have any insight into this?

Most importantly though:  Thank you Earthwormzim! You Rock! :guitar:

---

### Post by L815 on 2007-11-06
Little late for the reply I assume, but I would like to say thanks for the fix :D. Worked fine; the reconfiguring wasn't a big hassle unlike having to reinstall the entire thing.

---

### Post by denham2010 on 2007-11-10
I had a similar problem when clicking on my downloading torrents to view the file info. Azureus crashed with a java error. I was using Java 1.6 and the official repo azureus for gutsy.

I jus removed the repo azureus and installed v3 from the azureus/vuze site and all works perfectly again.

---

