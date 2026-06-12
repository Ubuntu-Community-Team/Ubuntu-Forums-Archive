---
title: "[SOLVED] Ubuntu failing to start"
date: 2008-02-14
forum: General Help
---

### Post by nzcyclone on 2008-02-14
Hiya all,

Ubuntu was working fine and really good. On a restart I now get the following error screen. Am hoping someone can decipher what this all means and also a solution on how to fix it :)

This happens once the Ubuntu startup screen appears the bar that shows progress starts and then goes to this message

=====Error Screen Message======
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   223.561967] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[   223.562010] ata3.00: cmd c8/00:01:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in


[223.734501] Buffer I/O error on device sda, Logical Block 0
also Logical blocks 1,2,3,4,5,6 and 7

and it keeps trying the numbers in [ ] change but the message itself doesn't.
=======================

Many thanks to anyone who knows what this all means :)
Greg

---

### Post by dcstar on 2008-02-14
> **nzcyclone said:**
> Hiya all,

Ubuntu was working fine and really good. On a restart I now get the following error screen. Am hoping someone can decipher what this all means and also a solution on how to fix it :)

This happens once the Ubuntu startup screen appears the bar that shows progress starts and then goes to this message

=====Error Screen Message======
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   223.561967] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[   223.562010] ata3.00: cmd c8/00:01:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 3584 in


[223.734501] Buffer I/O error on device sda, Logical Block 0
also Logical blocks 1,2,3,4,5,6 and 7

and it keeps trying the numbers in [ ] change but the message itself doesn't.
=======================

Many thanks to anyone who knows what this all means :)
Greg

It looks like your hard disk has bad blocks on it - you should find a downloadable Utilities boot CD and try and diagnose your disk.

---

### Post by nzcyclone on 2008-02-14
Hiya dcstar,

thanks, I had a feeling someone was going to say that is a  hard drive problem and it isnt an old hard drive either (less than 6 months)

I have gparted on a bootable cd would that do what I would need or do I need to find and use something else?

Many thanks :)

---

### Post by nzcyclone on 2008-02-14
although.. . . if is bad blocks is it usual for them suddenly to fail like that as a whole section so to speak and at once?, As said Ubuntu was working perfectly until rebooted it (had just done some updates to Ubuntu and firefox) it was only on reboot that everything turned to custard and went into the downward spiral.

---

### Post by Artificial on 2008-02-15
I have the same problem, but with Debian. Everything was working fine, than i updated it and it updated kernel too, so i had to reboot. After reboot i get grub error 25 at stage 1.5.
When i try to mount the partition from a live CD (ubuntu or debian setup CD) i get that error, but there are no bad sectors on disk.  I checked it with badblocks command.
When i try to mount the partition o get only logical block 2 buffer I/O error, but when i test with badblocks i get the buffer I/O error for blocks from 2 to 15. And report of 0 bad blocks found.

---

### Post by nzcyclone on 2008-02-18
Hiya all,

Just thought would try something so have put the Installation CD in for Ubuntu and it gets to its main screen, I then mount the hard drive which it sees and all my files etc etc when go into disk properties > Basic it then tells me the following;

119487 items totalling 2.3GB
(some contents unreadable)

Ok I know have a hard drive fault and normally would just reformat and start again trouble is there is e-mails on this computer which do not if can avoid it want to loose.

Could someone please point me in the direction of a hard disk utility program which is good.

Or I guess will just have to reinstall but if do that there isnt a way to stop it overwriting and reformating is there? doesnt it do that by default reformat the hard drive? or have I got that wrong?

Many thanks everyone

Ok have reinstalled and everything is working fine and dandy long may it stay like that :)

---

