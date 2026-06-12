---
title: "ecryptfs files - guidance"
date: 2014-07-18
forum: General Help
---

### Post by GSD4ME on 2014-07-18
Dear all

I have previously posted a thread about data recovery after a major crash on my Ubuntu machine:

[http://ubuntuforums.org/showthread.php?t=2213464](http://ubuntuforums.org/showthread.php?t=2213464)

and many thanks to all that replies there.

I have managed to make further progress here, by using the "testdisk" and "photorec" utilities to extract the files from my HDD.
As well as others, I now have a lot of them of type ECRYPTFS sitting on a new laptop and wish to un-encrypt them. (Note that the new laptop is a Windows 8 machine, but that is only because it is easier to store them there pro tem)

I have the encryption key so there is no problem there and my question here is:

Is there a quick, easy and reliable way of decrypting the files? IE is there an available utility that can be used to extract the details, apart from the one that is available on UBUNTU as  a default? Or do I need to somehow use that?
Also, do they need to sit in a certain file structure to be accessed, or can the files be anywhere and the decryption utility be told where to get them from via a folder selection?

I have still lost a collection of files - as usual, most of them irreplaceable photographs etc. - but am slowly getting there.
Many thanks

---

### Post by whitesmith on 2014-07-18
Glad to hear you've made progress. Things looked bleak earlier this year.
> **GSD4ME said:**
> (Note that the new laptop is a Windows 8 machine, but that is only because it is easier to store them there pro tem)

This statement troubles me. Windows can't read Linux partitions (ext[2-4]), so the HDD in this machine must be formatted as something Windows recognizes such as NTFS. Problems now arise. For starters, Linux can read/write, but not run on, these partitions. This means the combination is incompatible. How are you going to decrypt your data? Even doing the job file-by-file requires copying everything to a Linux-formatted partition, assuming that I correctly understand your problem. If not, clarify matters and I'll try to help.

---

### Post by GSD4ME on 2014-07-19
Whitesmith

What I am doing is using my (still unusable) Ubuntu machine and booting it up, and then logging in to TERMINAL and running "testdisk" and "photorec" under that to analyse the partitions on the internal HDD
I have an external HDD attached - formatted as NTFS - where all the 'recovered' files are put by the utilities.
I then transfer all these files to my Windows 8 machine for storage, whilst I then move on to recovering the next partition on the Ubuntu machine (some of these partitions are taking over 24 hours to analyse!)
I therefore have all my recovered data on the Windows 8 machine, purely for storage at the moment.
The plan is (hopefully) to reformat and re-install Ubuntu on my 'old' machine and then transfer all my recovered files to it, thence to analyse the files.
Therefore, I just need guidance as to how to decrypt the encrypted files that I will have transferred back to my old machine.
Alternatively, if there is a way of decrypting the files on my Windows machine, then so much the easier
Thanks for the initial heads-up on the compatibility issues on ext[2-4] and NTFS

---

### Post by GSD4ME on 2014-07-27
I have downloaded the TED Technology utility "eCryptfs-Header-Parser" and run it.
It provides a lot of information.
But what does it all mean? Can I recover my files using some of the information supplied by this utility and the encryption key that I have?

---

