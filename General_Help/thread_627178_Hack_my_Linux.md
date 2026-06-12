---
title: "Hack my Linux"
date: 2007-11-29
forum: General Help
---

### Post by RealG187 on 2007-11-29
You know how there is an option at the GRUB boot for recovery mode, well I notice that it is easy to get into this, so could someone mess up the computer? I learned recetnly about the "[RM]("http://www.justpasha.org/folk/rm.html")" command (I shouldn't have used caps, Linux is case sensitive).

---

### Post by Zack McCool on 2007-11-29
> **RealG187 said:**
> You know how there is an option at the GRUB boot for recovery mode, well I notice that it is easy to get into this, so could someone mess up the computer? I learned recetnly about the "RM" command (I shouldn't have used caps, Linux is case sensitive).

Yes.  It is very easy to get into it, if a person has physical access to the machine, and great damage can be done, or something as simple as changing the root password for later access...

If there is an issue with untrusted people having physical access, you should edit your grub configuration to 1) remove these entries, and 2) set a grub password to prevent someone from modifying the boot line and granting themselves access.

You should also set your machine to boot first from HD, and set a BIOS password.

None of this is foolproof, as a person can simply remove the cover of the PC, set a jumper to clear the password, and boot from a floppy or livecd to make the changes they want, but every little step helps.

---

### Post by atlfalcons866 on 2007-11-29
also premissions are useless when a hacker logins as root. Root can access anything on the computer.

---

### Post by RealG187 on 2007-11-30
So by default Grub on Ubuntu in unsecure?

---

### Post by Zack McCool on 2007-12-05
> **RealG187 said:**
> So by default Grub on Ubuntu in unsecure?

Grub on any Linux distro is unsecure, by default.  If physical access to a machine is possible for the attacker, then you need to take several steps to increase security.  Keep in mind that total security in this case isn't really possible, but you can do things to slow someone down...

---

### Post by Tyke91 on 2007-12-05
physical access to any computer (linux/windows/mac or otherwise) will make it a lot easier for a person to invade your computer... for instance, if you had boot from CD rom enabled first in the list instead of 2nd or 3rd, a person could just put an Ubuntu 7.10 live CD into the computer and restart it. Not only would this compromise your linux partition, but it would also allow the attacker to affect windows and mac files as well.


as a rule of thumb, if you want to make sure your computer is secure, don't let anyone else touch it :)

---

### Post by aysiu on 2007-12-05
> **Zack McCool said:**
> 
If there is an issue with untrusted people having physical access, you should edit your grub configuration to 1) remove these entries, and 2) set a grub password to prevent someone from modifying the boot line and granting themselves access. If there is an issue with untrusted people having physical access, you should find a way to keep them away from your computer. Physical access + time + malicious intent = compromised computer.

---

### Post by RealG187 on 2007-12-05
I actually can boot the live CDs at school, couple days ago the tech asked me to stop so I did, but I wanted to I could take Windows off and put Ubuntu on!


Anyways, what left the school machines vulnerable was that one could press F9 for a boot menu which overrides the BIOS set to boot the hard drive and not the CD ROM. My laptop has that too (except it's F12) for security I disabled that, but let's say I wanted to boot off a CD once, I could set it to boot the CD before the hard drive, but if I leave it that way it's even more unsecure than F12 since a potential snoop (I wont say hacker since it's so easy they dont even have to hack) can boot their disk without even having to press F12, worse than having a sticker saying if you want to bypass my security press F12!!!


So I was wondering, can I get it to maybe start the last OS uses, unless I press a certain button to access GRUB, from there it asks for a password, then shows the normal grub menu with options to boot Ubuntu or Windows off the hard drive and options to boot off CD-ROM or Floppy/USB (One of my older machines has a floppy, but I dunno if it can boot USB).

So lets say I used Windows last  it will continue to start windows everytime until I press the GRUB button, enter the password and choose Ubuntu, it will then start Ubuntu that time and every time after until I repeat the process, also if I wanna boot off CD/Floppy/USB once I can do that too wothout having to use the BIOS which is unsecure.

---

### Post by oeolycus on 2007-12-05
Like others have said before, if someone has/might have physical access to your computer, it's not very hard to mess things up. Even BIOS passwords can be reset (short the right part on the mobo) or altogether skipped by removing the HD. The safest bet for your information is to make it unreadable--you may not be able to protect it's being lifted or destroyed or tampered with, but you can at least protect it from being read.

Have you thought about whole disk encryption?

---

### Post by RealG187 on 2007-12-06
I just wanna twart the average user, like a recovery option is bad...

Plus if I do my Laptop it will be harder to take that apart.

Is there a way to add CD and/or floppy boot to GRUB and make it so recovery is locked and so it booting off CD and/or floppy?

---

### Post by daimaru on 2007-12-06
if your using a laptop that is easily stolen or accessed in public you should encrypt your hard drive. this of course will not stop anyone from destroying all your date, it will just keep them from being able to read it:)

---

### Post by louieb on 2007-12-07
> **RealG187 said:**
> I just wanna thwart the average user, like a recovery option is bad...
Is there a way to add CD and/or floppy boot to GRUB and make it so recovery is locked and so it booting off CD and/or floppy?

Hello RealG, IF you like to thwart an average use you could always remove the recovery entry from menu.lst. I doubt the average user would know how to edit the default entry and turn it into one that boots the PC into recovery mode. 

Theres a phrase  for it  -  :evil: ***Security by ignorance :confused:***

---

### Post by RealG187 on 2007-12-07
All my personal files are on externa; hard drive anyways (in theory, if I am too lazy to plug it in, or it's on the downstairs desktop for backup like it is now [Thank God for VNC, I can manage the backup process from up here])

---

### Post by Dr Small on 2007-12-07
You could also add a password to the GRUB recovery entry, so they must enter a password to boot into that.

---

### Post by Zack McCool on 2007-12-08
No.  You want to go into your BIOS, and set the boot order to HD First.  Then, set a BIOS password for boot.  This will prevent anyone from changing the boot options unless they have the password.  Once the password is entered, the grub menu comes up, and the system boots.

Like I said before, it is still beatable by opening the box, but if you can live with that, this is your best solution...

---

### Post by RealG187 on 2007-12-08
But I dont wanna type in a password everytime I boot.

---

### Post by dfreer on 2007-12-09
> **RealG187 said:**
> But I dont wanna type in a password everytime I boot.

Most BIOS's allow you to set a password just for BIOS, that let's you boot normally but if someone tries to access the BIOS, *then* they have to enter the password. In my case, my BIOS menu has a Supervisor and User Password. I believe, if I set the User Password only, it only restricts the BIOS.

On top of that, look into GRUB's security features. You can restrict the recovery mode from being entered with a password, and (just as important!) prevent the boot options from being accessed without a password. You will still be able to access your regular Ubuntu partition without having to enter a password, if you wish.

The most important thing, of course, is to keep your PC physically secure as others have said.

EDIT: I don't think it's possible to boot a bootable CD/floppy from GRUB, at least in the terms of standard Live CD's/Windows Install CD's. That is normally handled by BIOS anyways.

---

### Post by RealG187 on 2007-12-10
> **dfreer said:**
>  prevent the boot options from being accessed without a password.


So I can make it lock into Windows or Ubuntu?



> **dfreer said:**
> 
EDIT: I don't think it's possible to boot a bootable CD/floppy from GRUB, at least in the terms of standard Live CD's/Windows Install CD's. That is normally handled by BIOS anyways.

Well that's insecure though...

---

### Post by Zack McCool on 2007-12-12
> **RealG187 said:**
> So I can make it lock into Windows or Ubuntu?

What do you mean "Lock into Windows or Ubuntu"?  You can use grub to set a default, but no, it doesn't lock it into anything.  That would be silly.

> 
Well that's insecure though...

It's as secure as ANY PC can be if physical access is possible.  If that is not enough security for you, you have to look to securing the location better.  The OS Cannot do it for you, nor can the bootloader.  Boot drive selection happens before the drive is involved, and is controlled by the BIOS.  The BIOS has the aforementioned security tools, but they are easily bypassed on a desktop by opening the case and shorting the BIOS clear Password jumper.  Most laptops do not have such a jumper, so on a laptop, the security is tighter.  Last time I was given a laptop with an unknown BIOS password, the only solution was shipping it to dell, as the battery was soldered on the mainboard, and they had no jumper.

*nix is built on a very strict network security model, but with physical access to any machine, security is limited.

---

### Post by dfreer on 2007-12-12
> **Zack McCool said:**
> What do you mean "Lock into Windows or Ubuntu"?  You can use grub to set a default, but no, it doesn't lock it into anything.  That would be silly.

Not that silly, if you don't want, say your little brother, to be able to boot into ubuntu, but you do want to allow them access to windows. And yes, you can password protect certain GRUB entries if you wish.

> **RealG187 said:**
> Well that's insecure though...

The whole point is this: If you are worried about malicious hackers breaking into your house to access your data, then restricting physical access to the machine is paramount. This is why most universities/large business have the server room locked and access is restricted.

However, if you are just trying to prevent your douchebag friends from messing with your root password while you are out of the room, or you happened to have [made a silly bet with an IT security specialist]("http://ubuntuforums.org/showthread.php?t=590262"), locking the BIOS with a password and changing the boot order so the Hard Drive is the only thing booted and locking GRUB entries and kernel options with a password is your best bet.

Encrypting the contents of the Hard Drive.

Here's some how-to's you may find useful:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_all_interactive_editing_control_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_all_interactive_editing_control_for_GRUB_menu)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_hide_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_hide_GRUB_menu_on_boot-up)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_timeout_seconds_for_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_the_timeout_seconds_for_GRUB_menu_on_boot-up)

---

### Post by bodhi.zazen on 2007-12-12
+1 dfreer

The bottom line is physical access is bad news.

The problem is not with insecure grub settings and setting a bios password and such will not stop and serious cracker.

---

### Post by RealG187 on 2007-12-12
> **dfreer said:**
> However, if you are just trying to prevent your douchebag friends from messing with your root password while you are out of the room, or you happened to have [made a silly bet with an IT security specialist]("http://ubuntuforums.org/showthread.php?t=590262"), locking the BIOS with a password and changing the boot order so the Hard Drive is the only thing booted and locking GRUB entries and kernel options with a password is your best bet.


> **dfreer said:**
> locking the BIOS with a password and changing the boot order so the Hard Drive is the only thing booted and locking GRUB entries and kernel options with a password is your best bet.

Let's say I want to boot from a CD, what is the best option? Do I have to set it to go back to CD and then when I am done set it back, is there a temporary override, there is the F12 boot menu, but that's not secure, is there a way I can make it ask for a password when I boot off CD.

---

### Post by dfreer on 2007-12-12
> **RealG187 said:**
> Let's say I want to boot from a CD, what is the best option? Do I have to set it to go back to CD and then when I am done set it back, is there a temporary override, there is the F12 boot menu, but that's not secure, is there a way I can make it ask for a password when I boot off CD.

It depends on your BIOS, some will let you hit a key to enter BIOS proper, and then another key will let you enter a small menu where you can pick which device in a list of allowed devices you want to boot from. 

Most will require that you enter the BIOS and switch your boot order around. I believe this is generally because live CD's didn't use to exist until recently, and so the only reason to change the boot order would be to install your OS. 

But still, even if your BIOS doesn't have a specific boot menu, you can still password protect just the BIOS and change the boot order like we said. Then, all that is required when you wish to boot to the CD, is that you enter BIOS, enter your password, and change the boot order back.

EDIT: And since the BIOS is completely separate from the Hard Drive or the OS, there isn't much you can do about it if your BIOS doesn't have this functionality. But honestly, if your NEED to protect your system from people booting a live CD, having to go through the trouble of entering your password and changing the boot order in BIOS should be worth it. I'm going to have a look around to see if GRUB can boot a CD, but I haven't heard of it before.

FURTHER EDITING: It appears I didn't read your previous question all the way through, sorry about that :( Anyways, so your F12 boot menu key doesn't require a password? I'll have to try mine out, I thought it did.
RE: GRUB booting a Live CD.
Hmm, it does seem to be possible. Very interesting to know, since it appears you could boot to a CD from a system whose BIOS doesn't support it.
[http://forum.insanelymac.com/lofiversion/index.php/t21605.html](http://forum.insanelymac.com/lofiversion/index.php/t21605.html)
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

---

### Post by RealG187 on 2007-12-12
[http://forum.insanelymac.com/lofiversion/index.php/t21605.html](http://forum.insanelymac.com/lofiversion/index.php/t21605.html)

So I could add the CD to grub and just password protect that then, that would be good.

---

### Post by bodhi.zazen on 2007-12-13
I can't resist, I feel the need to caution you, although those changes are somewhat helpful, they are very easily defeated and will keep out only the most casual of intruders.

I mention that because I would not want you to get a false sense of security with those changes. All those changes can be defeated in under a minute.

---

### Post by yaknowwat on 2007-12-13
With the availability  of recovery CD's about every operating system is insecure by direct access.

Not too often do people have friends/family that'd want to go up to a relatives computer and screw it up.

if somebody gets physical access to your computer the most secure thing you can do is blow it up.

Though yes Grub is a bit too insecure for a boot loader :(.
It's most likely like that to help with recovering if there is a problem anyways...
Basically a balance between insecurity & usuability & speed

---

### Post by dfreer on 2007-12-13
> **RealG187 said:**
> [http://forum.insanelymac.com/lofiversion/index.php/t21605.html](http://forum.insanelymac.com/lofiversion/index.php/t21605.html)

So I could add the CD to grub and just password protect that then, that would be good.

That's the way it looks, although the exact method of adding the CD Drive to GRUB might be difficult (I'm not sure what it's "rootnoverify" would be, something like "hda(1,0)" maybe?). One of the links I posted earlier should password protect GRUB, and then you add a new line to the entry you want to protect with the word "lock". Like so:
```
**title  Boot From CD**   ## You'll probably want a title like this
rootnoverify (....)     ## You'll need to figure out what needs to be here, not sure if I can help with this
**lock**
chainloader +1

```

---

### Post by RealG187 on 2007-12-13
I will try that when I get time.

Also, so I could also do USB and boot off USB on my old PC where the BIOS doesnt boot USB?

---

### Post by dfreer on 2007-12-13
> **RealG187 said:**
> I will try that when I get time.

Also, so I could also do USB and boot off USB on my old PC where the BIOS doesnt boot USB?

Interesting idea, although I don't know how. I guess this is where google comes in handy ;)

---

### Post by Zyphrexi on 2007-12-13
Solution:

Leave a sticky note on the monitor threatening physical injury to any evildoers. Just like in the movies, bad guys are usually cowards who don't like getting hit. Leave pictures of your past 'judgement' for good measure. Pace around it regularly swinging a metal bat agitatedly. Growl randomly at passers-by for no apparent reason


Disclaimer: In case you have no sense of humor, this is a joke. I should never be held responsible for anything I say, legally or metaphysically. By reading this disclaimer, you agree to agree with everything I say, have said, and may or may not say. Furthermore, all your base are belong to us.

---

### Post by Shazaam on 2007-12-13
You could put grub on a usb thumbdrive, set up the pc bios so it boots usb first. Then you will need to set it up to boot  Windows by default without the thumbdrive plugged in. Most modern pcs go through the boot order pretty fast.
Or you could put something like PuppyLinux or dsl on the thumbdrive and just change the boot order to usb first.

---

### Post by erginemr on 2007-12-14
> **Zyphrexi said:**
> Solution:
........
Furthermore, all your base are belong to us.

:lolflag: 

Aahh, good old days when games were made for good gameplay, not for fancy graphics...

---

### Post by RealG187 on 2007-12-14
> **Shazaam said:**
> You could put grub on a usb thumbdrive, set up the pc bios so it boots usb first. Then you will need to set it up to boot  Windows by default without the thumbdrive plugged in. Most modern pcs go through the boot order pretty fast.
Or you could put something like PuppyLinux or dsl on the thumbdrive and just change the boot order to usb first.

That wont work, someone could then just bring their USB drive in and get it...

---

### Post by chips24 on 2007-12-14
who would want to hack linux?

---

### Post by RealG187 on 2007-12-14
> **chips24 said:**
> who would want to hack linux?

Computer theif? I dunno, I ran it at school and could have did damage if I wanted to.

BTW can someone reply here:
[http://ubuntuforums.org/showthread.php?t=641021](http://ubuntuforums.org/showthread.php?t=641021)

It's off topic, but i **need** help **really** bad!

---

### Post by ~LoKe on 2007-12-15
If someone has physical access to your computer, there's nothing you can do.

**NOTHING**.

Don't even consider that when worrying about security.  Everything goes out the window when they have physical access.

---

### Post by Lostincyberspace on 2007-12-15
lots of people would like to hack linux.

---

### Post by Chayak on 2007-12-15
If you want to protect your system from physical access then get the alt install CD and install your system with the LVM + encrypted filesystem.  You'll have to enter a passphrase (yes phrase as a weak password on this doesn't do any good) every time you boot but anyone booting a live cd will only see the encrypted drive.  Though they could do something like install a hardware keylogger and wait for you to type the password in and retrieve it later.

The general rule is if I have physical access I can root a box in the time it takes to boot into a live cd and type a few lines in the shell or depending on what I want I might just yank it right from the drive while in the live cd enviornment.  The same goes for windows systems.  If your drive is encrypted then the worst thing they could do is corrupt it but thats why you make regular backups right?

There are hardware encryption solutions like the seagate secure drives for notebooks

I've seen some crazy solutions people have come up with.  Your boot sector and encryption on a usb drive that you boot off of and then remove from the computer.  You keep that thumb drive on you.  That particular setup was for a server.  I have seem more elaborate ones.

You really need to realistically assess the risk to your system and find the most fitting solution for you.  I really doubt you'd need something like a harddrive that has it's own smartcard slot and pin entry to spin up and if you enter it wrong three times it zeros the keys (ie. perminately erases to DOD/NSA standards)

If you want something like that look at the Common Criteria Certification list for EAL4+ poducts.  Those are the things the DOD and three letter agencies use to protect classified data.

---

### Post by sloggerkhan on 2007-12-15
It's probably been said:
Any system of any OS, if someone has physical access it's insecure.
The best you can do is encrypt things and lock out the bootloader and bios.

---

### Post by RealG187 on 2007-12-17
Well just because they have physical accesss that doesnt mean I shuold not try to prtect the BIOS, Bootloader and OS.

---

### Post by ~LoKe on 2007-12-17
> **RealG187 said:**
> Well just because they have physical accesss that doesnt mean I shuold not try to prtect the BIOS, Bootloader and OS.

You could do whatever you'd like, but if you give me access to your machine, I will get your information.  The only security that's even viable is to stick your computer in a locked safe. =/

---

### Post by bodhi.zazen on 2007-12-17
> **~LoKe said:**
> You could do whatever you'd like, but if you give me access to your machine, I will get your information.  The only security that's even viable is to stick your computer in a locked safe. =/

+1

---

