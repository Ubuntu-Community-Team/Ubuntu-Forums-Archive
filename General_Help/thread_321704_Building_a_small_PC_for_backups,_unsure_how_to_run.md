---
title: "Building a small PC for backups, unsure how to run the backups"
date: 2006-12-19
forum: General Help
---

### Post by linuxbun on 2006-12-19
Running solely off a laptop has always given me big issues when backing up. I used to go by an external harddrive but after that failed on me, I've not backed up for a while.

A harddrive has become available and with what parts I've got knocking about here, I reckon I'll be able to build a small pc for backup purposes for nowt.

Basically what I want to know is:

1) What's the securest way to backup from my webspace?
2) Will ubuntu protect my files once downloaded (from being hacked) and is a bios password on the hdd enough to stop unauthorized physical access?
3) Once set up and running, will I be able to remote desktop it from a laptop without loggin in first? (never used the software before, unsure how it works. Once built, if I can, I don't want anything plugged into it bar the power & network cable so it can be controlled from my laptop).

Any help would be most appreciated :)

---

### Post by aysiu on 2006-12-19
If someone has physical access, then all your data is compromised, BIOS password or not.

---

### Post by linuxbun on 2006-12-19
> **aysiu said:**
> If someone has physical access, then all your data is compromised, BIOS password or not.

How can you bypass a bios password? :o 

Is there no way to protect the data from physical access? Maybe I do need to encrypt everything that's downloaded but,, if the original was on there first, I'm not sure if some recovery software will just read it :confused:

---

### Post by aysiu on 2006-12-19
I would bypass it by taking the hard drive out of the computer.

---

### Post by linuxbun on 2006-12-19
> **aysiu said:**
> I would bypass it by taking the hard drive out of the computer.

That won't get you anywhere, I think you've missunderstood :). In bios you can set a password on the hard drive. I did this once and moved the harddrive out of an old laptop into a new laptop. It still prompted me for my password at bootup.

I'm just not sure what sort of attacks are out there to hack a bios set hdd password.:-k

---

### Post by aysiu on 2006-12-19
> **linuxbun said:**
> That won't get you anywhere, I think you've missunderstood :). In bios you can set a password on the hard drive. I did this once and moved the harddrive out of an old laptop into a new laptop. It still prompted me for my password at bootup.

I'm just not sure what sort of attacks are out there to hack a bios set hdd password.:-k
I'm no techno-genius, so someone correct me if I'm wrong, but I don't think the BIOS password has anything to do with the hard drive. If you take the hard drive out and put it into another computer, you can just mount the drive in that computer and steal all the data off it.

I believe there are also ways to physically reset the BIOS, too, but... again, I'm not a techno-genius, so I don't know the details of how that works.

---

### Post by linuxbun on 2006-12-19
To my knowledge, the bios password can be re-set easily be simply removing it's battery (as it loses it's memory).

My apologies, bios is probably the wrong word I'm using here. When you do enter bios (well on my dell) it gives me an option to set either a password at bootup for everything, password to enter bios menu or to password protect my harddrive (so it's configures the hard drive some way). This does work as when I've swapped this hdd out into another laptop, the password indeed has stayed in tact :)

---

### Post by milton1 on 2006-12-19
Aysiu is right, if yout have physical access, you have root access. There is no perfect security. As for secure reansfer from your webspace, that depends on what protocols the webspace uses. If it only provides for ftp, your are out of luck. Best, simplest option, if you can use it, would be sftp or scp, both of which operate over ssh.

---

### Post by aysiu on 2006-12-19
> **linuxbun said:**
> To my knowledge, the bios password can be re-set easily be simply removing it's battery (as it loses it's memory).

My apologies, bios is probably the wrong word I'm using here. When you do enter bios (well on my dell) it gives me an option to set either a password at bootup for everything, password to enter bios menu or to password protect my harddrive (so it's configures the hard drive some way). This does work as when I've swapped this hdd out into another laptop, the password indeed has stayed in tact :)
But passwords don't mean anything if you have a Knoppix CD.

A BIOS password stops only someone changing the boot order (allowing them to boot from CD), but if the hard drive gets physically removed and placed in another computer, that computer can be booted from CD and thus can mount your hard drive with Knoppix (or Ubuntu or whatever).

---

### Post by linuxbun on 2006-12-19
> **aysiu said:**
> 
A BIOS password stops only someone changing the boot order (allowing them to boot from CD), but if the hard drive gets physically removed and placed in another computer, that computer can be booted from CD and thus can mount your hard drive with Knoppix (or Ubuntu or whatever).

Hmmm, this is strange and it is bugging me now. I'm sure I set a password on my hdd and when I had a new laptop (same model etc) I switched the hdd over and it still prompted me for a password. (OT) I'm about to install fedora (not permanent! don't worry) to recover some very old docs that I lost a long time ago (found this hdd). I'm going to format this with fed, place a bios password on the hdd and swap it out into another computer (while I have so many machines here at my disposal). I'll let you know the outcome tonight :D

---

### Post by linuxbun on 2006-12-19
> **milton1 said:**
> Aysiu is right, if yout have physical access, you have root access. There is no perfect security. As for secure reansfer from your webspace, that depends on what protocols the webspace uses. If it only provides for ftp, your are out of luck. Best, simplest option, if you can use it, would be sftp or scp, both of which operate over ssh.


Dude, thanks for your reply, atm, I only access my webspace via ftp, they're pretty good hosts, I'll see if they allow other connections.

---

### Post by technodigifreak on 2006-12-19
OK, just to correct a few misunderstandings............... :D

There are BIOS Passwords and then there are password locked HDD's.  They are two different things.  All modern BIOS can be password protected (which can be defeated by removing the CMOS battery temporarily), but depending on your BIOS manufacturer, you can also set a boot password in your BIOS which will keep your PC from booting off of any media (HDD, CD, PXE, Floppy, etc.) unless you supply the password.  A password locked HDD is different, and not all HDD models support this.  The HDD lock will prevent the drive from responding to access requests unless the password is supplied.  My understanding is that this applies to whether the HDD is in the original machine or not.  However, I've also seen HDD's that use locks that are dependent on the original machine, instead of a password.  Meaning, if they are removed from the original machine, they will not respond to access requests regardless of if they are in an external drive or not.  I believe this relies on hardware addressing, but am not 100% sure.

basically, if they have physical access to your machine, they can get your data.  The only way around this is to use disk encryption.  but disk encryption is useless when your machine is active and your data is being accessed (because it is *unencrypted*).  Also, transmission of your data (the backup process) will need to be encrypted.  An ssh tunnel or vpn will work just fine for this.

**It depends on how much time you're are willing to put into this and how valuable you think your data is worth.  Security is about making it more of a pain in the *** for a cracker to access the data, then the actual/perceived value of the data.  The important thing to remember is that given enough time and effort, your data will eventually be compromised, the trick is getting the attacker to give up before they reach the payoff point.**

In most cases, it's just important that you *have* a backup.

---

### Post by technodigifreak on 2006-12-19
> **linuxbun said:**
> Dude, thanks for your reply, atm, I only access my webspace via ftp, they're pretty good hosts, I'll see if they allow other connections.

You're trying to backup webspace?  Nevermind my previous post.  Just assume it's insecure.  Highly private information should never be on a web/ftp server.

Write a simple ftp script to download your public_html folder once a day and leave it at that. :D

---

### Post by aysiu on 2006-12-19
Thanks for that clarification, technodigifreak.

---

### Post by joneberger on 2006-12-19
> **technodigifreak said:**
> You're trying to backup webspace?  Nevermind my previous post.  Just assume it's insecure.  Highly private information should never be on a web/ftp server.

Write a simple ftp script to download your public_html folder once a day and leave it at that. :D

exactly.  if it's already on a webserver, then it's already insecure and encryption passworded backups are useless.

to add fuel to the BIOS fire, i believe there were tons of mobos made so that to reset the BIOS password, you simply removed a jumper shunt and rebooted

---

### Post by linuxbun on 2006-12-19
Many thanks to all, that has cleared up a few things :D 

This box will only be used for backups, I'll never need to go to the data unless I want to do a restore etc, so maybe encryption is the way forward.

The stuff that's stored on the webserver is websites and it's databases that I want to backup. That's still insecure? I pay a lot of money for the webspace :confused: I'm just looking for a way to set an automated backup of the webspace that will be secure in the downloading.

---

