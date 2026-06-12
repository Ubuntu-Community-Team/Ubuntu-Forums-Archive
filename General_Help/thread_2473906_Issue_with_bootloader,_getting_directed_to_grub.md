---
title: "Issue with bootloader, getting directed to grub"
date: 2022-04-18
forum: General Help
---

### Post by 78chip5 on 2022-04-18
I made a reddit post of my issue, but on the guide to boot repair it said to go here, so I'll just link and paste my post on reddit.

[https://www.reddit.com/r/linux4noobs/comments/u67ad1/have_i_****ed_everything_up_explanation_in/](https://www.reddit.com/r/linux4noobs/comments/u67ad1/have_i_****ed_everything_up_explanation_in/)

"I'm new to Ubuntu, switched from Windows 10 a couple months ago now. Well today for various reasons, I decided I wanted to dual boot Windows and Ubuntu, so I went ahead and installed Windows again. Just now I tried booting Ubuntu and got this screen. I've done some googling, but can't figure out where to go from here.
I'm not very computer wise, but I do have a small idea of where I could've messed up. When I was installing Windows, I deleted a partition in order to make a new one that was formatted properly, but it was only about 500 mb so I don't know what could've been on there that was so important.
My biggest concern is of course my data. For some incredibly stupid reason, I deleted the backup that I made after transferring over from Windows, and of course I have literally everything important you can think of stored on my computer. Rest assured, I will be making a new backup if this all works out."

Per the advice on reddit, I installed boot-repair (I still had my live USB from when I installed Ubuntu) and followed the directions to make a pastebin, which is here: [https://paste.ubuntu.com/p/rBDTKkPMy4/](https://paste.ubuntu.com/p/rBDTKkPMy4/). Can anyone tell me where to go from here? Many thanks.

---

### Post by oldfred on 2022-04-18
Did you erase your Linux install?
In one place in report you show p2 as ext4, but the other shows it as the Microsoft reserved.
The Microsoft reserved must be unformatted & before the first NTFS partition. It cannot be ext4.
It looks like Microsoft also converted p2 to 16M, typically size of Reserved partition, but kept the UUID of your Linux ext4 partition.

You also show UEFI Secure Boot on.

Since Microsoft with NTFS writes to the beginning of the partition first and Linux randomly writes into the ext4 partition, you may have some data on the drive, if the ext4 was entire drive. But difficult to recover. You can try photorec. I used Photorec & it took overnight to scan a smaller drive and copy data to another drive. Then it took me weeks to recover files as it also recovered all the deleted versions. So I had multiple copies of most files & had to compare to an old backup and each file. It only recovers files by extension or the file type, not full name. 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by 78chip5 on 2022-04-19
Yeah, I'm still not sure what I did, but thank you. Photorec is working like a charm, and I've been able to recover a lot of my most important data so far. I'll just do a fresh install after.

---

