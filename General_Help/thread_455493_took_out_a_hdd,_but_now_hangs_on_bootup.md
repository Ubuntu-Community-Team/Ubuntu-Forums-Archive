---
title: "took out a hdd, but now hangs on bootup"
date: 2007-05-26
forum: General Help
---

### Post by stabu on 2007-05-26
Hi, 

I took out an IDE HDD from my PC and suddenly Feisty is not booting up. Getting rid of the "quiet" option allows me to see where it might be hanging ... it happens when rc.local is being called, which I imagine is towards the end of the boot process.

I decided to render this unexecutable, and then it started hanging on init.d/rc2.d/s99rc.local.

I'm not too sure what's going on. Has anybody else seen this?

Nope,I haven't looked at syslog yet ... will do soon.

Thanks in advance for suggestions.

---

### Post by zek725 on 2007-05-26
> **stabu said:**
> Hi, 

I took out an IDE HDD from my PC and suddenly Feisty is not booting up. Getting rid of the "quiet" option allows me to see where it might be hanging ... it happens when rc.local is being called, which I imagine is towards the end of the boot process.

I decided to render this unexecutable, and then it started hanging on init.d/rc2.d/s99rc.local.

I'm not too sure what's going on. Has anybody else seen this?

Nope,I haven't looked at syslog yet ... will do soon.

Thanks in advance for suggestions.

Haven't seen that kind. 

I had the same issue when a cdrom/hdd is removed. It does not freeze but it slows down when it tries to probe the missing hardware. I solved it by adding **ide1=noprobe** (for the the whole secondary ide) in the kernel line. But if you want to isolate it to a single harddive then **hd*b*=noprobe** would do. 

Let *b* be the hardware (harddisk or cdrom) you have removed.

---

### Post by stabu on 2007-05-27
Hi zek725,

Thnaks for the reply. Thanks for the heads-up on the noprobe bootparam. It won't help me, because my system is totally hanging, but it's help localise the problem, as I think that it's got to be the kernel bootparams.

What's got me confused in the root=UUID option. I've used grub and bootparams alot, and I haven't come across it. Usually you just say root=/dev/hda (hda being your boot HDD)  but the UUID and the 8-4-4-4-12 hex sequence afterwards is out of my depth.

However, it's probably identifying the root user in a special way and this maybe where the denied access is coming in.

I tired syslong, it hardly says anything.

BTW instead of the HDD I put a CDROM so I can boot knoppix for the necessary troubleshooting.

Any more clues on UUID and kernel bootparams (which, Ubuntu, by the way, seems to use in a special way) wil be appreciated.

Cheers.

---

### Post by stabu on 2007-05-27
I'm still having trouble .. this really is a lethal fault I'm having. IT is now the third major  stopping point that Fesity is giving me ... could these be bugs? Hmm . I wish there was a sitcky about Feisty bugs, not only edgy ones.

Anyhow I'd love to find a place that explains ubuntu boot parameters to me. 

And that "casper" business it turns up on the CD as a boot parameter .. how enigmatic ... how unuseful!

---

### Post by stabu on 2007-05-27
well, after my various mods ... it's hanging on 

* Checking battery state ...

My PC seems to be having a competition with me: in how many ways can it get ubuntu to hang?

the problem is hat I still haven't discovered the key problem ... I've been booting up the PC all day every time I do the tiniest of mods. Quel desastre!

---

### Post by confused57 on 2007-05-27
> **stabu said:**
> I'm still having trouble .. this really is a lethal fault I'm having. IT is now the third major  stopping point that Fesity is giving me ... could these be bugs? Hmm . I wish there was a sitcky about Feisty bugs, not only edgy ones.

Anyhow I'd love to find a place that explains ubuntu boot parameters to me. 

And that "casper" business it turns up on the CD as a boot parameter .. how enigmatic ... how unuseful!

What you can experiment with is to highlight your Ubuntu entry in the grub boot menu, press "e", then try changing the root to (hd0,x), (hd1,x), or  (hd2,x), then press "b" to boot.  I think maybe your Feisty grub designation(hd0,hd1,hd2,etc) may have changed when you removed the IDE drive.

You could boot the live cd and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You might want to mount your Feisty root partition & post the output of:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

Here's an excellent website that explains grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Added:  On second thought, it might be Feisty is trying to mount IDE  partition(s) listed in /etc/fstab & is unable, since the IDE drive is removed.

---

### Post by stabu on 2007-05-27
Hi Confused57,

Many thanks for your reply! After more troubleshooting, I'm going away from the HDD theory. That sounds very grand, but what I've probably done is created another fault in the init scripts.

I use grub frequently and when it fails, it fails very early in the boot process. In my case, the failure is at the end. The recovery bootoption DOES work, but without many services of course.

I am now in the process of battling with the debian init script sequence. How can I put it? ... it's exciting! Each time I disable a script (by setting its name to K10S90acpi-support in rc2.d, for example) it fails on the next script in the sequence (with a lower S number). This is some sort of permissions thing. 

All the init.d scripts source lib/lsb/init-functions and /etc/defaults/rcS, and maybe other stuff besides ... it's pretty hellish, though there is no doubt some solid reasons for doing it this way.

I was BOUND to fall into this problem, coming, as I do, from Slackware, which uses a simple / primitive boogtscript style.

Off I go to read the Debian Policy on Bootscripts ...

However what I do hate about all this, whatever the fault is that I have developed, is the consistent hanging of the system. THi sis linux, things are not meant to hang!

---

### Post by stabu on 2007-05-27
OK, well, once in recovery mode, I am able to run any of the init script as root. They complete successfully.

However, as normal user, they fail, quoting permission problems. 

The Debian Policy manual talks about the need to examine scripts when runlevels are being changed. Am I changing runlevels? Didn't think so ...

However, the the fault MAY be (of course, one doesn't know, as there is just a general hanging, and no error messages) that the init scripts are not being run as rootuser, or that the user that the init sequence start up in, does not have the right access level.

Pfff ... back I go again.

---

### Post by zek725 on 2007-05-28
> **stabu said:**
> Any more clues on UUID and kernel bootparams (which, Ubuntu, by the way, seems to use in a special way) wil be appreciated.

[*Warren Butler*]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html#6522374720091700681") forwarded me these links: 
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

---

