---
title: "transmission problems - files, install, etc"
date: 2018-03-04
forum: General Help
---

### Post by jgw on 2018-03-04
I was checking my stuff and seemed to have transmission in my browser (firefox) running.  I then checked system monitor and it wasn't there.  Then I checked the status and it was not found.  

My first thought was to install/update with (the right ppa was already installed):
sudo apt update
sudo apt install transmission

result snippit of that was:
invoke-rc.d: initscript transmission-daemon, action "start" failed.
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-03-04 10:27:28 PST; 7ms ago
  Process: 19698 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 19698 (code=exited, status=217/USER)
Mar 04 10:27:28 movies systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 04 10:27:28 movies systemd[1]: transmission-daemon.service: Main proces...ER
Mar 04 10:27:28 movies systemd[1]: Failed to start Transmission BitTorrent ...n.
Mar 04 10:27:28 movies systemd[1]: transmission-daemon.service: Unit entere...e.
Mar 04 10:27:28 movies systemd[1]: transmission-daemon.service: Failed with...'.

So, I decided to purge it (found a lot of files) and ran:
sudo apt-get remove --auto-remove transmission
sudo apt-get purge transmission
sudo apt purge transmission

I then searched for 'transmission and found: [https://pastebin.com/gRLukUtz](https://pastebin.com/gRLukUtz)

The above has a list of 200 files.  I then y ppa manager and purged the transmission ppa.  That got rid of at least over 100 of the files listed above.  (justg thought that was interesting)

So, given what I found I decided to stop and try and get some help.  I have all these files, I can't purge, I can't install, I have a problem.....

Thank you..........................

---

### Post by #&amp;thj^% on 2018-03-04
Try this to get rid of the whole kit and kaboodle:
```

sudo apt purge --autoremove transmission-gtk transmission-common transmission-dameon transmission-cli transmission-remote-cli transmission-remote-gtk
```

Sorry About that, I fixed the code

---

### Post by jgw on 2018-03-04
I did as you suggested.  Results:
eading state information... Done
E: Unable to locate package trasmission-gtk
E: Unable to locate package transmission-dameon

still have 112 transmission files

---

### Post by #&amp;thj^% on 2018-03-04
I have a few more than you left over but how dose this now show?:
```
apt policy transmission*
transmission-common:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
transmission-remote-cli:
  Installed: (none)
  Candidate: 1.7.0-1
  Version table:
     1.7.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
transmission-remote-gtk:
  Installed: (none)
  Candidate: 1.3.1-2build1
  Version table:
     1.3.1-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-proposed/universe amd64 Packages
     1.3.1-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
transmission-qt:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
transmission:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
transmission-daemon:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
transmission-cli:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
transmission-gtk:
  Installed: (none)
  Candidate: 2.92-3ubuntu2
  Version table:
     2.92-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```
So now the left overs are just icons and docs and manuals.

---

### Post by jgw on 2018-03-04
I kinda went a bit nuts and proceeded to reinstall transmission (sudo apt update then sudo apt install transmission) and it worked!  The problem, of course, is that its not the daemon (I could install that too but transmission is showing up in my browser so I can live with it)

What happened is very strange.  I started to get messages that my drive was full (.5tb drive).  I searched the drive for what was causing that but I could find nothing that would fill that drive.  Then the machine went bonkers and suddenly the machine was no longer full.  However, that being said I lost a LOT of stuff (transmission was just the tip of that iceburg).   I have another drive which I store data on so that part was fine but I lost all my setup files so I am fixing stuff on the fly.  I am going to ignore my transmission problem until I have time.  I have files from transmission-gtk, transmission, transmission-daemon, etc., transmission-qt, etc.,,   and a lot of them (as you saw).  

I also have clamtk running and it has found possible bad stuff but most of it would only apply to windows - interesting times.

I thank you for your help and I will get back to it but many fires to put out so I am trying to work on stuff that's not currently working (or barely)

Thanks again!

---

### Post by polyoz on 2018-03-05
Doing the right thing and updating this morning - it tells me that Transmission needs updating - so I go ahead and get the following output after the first failure of dpkg: error processing package transmission-daemon (--configure)  :-

> 0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up transmission-daemon (2.93-1ubuntu1~16.04.1ubuntu1) ...
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript transmission-daemon, action "start" failed.
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2018-03-05 16:11:36 AEDT; 8ms ago
  Process: 4315 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 4315 (code=exited, status=217/USER)


Mar 05 16:11:36 server1 systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 05 16:11:36 server1 systemd[1]: transmission-daemon.service: Main proce...ER
Mar 05 16:11:36 server1 systemd[1]: Failed to start Transmission BitTorrent...n.
Mar 05 16:11:36 server1 systemd[1]: transmission-daemon.service: Unit enter...e.
Mar 05 16:11:36 server1 systemd[1]: transmission-daemon.service: Failed wit...'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server1:~# 1 not fully installed or removed.




Tried uninstalling and reinstalling but no joy - same error
any clues please...

[COLOR=#000000]Operating System: Ubuntu 16.04.3 LTS[/COLOR]

---

### Post by #&amp;thj^% on 2018-03-05
Transmission-gtk stores your torrent files in your standard config folder, at ~/.config/transmission/torrents where it is your home folder.

The .config folder is usually hidden. To get there, open the File Browser and go to your home folder. Choose View > Show Hidden Files in the menu, then look for ".config". In that folder you'll find transmission, and the rest should be pretty straight-forward. 

Now Trnsmission-daemon If you're daemonizing transmission on Ubuntu (using the package transmission-daemon) and using a gui then:

This data is stored in **/var/lib/transmission-daemon/info** (_requires root access to view_, use sudo carefuly from the command line. Specifically, your torrents are in the directory **"/var/lib/transmission-daemon/info/torrents".**
So you will manually have to move those files by hand.
*****BTW the transmission-daemon from the PPA is filled with the same reports you both are reporting. *****
My advice or 2 cents worth is don't use the PPA and stay with Stable version in the standard repos. ;)

---

### Post by polyoz on 2018-03-05
Still the same issue - it wants to keep downloading the 2.93 version, how can I force it to download and use 2.92?

---

### Post by #&amp;thj^% on 2018-03-05
> **polyoz said:**
> Still the same issue - it wants to keep downloading the 2.93 version, how can I force it to download and use 2.92?

I think you missed the point with the PPA added: See this: [https://github.com/transmission/transmission/issues/537](https://github.com/transmission/transmission/issues/537)
As near as i can figure this points to **systemd permissions**. (OMG I Love systemd :p)
```
sudo transmission-daemon -g /etc/transmission-daemon/ -f
[sudo] password for me: 
[2018-03-05 13:22:32.643] Transmission 2.93 (3c5870d4f5) started (session.c:740)
[2018-03-05 13:22:32.643] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:971)
[2018-03-05 13:22:32.643] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1213)
[2018-03-05 13:22:32.643] RPC Server Whitelist enabled (rpc-server.c:1217)
[2018-03-05 13:22:32.643] UDP Failed to set receive buffer: requested 4194304, got 425984 (tr-udp.c:84)
[2018-03-05 13:22:32.643] UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:89)
[2018-03-05 13:22:32.643] UDP Failed to set send buffer: requested 1048576, got 425984 (tr-udp.c:95)
[2018-03-05 13:22:32.643] UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:100)
[2018-03-05 13:22:32.643] DHT Generating new id (tr-dht.c:311)
[2018-03-05 13:22:32.643] Using settings from "/etc/transmission-daemon/" (daemon.c:528)
[2018-03-05 13:22:32.643] Saved "/etc/transmission-daemon//settings.json" (variant.c:1266)
[2018-03-05 13:22:32.643] Port Forwarding (NAT-PMP) initnatpmp succeeded (0) (natpmp.c:70)
[2018-03-05 13:22:32.643] Port Forwarding (NAT-PMP) sendpublicaddressrequest succeeded (2) (natpmp.c:70)
[2018-03-05 13:22:40.643] Port Forwarding State changed from "Not forwarded" to "Starting" (port-forwarding.c:92)
[2018-03-05 13:22:53.643] DHT Attempting bootstrap from dht.transmissionbt.com (tr-dht.c:249)
[2018-03-05 13:24:40.644] Port Forwarding State changed from "Starting" to "???" (port-forwarding.c:92)


```

---

### Post by polyoz on 2018-03-05
Thanks

I found there was still a ppa there and I purged it and got an install OK - now trying to fix the white list so as I can connect

---

### Post by #&amp;thj^% on 2018-03-05
> **jgw said:**
> The problem, of course, is that its not the daemon (I could install that too but transmission is showing up in my browser so I can live with it)


Oh goodness let's see if we can fix that (If you want of course ;) ), open a terminal and run:
To set transmission as the default program for magnet links:
```

gvfs-mime --set x-scheme-handler/magnet transmission-gtk.desktop
```

And we can use Firefox also to set the right procedure.
you can set the default program to open magnet links. _This setting will override the system setting for magnet links_.

In Firefox Select Edit > Preferences > Applications, find the content type of magnet in the applications panel and select use other, then select the torrent program in **/usr/bin/ **directory.**(transmission-gtk)**

Bonus Tip: Here is a little trick you can use to transfer unfinished torrents from one torrent client to another, or from one OS to another OS on the same computer.

Right click your unfinished torrent and select copy magnet link. Now your magnet link is in the clipboard, you can open it up in another torrent client. For instance, in Transmission, select File > Open URL to open the magnet link.

---

### Post by jgw on 2018-03-05
thanks to everybody who responded!

I finally got transmission installed and it seems to be working.  so I will mark this one as solved.  I just left all the existing files alone (after purging everything I could for each iteration of transmission) and reinstalled and, this time, its all working, including the daemon.  

Life is good!

---

### Post by typos1 on 2018-03-07
Software updater said there was an update earlier today, I looked and it was a partial upgrade, not sure why only a couple of things were going to be updated and transmission was one, anway I installed them.

Hours later I happened to download a torrent and I was asked to save the file rather than open using transmission, it turns out the entire transmission app has been removed from my computer!

Just came across this thread searching to tr and find out what the hell is going on - anyone know why this would happen ?

---

### Post by #&amp;thj^% on 2018-03-07
Well a partial upgrade was never a good idea to take, I would have searched first as to why a partial upgrade was happening.
 
But this has been a ongoing topic here for the past couple of days now.

[https://github.com/transmission/transmission/issues/537](https://github.com/transmission/transmission/issues/537)
And
[https://ubuntuforums.org/showthread.php?t=2386355](https://ubuntuforums.org/showthread.php?t=2386355)

---

### Post by typos1 on 2018-03-07
I ve never had a problem with a partial upgrade before, although I ve rarely done them, I usually rely on software updater to get things right, not had it get anything wrong before. 

I dont get any messages about the daemon, transmission just isnt there and cant be installed apparently.

EDIT: couldnt install it from the terminal, but could from the software centre.

SECOND EDIT: it says "installing" goes to 100% then the "install" icon returns and transmission isnt in my software lists, guess I ll have to use an older version.

---

### Post by #&amp;thj^% on 2018-03-07
> **typos1 said:**
> I ve never had a problem with a partial upgrade before, although I ve rarely done them, I usually rely on software updater to get things right, not had it get anything wrong before. 

I dont get any messages about the daemon, transmission just isnt there and cant be installed apparently.

The update with a PPA to version 2.93 and systemd did not mix well.
Lets see what apt has to offer
```
apt search transmission
```

---

### Post by typos1 on 2018-03-07
> **1fallen said:**
> The update with a PPA to version 2.93 and systemd did not mix well.
Lets see what apt has to offer
```
apt search transmission
```

```
transmission/xenial,xenial 2.93-1ubuntu1~16.04.1ubuntu1 all
  lightweight BitTorrent client

transmission-cli/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (command line programs)

transmission-common/xenial,xenial 2.93-1ubuntu1~16.04.1ubuntu1 all
  lightweight BitTorrent client (common files)

transmission-daemon/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (daemon)

transmission-dbg/xenial 2.92-0ubuntu0.16.04.2 amd64
  lightweight BitTorrent client (debug symbols)

transmission-gtk/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (GTK+ interface)

transmission-qt/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (Qt interface)

transmission-remote-cli/artful,artful 1.7.0-1 all
  ncurses interface for the Transmission BitTorrent daemon

transmission-remote-gtk/artful 1.3.1-2 amd64
  GTK+ interface for the Transmission BitTorrent daemon
```

Thats what I get.

---

### Post by #&amp;thj^% on 2018-03-07
> **typos1 said:**
> ```
transmission/xenial,xenial 2.93-1ubuntu1~16.04.1ubuntu1 all
  lightweight BitTorrent client

transmission-cli/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (command line programs)

transmission-common/xenial,xenial 2.93-1ubuntu1~16.04.1ubuntu1 all
  lightweight BitTorrent client (common files)

transmission-daemon/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (daemon)

transmission-dbg/xenial 2.92-0ubuntu0.16.04.2 amd64
  lightweight BitTorrent client (debug symbols)

transmission-gtk/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (GTK+ interface)

transmission-qt/xenial 2.93-1ubuntu1~16.04.1ubuntu1 amd64
  lightweight BitTorrent client (Qt interface)

transmission-remote-cli/artful,artful 1.7.0-1 all
  ncurses interface for the Transmission BitTorrent daemon

transmission-remote-gtk/artful 1.3.1-2 amd64
  GTK+ interface for the Transmission BitTorrent daemon
```

Thats what I get.

And this also:....And it would be helpful if I knew which you had installed previously IE: GTK or Daemon
```
apt policy transmission-gtk
```

---

### Post by typos1 on 2018-03-07
Sorry, in all the years I ve used Ubuntu I never took any notice which version of Transmission was used - never really needed to, its always been installed with Ubuntu, I didnt even realise there were GTK and daemon versions. At a guess I d say the GTK version was previously installed, as I havent got the Daemon errors others have reported.

```
transmission-gtk:
  Installed: (none)
  Candidate: 2.93-1ubuntu1~16.04.1ubuntu1
  Version table:
     2.93-1ubuntu1~16.04.1ubuntu1 500
        500 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu xenial/main amd64 Packages
     2.92-2ubuntu3.1 500
        500 http://gb.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu artful-security/main amd64 Packages
     2.92-2ubuntu3 500
        500 http://gb.archive.ubuntu.com/ubuntu artful/main amd64 Packages
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

---

### Post by #&amp;thj^% on 2018-03-07
Chances are good then if you** purge** the PPA "ppa.launchpad.net/transmissionbt" with the "ppa-purge package"
You should be good with update && upgrade.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:transmissionbt/ppa
```
Sometimes like this, it can lull us to sleep and Bam!
Good Luck! :)

---

### Post by typos1 on 2018-03-07
Great, thanks I ll give it a go. It only purges the ppa and deffo wont get rid of the partially downloaded files I have in the Transmission folder ?

---

### Post by #&amp;thj^% on 2018-03-07
It should not, but back it up anyway nothing is a **given**..;)
And Please let us know how it goes for you here.
Kind Regards

---

### Post by typos1 on 2018-03-07
> **1fallen said:**
> Chances are good then if you** purge** the PPA "ppa.launchpad.net/transmissionbt" with the "ppa-purge package"
You should be good with update && upgrade.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:transmissionbt/ppa
```
Sometimes like this, it can lull us to sleep and Bam!
Good Luck! :)

Hmm, after running ```
sudo ppa-purge ppa:transmissionbt/ppa
``` I get this :

 ```
Warning:  apt-get update failed for some reason
```

---

### Post by typos1 on 2018-03-08
I just removed the ppa manually, then installed transmission ad it seems successful . .  so far at least. 

Thanks for your help.

---

