---
title: "Moving partitions in multi-boot laptop..."
date: 2015-12-03
forum: General Help
---

### Post by andrew.t.sullivan on 2015-12-03
Hello

I have a Lenovo G505s which has the following OS installed: Windows 10, Linux Mint 17.2 and Ubuntu 15.10;  I have attached a screenshot from gParted to show the way things are currently organised on the hard drive.

I would like to move the three ntfs partitions (sda10, sda11 and sda12) to(wards) the end of the disk so that I have more flexibility in resizing the Linux partitions - in particular, sda9 is getting a bit full. I also might want to move some of the Linux /home partitions.

I realise that I could have avoided some of these problems by thinking about things more when I started installing Linux (although in my defence, I have replaced the 1TB drive that the laptop came with with a 2TB drive...), but my question is - am I likely to render the laptop un-bootable by doing any of what I have described?

TIA

Andrew

---

### Post by yancek on 2015-12-03
The problem with moving the ntfs partitions is the fact that you have two Linux partitions sda13 and sda14 between them and the unallocated space which means if you want to move the three windows partitions, you would either need to first unmount all the partitions you are dealing with using GParted on either a Live CD or an OS that has it on a bootable medium.  You could also create new partitions or just a singel ntfs and copy data there.  I don't know what you have on them or if you want them separate.

---

### Post by grahammechanical on 2015-12-03
I have seen it written many times by those who know what they are talking about,

1) defrag Windows partitions more than once and restart Windows each time.
2) Use Windows utilities to resize/move Windows partitions.
3) Use Linux utilities to resize/move Linux partitions.

Moving and resizing partitions can take a bit of time especially if we have put several actions in to a queue. So, I like to do one action at a time and when it is finished to restart just to be certain nothing has broken.

So, when you have moved the Ubuntu Gnome partitions (sda13 & sda14) into unallocated space you can restart Ubuntu Gnome and if it is broken you should still have a working Linux Mint and a working Windows. The next three partitions (Windows sda10, sda11, sda12) are small and do not seem crucial to the Windows OS. Once they are moved there should be unallocated space behind the Linux Mint home partition (sda9) that sda9 can be expanded into.

I do not see a need to do anything to the Windows 8 OS partition. But as I said, do each action one at a time and test to see if each OS loads before moving on to the next action. And you do have space to create partitions to backup any data to.

Regards.

---

