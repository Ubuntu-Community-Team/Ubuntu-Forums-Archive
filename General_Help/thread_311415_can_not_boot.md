---
title: "can not boot"
date: 2006-12-02
forum: General Help
---

### Post by DougieFresh4U on 2006-12-02
bei9ng impatiant after 3 days of no answer to post in forum, I decided to download ISO and burn and reinstall. Well download went ok. K3B was saying no suitable buern program detected. then I change cd-rom drive and computer say not detecting cd-rom drive. 
Then I shut down computer and now it won't boot. I've got black screen with the following message::BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu2) Buikt-in shell (ash)                                        Enter 'help' for a list of built-in commands.        /bin/sh: can't access tty: job control turned off (initraqmfs)_

---

### Post by taurus on 2006-12-02
Not sure exactly what's the problem here!  You've donwloaded the ISO but k3b wouldn't burn!  Then when you tried to reboot your machine, it wouldn't boot!

---

### Post by bulldog on 2006-12-02
You have to be a little more specific in what you changed at your computer.
If you were messing with the cables which connects your cd-rom and hard drives to your motherboard,just change it back the way it was before.

I get the impression your hard disk is connected on another IDE port of your motherboard.

---

### Post by DougieFresh4U on 2006-12-02
Hi taurus.  I never got to burn the ISO.  So I just closed all out and I shut down machine and when I started back up I was presented with the message I posted. I have had no problem earlier booting up

---

### Post by taurus on 2006-12-02
If you haven't changed anything and only tried to burn an ISO image with k3b, then your computer should still be able to boot!  What did you do to the system before you tried to use k3b?

---

### Post by DougieFresh4U on 2006-12-02
The only thing I changed was the CD-ROM. I unplugged the old one and plugged in another one. I did not change any thing else

---

### Post by taurus on 2006-12-02
You didn't touch the harddrive or maybe somehow accidentally bumped the cable on the harddrive!!!  Check for connection again...

---

### Post by DougieFresh4U on 2006-12-02
I am putting back the origanal CD-ROM drive and I will reboot again. I shall post  when finished in a few , thanks guys for replies, be back

---

### Post by bulldog on 2006-12-02
It's not the cd-rom player but the cable is probably not properly connected.
You stated your new cd-rom wasn't recognized so the cable which connects the player and the hard disk is not properly connected.

---

### Post by DougieFresh4U on 2006-12-02
All cables are tight. I rebooted  and still have message: /bin/sh: can't access tty; job control turned off. then under neath thaty  there's: (initramfs) then a flashing cursor. Is there sme thing I can type there to make it go or can I put in a live cd as thats all I have, of course it's obvious that I am communicating via another machine

---

### Post by taurus on 2006-12-02
Didn't you say you planned to burn and reinstall it?  Maybe it's time to do that...

---

### Post by DougieFresh4U on 2006-12-02
I put a dapper cd in and the drive lites up for a few seconds but machiner is trying to boot from hard drive and not cdits and old dell optiplex gx50. how can I get it to boot from cd?

---

### Post by taurus on 2006-12-02
Try F2 when the machine first comes up to get into the BIOS.  Then, change the boot order from harddrive first to CD-ROM first!  Save it and reboot...

---

### Post by DougieFresh4U on 2006-12-02
I mput CD-ROM first but its says not installed

---

### Post by taurus on 2006-12-02
I guess your BIOS can't see your CD drive which means either the CD-ROM is bad, the cable is bad, or the cable doesn't connect securely to the back of the CD-ROM!!!

---

### Post by DougieFresh4U on 2006-12-02
I get to the grub menue and it starts to load then stops after second line  ' starting root file system or some thing like that
therte s nothing I mcan type in there to get to move along?

---

### Post by taurus on 2006-12-02
Boot with the LiveCD and see if you can read your harddrive!  It could be either connected wrong or something's wrong with your harddrive!  Are you sure you didn't move the cable around for the harddrive when you tried to switch the CD-ROM?

---

### Post by DougieFresh4U on 2006-12-02
i've been reading a few posts from 3 weeks aga pertaining to: tty: no job control. seemsa it was a problem but I still am quite con fused about it. no I did not f*** with the cables. sorry, I am just mad at my self.  At this point I have gotten it to :grub>  I guess thats a command line but I do not know what to put in there. When I was looking at the grub menue there was no recovery mode so I clicked 'c' to ghet command line. now 
I await a reply to move on w.command. thanks

---

### Post by taurus on 2006-12-02
The line for kernel for recovery mode is the same for normal boot up except you replace the "quiet splash" with the word "single"...

---

### Post by DougieFresh4U on 2006-12-02
Is there any thing I can type in where it says: grub> and then flashing cursor?

---

### Post by taurus on 2006-12-03
You need to know the exact kernel you have and where your / partition is...

[/code]
/boot/kernel-2.6.17-generic root=/dev/hda1 ro single
[/code]

---

### Post by DougieFresh4U on 2006-12-03
i did not partition when I installed. I did the erase entire disk an install so I  think it did the hd1 or some thing and ext3 and there was sopme thing with a 5 in  it. I have tyhe kernal 2.6.19.7 generic. I am not good at making the codes. could you possibly throw some thing together for me? Thank You!!

---

### Post by taurus on 2006-12-03
If you are using the default, then / is on /dev/hda1 while swap is on /dev/hda5...

Enter this line in GRUB to see if it boots or not!

```
/boot/kernel-2.6.19.7-generic root=/dev/hda1 ro single
```

---

### Post by DougieFresh4U on 2006-12-03
Do I need  sudo or any thing, becaus I typed exactly what you put and it came back: Error 27:Unrecognized command     then back to: grub>

---

### Post by taurus on 2006-12-03
Why don't you boot your machine with the LiveCD, mount your partition, /dev/hda1, and edit /boot/grub/menu.lst to include the recovery mode in there...

---

### Post by DougieFresh4U on 2006-12-03
CD-ROM is DEAD!! When i put in cd, the light on it flashes a few seconds then no more and I here it run but it's not doing any thing. BIOS says it's not installed. So back to grub

---

### Post by taurus on 2006-12-03
Try to hit either e or c for editing.  That's where you can modify your /boot/grub/menu.lst...

---

### Post by DougieFresh4U on 2006-12-03
nada. I am not ready to give up yet. e or c returned error 27

---

### Post by taurus on 2006-12-03
Before you see the actual grub> thing!  When it first boots up, you see a GRUB with a count down.  That's where you press either Esc to see the menu or e (or c) to edit it!

---

### Post by DougieFresh4U on 2006-12-03
got it.  first line says:  root  (hdo,o)    second line says:  kernel  /boot/vmlinuz-2.6.19.7-generic root=UUID=76aedf51-9beb-44e5-a  third line: initrd  /boot/initrd.img-2.6.19.7-generic  and the fourth line says: savedefault

---

### Post by taurus on 2006-12-03
There's your problem!!!  It should be

```
root (hd0,0)
(as in zeroes instead of letter os...)
```

---

### Post by DougieFresh4U on 2006-12-03
Forgive my stupidity, but how do I fix? I have highlighted the line. Do I erase it and put a new one, sorry, they are zero's

---

### Post by taurus on 2006-12-03
Yes.  However, it is only for that session so technically you still need to go in and modify that line in /boot/grub/menu.lst later when your system is up.

---

### Post by DougieFresh4U on 2006-12-03
ok now what? I see in the **[B]Hardware & Laptop**[/B]some one else has the same exact problem with the tty and no job control. ok what do I do nowas it didn't boot and I am back at the edit thingy

---

### Post by DougieFresh4U on 2006-12-03
taurus, you left me **Hanging**

---

### Post by DougieFresh4U on 2006-12-03
still trying to get past grub!! Any one. I know I am not the only one with this tty -problem. At the top of screen it says: Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exists

---

### Post by taurus on 2006-12-03
I already told you to modify your kernel entry to include a "single" at the end to boot into recovery mode...

```

kernel /boot/vmlinuz-2.6.19.7-generic root=/dev/hda1 ro single
```

---

### Post by DougieFresh4U on 2006-12-03
I did change that and when I get back to menue showing me kernaql versions my change is not there!!!

---

### Post by taurus on 2006-12-03
Well, I am not sure exactly what's going on with your machine so you probably have to play around with other options in GRUB to boot from your harddrive then.  I still think that while replacing the old CD-ROM with the new one, you either moved the cables around and didn't get it back the way it was.  That's why you can't boot into Ubuntu anymore!

---

### Post by DougieFresh4U on 2006-12-03
Taking machine out to dumpster now!!:mad: :mad: :mad: :mad:

---

