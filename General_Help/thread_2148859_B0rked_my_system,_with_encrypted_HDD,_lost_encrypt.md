---
title: "B0rked my system, with encrypted HDD, lost encryption key, cannot mount drive"
date: 2013-05-26
forum: General Help
---

### Post by snakeman21 on 2013-05-26
Hi all.  I'm kind of in a bind here.  I installed Ubuntu 12.10 a few months ago and chose to encrypt my drive when asked at installation.  When given the decryption key, I copied it to a text file and temporarily stuck in on the desktop with the intention of copying it over to a flash drive in the near future.  Well, half the crap I plan to do never gets done, and eventually that file ended up in a folder somewhere and was never transferred to an external media.  Stupid, I know, I'm banging my head against a wall over here.  

Yesterday, I was online using Facebook.  Not doing anything with my files or anything like that... Just perusing Facebook.  My computer started to run slow.  R-E-A-L-L-Y  S-L-O-W.  Firefox was the only program running.  I didn't know what the heck was slowing it down, so I simply hit the power button, waited 10 seconds or so until the prompt finally appeared (like I said, VERY slow), and chose reboot.  The computer logged out and shut down as it should, but upon reboot it brought me to the GRUB menu, which at this point had to kernel options, each with its own recovery mode.  I have tried all four options, and they all just bring me to the "intramfs:" prompt.  

No big deal, I said... I'd been wishing I installed 12.04 because I prefer the LTS releases anyways, so I figured I'd just back up and reinstall as I've done many times before. Well, that's when it dawned on me that the drive is encrypted and the decryption code is... Somewhere on the encrypted drive.

Crap.

So, I hit up Google, and found a few promising leads saying not to worry if you lost your decryption code, it can be recovered easily by booting a live Ubuntu CD/USB, mounting the encrypted drive, and running: 

```
ecryptfs-unwrap-passphrase /media/*04b67fb1-aafd-4082-aebc-493c509bdbe1*/home/.ecryptfs/**username**/.ecryptfs/wrapped-passphrase
```

Where the italicized text is replaced with the actual designation of your particular drive, and the bolded text is replaced with the username of the home folder you're trying to recover.  But no!  

The problem occurs in the mounting:  It will not allow me to mount the drive, seemingly because it's encrypted.  Without mounting the drive, I can't recover the passphrase that I need in order to... Mount the drive.  I tried live usb's of Ubuntu 12.04, Precise Puppy, CrunchBang, Slax, DSL, and my personal favorite, Porteus.  No luck, none of them could mount it.  At least I know nobody's getting my files from an encrypted Ubuntu drive!

Am I screwed up the proverbial wazoo as far as getting my files back?  There was nothing SUPER important on it, I do backups on a monthly basis, but there were a lot of new videos I took of my daughter that I'd much rather not lose.  Is there any hope of getting my stuff back or am I just going to have to cut my losses, reformat, and reinstall?

---

### Post by efflandt on 2013-05-27
You said you do backups. Is it possible that the encryption code is in those backups?

---

### Post by snakeman21 on 2013-05-27
> **efflandt said:**
> You said you do backups. Is it possible that the encryption code is in those backups?

Unfortunately, no.  It was in a folder on my desktop, and my desktop folder doesn't get backed up because it's pretty much just my "dump space" for partially completed projects and whatnot.  As things are completed, I put them in other folders and they get backed up.

I did open up my backup drive from Porteus and painstakingly went through every directory in an attempt to find it on the off chance I threw it on there without remembering.  No go.  I feel like an idiot.

---

### Post by Charlotte18 on 2013-05-27
Have you tried to use the live cd to purge and reinstall grub on the broken 12.10 installation?

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

