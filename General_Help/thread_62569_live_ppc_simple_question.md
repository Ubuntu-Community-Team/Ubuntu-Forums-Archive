---
title: "live ppc simple question"
date: 2005-09-05
forum: General Help
---

### Post by mikehallsted on 2005-09-05
just tried out the live ppc version, hoary, v5.04
looks pretty cool and works well on my snow imac G3.

my simple question....
is my local hard drive auto mounted when i boot from the live cd?
i did not see it anywhere in the file system, and the fstab file only mentioned the cdrom drive...

so my guess would be that it is not mounted, and until i mount it somehow, i have no access to any files on the hard drive.

thanks,
michael hallsted

---

### Post by rafakl on 2005-09-06
I dont know the PPC livecd version, but i think its like the x86, so: no, it dont mount your hard disk.

But you can try mount it by yourself because, for example the Knoppix live cd mounted automatically my windows and linux partitions.

try sudo mount /dev/hda

and see what happens
 :razz:

---

### Post by rafakl on 2005-09-06
I havent read the page, but it seems that it can help you:

[https://wiki.ubuntu.com/MountingHDDFilesystems?highlight=%28Live%29%7C%28CD%29](https://wiki.ubuntu.com/MountingHDDFilesystems?highlight=%28Live%29%7C%28CD%29)

---

### Post by mikehallsted on 2005-09-06
thanks for the link.  that was what i needed to know, guess i did not look in the right places the first time... local drives  are not mounted.

i have used knoppix many times before, and i am in complete agreement with its philosophy of initially mounting the local drives as read only.   but since the ubuntu live cd does not mount the drives at all... that's ok... just wanted to make sure.

i seem to be the computer guy that people ask questions to, and every once in a while, someone asks me about the "seedy" side of the internet.   i have no experience with whatever that means, and then i end up lecturing them about how dangerous that can be to  their computer.... viruses and trojans and other malware... and then i give them a cdrom with knoppix on it so they can satisfy their curiosity safely.  i really don't want to receive a phone call from them a week later about their computer melting down simply because they went to a website.  i already spend enough time removing malware from other computers.  lol...  it's better to be proactive instead of reactive. 

anyway... thanks.

---

### Post by sgmorr on 2005-09-18
Mike,

I'd be interested in mounting my HD in read only on my iMac G4 1GHz flat panel. I've fooled around with Ubuntu 5.04 live CD and recently with the preview of 5.10. They both start up and run well for me, but I haven't really found any instructions from a PPC person as to how to mount the Mac HD (or even if this is possible). Let me know if you ever actually do it. By the way, have you found a Mac version of Knoppix live? Thanks.

---

### Post by mikehallsted on 2005-09-19
since you asked, it peaked my interest...
and buried rather deeply in google, was this page:

[how to mount mac hd using ubuntu live cd ](http://jclark.org/weblog/Miscellany/ubuntumount.html) 

i'm printing this one out and saving the instructions.

---

### Post by sgmorr on 2005-09-19
Interesting, but it makes me nervous! I'm not going to try it right now so I'll file it away.

A couple of other questions arise.

Does Knoppix allow PC users to mount their drives in a more "user friendly" fashion? 

After the Mac switches to Intel processors, I assume users will have access to the full array of Linux products that are out there now for the PC. Correct?

---

### Post by mikehallsted on 2005-09-20
basically, knoppix is pretty awesome stuff.  no user intervention is necessary.

when one boots a computer with it, knoppix puts an icon on the desktop for each hard drive partition it finds.  if you have a USB thumb drive or external hard drive (USB or firewire) also plugged in, knoppix will also find them and put icons on the desktop for them. 

so, all one has to do is double click the icon for the hard drive partition you want to view, pretty simple.  and all internal hard drive partitions are mounted as read only.  my USB thumb drive was mounted as read/write.  with external drives, i know knoppix finds them, but i forgot to check about the permissions.

if the internal partition is formatted as FAT32 (typical for win95/98/ME) then right clicking the desktop icon and choosing (i forget which choice it is) allows one to easily change it to read/write.  if the internal partition is formatted as NTFS (typical for NT4/w2k/XP) then knoppix won't allow you to use the right-click gui to change it from read only to read/write.  linux can only read NTFS with 100% reliability.  linux can not (yet) write to NTFS with 100% reliablity.  (but with linux, from the command line, anything is posssible, so you "could" mount an NTFS drive as read/write, but at this moment in time, no sane person would).

with intel macs... it all depends on the hardware apple will finally decide to use, whether or not linux will work with it... out of the box that is to say.   i would think that there won't be a problem, but hardware compatibility is the area people overlook, but it should be the first thing people verify if they want a smooth linux experience.

toodles,
michael hallsted

---

### Post by ilmw on 2005-09-21
Can i ask how to boot apple from cd? i don't know how to change it ... it boots to mac by default ...

Thanks!

---

### Post by ilmw on 2005-09-21
never mind. i got it. thanks!

---

### Post by mikehallsted on 2005-09-21
well, just wanted to report that i followed the instructions for mounting the hard drive
[http://jclark.org/weblog/Miscellany/ubuntumount.html](http://jclark.org/weblog/Miscellany/ubuntumount.html)

and it does work just fine. do remember to unmount the drive before you quit the live cd session, it just makes sense and is a good habit to form.

however, my system folders were all locked, including my home folders, so i could not even browse into them to look.  i know that this is a good thing, but it does eliminate the live cd from any sort of rescue tool.

when i plugged in my USB thumb drive, ubuntu detected it and an icon for it appeared on the desktop.  right clicking on it in the file manager gave the option to unmount it.

---

### Post by sgmorr on 2005-09-21
Mike,

Is anyone working on something as elegant for the PPC as Knoppix is for x86? Is it just a matter of someone doing the work or is it a much more difficult or technically demanding task? Thanks.

---

### Post by mikehallsted on 2005-09-24
klaus knopper has been doing knoppix for a very long time ( like since 1999 ).  i can easily imagine that a whole lot of time and effort and programming brilliance makes knoppix what it is.  

i looked around for other live bootable ppc linux distributions, and there just isn't much out there at all.  gentoo had one, which i tried, but it looks like it was a side project, hasn't been updated since 2003, and i could only get 8bit color working on my imac.  other than that ubuntu looks like the best thing us mac people have.

i'm just guessing here, but i feel there are so many choices for windows computers because there is a real need for it.  windows can be down right hostile when trying to setup multiple hard drive partitions for booting into different operating systems, and forget about the concept of booting your windows computer from an external hard drive.  bootable linux cds for windows actually fill a desperate need for pc users for just basic disaster recovery.

macs, on the other hand, are truly marvelous in this respect, so i don't think there was ever much of a need for this type of capability.  i  have only been using a mac for a few years now, so i have never really got to use os9 and anything before that.  but i found it absolutely amazing that one could partition a hard drive, say into 5 volumes, and simply copy the os9 system folder to each of those 5 volumes, hold down the option key when one boots the mac, and then you could choose any of those 5 volumes to boot from.  shoot, one could then partition an external drive the same way, and you could have 10 different options for booting your mac.  this still blows my mind.  granted, with osX, you just can't copy a folder and have a volume bootable, but with very little effort, one can have multiple volumes with multiple copies of osX on internal and external hard drives and you can easily choose to boot the mac from any of them.  this is apple's greatest feature and there is nothing in the pc windows world that even remotely compares to this, past present or future.  maybe i'm easily amused, but i find this capability with apples truly amazing.... i spent my fair share of time installing dual boot windows/windows and windows/linux computers,  and it is no fun when the boot process gets hosed.  when that happens, all you have is either a floppy disk or a cd as recovery options.  apples are very cool.

ummm, sorry for rambling, i just don't think there was ever a need for it, so no one ever bothered doing a knoppix-like useable bootable live cd for ppc apples.

---

### Post by sgmorr on 2005-09-24
Thanks, Mike, for your interesting explanation of all this.

As an aside, do you think the switch to Intel is going to make Macs any less "Mac-like"?

---

### Post by mikehallsted on 2005-09-26
i wouldn't think so. what makes a mac a mac (for me anyway) is how i interact with the computer... which is mostly from a software standpoint.  installing software, using software, the icons, user interface... most computer users are pretty oblivous to the actual hardware.  i feel that a mac will be a mac, regardless of the hardware it runs on.  the one benefit, that i am looking forward to, with the upcoming switch to intel is... codeweavers said that they will support macs once they run on intel. codeweavers crossover office runs windows programs (some of them) natively, allowing one to install and run window programs.  i have a handful of small windows programs i like, and to be able to run them on a mac would be really cool.

---

