---
title: "How to add unallocated partition to ubuntu?"
date: 2013-04-21
forum: General Help
---

### Post by paradoxcy on 2013-04-21
Hi all.

I know that this particular question has been done to death. But I am not able to add the free space on the hard drive by deleting Peppermint OS to Ubuntu.

I have tried booting ubuntu from live USB and opening Gparted but still I am not able to figure out how to get rid of the unallocated free space and add it to Ubuntu.

On right clicking I see no options for the unallocated hard drive. I am sure I am missing something here a simple instruction perhaps?

And also I am not sure what is linux swap. Has that got something to do with this.

I have attached two screenshots. One is a screenshot of gparted as to what I want to accomplish. Second screenshot is the one where I right click the unallocated drive and click new. In this screenshot I have selected the file system as 'ext 4'  (which is the file system on which ubuntu is installed). I HAVE NOT IMPLEMENTED THIS, The screenshot is just so that you can advise whether this solution will work or not.

Any help is appreciated.

Regards,
Debayan

---

### Post by dabl on 2013-04-21
You can't "add" it -- disk partitions don't work that way.  Probably the fastest and easiest thing to do is this sequence:

1. Highlight /dev/sda2, and choose "Move/Resize", and slide (move) that partition as far as it will go to the right.  This will open the same amount of space between /dev/sda1 and /dev/sda2.

2. Now highlight /dev/sda1 and choose "Move/Resize" and grab the right edge of it, and stretch it to the right all the to the edge of /dev/sda2.

3. Now click the green "Apply" button, observe the warning, and "OK" and it will expand /dev/sda1 to fill the space available.  This will take some time -- be patient, go find something else to do, and DO NOT interrupt the process in any way, or your system will be damaged beyond recovery.

---

### Post by oldfred on 2013-04-21
You can have 4 primary partitions and one primary can be the extended partition. The extended partition can have many logical partitions.
You have two primary sda1 and the extended sda2. You have unallocated in the extended and swap in the extended. So if you want to add to sda1 you first have to move it out of sda2 or shrink extended partition and make unallocated into the space between sda1 & sda2.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Swap space is when you are running active programs that fill more than the amount of RAM you have. Generally when system uses swap you will see it slow or turn grey for a second or two as swap is slow compared to RAM. If you have 4GB or more of RAM you may never use swap.

 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Before you move your unallocated, you may want to think about a separate /home or data partition. System is slightly more efficient if all the system files that are accessed the most are closer together on drive. I generally suggest 25GB for / (root) and then the rest of the space you want for Ubuntu as /home. Or a bit more advanced, just make the space a data partition and mount and use it for storage of your files.
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by clearski on 2013-04-21
> **oldfred said:**
> 

Swap space is when you are running active programs that fill more than the amount of RAM you have. Generally when system uses swap you will see it slow or turn grey for a second or two as swap is slow compared to RAM. If you have 4GB or more of RAM you may never use swap.

I thinks that's a great piece of news to me. I have 4 GB of RAM, but I also created a 5 GB swap partition during installation. I know that I was way too generous. :) 

One of the things I read that could be done to increase the usage of RAM instead of swap usage is to reduce the swappiness to 10, which instructs the kernel to use more RAM and less disk swap. However, if I want to completely disable the swap partition and only use my RAM (I think of adding an extra 4GB to make it 8) is it enough to put the **#** sign before the UUID of te swap partition in /etc/fstab?  Or all I should do is to follow the *Empty swap guide* from [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) and let the 5GB partition as is? Or are they complementary?

---

### Post by ajgreeny on 2013-04-21
An added problem you will need to be aware of is that while running a live system, CD or USB, any swap partition will be found automatically and used by that live system.  In your case that means that the whole of the extended partition sda2 will be out of action until you set "swapoff" by right clicking on the swap partition, sda5, in gparted.  You may also need to right click on the extended partition itself, sda2, and choose "unmount".

---

### Post by oldfred on 2013-04-21
The system is smart enough to not use swap unless needed. But it will fill RAM because it knows we often reuse commands and it then has cached recent activity in RAM, but if an active program needs the space then it releases the older info. Only if all RAM is used by active programs is then swap needed.

       Memory use including swap, RAM may be full but that does not mean you are using all of it.
free -m
Memory use explained
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

I would always suggest some swap like 2GB, just in case a runaway task uses all RAM. And supposed it boots slightly faster if swap found. It has to search for swap and find there is none and you save the search.

---

### Post by paradoxcy on 2013-04-21
Hi all.

I faced the same problem as ajgreeny said.

And I being a Ubuntu Virgin did not know about swap-off and all that.

So instead of using UBUNTU live USB, I used G-PARTED live USB and then there is no need to swap-off nor unmount. And then I proceeded with the solution outlined in the first reply by dabl.

And old fred when I get a bit more experience with linux then I will try your solution. It seems a little complex and a little time consuming.

Thanks for your replies guys. I am marking the thread as solved.

---

