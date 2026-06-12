---
title: "Ubuntu hangs at Configuring Language"
date: 2005-04-04
forum: General Help
---

### Post by Timeless Enigma on 2005-04-04
I've only recently started trying out Linux and it's not working out so far.
I have 2 computers that I am trying Linux on and one of them refuses to boot.  I've only tried Debian-based distros so far, like Knoppix and Ubuntu, but while they will boot up fine on the other computer, this one has problems.

I am using the latest Ubuntu LiveCD and I hang at the "Configuring Language..." part of the setup.  It seems to hang since it stops at that screen and I hear no CD-Drive noise and no indication of activity.  I use the American English option.

The computer has
ASUS P4P800-E motherboard
Intel 865 Chipset
ATI RADEON 9800 PRO
P4 2.6 GHz Processor

I have 3 active hard drives, all are Maxtor.  The Primary drive and another are PATA-133, the other one is SATA.
My only disc drive is a Dual Layer DVD-RW drive.

I have used such boot options as noapic, nolapic, nofstab, but the point where it hangs is still the same.

When I tried using the latest Knoppix LiveCD it would always hang when trying to create an fstab.  nofstab did work successfully to complete the boot with the Knoppix LiveCD.

Thanks for any help provided.

---

### Post by Bob Lindstrom on 2005-04-12
I have the same problem. It appears that the system is waiting for keyboard input, but the system won't recognize input from the keyboard at that point. The program hasn't really "hung," it's just waiting for you to do something -- and you can't.

Anyone??

---

### Post by frugalmail on 2005-10-26
Just wanted to add a me-too post.

Gentoo gets an Oops on CPU detection.
Compaq 1850R (rack mounted server) 1GB RAM ATI (coincidence?) on board video, Smart Array 3200, on board RAID, etc...

BTW, Compaq servers are horrible, I have to dig up inflexible software to configure everything when it should be in configurable BIOS.  The Dell servers I used are far nicer.

---

### Post by pytron on 2006-02-24
Hate to dredge up an old thread, but wanted to add a "me three".

My machine also hangs when using the LiveCD.  I get CD-ROM activity periodically (sort of a rhythm), while it is "hanging".  I have not tried the Install CD to see if I get the same issue.

Specs:
Ubuntu 5.10 Live CD
Compaq Deskpro EN
866 MHz Intel P3
Onboard video: Intel 815E
512 MB PC133 RAM

Here is a link to show pretty similar specs (note that mine has onboard video):
[http://www.windowsmarketplace.com/specs.aspx?itemId=125140&stext=](http://www.windowsmarketplace.com/specs.aspx?itemId=125140&stext=)

If you need testing for a fix or want to contact me with questions, please feel free.

---

