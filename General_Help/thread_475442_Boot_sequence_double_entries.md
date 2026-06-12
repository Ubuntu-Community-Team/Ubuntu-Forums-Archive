---
title: "Boot sequence double entries"
date: 2007-06-16
forum: General Help
---

### Post by citizenofnowhere on 2007-06-16
Hi everyone... here's my very strange problem:

Certain processes are started** twice** during bootup. Please see attached log from bootchart (sorry, I know it's a huge file). As you can see, things like elements from my gnome session (beryl-manager, gnome-power-manager etc.) as well as processes way at the beginning of the sequence like readahead are run twice.

My usplash invariably throws me back to text mode, and then tells me disk check has failed because the device is being used by another process. I am guessing this is also because something is getting run twice? I then have the option to Ctrl+D and continue boot or debug as root, as if I booted recovery mode.

Does anyone else have this problem or any thoughts at all? I've searched high and low.

I have been having this problem ever since I upgraded to Feisty from Edgy. I've tried various 32 bit kernels and various numbered versions, from generic to 386 to lowlatency - the result hasn't changed. 

I'm really hoping someone could tell me what's going on because I've been using Ubuntu for more than a year now and I have never seen something like this before :)

---

### Post by asedas on 2007-07-03
i'm searching solution for this problem. some time ago i've changed something to proove my boot time and make it faster. but now i saw that i have twice boot entries during the boot :/ i dont use any splash so i can see console all the boot time [to gdm start] and i noticed that doubled entries are after init-bottom command [i dont remember how it is exactly] and this are commands of services like samba deamon, network deamon, etc. do You have problem like this? how could i make bootchart like Yours to check it?

---

### Post by allwin on 2007-07-03
Just a guess here.  In your GRUB menu.lst file, could you have an option that reads CONCURRENCY=SHELL vx. the standard setting of CONCURRENCY=NONE?  Some web sites recommend changing it to shell to make it boot faster, but I've done that and the only side effect seems to be getting TWO start messages for everything in the boot sequence.  However, I don't actually see everything running twice, just two messages.  Hope it's as simple as that.  Also, there's an option in GNOME to save sessions, which you can turn off.  I thought that meant change configuration changes made during the session, but what it does is restart all the programs that were running when you logged off (well, the desktop ones anyhow).  Think that's on preferences, sessions, one of the tabs there.

---

### Post by citizenofnowhere on 2007-07-04
Hi!

To install bootchart, just type 

```
sudo apt-get install bootchart
```

After you reboot you will find a large png image in the /var/log/bootchart folder which will be a graphical represetation of your boot. 

You may find out more about Bootchart in the following thread (but it's pretty old):
[http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

Unfortunately, I have been unable to solve my boot time problem. I got some geeks to take a look and they had no ideas, so in the end I sat down one day made some backups and reinstalled everything. Hope you have better luck!

---

### Post by citizenofnowhere on 2007-07-04
Allwin: thanks for the tips, but I did have none set instead of shell (and changing it had no effect in terms of double entries on my new feisty installation so maybe that's not it) and I'm not sure about the other poster but I didn't have my sessions saved either...

---

### Post by Ayuthia on 2007-07-04
Have you taken a look at /etc/rcS.d?  From your chart, it looks like only S01readahead and S06keyboard-set are the only ones called twice from that directory..  You might do an  ls -l and see if ../init.d/readahead and ../init.d/keyboard-set are called twice.

---

### Post by asedas on 2007-07-08
my bootchart below. i have any double process like modprobe, sh, dhclient3, dhclient-script, etc. what could it be?? and i dont have any entry "CONCURRENCY" in mu menu.lst in grub...
 [IMG]http://karpeta.com.pl/boot.png[/IMG]

---

### Post by asedas on 2007-07-08
ok, solved. i had in /etc/init.d/rc entry concurrency=shell and after change to concurrency=none it works perfectly and my computer get boot faster [1 sec but always ;)]. thanks for help. greetz...

---

