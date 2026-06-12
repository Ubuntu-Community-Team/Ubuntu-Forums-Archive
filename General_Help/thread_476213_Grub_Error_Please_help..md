---
title: "Grub Error Please help."
date: 2007-06-17
forum: General Help
---

### Post by bomb-24 on 2007-06-17
I installed Ubuntu on my HP system with Windows XP initially installed. I downloaded it as part of a dual Ubuntu/Xp boot. I partitioned my 160 gig hard drive at 50 percent of my total freed space. Everything seemed to work fine until I rebooted and it brought up an Error 21. Can someone please help me? I dont know what else to do or try. I am new to this stuff and I have no where else to turn. Any help or advice would be greatly appreciated. Thank you in advance.
 -Tim-

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> I installed Ubuntu on my HP system with Windows XP initially installed. I downloaded it as part of a dual Ubuntu/Xp boot. I partitioned my 160 gig hard drive at 50 percent of my total freed space. Everything seemed to work fine until I rebooted and it brought up an Error 21. Can someone please help me? I dont know what else to do or try. I am new to this stuff and I have no where else to turn. Any help or advice would be greatly appreciated. Thank you in advance.
 -Tim-
Grub error 21 is very unusual on a single hard drive dual boot...did you happen to have a USB flash drive inserted when you installed, then maybe removed it when your rebooted, or vice-versa?

---

### Post by bomb-24 on 2007-06-17
Yes I did. First I tried to run ubuntu strickly off of a 4 gig flash drive so I wouldnt disturb my xp setup in anyway and I could take it on the go. That is what I wanted and hope to accomplish at some point. When I installed it using the whole 4 gig flash drive, it did the same thing. but instead of the grub error 21, it gave me a grub error 5. I tried fixing it but again, I am new to all of this. So I went ahead and just installed ubuntu using a split harddrive and here is where I am getting my error 21. I dont know what to do. I cant even get into my xp setup. I am running off of the live cd. Anything would be greatly appreciated. I would pay somebody if they were here to show me. I dont know what else to do.

---

### Post by alienexplorers on 2007-06-17
Try inserting your install cd.
enter terminal and type sudo grub, which will put you in the grub editor.
enter
> find /boot/grub/stage1
you will get an output like (hd#,#)
type
> root (hd#,#)
type
> setup (hd#)
exit grub editor
reboot computer and see if this helps.

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> Yes I did. First I tried to run ubuntu strickly off of a 4 gig flash drive so I wouldnt disturb my xp setup in anyway and I could take it on the go. That is what I wanted and hope to accomplish at some point. When I installed it using the whole 4 gig flash drive, it did the same thing. but instead of the grub error 21, it gave me a grub error 5. I tried fixing it but again, I am new to all of this. So I went ahead and just installed ubuntu using a split harddrive and here is where I am getting my error 21. I dont know what to do. I cant even get into my xp setup. I am running off of the live cd. Anything would be greatly appreciated. I would pay somebody if they were here to show me. I dont know what else to do.
What I would suggest you trying is to remove your flash drive, boot up with the live cd, open a terminal(Applications---Accessories---Terminal), enter(copy & paste one line at a time, press "enter" after each line):
```
sudo grub
find /boot/grub/stage1
```
this should return  your root partition, e.g. "root (hd0,1)", you would then enter:
```
root (hd0,1)
setup (hd0)
quit
```

Then try to reboot without the live cd, if  you get a grub menu and Ubuntu still doesn't boot...try rebooting again, but in the grub menu, highlight your Ubuntu entry, press "e", and change root to (hd0,x), x meaning don't change what's there, (you may have to press "e" again to change), then press "b" to boot...this is temporary if it works and can easily be made permanent.

---

### Post by bomb-24 on 2007-06-17
ok, I typed sudo grub and it gave me this: 
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
then I typed find /boot/grub/stage1 and it gave me this:
Error 15: File Not Found
I looked in my boot folder in my partitioned drive and there are these files in there. I dont think the main grub is in there correctly.
/media/disk/boot/abi-2.6.20-15-generic
/media/disk/boot/config-2.6.20-15-generic
/media/disk/boot/initrd.img-2.6.20-15-generic.bak
/media/disk/boot/memtest86+.bin
/media/disk/boot/System.map-2.6.20-15-generic
/media/disk/boot/vmlinuz-2.6.20-15-generic
It was weird too when I installed ubuntu and it was installing and copying to my new partitioned drive because it went from 85 percent done to complete in a second. I knew it shouldnt have went that fast because that takes some time installing that. What can I do now? I have a copy of the grub program on my flash drive that I initially tried to use. But again when i initially installed ubuntu, I wanted it on the flash drive so I wasnt messing with my hard drive and it was giving me an error 5. In the end if I get this all fixed, I want to ultimately be able to boot and store all of my files and info and everything from ubuntu on the flash drive if I could. As of right now, I cant even get my xp running.

---

### Post by confused57 on 2007-06-17
What I would suggest is to reinstall Ubuntu with your flash drive removed...you can just reinstall on the same partitions you already have, just select to format the partitions(not your Window's partition, that's important)...you'd need to select "manual partitioning", on the larger ext3  partition(which is your root), select mountpoint as / , format as ext3...swap would be set as mountpoint swap...allow grub to be installed to (hd0).

Once you're able to boot into Ubuntu, then you can burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
this is an excellent utility to boot Windows or Ubuntu and it can restore the IPL of either

If you have access to another computer, you might want to burn a copy on it and try booting your Windows or Ubuntu before trying to reinstall Ubuntu.

Here's an excellent guide for installing with the live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Maybe someone else will have a better idea, if you want to wait & see.

---

### Post by bomb-24 on 2007-06-17
If I had to do that, once I got to the partitioning part, Can you explain a little better on what to do? Im sorry, I just dont understand some things. I know I have two roughly 80 gig drives now. I know which is which its just when I went into there, it is trying to partition them even more. like four 40 gig drives. and if I had to, how would you think I could get my windows back? I tried booting from the c drive but it keeps booting the ubuntu error. How would I delete all the ubuntu data, partitions and all to get back to the way it was before so I can start all over? Any idea? Im just stumped. Im going to wait and see if anyone can give me any further information but just so I can try to figure this out.

---

### Post by alienexplorers on 2007-06-17
You could put your windows disk in and boot to the restore section.  You could then do a fixmbr and fixboot.  That should give you back windows.

---

### Post by bomb-24 on 2007-06-17
what is swap? and when i partition it how big should it be in mbs?

---

### Post by bomb-24 on 2007-06-17
If anyone else has any information they can offer up, I would highly appreciate it. Anything at all.

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> what is swap? and when i partition it how big should it be in mbs?
Before you start installing, please post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

this will show your partitions & maybe someone can better guide you through the install

---

### Post by bomb-24 on 2007-06-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         751     5677528+   b  W95 FAT32
/dev/sda2             752       10559    74148480    7  HPFS/NTFS
/dev/sda3   *       10560       20473    74949840   83  Linux
/dev/sda4           20474       20673     1512000    5  Extended
/dev/sda5           20474       20673     1511968+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I ran a check on the cd. Its fine. I was just going to try installing it again. Unless there is someway i can import or fix the grub thats on there. If thats the problem

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         751     5677528+   b  W95 FAT32
/dev/sda2             752       10559    74148480    7  HPFS/NTFS
/dev/sda3   *       10560       20473    74949840   83  Linux
/dev/sda4           20474       20673     1512000    5  Extended
/dev/sda5           20474       20673     1511968+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I ran a check on the cd. Its fine. I was just going to try installing it again. Unless there is someway i can import or fix the grub thats on there. If thats the problem

Your root partition is /dev/sda3...what you would do is select this partition, set the mountpoint as /, format as ext3, make it a primary partition.
The swap partition is /dev/sda5...the mountpoint(select in the dropdown menu) is swap, select logical partition(or extended).

Did you get a grub prompt(grub>) when you entered "sudo grub" in the live cd terminal?  Then enter the "find /boot/grub/stage1" & the file was not found?  You might want to try this again just to make sure, before you reinstall Ubuntu.

---

### Post by bomb-24 on 2007-06-17
Yes. I got grub>. when I partition swap, it asks me to put in how many mega bites Im using for that. What should I put in for that? What is swap by the way? Im sorry, I am new at this. and Is this our only way of fixing this you think? Is there any way of getting grub to work without reinstalling?

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> Yes. I got grub>. when I partition swap, it asks me to put in how many mega bites Im using for that. What should I put in for that? What is swap by the way? Im sorry, I am new at this. and Is this our only way of fixing this you think? Is there any way of getting grub to work without reinstalling?

Swap is a partition on your hard drive that is used as temporary memory, if your ram memory becomes full...Windows does the same thing, but doesn't require a separate partition.

Your current swap partition is approx. 1.5 Gb, you should be able to just click on your current swap partition and not have to specify a size, it should use the same partition size for the new swap...
> /dev/sda5 20474 20673 1,511,968+ 82 Linux swap / Solaris
I put the commas in so you can see the size of your current swap in Kb's.

---

### Post by bomb-24 on 2007-06-17
Reinstalled Ubuntu. Applied partition settings as you told me to. Dual booting working great! Thank  you very much. Problem Fixed.

---

### Post by confused57 on 2007-06-17
> **bomb-24 said:**
> Reinstalled Ubuntu. Applied partition settings as you told me to. Dual booting working great! Thank  you very much. Problem Fixed.
Good job getting your dual boot working...always great to hear good news.

If you haven't already, it would still probably be a good idea to make a copy of the Super Grub Disk...it might come in handy, if you have trouble booting.

---

