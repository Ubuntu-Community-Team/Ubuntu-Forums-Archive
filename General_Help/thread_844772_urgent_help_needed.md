---
title: "urgent help needed"
date: 2008-06-29
forum: General Help
---

### Post by eternalnewbee on 2008-06-29
****I think I messed up big time!
I've been using Ubuntu for over 2 years and have no complaints.
the problem is, I convinced a teacher to try it too. I installed Hardy Heron on a partition and kept xp on the other. So far so good. A week later the teacher complained that she couldn't use Ubuntu and urged me to remove Ubuntu. Newbee that I am I used Partlogic boot cd to erase Ubuntu. After having committed the changes I rebooted, only to get a Grub 22 error. I started up the boot cd and formatted the former Ubuntu partition into fat (no ntfs option) and after rebooting I got a Grub 17 error. And then... feeling desperate, started up the Partlogic boot cd and accidentally deleted the xp partition and couldn't undo the changes. My HUGE question is, is it still possible to save the xp partition? or has it permanently been deleted.
Please help me (desperate and ashamed I am)
PS. One of the main reasons for the teacher not wanting to use Ubuntu is because Open Office lacks certain fonts that are widely used, here in Thailand, namely Angsana UPC fonts
Thanks...:***********[I][B][COLOR="Navy"][COLOR="Navy"][/COLOR][/COLOR]***[/I][/B]

---

### Post by rossjman1 on 2008-06-29
If you have an XP boot disk, there is a switch you can use in the fdisk program that will fix it for you. The reason you're getting these errors, is when you deleted the Ubuntu partition, you (unknowingly) deleted all the grub bootloader files.

---

### Post by kuja on 2008-06-29
If there's any software that can help you, it's testdisk.

---

### Post by eternalnewbee on 2008-06-29
Thanks for your help. Will try

---

### Post by eternalnewbee on 2008-06-29
Thank You. Will try that too.

---

### Post by rossjman1 on 2008-06-29
If you dont have an XP boot disk, you can get the ultimate boot cd, and install a new bootloader (which doesn't have to show up when you boot the computer).

---

### Post by eternalnewbee on 2008-06-29
OK. I downloaded testdisk. What should I do next?

---

### Post by kuja on 2008-06-29
Pull up a terminal, maximize it, type testdisk followed by the drive name (ie: testdisk /dev/sda) and press enter. Then follow the instructions and run a scan and see what it finds.

---

### Post by eternalnewbee on 2008-06-29
I'm really sorry Kuja, but I'm communicating with you from my Ubuntu computer. The computer in question is at another location and Unbootable; Nothing to boot: Ubuntu was already deleted and xp (accidentally) next, so I need to (or at least I think I do) boot from from a cd other than Partlogic to recover the lost xp partition. I thought testdisk would be a bootable cd...
By the way, I'm downloading *Ultimate Boot CD v4.1.1 ISO*, (following Rossjman's suggestion..). 
Do you think or know if that would be of any help?..

---

### Post by kuja on 2008-06-29
Testdisk ~should~ be on the ubuntu live cd.

---

### Post by VMC on 2008-06-30
> **eternalnewbee said:**
> I'm really sorry Kuja, but I'm communicating with you from my Ubuntu computer. The computer in question is at another location and Unbootable; Nothing to boot: Ubuntu was already deleted and xp (accidentally) next, so I need to (or at least I think I do) boot from from a cd other than Partlogic to recover the lost xp partition. I thought testdisk would be a bootable cd...
By the way, I'm downloading *Ultimate Boot CD v4.1.1 ISO*, (following Rossjman's suggestion..). 
Do you think or know if that would be of any help?..

It's been awhile since I use UBCD, but if it has dos tools, you could froma DOS prompt type > 'fdisk /mbr'

It's that simple. That's DOS's fdisk, not to be confused with Linux.

---

### Post by jrz on 2008-06-30
Hi, Nothing new to add but noticed you said you are in Thailand, and I also am in Thailand and am trying to get the schools in my area to give Ubuntu a try. The main reason is I am tired of removing viruses from memory sticks and floppy disks, but I also feel that Linux promotes more learning and less gaming. Do you know of any other complaints about Ubuntu that might also need addressing? I'm in the North, Chiang Saen District. Thanks, and I hope you are able to resolve your problem satisfactorily. I had a similar problem before when I was dual booting CentOS and WinXP, but can't remember exactly how I resolved it. Not certain, but I believe I had to edit the boot.ini file on the C: drive to show WinXP as the default system to boot.

---

### Post by eternalnewbee on 2008-06-30
Then I should download the Ubuntu live cd...

---

### Post by kuja on 2008-06-30
No worry, I checked afterwards, after I read more of what you said. I do believe ultimatebootcd has testdisk also :)

---

### Post by eternalnewbee on 2008-06-30
Most obliged Kuja. I'm at 40% of downloading ultimatebootcd, so that'll save me some time.

---

### Post by eternalnewbee on 2008-06-30
Well jrz, the main obstacles be unfamiliarity, being used to using windows, and in particular not being able to use Angsana UPC, Angsana new, Cordia UPC, and Cordia new fonts, as most Thai people I know use them in microsoft office...
Nice to meet you by the way. Ayutthaya is my place to be.
PS. I agree with you on what you said about less gaming and more learning, but since being a bit of a gamer myself, developing games for Linux might just be what hesitaters have been waiting for. For example, my private students love playing Supertux and the younger ones love Tux paint, which is quite educational itself.
sawad dee kap

---

### Post by eternalnewbee on 2008-06-30
After having played around with ultimatebootcd for a while, I found the deleted xp partition, was at a loss as to how undelete it...
I've given up. The teacher is taking the computer to a technician. I hope he/she can sort out things...
Thanks for your help anyways... may the Ubuntu force grow stronger and be with with all of us

---

### Post by jrz on 2008-06-30
I wish you had sought some help before removing ubuntu as I believe it is possible to install the desired fonts from Windows into ubuntu. I'll give that a try on my system when I can get time as I really would like to see the schools here move to ubuntu or some version of linux if possible. I hope the problem is easily corrected and hope you might get them to give ubuntu another try at a later date.

---

### Post by kuja on 2008-06-30
> **eternalnewbee said:**
> After having played around with ultimatebootcd for a while, I found the deleted xp partition, was at a loss as to how undelete it...
I've given up. The teacher is taking the computer to a technician. I hope he/she can sort out things...
Thanks for your help anyways... may the Ubuntu force grow stronger and be with with all of us

Well, I do believe after that scan, you can have testdisk "restore the partition table" or something similar to that. Lets see if I can find a good howto, just in case it's not too late already ... this [http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_a_Lost_Partition_With_may](http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_a_Lost_Partition_With_may) be

---

