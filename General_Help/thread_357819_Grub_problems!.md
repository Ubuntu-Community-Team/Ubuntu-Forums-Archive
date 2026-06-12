---
title: "Grub problems!"
date: 2007-02-10
forum: General Help
---

### Post by hempa on 2007-02-10
Hi i hope that somebody out there will take pity on me.I think i have put myself in a big mess here i will start from the beginning.i have used windows all my life and now little to nothing about linux/ubuntu. recently i tried an ubuntu live cd and a liked it a lot better than windows so i wanted to give it a try. first i tried to partition my hard drive, actually theres two (maxtor, 150 gig each) i used partition magic but it would not partition my hard drives, it said something about that there were some partitions that could not be moved or deleted.So instead i put in the live cd with ubuntu .6.06 wich always works great but i have to start it in safe graphics mode otherwise i get a message that i have to change some settings that i dont know how to change.Anyways when the cd was running i chose the install option and everything worked out allright. when it came to the partition options i choosed one of the hard drives for ubuntu. when i restarted my computer without the live cd i came to the point where it said loading grub and then i got an error 21 message now i dont remember if the error message came while loading grub or grub .1.5 so i found a thread about how to restorel grub from a live cd 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

there is two parts in the thread the first part is about grub being installed in the mbr so i followed the instructions and everything worked i restarted the computer again without the live cd. this time i did not get the error message while grub was loading but it just said  loading grub and it stopped there nothing happened. So i put in the live cd again and installed ubuntu on my second hard drive restarted the computer but the same thing happend again it just said loading grub and it would not go on from there. so i tried the other part of the thread that is about getting chrooted to yor drive as root and then start working with grub.first everything was ok i chrooted in as root, and then after that the first command that you are supposed to write is sudo grub. but when i wrote that i got an error message, i have copied it from the terminal it loks like this.

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo grub
sudo: unable to lookup ubuntu via gethostbyname()

Please help me with this.

This is another thing that might explain something. I have a dell Dimension 8400 and i think the reason that i could not partition my hard drives with parttition magic is because dell had some crap there that could not be deleted or moved. and when i click on the examples folder on the desktop while using the ubuntu live cd and then on the computer icon inside i can se my drives CD ROM/DVD ROM    CD-RW/DVD Drive   143.2 gig Volume   Filesystem. and then there is Dell utility device how did that get there!

So i think that i now have ubuntu on both my hard drives but i cant acces any of them because of the grub problem when i start ny computer.

another thing when i check my hard drives in bios it says device not present next to both of them.
if anybody could help me with this and maybe explain what i have done and how i can fix it  it would be great. i have no problems whatsoever to erase everything that has to do with dell or windows 
All help is very wlcome.

---

### Post by waster on 2007-02-10
The problem with grub is probably that it is not indicating correctly that the ubuntu installation is on the second hard drive.
What is in your  /boot/grub/menu.lst ?
Try using grub interactive session to confirm that the correct partitions are used. This is tricky but definitive. Alternatively, perhaps you could install grub on the second drive, and tell you computer via BIOS to boot that drive.


what does

cat /etc/hostname

give you?

---

### Post by hempa on 2007-02-10
Hello my friend thanks for helping me out. I tried to type /boot/grub/menu.lst but then it just says permission denied. when i type cat /etc/hostname
 i get armcandy-desktop wich is the name that i chose during the installation. 
another qustion should not grub detect ubuntu since i have installed it on both my hard drives.
and about grub interactive session i would gladly try it but since i am a complete newbie i need some help with it what commands to use and so on.
thanks again for the help.

---

