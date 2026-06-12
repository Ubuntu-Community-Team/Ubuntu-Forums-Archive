---
title: "Slow boot"
date: 2007-05-27
forum: General Help
---

### Post by ar1stotle on 2007-05-27
OK, I just installed Ubuntu on my grandpa's desktop to see if he can handle it. I was just trying to get stuff set up like beryl and gaim, when I noticed that session infomation wasn't being saved. Like I couldn't change what started up. So I modified the autostart stuff so that my user owned it instead of root. Well after I did that, whenever I boot the splash screen kind of hangs with nautilus. The computer is all useable, but the network configuation thing, beryl, gaim, and a few other things don't start up for like 3 minutes. I tried changing the permissions back to root since that was all I changed, but that didn't help. Any clue as to what's makin this happen? thanks.

---

### Post by ar1stotle on 2007-05-27
Bump

---

### Post by eytan on 2007-06-01
Happening to me too. Bumpity bump bump.

---

### Post by Crafty Kisses on 2007-06-01
> **ar1stotle said:**
> OK, I just installed Ubuntu on my grandpa's desktop to see if he can handle it. I was just trying to get stuff set up like beryl and gaim, when I noticed that session infomation wasn't being saved. Like I couldn't change what started up. So I modified the autostart stuff so that my user owned it instead of root. Well after I did that, whenever I boot the splash screen kind of hangs with nautilus. The computer is all useable, but the network configuation thing, beryl, gaim, and a few other things don't start up for like 3 minutes. I tried changing the permissions back to root since that was all I changed, but that didn't help. Any clue as to what's makin this happen? thanks.

When you're at the boot screen press:
```
Ctrl+Alt+F2
```
See if you have any errors in Verbose mode.
Also please post your system specs.

---

### Post by Crafty Kisses on 2007-06-01
> **ar1stotle said:**
> OK, I just installed Ubuntu on my grandpa's desktop to see if he can handle it. I was just trying to get stuff set up like beryl and gaim, when I noticed that session infomation wasn't being saved. Like I couldn't change what started up. So I modified the autostart stuff so that my user owned it instead of root. Well after I did that, whenever I boot the splash screen kind of hangs with nautilus. The computer is all useable, but the network configuation thing, beryl, gaim, and a few other things don't start up for like 3 minutes. I tried changing the permissions back to root since that was all I changed, but that didn't help. Any clue as to what's makin this happen? thanks.

Or you can try going in terminal and type:
```
top
```
To see if any process is eating up your resources. :D

---

### Post by armaud on 2007-06-01
Hello
      I am having a very severe problem of slow boot. I have just shifted from windows and i first tried Kubuntu but i deleted it because of slow boot. I reinstalled it but problem still persisted. I then installed Ubuntu(both 7.04) two times but am having the same problem. It takes nearly 5 minutes for my computer to boot and no flash screen appears. The screen just stays blank for 5mins and then the login screen appears. I have posted my problem and system log here.
[http://ubuntuforums.org/showthread.php?t=439960&highlight=Kubuntu+7.04+startup+problem](http://ubuntuforums.org/showthread.php?t=439960&highlight=Kubuntu+7.04+startup+problem)

Please see if anyone can help. Someone told me to go to boot manager and enable boot scripts. Can you tell me how to do that? You can search for my earlier posts by searching for 'Kubuntu 7.04 startup problem' in absolute beginners talk section if the above link fails.

---

### Post by Crafty Kisses on 2007-06-01
> **armaud said:**
> Hello
      I am having a very severe problem of slow boot. I have just shifted from windows and i first tried Kubuntu but i deleted it because of slow boot. I reinstalled it but problem still persisted. I then installed Ubuntu(both 7.04) two times but am having the same problem. It takes nearly 5 minutes for my computer to boot and no flash screen appears. The screen just stays blank for 5mins and then the login screen appears. I have posted my problem and system log here.
[http://ubuntuforums.org/showthread.php?t=439960&highlight=Kubuntu+7.04+startup+problem](http://ubuntuforums.org/showthread.php?t=439960&highlight=Kubuntu+7.04+startup+problem)

Please see if anyone can help. Someone told me to go to boot manager and enable boot scripts. Can you tell me how to do that? You can search for my earlier posts by searching for 'Kubuntu 7.04 startup problem' in absolute beginners talk section if the above link fails.

System specs please?

---

### Post by CanadianDSM on 2007-06-02
If you would have followed that link, you would have noticed his system specs in the first post:

[QUOTE=armaud]My system is P4 2.4, 512MB ram and harddisk i am using for kubuntu has 5.1GB space.[/QUOTE]

I am also running into the same problem. Booting takes 2-5 minutes, and seems to hang at "Nautilus" on the splash screen. After it's finished booting, it acts as normal.

Here are my specs:

Dell Inspiron 6400
Core2Duo T5600 (1.83GHz)
1GB DDR2
ATI X1400
Broadcom NIC & Wireless NIC

It was running fine up until a day or so ago. This problem just popped up. Not sure if it was due to a kernel update or not that had been performed a few days before that?

---

### Post by armaud on 2007-06-02
Hello
     My computer is P4 2.4G 512 Mb ram. I do not connect to any network and have no networking card. Its only a home pc used for making documents and some other programs. My windows boots in about 30 seconds and i tried ubuntu 6.06, it too booted in 30 seconds. The main problem is that for 5 mins the screen remains blank and i never get that screen where it is written ubuntu and it is loading. After 5 mins login screen requiring password appears. Then my computer runs fine. I had no such problem in 6.06. If you follow the link and see the system log it seems as if the ubuntu os restarts 2 to 3 time while booting. Although i am not experienced enough it just seems to me that there is some problem with initializing something during boot. Please see the system log yourself. I have no idea what to do.

---

### Post by eytan on 2007-06-02
I have looked into my problem a little more. Pretty frustrating because I am more than fairly proficient with Windows but am totally lost in Ubuntu. Seems that something called gnome-wm is getting frozen on boot up and that the session manager waits for that to resolve itself before it continues with everything else. Running Fiesty Fawn on a Intel 1.6 ghz processer, Dell 700m, 512 RAM.

---

### Post by eytan on 2007-06-02
More information:
During bootup, the splash screen will pop up and will stay open right after "The Panel" appears. The computer works with the default windows manager until 2 or 3 minutes later everything else comes in (Beryl, some applets, the network manager applet); basically everything that has a 50 priority. As I said before, I am pretty sure that gnome-wm or metacity is freezing it up (there is a little clock icon next to it in the session manager during the 2-3 minutes). I have been using Ubuntu for a few months, love it and have converted friends but am driving myself against a wall here. Anything?

---

### Post by eytan on 2007-06-02
Hate to be flooding this thread but I worked out a fix that worked and saved me the anxiety of actually dealing with the problem. I realized that the problem was with Metacity so I just reset it to the default settings (took 5 minutes to retrieve the preferences). Followed directions from this page:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

and it worked like a charm. Good luck.

---

### Post by CanadianDSM on 2007-06-02
Thanks for the link! I started to think about problems I had years ago with Debian and various other Linux distros hanging after logging in at the console. Those problems were resolved by installing bind9 on the local machine so that it can look at itself to resolve things.

I tried this on Feisty and it seems to have worked. No more frozen splash screen!

---

### Post by DuckOne on 2007-06-02
I have been trying to install Feisty Fawn for the last two days on two of my Windows machines. To boot up from the CD takes about 6 minutes. Thereafter the keyboard and mouse response is terribly slow. To run through the install process takes about 6 hours (and I still have not managed to complete this!) Each of the 7 steps takes about 20 minutes to complete, the CD drive is reading continuously and the dialogues are populated in slow motion. The two machines are 433MHz and 1.8Gz Celerons, with 760MB and 512MB RAM resp. Currently running NT and XP quite happily. I really would like to give Linux an opportunity, but I cannot get past the starting gate.

---

### Post by CanadianDSM on 2007-06-02
Have you tried the alternative installation CD? It's got a text-based installer, and caused me less problems when installing Ubuntu on my machine. I couldn't even get X to initialize, so it was my best option. If you haven't tried it, I would highly suggest giving the alternative installation CD a try.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Make sure you check the checkbox at the bottom indicating that you want to download the alternative installation CD.

---

### Post by armaud on 2007-06-03
Hello
 I saw the system log and i saw the following lines repeating 2 to 3 times.This is only some portion as actual system log is very long. I have posted my problem in absolute beginner section. You can see it by searching for 'Kubuntu 7.04 startup problem'. Please keep in mind that i am a novice to Ubuntu so please explain.


May 28 18:51:01 maud-desktop kernel: [ 199.666781] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 18:51:05 maud-desktop gconfd (armaud-5334): starting (version 2.18.0.1), pid 5334 user 'armaud'
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 1
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:51:05 maud-desktop gconfd (armaud-5334): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:51:15 maud-desktop gconfd (armaud-5334): Resolved address "xml:readwrite:/home/armaud/.gconf" to a writable configuration source at position 0
May 28 18:53:06 maud-desktop gconfd (root-554: starting (version 2.18.0.1), pid 5548 user 'root'
May 28 18:53:06 maud-desktop gconfd (root-554: Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:53:06 maud-desktop gconfd (root-554: Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:53:06 maud-desktop gconfd (root-554: Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:53:06 maud-desktop gconfd (root-554: Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:53:06 maud-desktop gconfd (root-554: Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:53:36 maud-desktop gconfd (root-554: GConf server is not in use, shutting down.
May 28 18:53:36 maud-desktop gconfd (root-554: Exiting
May 28 18:56:06 maud-desktop gconfd (armaud-5334): Failed to send buffer
May 28 18:56:29 maud-desktop gconfd (root-5777): starting (version 2.18.0.1), pid 5777 user 'root'
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:56:29 maud-desktop gconfd (root-5777): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 18:57:29 maud-desktop gconfd (root-5777): GConf server is not in use, shutting down.
May 28 18:57:29 maud-desktop gconfd (root-5777): Exiting
May 28 18:57:40 maud-desktop gconfd (root-5856): starting (version 2.18.0.1), pid 5856 user 'root'
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 28 18:57:40 maud-desktop gconfd (root-5856): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 28 19:03:10 maud-desktop gconfd (root-5856): GConf server is not in use, shutting down.
May 28 19:03:10 maud-desktop gconfd (root-5856): Exiting
May 28 19:03:16 maud-desktop gconfd (armaud-5334): Exiting
May 28 19:03:25 maud-desktop exiting on signal 15
May 28 19:06:39 maud-desktop syslogd 1.4.1#20ubuntu4: restart.
May 28 19:06:40 maud-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic
May 28 19:06:40 maud-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May 28 19:06:40 maud-desktop kernel: Symbols match kernel version 2.6.20.
May 28 19:06:40 maud-desktop kernel: No module symbols loaded - kernel modules not enabled.
May 28 19:06:40 maud-desktop kernel: [ 0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
__________________

---

### Post by flowerdealer on 2007-06-10
I have exactly the same problem as you describe aristotle, and it suddenly happened, I don't think I changed anything. I've deleted my gnome preferences but it doesn't solve the problem.

---

### Post by flowerdealer on 2007-06-11
Correction, deleting my gnome preferences did solve the problem, but only after a reboot! Thanks.

---

### Post by EnthropyinAction on 2007-09-26
I had a similar problem for a while.  It started up normal until I logged into gnome.  All that I had starting was Beryl and Gaim, but it took about 5 minutes for both of them to start up.  In fact, I could run them from the menu and the process would load faster than it's auto-loading counterpart.

I figured out that the only thing I changed was I saved a gnome session to start Gaim instead of just putting it into the boot script.  I deleted the saved session (instructions here: [http://ubuntuforums.org/showthread.php?p=3422671](http://ubuntuforums.org/showthread.php?p=3422671)) and it starts like a dream again.  Hope this helps one of you, at least

---

### Post by freeflyer57 on 2007-09-26
I just bought a Dell 1420n with duo core 2.2 GHz and 2BG DDR2. My computer computer was shut off by some idiot by holding the button. Before the computer would only take about 1 min to boot. Now it takes about 8-9 minutes. Once I am logged in it takes nautilus another 5 minutes to get finished. Then to top it off my computer was so fast that it would open something before I clicked on it, and now it takes a few minutes to open a terminal. Please help. Plus I can't get  on to my network, but that must be something else.

---

### Post by freeflyer57 on 2007-09-26
Thank you so much man! that completely worked. I wrote the first part because I didn't see the solution to reboot instead of just logging out!

---

