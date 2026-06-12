---
title: "Dual boot but common folder"
date: 2018-11-04
forum: General Help
---

### Post by debanandasagar on 2018-11-04
Hi All,

I am new to linux/ubuntu

Below is the scenario and question I have.

I have got a new laptop, in that I have 256 GB SSD and 1TB HDD. What I want is, to install windows and ubuntu on SSD and store all the files on HDD(I should be able to access Windows files to ubuntu and vice versa).

My question may sound like a dumbo but as I am new to this and having no knowledge on ubuntu. Please guide me how to do this. The little I know is to install Windows and Ubuntu on SSD(again some one was saying if config files are stored in ssd for ubuntu the performance for installation files may be little faster).


Please help me out on this. Instead of sharing the other discussion links. Let me know the steps and copy&Paste the right answer.


Thanks in advance.

---

### Post by howefield on 2018-11-04
Thread moved to the "*General Help*" forum.

---

### Post by yancek on 2018-11-04
If you mean access data folders/files from Ubuntu and Linux on a separate data partition, yes you can do that.  Since a default windows system cannot read/write to a partition with a Linux filesystem, you will need to format the data partition ntfs so it can be read/written to from both windows/Ubuntu.  YOu should definitely not "write" to a windows system partition from a Linux system or vice versa but a data partition should be no problem.

You neglected to mention which version of windows you are using and that is significant since microsoft has been selling/licensing operating systems for over 30 years!  It is particularly important if you are using a more recent version of windows */10) as there have been major changes with UEFI/GPT.  If that is the case, you need to read the Ubuntu documentation at the site linked below.  There is no point in repeating everything for everyone who posts when the details are readily available.  Good luck.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

