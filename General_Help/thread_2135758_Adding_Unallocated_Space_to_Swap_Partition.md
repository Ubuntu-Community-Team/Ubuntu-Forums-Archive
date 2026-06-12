---
title: "Adding Unallocated Space to Swap Partition"
date: 2013-04-15
forum: General Help
---

### Post by ChochiWpg on 2013-04-15
Hi Everyone,

I successfully installed Ubuntu 12.04.2 LTS over the weekend on a classic dual boot scenario.  I followed the instructions on the below website to create a /boot, /, /home and /swap partition.  I then used EasyBCD to tell Windows that it is sharing the computer with another OS.  Now when I boot up, the Windows Bootloader recognizes (and I have the choice) of booting into Windows or Ubuntu at startup.

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) 

During the install process, I repartitioned my main C:/ drive, allocating 100000MB to Ubuntu.  I placed 500MB into /boot, 20000MB into /, 75000MB into /home and 4000MB into /swap.  This leaves me with 500MB of unallocated space.  

Now that I have my system setup and running, is there a way I can take that unallocated space and add it to my /swap partition?  I figure 500MB would be better used in /swap than it would be in any other partition. In hind sight, I should have just allocated 4500MB to /swap at the beginning, but that was a mistake on my part.

I am not sure the best and easiest way to add the unallocated space to /swap.  Thanks in advance for anyone that can help.

---

### Post by ibjsb4 on 2013-04-15
How much ram do you have.  Could you show us a pic of you partition layout?

---

### Post by ChochiWpg on 2013-04-15
> **ibjsb4 said:**
> How much ram do you have.  Could you show us a pic of you partition layout?

I have 4GB of RAM.  Currently I am at work so I don't have the ability to provide a screenshot/pic of my partition layout at the moment.  I can provide this feedback when I am home from work later this afternoon though.

---

### Post by pfeiffep on 2013-04-15
Before you decide to allocate more swap it's adviseable to review how much swap is [recommended]("https://help.ubuntu.com/community/SwapFaq") for your system:

**Example Scenarios***[SIZE=2](copied from above link)[/SIZE]*

[LIST]
[*][FONT=inherit]_Low RAM and low disk space_[/FONT] With 512 MiB RAM and 30 GB hard disk, use 512 MiB for swap since RAM is very low.
[*][FONT=inherit]_Low RAM and high disk space_[/FONT] With 512 MiB RAM and 100 GB hard disk, use 1 GiB for swap since RAM is very low and hard disk space is plentiful.
[*][FONT=inherit]_High RAM and low disk space_[/FONT] With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.
[*][FONT=inherit]_High RAM and high disk space_[/FONT] With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful.
[/LIST]

---

### Post by ChochiWpg on 2013-04-15
> **pfeiffep said:**
> Before you decide to allocate more swap it's adviseable to review how much swap is [recommended]("https://help.ubuntu.com/community/SwapFaq") for your system:

**Example Scenarios***[SIZE=2](copied from above link)[/SIZE]*

[LIST]
[*][FONT=inherit]_Low RAM and low disk space_[/FONT] With 512 MiB RAM and 30 GB hard disk, use 512 MiB for swap since RAM is very low.
[*][FONT=inherit]_Low RAM and high disk space_[/FONT] With 512 MiB RAM and 100 GB hard disk, use 1 GiB for swap since RAM is very low and hard disk space is plentiful.
[*][FONT=inherit]_High RAM and low disk space_[/FONT] With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.
[*][FONT=inherit]_High RAM and high disk space_[/FONT] With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful.
[/LIST]


Thank you for your reply.

I actually did read the swapFAQ prior to performing the install as well.  With my current situation I was in the category of High RAM (4GB) and high disk space (100000MB).  So I chose to allocate the same amount of RAM for /swap as I have actual RAM on my system (4GB).  

However, in the Ubuntu installer they provide you with size allocations in MB as opposed to GB.  So in entering 4000MB for /swap I actually allocated 3.9GB and not exactly 4GB.  When I go to system info it actually says I have 3.7GB RAM for some reason.  If I can allocate the unused 500MB to /swap that would provide 4500MB total or 4.39GB for /swap.

I don't know if the 0.49GB extra will make much of a difference in the end.  But I just wanted to use up the extra 500MB of free space.

Or is it best that I just don't worry about it and just leave it unallocated?

---

### Post by pfeiffep on 2013-04-15
> **ChochiWpg said:**
> Thank you for your reply.

I actually did read the swapFAQ prior to performing the install as well.  With my current situation I was in the category of High RAM (4GB) and high disk space (100000MB).  So I chose to allocate the same amount of RAM for /swap as I have actual RAM on my system (4GB).  

However, in the Ubuntu installer they provide you with size allocations in MB as opposed to GB.  So in entering 4000MB for /swap I actually allocated 3.9GB and not exactly 4GB.  When I go to system info it actually says I have 3.7GB RAM for some reason.  If I can allocate the unused 500MB to /swap that would provide 4500MB total or 4.39GB for /swap.

I don't know if the 0.49GB extra will make much of a difference in the end.  But I just wanted to use up the extra 500MB of free space.

Or is it best that I just don't worry about it and just leave it unallocated?

It's probably best to leave the space unallocated for a while - if you feel as if you need it for swap later then add it, if not maybe add it elswhere;)

---

### Post by ibjsb4 on 2013-04-15
I personally do not think that adding 500M swap is going to make a difference.  Thats why I ask for a pic.  If that 500M is located next to swap, then sure, go for it.  If its far away, then it will be a pain.  Swap to me is not a big deal when running 4G of ram.  Unless you get into something heavy like cad or video editing where swap may kick in.  You can usually tell when it does, you take a noticeable performance hit.  Also if your using Hibernate, you need swap.

Not using the above, you may not even need swap :)  I do not use it on some installs, on others I do.  You can turn swap off using gparted and see what happens if you feel like playing asround.  You can also adjust swapiness.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by ChochiWpg on 2013-04-15
> **pfeiffep said:**
> It's probably best to leave the space unallocated for a while - if you feel as if you need it for swap later then add it, if not maybe add it elswhere;)

> **ibjsb4 said:**
> I personally do not think that adding 500M swap is going to make a difference.  Thats why I ask for a pic.  If that 500M is located next to swap, then sure, go for it.  If its far away, then it will be a pain.  Swap to me is not a big deal when running 4G of ram.  Unless you get into something heavy like cad or video editing where swap may kick in.  You can usually tell when it does, you take a noticeable performance hit.  Also if your using Hibernate, you need swap.

Not using the above, you may not even need swap :)  I do not use it on some installs, on others I do.  You can turn swap off using gparted and see what happens if you feel like playing asround.  You can also adjust swapiness.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Thanks guys, maybe I will just leave it for now.  The system feels fairly snappy to me, the only time it takes a performance hit is when I have a couple apps running at the same time, more so when I was running ClamTK (which I decided to uninstall, I was just using it to scan my Windows partition anyway).  I also changed the swapiness to 10 from the default 60, but didn't really notice a difference with regards to performance, it still felt the same to me, so I changed it back to the default.

I will still download gparted and check out where exactly the free space is allocated and make my decision from there I guess.  Thanks again for all your help.  Much appreciated.  

On another note, I don't know why it took me this long to install Ubuntu, I already love it a lot more than Windows Vista.  Simple, beautiful and worry free (no more worrying about viruses).  It's a very nice change of pace.

---

### Post by ChochiWpg on 2013-04-15
> **ibjsb4 said:**
> How much ram do you have.  Could you show us a pic of you partition layout?

Here's the screenshot you were looking for, is it possible to allocate the unused space to /swap?

---

### Post by ibjsb4 on 2013-04-15
Easy enough in this case.  Just resize sda8 to take up that 477M.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Edit: I just about forgot :) you must turn off swap (in gparted) to resize

---

### Post by ChochiWpg on 2013-04-15
> **ibjsb4 said:**
> Easy enough in this case.  Just resize sda8 to take up that 477M.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Edit: I just about forgot :) you must turn off swap (in gparted) to resize

Maybe it's because I am reading the instructions from a phone, but they seem pretty overwhelming and complicated to me. This is the first time I have dealt with partitions so I am not really sure what I am doing.

---

### Post by ibjsb4 on 2013-04-15
To resize sda8, highlight it and just click on the arrow and drag to right until all of the 477M has been added.

[ATTACH=CONFIG]241428[/ATTACH]

Then to save the change, click on the "check mark"

[ATTACH=CONFIG]241429[/ATTACH]

Turn on your swap and your done :)

Hope you can see this on your phone.

---

### Post by ChochiWpg on 2013-04-15
> **ibjsb4 said:**
> To resize sda8, highlight it and just click on the arrow and drag to right until all of the 477M has been added.

[ATTACH=CONFIG]241428[/ATTACH]

Then to save the change, click on the "check mark"

[ATTACH=CONFIG]241429[/ATTACH]

Turn on your swap and your done :)

Hope you can see this on your phone.

I turned swap off and it brought up the menu to resize, but in the menu it doesn't allow me to drag and make it bigger.  I can see the screen in the screen shot, but there is no extra space to drag to make it bigger.

---

### Post by ibjsb4 on 2013-04-15
Is there free space following?

[ATTACH=CONFIG]241430[/ATTACH]

---

### Post by ChochiWpg on 2013-04-15
No, for some reason it says 0 for free space following.

No worries man, you have gone out of your way to try and help me with this issue.  I noticed that things started to become laggy so wanted to use that extra 500MB for swap.  But was reading somewhere to logout and sign into Ubuntu2D and now everything is very snappy and smooth.  

If you have other suggestions I would be willing to try them out, but no worries if it can't be fixed, it's running good now.  I am also heading off to bed now so won't respond until tomorrow.  Peace man.

---

### Post by ibjsb4 on 2013-04-15
Sounds good to me :)

That extra space must be in the primary.  That would mean passing it to sda3 to 5 to 6 to 7 and then to 8.  Too much moving for too little gain.  No to mention the risk in doing such things.  goodnight :)

---

### Post by ChochiWpg on 2013-04-16
> **ibjsb4 said:**
> Sounds good to me :)

That extra space must be in the primary.  That would mean passing it to sda3 to 5 to 6 to 7 and then to 8.  Too much moving for too little gain.  No to mention the risk in doing such things.  goodnight :)

Agreed, thanks again for all your help.  I will mark this thread as solved.  Much appreciated.  Peace.

---

