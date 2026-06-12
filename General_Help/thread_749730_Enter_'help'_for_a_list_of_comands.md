---
title: "Enter 'help' for a list of comands"
date: 2008-04-08
forum: General Help
---

### Post by Pan-Head on 2008-04-08
Hey everyone! I'm new to Ubuntu, I've had Linux a few years ago, but it was Mepis. I am currently using Windows XP and downloaded Wubi. everything seemed to be going fine, I restarted my computer, chose Windows, restarted again, and chose Ubuntu, and It went fine till i got to a black screen that read:

busybox v1.1.3 (debian 1:1.1.3-5ubuntu7) built-in shell (ash)
enter 'help' for a list of built-in commands.

(initramfs) help

built-in commands:
-----------------
(it lists bunch of commands)

So I tried entering a few of the commands with no success. Can anyone help me?

---

### Post by ago on 2008-04-08
What version of Wubi was that?

---

### Post by Pan-Head on 2008-04-08
Wubi-8.04-beta-rev479

---

### Post by ago on 2008-04-08
Press esc after selecting ubuntu and choose safe graphic mode

---

### Post by Pan-Head on 2008-04-08
I'm sorry to say I tried and still got the same screen.

---

### Post by ago on 2008-04-08
have a look into /casper.log for relevant errors (use the commands "cat" or "more", shift pgup to scroll, q to exit)

---

### Post by Pan-Head on 2008-04-08
when i typed /casper.log this is what it responded with:

/casper.log
/bin/sh:casper.log:permission denied

---

### Post by ago on 2008-04-09
cat /casper.log

---

### Post by Pan-Head on 2008-04-09
ok so when i tried that this is what came up:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount 'dev/sdal': operation not supported
mount is denied because NTFS is marked to be in use. choose one action

Choice 1: If you have Windows then disconnect the external devices by clicking on the "safely remove hardware" icon in the Windows taskbar then shutdown windows cleanly.


Then choice two was something not windows related. But I didn't have any external devices, but then I remembered I did durring installation, so I am going to do the noob thing and uninstall then reinstall wubi, haha. lets see how this goes.

---

### Post by Pan-Head on 2008-04-09
Ok uninstalling and reinstalling helped nothing...oh and I just realized I put the wrong thing in the error message, it says "Ubuntu12" not "Ubuntu7" sorry! hope that doesn't like change anything dramatically

---

### Post by ago on 2008-04-09
run chkdsk /r

---

### Post by Pan-Head on 2008-04-09
would a regular Windows diskcheck work as well? It has been trying to perform one since yesterday afternoon.....I feel kind of stupid not running it yet, seeing as that might be causing the problem. I am going to do it today at about noon. Or do I need to run the dskchk on Ubuntu?

---

### Post by ago on 2008-04-09
You have to run that in windows, you can open a dos console, cd to the drive where you have wubi and run chkdsk /r

---

### Post by Pan-Head on 2008-04-09
So I can't just run the disk check it asks me to perform at start up? and if not, can you go into further detail in how to "open a dos console, cd to the drive where you have wubi and run chkdsk /r"

---

### Post by ago on 2008-04-09
> **Pan-Head said:**
> So I can't just run the disk check it asks me to perform at start up? "

That's correct, when you reboot into windows it will scan the disk

---

### Post by Pan-Head on 2008-04-09
*sigh of disapointment* i just tried running the disk check at start up, it finished, rebooted, tried going into Ubuntu, still getting the same message. any other suggestions?

---

### Post by ago on 2008-04-09
ununistall wubi, run chkdsk /r again then reinstall wubi

---

### Post by Pan-Head on 2008-04-09
sorry man, still getting the message

---

### Post by ago on 2008-04-09
If you have USB disks try to disconnect them (sometimes other usb devices appear as mass storage)

---

### Post by Pan-Head on 2008-04-09
all USB slots are empty

---

### Post by ago on 2008-04-09
Hmm strange it looks like you have at lease one removable drive
See if any of the generic solutions help:

[http://www.google.com/search?q=%22mount+is+denied+because+NTFS+is+marked+to+be+in+use%2e+choose+one+action%22](http://www.google.com/search?q=%22mount+is+denied+because+NTFS+is+marked+to+be+in+use%2e+choose+one+action%22)

---

### Post by Macdon on 2008-04-09
i went over to my friends house today (yesterday i had installed wubi and it worked fine) so i did it for him. that exact same message popped up and i figured his comp was retarded. i go home and tried to boot up linux. exact same message too.

really need help too.

---

