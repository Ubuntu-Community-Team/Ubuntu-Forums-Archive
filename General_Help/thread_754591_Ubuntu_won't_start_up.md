---
title: "Ubuntu won't start up"
date: 2008-04-13
forum: General Help
---

### Post by ekmon1582 on 2008-04-13
All of the sudden, when I select my PC to boot Ubuntu, it gets to the username and password screen, I enter it in, and it goes through. Now the problem is that it gets the peach colored screen it usually shows before showing my actual desktop, it sits there, on the peach screen and does nothing. My mouse moves, my PC will go to sleep and wake up again, like normal, but no display. Any ideas?

---

### Post by ago on 2008-04-14
Try to boot with an older kernel (in case there was a kernel upgrade) at boot press esc after "Ubuntu".

---

### Post by ekmon1582 on 2008-04-14
Did it, but no luck, does the same thing.

---

### Post by ago on 2008-04-14
Use ctrl+alt+f1 to get a console
Then you can monitor the processes via 

ps ax

Or you can look at the log (nano /var/log/syslog)

One thing to try is to set the video driver to vesa

sudo dpkg-reconfigure xserver-xorg

---

### Post by ekmon1582 on 2008-04-14
I pressed Ctrl, Alt, and F1. Nothing happened.

---

### Post by ago on 2008-04-14
can you boot in rescue mode? (press esc after selecting "ubuntu" at boot and go for the second option)

---

### Post by ekmon1582 on 2008-04-14
I tried all modes, did the same thing.

---

### Post by ago on 2008-04-14
See if you can access the logs using another linux installation / live CD

You will have to mount manually the windows drive
And then mount -o loop c:\ubuntu\disks\root.disk /mnt

---

### Post by ekmon1582 on 2008-04-14
What do you mean by mount?

---

### Post by ago on 2008-04-14
A disk device is mounted to a folder in linux.

mkdir /tmp/windows
sudo mount /dev/sda1 /tmp/windows
sudo mount -o loop /tmp/windows/ubuntu/disks/root.disk /mnt

Now look into /mnt/var/log/syslog
In the above sda1 meas disk 1 (a) partition 1 (1), change as appropriate

---

### Post by ekmon1582 on 2008-04-14
Erm, what am I suppose to be doing here?

---

### Post by ago on 2008-04-15
You are using a Live CD to try access the logs inside of root.disk. See guides for mounting files and partitions in Linux.  The instructions are above.

---

### Post by ekmon1582 on 2008-04-19
> **ago said:**
> A disk device is mounted to a folder in linux.

mkdir /tmp/windows
sudo mount /dev/sda1 /tmp/windows
sudo mount -o loop /tmp/windows/ubuntu/disks/root.disk /mnt

Now look into /mnt/var/log/syslog
In the above sda1 meas disk 1 (a) partition 1 (1), change as appropriate

I got as far as "sudo mount /ev/sda1 /tmp/windows". After I put that in, it told me permission was denied. I was using an installation Live CD.

---

### Post by ago on 2008-04-19
it's /dev/sda1 (might be something different to such as sdb3)

---

### Post by |{urse on 2008-04-19
ctrl + alt + f2
will get you to a login
then 
sudo nano /etc/X11/xorg.conf
scroll down to the device identifier section
change your driver to "vesa"
press ctrl + x to save
sve modified buffer? = y
sudo init 6

looks like your vid card is writing checks that your monitor cant cash lol

---

### Post by |{urse on 2008-04-19
> **ago said:**
> Use ctrl+alt+f1 to get a console
Then you can monitor the processes via 

ps ax

Or you can look at the log (nano /var/log/syslog)

One thing to try is to set the video driver to vesa

sudo dpkg-reconfigure xserver-xorg

Just saw this, sorry. Didn't say whether he/she tried it or not though.

---

### Post by ekmon1582 on 2008-04-19
OK I tried the suggestion in the second post above this one, and for some reason, under "device" identifier, all it says is "configured video device." Nothing else, no drives, nothing. If I haven't mentioned already, I'm using 8.04 Hardy (beta), and installed it with Wubi. Just to clear it up a bit, my device identifier is "configured video device." I'm guessing that's what I want to change to vesa?

---

### Post by Gripp on 2008-04-20
just a thought... maybe copy the xorg.conf file from your live CD to your install (back up your installed version first...) and try making the edits that he suggested from there

---

### Post by ekmon1582 on 2008-04-20
I don't know what your talking about, sorry, I'm a Ubuntu newbie. So can anyone answer my question above?

---

### Post by |{urse on 2008-04-21
to the right of where it says 
driver     ""       <-----put "vesa" there

---

### Post by ekmon1582 on 2008-04-21
It doesn't say driver anywhere. It says this:

"Device"
  Identifier                                         "configured video device"





No drivers or anything, just that.

---

### Post by ekmon1582 on 2008-04-22
So does anyone know what I should do?

---

### Post by Kanoga on 2008-04-24
I'm having this same problem, there's no option for me to choose "vesa" when I try.

---

### Post by ekmon1582 on 2008-04-24
I can't find a fix for it, I'm going to start fresh and use a dual boot with the LiveCD itself, instead of Wubi.

---

