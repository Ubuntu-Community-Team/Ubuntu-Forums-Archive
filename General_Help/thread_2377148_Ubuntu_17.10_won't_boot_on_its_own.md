---
title: "Ubuntu 17.10 won't boot on its own"
date: 2017-11-09
forum: General Help
---

### Post by euphgeek on 2017-11-09
This started when I was testing some RAM for another computer.  The computer powers on just fine, runs through the POST, it gets to "Boot from CD/DVD" then just sits there on the next line without doing anything.  If I put in a bootable CD/DVD, then it recognizes that just fine and boots to it.  If I tell the bootable CD/DVD to boot from the hard drive, Ubuntu boots up just fine.  I formatted the root partition and installed Ubuntu 17.10 fresh.  I tried putting grub on /dev/sdb and on /dev/sdb1.  Neither one worked.  I even scanned the 80GB hard drive for errors with GRC SpinRite 6 but nothing was found.  Any ideas?

---

### Post by RobGoss on 2017-11-10
> This started when I was testing some RAM for another computer  

Do you still have the Ram in this machine you used from another computer? It may not be compatible 

And is this a single boot machine with only Ubuntu on it?

---

### Post by euphgeek on 2017-11-10
> **RobGoss said:**
> Do you still have the Ram in this machine you used from another computer? It may not be compatible 

And is this a single boot machine with only Ubuntu on it?

I've tried it with and without the RAM from the other computer.  Makes no difference.  And yes, this a single boot machine.  Grub has been working for years up until now.  It just seems like the computer freezes at the point where it's supposed to hand off control to the operating system on the hard drive.  I'm starting to consider the possibility that there may be an issue either with the BIOS or the motherboard itself.  I checked the boot order in the BIOS and the hard drive is there.

---

### Post by RobGoss on 2017-11-10
Can you even boot to the live desktop? 

I don't really like advising to replace any hardware if I'm not certain it's faulty.

What are the specs for your machine?

Seeing it's only a 80-GB drive I'm assuming it's a old machine

If you're installing Ubuntu and using the entire disk you should not have any trouble installing the Grub menu it will do everything for you

---

### Post by euphgeek on 2017-11-10
> **RobGoss said:**
> Can you even boot to the live desktop? 

I don't really like advising to replace any hardware if I'm not certain it's faulty.

What are the specs for your machine?

Seeing it's only a 80-GB drive I'm assuming it's a old machine

If you're installing Ubuntu and using the entire disk you should not have any trouble installing the Grub menu it will do everything for you

Yes I can boot to my desktop as long as I use a bootable DVD that has an option to boot from the hard drive.

My computer is old, but not as old as the 80GB hard drive would indicate.  It has a second 1TB hard drive.  The motherboard is a Gigabyte GA-MA78LM-S2H, socket AM2+.  It now has 6GB RAM, up from 4 previously.  I bought it seven years ago.  I can't think what the issue would be if not hardware.  If you can think of anything I'm missing, I'm willing to try it.

---

### Post by RobGoss on 2017-11-10
Have you tried creating a bootable USB and installing Ubuntu that way? I find using a USB works a lot better in most cases

---

### Post by euphgeek on 2017-11-10
> **RobGoss said:**
> Have you tried creating a bootable USB and installing Ubuntu that way? I find using a USB works a lot better in most cases

No, I just used a bootable DVD.  What's the difference between the two?

---

### Post by RobGoss on 2017-11-10
In my experience using a DVD or CD, may not always work depending on the machines and how old the DVD or CD drive is, A USB is a lot faster when it comes to getting the OS installed and may be another option for you

---

### Post by euphgeek on 2017-11-10
> **RobGoss said:**
> In my experience using a DVD or CD, may not always work depending on the machines and how old the DVD or CD drive is, A USB is a lot faster when it comes to getting the OS installed and may be another option for you

Well the install seemed to go fine.  As a matter of fact, this started before I even installed 17.10, while my computer was still running 17.04.

---

