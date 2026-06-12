---
title: "Ubuntu 14.04 Login Loop"
date: 2015-06-11
forum: General Help
---

### Post by tomblake6794 on 2015-06-11
Hi I'm a bit new to this and have scoured the forums here but my problem is the login loop. I tryed to login to tty1...6 etc but i get the same loop as the login screen so cannot get to input commands. I have tried to login on a live session but cant find a way to navigate to the drive in question to check the .xauthority file. Sorry if this has been covered but I checked and couldnt find any answers to this particular problem. Thanks for any help.

---

### Post by cariboo on 2015-06-11
Just to be clear, after you log in , in a console, are you taken back to a login prompt?

---

### Post by tomblake6794 on 2015-06-12
Hi Cariboo, yes thats right when I access the tty1 etc I still get the login loop issue as per the standard login screen, and so cant enter the commands to free the loop up. I try to enter my login name and password but it simply reverts after a split second to the enter username request.

---

### Post by efflandt on 2015-06-13
What video card do you have? I initially had that problem in 14.04 with my nvidia GTX 750 Ti that has the new Maxwell chip, even though live/install iso worked fine (using nomodeset boot parameter). I could not log into X and virtual terminals would flash something and immediately return to login prompt. Apparently nouveau did not support my video card yet. So I booted into (recovery mode), enabled networking (if you get an error about unrecognized hardware wait for a while for it to return to menu), went to root console, but installing nvidia-current and rebooting still could not get into X because that old nvidia 304 version did not support my card either (according to logs). Although, I could at least log into the virtual terminals at that point.

So I purged nvidia-current, installed nvidia-331-updates, rebooted, and that worked fine. I am currently running nvidia-352 from xorg-edgers ppa (needed 337 or newer version to play around with video overclocking).

But strangely I had no trouble with whatever updated 304 version nvidia-current was in 12.04 on my backup system on an old SSD (I was using newer nvidia version on my main drive before 14.04 fresh install).

---

### Post by ventrical on 2015-06-13
> **tomblake6794 said:**
> Hi I'm a bit new to this and have scoured the forums here but my problem is the login loop. I tryed to login to tty1...6 etc but i get the same loop as the login screen so cannot get to input commands. I have tried to login on a live session but cant find a way to navigate to the drive in question to check the .xauthority file. Sorry if this has been covered but I checked and couldnt find any answers to this particular problem. Thanks for any help.

Here is an old link from development version that worked a few cycles back.

[http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

regards..

---

### Post by tomblake6794 on 2015-06-13
Thanks Ventrical, but I cant enter any commands (codes...lol ;) ) on the console as it will not take my login details. Same loop.

Efflandt, My Card is an Radeon 6670HD but has been fine for the year or so I've been messing about with Ubuntu, although I know how things can suddenly turn on you lol. I tried recovery mode but have the same problem, login loop. :mad:

---

### Post by v3.xx on 2015-06-13
I don't understand why the live cd is not seeing your hdd(s).  Using raid?  A hardware (hdd) problem?

What about
```
gksudo nautilus
```
Did you try that?

---

### Post by tomblake6794 on 2015-06-13
Hey V3, No just standard drive. I tried nautilus but couldnt figure out how to navigate to the drive from the terminal. I tried /dev/sda but I just got told permission denied.

---

### Post by deadflowr on 2015-06-13
You're having login problems all around, meaning you cannot login via tty1-6?
Then doing anything to the .Xauthority file is pointless.
Something else is broke somewhere...

Can you try booting into an older kernel?

---

### Post by tomblake6794 on 2015-06-13
Thanks Dead, I'll research how to do that and give it a whirl, I REALLY don't wanna have to reinstall, especially as I finally managed to get Epson Scan working lol

---

### Post by tomblake6794 on 2015-06-13
ok I just booted up the oldest version (3.13.0-44) and the recovery mode but same thing, loops. My newest version is 
3.13.0-54.

---

### Post by pbwolf on 2015-06-13
Ubuntu instantly logs you out if your home directory does not exist.  You can figure out whether this is the case (having booted from the live image and resolved the question of how to look at the hard drive) by examining the /etc/passwd on the hard drive to see where your home directory should be, and then checking whether it still exists.

---

### Post by tomblake6794 on 2015-06-14
Hi PbWolf, I'll check that thanks dude.

---

### Post by tomblake6794 on 2015-06-16
Hi PBWolf, Sorry in the delay responding, I cant find a folder called passwd (or any derivative of password) in the etc folder. Could this be the cause? Im looking at the HDD from in windoze using Ext2.


Edit* I found the file passwd in etc.

---

### Post by tomblake6794 on 2015-06-16
This is the Passwd file I cant find a ref to Home folder except from my name

root: x:0:0:root:/root:/bin/bash
daemon: x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin: x:2:2:bin:/bin:/usr/sbin/nologin
sys: x:3:3:sys:/dev:/usr/sbin/nologin
sync: x:4:65534:sync:/bin:/bin/sync
games: x:5:60:games:/usr/games:/usr/sbin/nologin
man: x:6:12:man: /var/cache/man:/usr/sbin/nologin
lp: x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail: x:8:8:mail:/var/mail:/usr/sbin/nologin
news: x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp: x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy: x:13:13: proxy:/bin:/usr/sbin/nologin
www-data: x:33:33:www-data:/var/www:/usr/sbin/nologin
backup: x:34:34:backup:/var/backups:/usr/sbin/nologin
list: x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc: x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats: x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody: x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid: x:100:101::/var/lib/libuuid:
syslog: x:101:104::/home/syslog:/bin/false
messagebus: x:102:106::/var/run/dbus:/bin/false
usbmux: x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq: x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd: x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops: x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit: x:107:114:RealtimeKit,,,:/proc:/bin/false
saned: x:108:115::/home/saned:/bin/false
whoopsie: x:109:116::/nonexistent:/bin/false
speech-dispatcher: x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi: x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm: x:112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord: x:113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip: x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse: x:115:122: PulseAudio daemon,,,:/var/run/pulse:/bin/false
tom: x:1000:1000:Tom,,,:/home/tom:/bin/bash
Debian-ufoai: x:116:60:UFO Alien Invasion dedicated server,,,:/var/games/ufoai-server:/bin/false

---

### Post by pbwolf on 2015-06-16
Right, it says there tom's home directory is /home/tom. Does such a directory exist?

---

### Post by deadflowr on 2015-06-17
> **pbwolf said:**
> Right, it says there tom's home directory is /home/tom. Does such a directory exist?

The user cannot even use recovery mode, which has nothing to do with the user or the user's home folder.
Which means something else is causing looping.
Best I can think of is to try a livecd to chroot to do a system update.
From here:
[https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure](https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure)
Perhaps running an update might clear up the breakage.
Bad updates can happen...

---

### Post by sebastiaan5 on 2015-06-17
I had the same problem, I couldn't get pass login screens it kept looping, here is my thread.

[http://ubuntuforums.org/showthread.php?t=2272669](http://ubuntuforums.org/showthread.php?t=2272669)

greetings

---

### Post by tomblake6794 on 2015-06-18
Thanks you guys, I'll try those out and let you know what luck I have. I really appreciate your time spent helping me too, Big thanks all.

---

### Post by tomblake6794 on 2015-07-01
Sorry for late response i have been very busy with work. First i type "sudo mount /dev/sda1 /mnt" and it seems to work just starts a new line. Then when i type "sudo chroot /mnt" i get "chroot: failed to run command '/bin/bash': No such file or directory. Is this the root of the problem? (Lol see what i did there;) )

---

### Post by cariboo on 2015-07-02
First make sure the live cd is the same version as the one you are trying to chroot rg: if it's a 32bit install use a 32bit live cd. then

```
sudo mount /dev/sda1 /mnt
sudo mount -o  bind  /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

---

### Post by tomblake6794 on 2015-07-04
ok cariboo, thanks will try that and let you know results.

---

### Post by tomblake6794 on 2015-07-08
Hi cariboo. I tried that. The last line "sudo chroot /mnt" returned the same message. "Chroot: failed to run command 'bin/bash': no such file or directory" the first lines all seemed ok though.

---

### Post by tomblake6794 on 2015-07-08
The live disc im using is the same one i used for the original install. Obviously the installation has been updated since the install so i'm going to guess its still classd as the same version however.

---

### Post by tomblake6794 on 2015-07-09
I have been looking into the error report, using Windows I have the path "Local(G:/Bin Would this be where the bash file is stored as there is no bash file inside. I also read that "ld-lsb-x86-64.so.2" links to the bash would this be a misplaced/lost file? Clutching at straws as I dont really know what |m talking about but ask a question and your an idiot for 5 mins, dont ask and your an idiot for life eh? :)

---

### Post by tomblake6794 on 2015-07-13
Well looks like I stumped a few good folks. Maybe a full re-install will be necessary. Oh well thanks all *sigh*

---

