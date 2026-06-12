---
title: "Which issue do I start with?"
date: 2007-12-30
forum: General Help
---

### Post by ne_plus_ultra_1 on 2007-12-30
OK, here we go.

I really like Ubuntu.  I think we can start there.

Lotsa issues for me right now though.

My MA111 wireless didn't work BUT WAS recognized as a wired and I could configure nothing.

I put in a lan card and a really long wire to get the internet working at all.  I can't keep the wire as everyone is walking on it.  I mostly just wanted to see the internet work at all.

Synaptic worked or seemed to at least the first time I used it.  It "downloaded" the packages of ndiswrapper** (which the help file calls ndisgtk?)** and now claims they are installed.  I can not find them in the place that the help file says I can though which I believe was system>administration>ndisgtk..

NOW I try to use Synaptic and it doesn't find the 7.1 CD nomatter which drive i put it in...  It doesn't even try to look online either.  I don't see any options for this.

I see a prism2 util called linux-wlan-ng that I'd like to get working but Synaptic's not finding the 7.1 CD.

I used an earlier release before and the package manager found LOADS of packages on the internet and this is not happening at all now.

If anyone is going to suggest command line stuff, please be specific and include all steps as I don't know anything about that besides dmesg.  I hated the switch from command line to GUI going from C64 to Amiga but I have become used to it and have no inclination to go back to antiquated methodologies at this point.  Let's keep this GUI is at all possible.

SO: 
Synaptic is not finding the CD or looking online and ndisgtk doesn't exist or work as the help file says it does.

MA111 doesn't work although I find plenty of people that get it working on a google search.

I'd like to get my nvidia graphics card working and when I went to restricted hardware it told me I needed something that I don't have...

Why can't I run ndiswrapper after I supposedly installed the package?

As I type this I watch my kids play Warhawk on the PS3 and notice how great it is when things just work...

Help appreciated as I would like to make this box just work too.

Best,
-ultra

---

### Post by Vadi on 2007-12-30
ndisgtk is the graphical configuration for ndiswrapper. ndiswrapper alone is just in the terminal (I actually prefer the terminal version, it's easier to get around with).

I found a guide here ([click]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111?highlight=%28MA111%29")), does that work?

Though, regarding your repositories problems. The CD itself doesn't have too many packages, so it's best to disable it. Go to System - Administration - Software Sources, and uncheck the CD. Then, check off the first 4 lines (all except source code). I think what happened is because you didn't have Internet during the installation, it disabled online stuff (stupid, I know, there's a bug report about this).

After that, synaptic will properly be able to find online repositories. Also, in the same software sources, go to updates, and check off the first 2 lines (gutsy-security and gutsy-updates), so that way your system will be up to date and all too.

---

### Post by ne_plus_ultra_1 on 2007-12-30
AWESOME!

Vadi, that's good help.

Synaptic already downloaded a bunch of something or other...

As far as the guide, I'll check that out now.

The update thing DID try to check for updates when I installed and I believe I had to cancel it as I didn't have internet.  So bug, probably not.  Dumb design to permanently disable if can't connect at install, probably yes.

Wicked good help bro.

Please check this post again if possible when you get the chance.  I'll let you know how I do with the MA111 usb wireless adapter.

Best,
-ultra




.

---

### Post by ne_plus_ultra_1 on 2007-12-30
Hmm, I didn't change anything more than doing the updates and now it recognizes my usb wireless adapter just fine!

How do I check if it's working?

I can't find a util to see signal strength or connectivity...

Any ideas?

---

### Post by Vadi on 2007-12-30
There's an icon top-left that does your networking. When you aren't connected, it looks like this:

[[IMG]http://img91.imageshack.us/img91/4706/screenshotgc8.th.png[/IMG]](http://img91.imageshack.us/my.php?image=screenshotgc8.png)

When you right-click on it, you should have an option to enable wireless, if it's not enabled already:

[[IMG]http://img177.imageshack.us/img177/958/screenshot1zk9.th.png[/IMG]](http://img177.imageshack.us/my.php?image=screenshot1zk9.png)

And then when you left-click on it, it'll display the networks around you. To connect to any. just click on the network:

[[IMG]http://img413.imageshack.us/img413/6673/screenshot2bd1.th.png[/IMG]](http://img413.imageshack.us/my.php?image=screenshot2bd1.png)

---

### Post by ne_plus_ultra_1 on 2007-12-30
Should I be concerned about this?  After I post this I will read your reply in detail.

It's a new error:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by ne_plus_ultra_1 on 2007-12-30
Once again, awesomely detailed and informative reply.

I do not have any of those icons but I see a lot of updates I need to do now and we'll see what happens after I update and I'll post back here.

Thanks SO much for your attention to this; i appreciate it immensely.

---

### Post by ne_plus_ultra_1 on 2007-12-30
Nice, no error messages after update but I still don't have the icons you mentioned...  It doesn't seem that I have them.

Now, if I follow your link instructions for the MA111 do you think I may arrive at the point where I have the connectivity icon?

Best,
-ultra

---

### Post by Vadi on 2007-12-30
You know before you try that guide, there are a few things I'd like to try first. Just because that guide was written for ubuntu 5.10, which is very old in linux terms.

In the terminal, do **ifconfig** and **iwconfig** for me, and paste the output here.

---

### Post by ne_plus_ultra_1 on 2007-12-31
Well how about that, according to this it's connected.  It's excellent that you know these commands.  

I actually didn't disconnect the ethernet wire yet to check if it keeps connected.  

I wonder why I don't have that little util that you have in your pictures.  Missing a package maybe?


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:09:5B:8C:F6:8E  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe8c:f68e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2526694 (2.4 MB)  TX bytes:556557 (543.5 KB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:66:A4:54  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe66:a454/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1274331 (1.2 MB)  TX bytes:20907 (20.4 KB)



iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"xxxxx"  Nickname:"xxxxx"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B3:40:1B:1E   
          Bit Rate:5.5 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-58 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ne_plus_ultra_1 on 2007-12-31
I just wanted to add a little data about the networking icon that you mentioned earlier.

Enable networking is checked but enable wireless does not exist as an option.

Best,
-ultra

---

### Post by Vadi on 2007-12-31
Yeah. The default network manager in Ubuntu is... iffy. There's one that you can get that works in more situations, WICD.

Here's the link: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/). I'm sure that'll work out for you then, since your drivers are already setup just fine.

---

### Post by ne_plus_ultra_1 on 2007-12-31
Hmm, not so much luck with Wicd.

I followed instructions and altered the "/etc/network/interfaces" file.

Now my built-in network thing doesn't launch and I don't know how to start it.

Unreliability with built-in thing and Wicd both.  A few times I've briefly seen the adapter on my 192.168.1.1 page but with no consistency.

TO get Wicd to work what I did was in preferences I typed wlan0 in wireless interface as none was found initially.  I selected WEP and put in my key.  It actually worked briefly but then no more.  Something happened and my router stopped working too which is unusual and I have 5 other wireless connections to it and 2 wired and none worked for a bit until I just reset everything in it.

I didn't copy any info from etc/network/interfaces I just followed directions.  IF I were to decide to repair this file I assume I can probably find some info on how it should be by googling it but is there any button to press to have the system automatically repair it?

Best,
-ultra

---

### Post by Vadi on 2007-12-31
Here is how my file looks like, unaltered:

> auto lo
iface lo inet loopback


Which looks the same as on there. :/

---

### Post by Vadi on 2007-12-31
Okay, another thing you can try - this pretty much always works. I don't know where I got these instructions from though..

> sudo iwconfig wlan0 essid myessid
sudo iwconfig wlan0 key open myhexkey
sudo ifconfig wlan0 up
sudo dhclient wlan0

Relace "myessid" and "myhexkey" as needed.

---

### Post by ne_plus_ultra_1 on 2008-01-01
OK neat,

Now do I place these in the "/etc/network/interfaces" file the way they appear or do I run these in terminal one at a time?

The data I deleted out of that file did originally have essid and **unencrypted** WEP key as well.

I would guess that i run them one at a time as I believe I normally see sudo as something that someone types in for a specific task.  I know it's a noob question but well, then I'm kinda a noob still.

The most rewarding thing so far is learning where some of the functions are located, like screen resolution, how to end processes, install packages and where they update from and so forth.  I am enjoying the learning process so don't give up on me yet.

Oh, and BTW, this may be important, I don't know.  The WEP key on the bottom of my router does not have colons ( : ) in it.  I usually see a choice of WEP key length ( and sometimes option for ascii vs. hex as well ) in the options for such a utility.  It converts it to a format where it does have colons but is the same basic key.  Is this something that I need to compensate for?

Best,
-ultra

---

### Post by Vadi on 2008-01-01
Hm, sorry. I'm just a newbie too but one who has learned those commands already. And I have no idea how to proceed further :(

---

