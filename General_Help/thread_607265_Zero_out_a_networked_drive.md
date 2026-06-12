---
title: "Zero out a networked drive"
date: 2007-11-08
forum: General Help
---

### Post by Mongo5000 on 2007-11-08
So I have a mybook world edition NAS and just not happy with it so im gonna return it.

How can I zero out the data on it so it can't be retrieved?

---

### Post by BoneKracker on 2007-11-08
It's simple:

```
sudo dd if=/dev/random of=/dev/whatever
```
(where "whatever" is the drive in question).

This will take some time -- you are writing random data to every bit on the device.  Depending on your system, we're talking hours -- do it overnight.

You can also use this to "shred" any file.  Just replace of=/dev/whatever with of=/path/to/file.

People may tell you differently, but multiple passes are unnecessary.  This is virtually impossible to recover data from even with a magnetic microscope.  If you're paranoid, you can do it more than once.

You should always make sure you understand any command someone tells to you run before you do it.  Read the man page for dd.  (At the command prompt, type "man dd".  Be careful, one typo and you you'll irreparably erase whatever you pointed it at.

---

### Post by dcstar on 2007-11-08
> **Mongo5000 said:**
> So I have a mybook world edition NAS and just not happy with it so im gonna return it.

How can I zero out the data on it so it can't be retrieved?

There are various freeware downloads that can be used to securely erase hard drives (and I mean to military standard), a quick web search should bring up many options.

Modern IDE drives have a secure erase function built into the firmware, but you'd have to directly connect the hard drive to your motherboard to use it with the packages that I've seen, erasing a NAS device makes things a bit tricky as it is an external device with it's own O/S.

---

### Post by dcstar on 2007-11-08
> **BoneKracker said:**
> It's simple:

```
sudo dd if=/dev/random of=/dev/whatever
```
(where "whatever" is the drive in question).
.........


A NAS device is not a mounted hard drive, it has it's own O/S (usually Linux) and is accessed as a mounted drive on an external server, so that method does not apply.

---

### Post by BoneKracker on 2007-11-08
I thought this would work with any "file", for example, anything you could point netcat at you could use this on.  Not the case?

---

### Post by BoneKracker on 2007-11-08
Okay, I did a little checking around.  I think what I suggested would work.  

People are using dd to back systems up to NAS.  If that's the case, then why wouldn't one be able to write random data instead of the contents of some filesystem?  A file is a file as far as unix is concerned.

But if the NAS or the firmware of the disk(s) has the functionality to do it directly, that's definitely going to be better -- if for no other reason than eliminating the LAN as a speed constraint.

---

### Post by Mongo5000 on 2007-11-09
whoa, this stuff is WAY over my head!  but I really appreciate the help everyone!

So i was wondering this.  My NAS has 2 500g drives in it in a RAID 0 right now.  Using the supplied software, I can turn it into a RAID 1.

Now I know it will have to reformat the drives to build the array, what kind of formatting would that do?  Would it be good enough?

---

### Post by BoneKracker on 2007-11-09
I'll defer to dcstar as he knows more about this than I do.

---

### Post by dcstar on 2007-11-11
> **Mongo5000 said:**
> whoa, this stuff is WAY over my head!  but I really appreciate the help everyone!

So i was wondering this.  My NAS has 2 500g drives in it in a RAID 0 right now.  Using the supplied software, I can turn it into a RAID 1.

Now I know it will have to reformat the drives to build the array, what kind of formatting would that do?  Would it be good enough?

It depends how paranoid you are as to whoever may try to access you previous files, if you reconfigure and install/format it would probably prevent 99.99% of people getting access to anything that was on them previously, the question is how concerned are you about the remaining 0.01%?

---

