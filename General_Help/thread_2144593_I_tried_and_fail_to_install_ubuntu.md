---
title: "I tried and fail to install ubuntu"
date: 2013-05-12
forum: General Help
---

### Post by Kojak Peg on 2013-05-12
Hi Everyone
I'm running a dual boot with windows xp and zorin. And want to install ubuntu over zorin. I thought I'd have to unistall zorin and use easybcd to remove the linux boot screen thing. However was told I could just install straight over zorin. So I put the ubuntu cd in my dvdrom. Restarted the computer pressed F12 and got the boot screen. Where it gave me options:

*boot for hard drive
*boot from dvdrom

*setting
*can't remember
*Intel something or other

So I chose the dvdrom, and heard it whirring away for awhile, but nothing happened. In the end, I had to take the cd out of the drive and turn the power off. Fully expecting big trouble when I switch the computer back on. Thankfully all seems well, but what did I do wrong

How am I supposed to properly install ubuntu over zorin

Thanks

---

### Post by ibjsb4 on 2013-05-12
I just turn the Zorin partition into free space and then install Ubuntu.  You could do this with the live CD, it has gparted built into it.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

You box probably will not boot until Ubuntu is installed, so make sure you understand the install procedure.

---

### Post by Kojak Peg on 2013-05-12
Hi ibjsb4
I downloaded ubuntu and burnt it to a new dvd just in case, it was my copy that was bad. And it worked. However, when I clicked install it said I wasn't connected to the internet. Which I should have been, wirelessly at least. So I chickened out, just in case there was something wrong. Clicked back and clicked try ubuntu instead. 

As for turning zorin into free space, I've only ever deleted a partition during a full format. So I'm a little hesitant to do it. If I did delete the partition, without a full format, I think I would have to do it in windows. And as I understand it, that would still leave the boot loader on. I've seen tutorials for easybcd that look start forward enough, but I was told in another thread that easybcd doesn't work in windows xp, which is what I'm using. 

So Install ubuntu over zorin, would be me preferred choice, if it was possible. If not I would have to go into disk manager, in windows, delete the partition and then delete the grub. However, without easybcd I have no idea how to do that

So what is the best and easiest option,

Thanks 


Thanks

---

### Post by ibjsb4 on 2013-05-12
> when I clicked install it said I wasn't connected to the internet.

You can install without the internet, but after you will probably need to install the proper driver to get internet working.

> If I did delete the partition, without a full format, I think I would have to do it in windows. And as I understand it, that would still leave the boot loader on.

Thats fine, whatever you understand is best way to go.  The boot loader will (should) be replaced with ubuntu boot loader (known as grub), so no worry there.

> So Install ubuntu over zorin, would be me preferred choice

Try it.  If you get the option to install over zorin then that will just make the process easier.  If you do no, then just back out of the install and go to plan 'B'.  Just remember, once zorin is removed by wiping the partition your box will not boot until ubuntu is installed and ubuntu boot loader (grub) takes over.

And my last thought is have a windows restore disk handy just in case everything goes south.

---

### Post by oldfred on 2013-05-12
If you are going to install over an existing partition, you have to use Something else or manual install.

Then choose the partition that is the current Zorin install. Click change, use as ext4, check format (erases everything in Zorin, so have your data backed up), and choose mount as / (root). if you have an existing /home you can mount it but DO NOT format it and if you have an existing swap it finds that. Let it install grub to the default of sda which is shown in a combo box at the bottom of the partitioning screen.

---

### Post by Kojak Peg on 2013-05-13
Thanks Guys

Hi Oldfred 
So during install I should

1)choose "something else" or "manual install" option
2)choose the partition I want to write over i.e zorin
3)click change => use as ext4
4)click format
5)choose mount as /(root). _*However, swap is not found?*_
6)*_click format?_*
7)_*How do I find swap?*_
8)let it install grub to default sda
9)_*install complete?*_

Now I lost you on the next bit here
> [COLOR=#000000]if you have an existing /home you can mount it but DO NOT format it and if you have an existing swap it finds that[/COLOR]

This is how I read it please correct me

alternative 4) do not format
alternative 5)choose mount as /(home) =>swap is found. Do not format go straight to step 6
alternative 6)install grub to default sda
alternative 7)[U][I]install complete? 
[/I][/U]
2nd alternative 4)click format
2nd alternative 5)choose mount as /(home)=>swap is found. Do not format go straight to step 6
2nd alternative 6)install grub to default sda
2nd alternative 7)_install complete?_

Thanks

---

### Post by oldfred on 2013-05-13
I assumed you had swap with your current install. If not you should create one. If you have a fair amount of RAM or 4GB or more you do not need much, maybe 2GB. But if you hibernate then it needs to be the same as RAM in GiB not GB.
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)



Many installs have a separate /home. That is to make it easier to reinstall as then your user settings & data are in a separate partition that you do not overwrite, but reuse. Backups still required.

Install process has not really changed, graphics are even only slightly different between versions.
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by Kojak Peg on 2013-05-13
Thanks oldfred
The softpedia link is very helpful, because it's laid out, so even I can understand it, lol. I think I'll read over it, a few time, just to be sure. And since I'm a novice to intermediate. I'll definitely back my files up just in case. I am assuming that if everything goes pearshaped, I can simply reboot and do a full install. And everything will be okay 

once I'm finally ready to take the plunge. I'll start a new thread, just so I'm absolutely clear on what to do. I'm sure it'll turnout to all make perfect sense, once I've done it. At least I hope it will, lol
 
Thanks again

p.s since I'm dual booting already windows xp =/dev/sda (ext4) and linux= /dev/sdb (ext4) and I'm assuming the swap =/dev/adc (linux-swap) if I have one.
 
or is it windows xp=/dev/sda1 (ext4) linux=/dev/sad2 (ext4) swap=dev/sad3 (linux swap)

---

### Post by oldfred on 2013-05-13
Windows has to be NTFS formatted, unless you have a really old XP that might be FAT32. 
Ubuntu requires Linux formatted partitions and ext4 is the current standard.
You only have to have / (root) as ext4 & swap. But we often suggest separate /home.
We also often suggest another NTFS shared data partition. The Linux NTFS driver reads & writes NTFS, but Windows often does not like too much activity in its system partition. Also the NTFS driver exposes all the normally hidden files & folders in Windows which can lead to user error. In Windows I would always change it to see those hidden files & folders and then learned how to repair it after I broke it. :)

---

### Post by Kojak Peg on 2013-05-13
I've taken a look at it with Gparted and it makes a lot more sense now that I'd had a look at it.

My hard drive is split into three. the primary is /dev/sda1, which is the ntfs system file. Then there is the extended partition with the /dev/sda5 ext4 and the /dev/sda6 linux-swap in it 

So I need to format the /dev/sda5 ext4 and install the new OS in that partition, but do I need to format the swap system file as well, or do I leave that alone

As for the /home partition now I know what it is. It sound like a very good idea. I used to do something similar years ago in dos windows. So I think I will add one, now, but I'll do that with Gparted before I install, because it look easier to change things around in Gparted.

As for the ntfs shared data partition and windows hidden files I will have to look into that as I know nothing about it. When I installed linux it was to get away from windows. I had know idea idea learn so much other stuff, lol, but it's a steep learning curve at the minute 

Thanks again for all the help and advice

---

### Post by oldfred on 2013-05-13
How large is current Linux partition? If less than 30GB I would not make a separate /home. If larger then 10-25GB for / and the rest for /home.

I have always created partitions with gparted, but you still have to use manual install and format, & mount partitions. It should auto find swap. Swap is just unformatted space and as long as it is specified as swap it should be used. When I do an install if finds my swap file on other drives.

---

### Post by Kojak Peg on 2013-05-13
The linux partition is 103 GB the swap is 3.89 GB and the windows one is 126 GB. So I thought I'd resize everything in Gparted and then it's all ready for formatting and installing. I don't need a ton of space for /home and would prefer a fast machine. So I thought I would take some form the windows partition and some from linux, but not sure how much 


So after resizing in Gparted:
the linux partition needs to be formatted and installed on
swap is left alone, no format, no install
and the /home system file should be formatted only, is that correct

Is it also possible to give some hard drive over to virtual memory to increase the ram. I used to do that in control panel in windows but not sure if I can or even need to in linux

---

### Post by oldfred on 2013-05-13
That is what swap is. But you really do not want to use hard drive as RAM as it is a lot slower. 
How much RAM do you have? 
Linux is pretty efficient at using RAM.

---

### Post by Kojak Peg on 2013-05-14
The RAM is 3.8 GB

Am I right about what needs to be done with the four system files

format and install the linux partition
do nothing with the swap and the windows partitions 
and create a partition in Gparted for the /home partition then format it in the install

---

### Post by oldfred on 2013-05-14
That should work. But you have to create partition for /home before the install. :)

---

### Post by Kojak Peg on 2013-05-14
Thanks

---

