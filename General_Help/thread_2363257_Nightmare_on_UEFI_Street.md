---
title: "Nightmare on UEFI Street"
date: 2017-06-08
forum: General Help
---

### Post by john_ladasky on 2017-06-08
Hi folks,

They say, if it's not broken, don't fix it.  Well, it wasn't exactly broken, and I tried to fix it, and now I have a mess.

My hardware: a Gigabyte GA-X99-UD4 motherboard, released August 2014; Intel i7-5820 CPU; 16 GB RAM; NVidia GTX 760 GPU.  All reasonably recent and powerful.  I had the system configured to dual-boot Windows 7 and Ubuntu 16.04 from BIOS.  It was running perfectly stably.  But...

 I get tired of manually building cutting-edge scientific computing packages from source.  I need the latest bug fixes in Python.  I use CUDA and TensorFlow, which are in constant flux.  Therefore, I upgrade Ubuntu frequently. I like to use as many pre-built packages as I can. 

I have to keep a copy of Windows around for income tax time.  Also, my son and I talk about eventually playing games online together (if I can ever find time).

I made several big changes at once.  Everything worked, at least initially:


[LIST]
[*]I got an SSD.  A Samsung V-NAND Evo 850, 500 GB.  I got one for my work computer 18 months ago, and it was the best performance upgrade per dollar I have seen in computing in many years. I have kept my old HDD in the system, but I removed the OS partitions and kept my data partitions.  I'll use it for backups. 
[*]I got Windows 10 Home.  I installed it in 64-bit mode on the SSD using the UEFI configuration.  Good bye to BIOS, and msdos partition tables.  (I figured that would help... maybe not?) 
[*]I installed Ubuntu Gnome 17.04, which I also installed in 64-bit mode on the SSD using UEFI. 
[/LIST]

I managed to boot into each operating system a few times without incident.  I installed the GPU drivers on both Windows and Ubuntu.  I happen to have a configuration this time around that needs "nomodeset" on booting Ubuntu in order to play nicely with the GPU.  I've been with Ubuntu for 11 years, and I only encounter the nomodeset problem every three years or so, so I have a tendency to forget about it, and then to remember it all over again.

After a few days of use, suddenly I couldn't boot into either OS.

Windows 10 auto-repair from the USB stick managed to bring Windows back from the dead.

I was expecting to find the Gtk Boot Repair tool on the Ubuntu Gnome 17.04 install disk.  It wasn't there, why not?  It seems like an obvious thing to include.  In any case, I found [these instructions]("https://askubuntu.com/questions/165255/unable-to-install-boot-repair"), installed Boot Repair while operating from the Live CD, and let it do its thing.  I acquired a dozen mysterious new entries in GRUB, but I could still find Ubuntu and Windows, and boot into both of them.

This configuration lasted me about two days of additional use.  This evening, everything crashed again.  

In both the first and the second crashes, I got error messages of the form "error:failure reading sector 0x1deb5000 from'hd0'." (I have seen other sectors listed).

Only on the second crash, I also saw "error: environment block too small."

Below those error messages, I also see "Press any key to continue...", but pressing keys does nothing.  I have to reboot.

This time, when I tried Boot Repair, it seemed to hang.  I know that Boot Repair warns that "the scan could take several minutes," but the first time it ran, the scan took about 30 seconds.  After a half hour, I gave up.

Right now I'm running from the 17.04 live CD.  My hardware is definitely functional, but there's apparently a huge problem with UEFI and disk partition management. 

Does anyone have any idea where to start?

Thanks for your advice!

---

### Post by john_ladasky on 2017-06-08
Following up to myself: I just found another web page that describes eerily similar symptoms:

[https://askubuntu.com/questions/712049/what-causes-error-environment-block-too-small-press-any-key-to-continue-mes/838334](https://askubuntu.com/questions/712049/what-causes-error-environment-block-too-small-press-any-key-to-continue-mes/838334)

This user had an intermittent MECHANICAL problem with the SATA power connector to his SSD.  Of course, I started working on my system with the case open, and then I closed it when I thought I was done.  I've never been entirely satisfied with the firmness of SATA connections, either data or power; the cables barely seem to snap onto their connectors, and they're still a bit wiggly afterwards.  On top of that, as I was bending the cables into the case when I closed it, I noticed some strain and crowding.

I am opening up my computer case and I will try again.  I will try system repairs with the case open.  I won't close the case after I'm done.

Maybe I should have entitled this thread "Nightmare on SATA Street" instead?  Time may tell.

If you have any other thoughts, though, please feel free to tell me I'm being superstitious.  Thanks!

---

### Post by oldfred on 2017-06-08
I used to do the same with the old PATA cables. I would have case open & everything worked, but then reaching in for something bumped cable. And it often looked fully plugged in, but when I had errors, it would let me push it in more firmly.
I like the new SATA connectors, but changed to the locking type, that are only sometimes included.

Back to your issue.
Some have had to update firmware in SSD.
I tried the Linux Samsung Magician, but could not get it to fully work. If you have Windows it should work there.

---

### Post by Habitual on 2017-06-08
I had one box in 1996 that when I screwed the case **down** it wouldn't boot.
Unscrewed, booted fine.
Sat there for 5 more years unscrewed.

---

### Post by john_ladasky on 2017-06-17
Here's a follow-up.  I believe that I had a mechanical problem after all.  I purchased a different computer case, slightly larger.  I moved my hardware into the new enclosure.  Everything has been running stably for eight solid days.  Strained SATA cables were most likely the culprit.  I was going crazy looking for a software problem.  Lesson learned!

---

