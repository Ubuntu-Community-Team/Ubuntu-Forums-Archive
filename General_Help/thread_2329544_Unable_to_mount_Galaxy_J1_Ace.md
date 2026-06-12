---
title: "Unable to mount Galaxy J1 Ace"
date: 2016-07-02
forum: General Help
---

### Post by Corvair on 2016-07-02
Hello everyone,

I have recently acquired a Galaxy J1 Ace SM-J111M/DS android version 5.1.1 I get a message: unable to mount Samsung Android.
Error initialising camera -60: could not lock the device. This is on camera setting (PTP). It does not accept MTP setting which is for windows and Imac.
I had a  Galaxy Ace before and had no problems mounting it.
I use version 12.04 precise 12 bit with GNOME 3.4.2.

Any suggestions on what i can do to solve the problem?

Thanks for reading

Corvair

---

### Post by mörgæs on 2016-07-03
How does it work in a live boot of 16.04?

---

### Post by Corvair on 2016-07-03
I use Ubuntu 12.04, I don't understand about booting with 16.04

---

### Post by mörgæs on 2016-07-04
Yes, that could be the problem and that's why it would be interesting to compare with 16.04.

A live boot does not change anything on the hard disk. It's only for testing.

---

### Post by skywalker4 on 2016-07-04
have you tried this?

```
sudo apt-get install mtpfs
```

---

### Post by Corvair on 2016-07-04
Thanks for the idea but it does not seem to install properly.
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
claude@claude-desktop:~$ 
claude@claude-desktop:~$

---

### Post by Corvair on 2016-07-04
You may be right but you will have to show me how to do this as this is more than I understand.
Thank you Morgaes

---

### Post by mörgæs on 2016-07-05
You could also backup your important files and do a fresh install (no upgrades) of 16.04 the same way as you installed 12.04.
Sooner or later you will have to do this anyway.

---

### Post by Corvair on 2016-07-05
Is 16.04 an LTS version? If not I would prefer to go to 14.04 LTS. 
All my files are backed up on another hard disk. I use a solid hard disk for my OS and work area, so this should not be a problem.

---

### Post by mörgæs on 2016-07-05
Yes, 16.04 is LTS.

All the 04's of even years are.

---

### Post by Corvair on 2016-07-05
Good, I am downloading it now, I let you know what happens

---

### Post by Corvair on 2016-07-06
OK. I have downloaded Ubuntu Gnome 16.04LTS PC 64 bits from the Ubuntu official site ubuntu.com. I have downloaded the direct download and not the torrent file, I don't know if this makes a difference.
I have burnt an image file to disk with K3b and one with Brassero disk burner since the first one does not seem to boot and the second does not boot either. The problem may be that when I turn the computer on it goes directly to hard disk boot. 
I opened the BIOS menu to change the booting from the cd/dvd drive and I do not have access to change this the boot order. I have an Intel motherboard number DP67BG. I don't see why since I have installed  version 12.04 from a cd and previous versions also without a problem. I don't recall if I was able to change the booting order or not.
So the only option I see is to make an upgrade instead, this worries me because upgrades often go wrong and then I will be up the creek without a paddle.

Any comments on this?

---

### Post by mörgæs on 2016-07-07
Agree, I would also stay away from upgrades. Let's focus on the clean install.

Do the DVD's work in another computer?

---

### Post by Corvair on 2016-07-07
I just loaded it on my old laptop without a problem so it is not the disk that has a problem. I suspect my BIOS. Maybe I could do a hard reset on the motherboard and see what happens, or download a BIOS update from Intel. I have downloaded a reset but I am hesitating on trying to load it onto the board.

---

### Post by mörgæs on 2016-07-07
Does the DVD drive work well for playing a standard movie DVD or sound CD?

You could also try booting from USB. 

I guess I have updated BIOS some 30-40 times, never with any bad experiences. Just search for what has been posted for your particular motherboard to see if there are any warnings.

---

### Post by Corvair on 2016-07-07
I have installed another cd/dvd drive just to make sure and that's not the problem. they work properly. I don't know how to burn an image file to USB drive. First should the drive be free of any other documents/files? 
I tried to installed a new BIOS that I downloaded and put on USB drive and tried t upgrade using F7 on start up but their seems to be no change . I still don't have access to changing anything in the BIOS, like the order of booting, it is just not accessible. I think the problem is there. I may have to go to a local technician to solve that BIOS problem.

---

### Post by Corvair on 2016-07-08
Looks like my latest message did not make it through, just in case here it is again. Problem solved. I had to change the pin settings on the BIOS in order to be able to change the booting order and be able to load the 16.04 image disk, so finely the new lts it up and running on my tabletop
and also on my laptop and they both recognize my cellphone. Thanks for the help and patience

---

### Post by mörgæs on 2016-07-09
Good. please spread the word. When the problem is hardware support a good first move is a fresh install of the latest release.

---

