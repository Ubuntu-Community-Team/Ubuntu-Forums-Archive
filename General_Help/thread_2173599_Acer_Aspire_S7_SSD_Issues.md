---
title: "Acer Aspire S7 SSD Issues"
date: 2013-09-10
forum: General Help
---

### Post by roger8 on 2013-09-10
Hello Ubuntu Community

I'm the proud owner of a Acer Aspire S7 , during installation there were several problems with the SSD Drive.
After searching the web i found out that the problem was probably the Raid configuration.

After de-connecting the software raid , i was able to intall ubuntu 12.04 (not 13) to my netbook.

Disk analysis shows us that i have a Main volume /
and a Home Folder /home/username

both these partitions shows each a capicity of 58.7GB


i can't my other ssd which should also be possible to mount as sdb ?
is that right ? if yes how 


Thanks in advance 
Greetings Roger

---

### Post by varunendra on 2013-09-11
Hello Roger, Welcome to the forums ! :)

It seems there is a typo in your post which is making your problem as well as the question a bit unclear -
> **roger8 said:**
> **i can't my other ssd** which should also be possible to mount as sdb ?
is that right ? if yes how 
Do you have 2 SSDs in the laptop?

Please try to rephrase your question, providing more details if possible. Output of the following command may help -
```
sudo fdisk -l
sudo parted -l
```
*(please use 'Code' tags to post the above outputs. Follow the "Using Code Tags" link in my signature to see how)*

Hopefully, whatever you need be done with the drive(s?) should be quite simple to explain/achieve.

---

### Post by oldfred on 2013-09-11
Also is this an Ultrabook or do you have Intel SRT?

        Ubuntu now installs with Intel SRT on, but when grub sees the RAID grub will not install. So you have to turn the SRT off and remove the RAID meta data from the drives. Some install Ubuntu to SSD, others install to hard drive and turn SRT back on and have had it work.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)

---

