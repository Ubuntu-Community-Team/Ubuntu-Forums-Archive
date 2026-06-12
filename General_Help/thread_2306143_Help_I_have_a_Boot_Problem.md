---
title: "Help I have a Boot Problem"
date: 2015-12-12
forum: General Help
---

### Post by jackyhughes on 2015-12-12
I realise there are numerous threads and even things on youtube but none of it is helping. Earlier today my laptop threw a fit and refused to reboot. I tried to boot up pressing "shift" and that gets me as far as "grub rescue'" The more I have read, the more confused I become about what I could type after that.

If I go to F2 I am asked for a password and cannot remember it and also this will not work if it has a p in it until I can borrow a keyboard as the p ke y and the y have stopped working.

I also tried a disk installation as I still have my old Ubuntu 12.04 disk. That is the only reason I am typing this now. I tried the different bits of code to repair or reinstall "grub" but they won't work.

I also cannot find the partitions on the hard disk so I cannot even reinstall Ubuntu because too much space is already used. When I finally thought I was getting there I seem to be locked out of my own system.

I would like to get back in to get the stuff I hadn't backed up when the cloud I use got full.......How do I solve any of this an Acer Asire 6930g?

I am sure I have used a combination of keys other than shift to get into the boot menu before but F10 seems to be stuck so I cannot change the boot order.

I do not have Windows on the machine.

I am sure someone will want me to be more technical but I have been trying stuff all day to get the ability to boot the system back and now my head hurts and I am not sure what I have not done?

All ideas welcome. I am not technical so please if you give me code to copy and paste I would be grateful. I know it is usually something that can be sorted in a terminal but am not sure why all the usual fixes are not working for me.

Sorry to sound muddled but my head is aching with it all....

---

### Post by grahammechanical on 2015-12-12
You can start by

a) describing the hardware specification of the machine and include information about the graphic adapter
b) inform us what version of Ubuntu you have installed
c) describe what happens when you power up the machine. What do you see? What messages do you see. "Refused to boot" does not provide any information that can be used to even guess the problem.
d) run the live session & load Gparted and then take a screenshot of the partitions and post it in this thread. Or write the information down and then type it in this thread.
e) use the live session to backup any data that you do not want to lose. How you do that we cannot say as you have not told us anything that can help us to help you.

We need to see the partition layout. It may be possible for you to create another Ext4 partition and transfer your data on to that and then simply re-install using the Something Else option.

f) learn about primary, extended & logical partitions
g) become familiar with the instructions on how to partition.
h) get a good night's sleep and tomorrow re-install by using the Erase disk and install Ubuntu option and kiss good-by to that data.

[URL="https://help.ubuntu.com/community/HowtoPartition"]https://help.ubuntu.com/community/HowtoPartition

[/URL]And that is the limit of the help that I can give.

Regards

---

### Post by howefield on 2015-12-13
Hello jackyhughes, your post has been removed due to the large quantity of base64 code in your posting, please repost using the paperclip icon to attach your images rather than dragging an image into your posting window to avoid this "bug".

---

### Post by jackyhughes on 2015-12-13
Thanks I am more awake now. Gparted and removing everything solved the problem. I lost some data  but at least I am back to 14.04 on a reinstall. Thank you for pointing me in the right direction,

Oh I am so sorry. I though I had removed it and then got distracted solving my problem and could not access the Internet. I have thanks to the person above solved the problem by using gparted and reinstalling. Thank you so much,

---

