---
title: "CD RW disappeared from Feisty"
date: 2007-11-24
forum: General Help
---

### Post by Rockatansky on 2007-11-24
Hello-

I installed Feisty Fawn on a Xander 64-bit system about 4 months ago for my girlfriend to use.  Besides a few problems with getting flash to work on the 64-bit system it's been great.

But...

A couple of weeks ago the optical drive stopped working.  It is a CD-RW/DVD-ROM, and up until then had been fine.  It will not recognize any media put in it when the system is booted up, nor will it boot from the install CD.  To fix it I've tried:

-Buying a used CD drive and replacing the drive
-replacing the IDE cable with a different one
-installing the drive as a slave on my hard drive IDE channel in case the IDE channel 2 is completely bad.

None of this has helped.

My BIOS always recognizes that the drives are there, and how they are configured.  In Ubuntu the hardware manager also always sees them.  If I try to force mount I just get a "there is no media in the drive" response.  


The one thing that seems fishy (besides the drives not working) is that my bios looks like it flashes a "no boot found" message or something like it and then skips the CD and goes straight to the hard drive.  It's hard to see exactly what it says, because GRUB pops up as soon as that message shows.

Any help would be appreciated... so far I've found a few posts with similar problems, but no great solution on how to deal with it.  Thanks for taking the time.

Mike

---

### Post by n_i_c_k on 2007-11-24
Does a CDROM appear in the output of
```
sudo lshw -class disk
```
?

---

### Post by Rockatansky on 2007-11-24
Hey there-

Thanks for the help.

Yes, a CD ROM does appear with the logical name of /dev/hdc; its the same in my /etc/fstab.

Have you run into similar problems?  So far from checking out the forums it seems like there's no real fix for other people with similar problems... I'm starting to think about trying to install the LTS release from a USB drive and see if that fixes things.

I'll probably be slow on the replies... the box is at my GF's apartment, so I don't always have it in front of me.  Thanks for taking the time, though, and I hope someone has an idea.

---

### Post by Rockatansky on 2007-11-25
After posting I tinkered some more, and with a little coaxing I was able to make my BIOS boot from an install CD; that makes me 100% sure it's a software thing, and not a problem with my system setup.

Well, now that I can boot from a CD going to the LTS is looking more and more appealing...

---

