---
title: "Virtual Machine"
date: 2007-07-05
forum: General Help
---

### Post by benzies on 2007-07-05
Hi,

Im interested to know if someone might have already done this.  But...  Its slighty a different idea, i would like to run a virtual machine but i already have partitioned my HDD to have Winxp on Dual boot with ubuntu.  Since the great virtual machines have come out you can of course run windows while using ubuntu, and thanks to this website we can now have it run with ubuntu 

[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

Thanks to the new updates Ubuntu can now read and write to NTFS partitions, in accordance to that why not just get these virtual machines to run the partition?  It would save Processes (Or lag out, since its windows and all)  Rebooting, and at least when you do run windows souley (meaning you boot the partition) it would have all the apps already installed to it. Meaning that you could play css in ubuntu Via windows and Windows :S.  It's almost like booting to windows but windows would have two sets of BIOS Drivers (BIOS from the VM)

If it sounds too confusing then let me know, its an idea all mixed in my head right now.  I can explain it better. :)

---

### Post by kuja on 2007-07-05
Yes, yes explain it better. I found that a bit confusing.

---

### Post by benzies on 2007-07-05
Alrighty,  Maybe after a good energy drink i can chuck it all into sense.

So you have a Dual Boot computer.

HDD| Partition 1 (Winxp(NTFS)) | Partition 2 (Ubuntu Linux(EXT??))|

When your using Ubuntu you have can Have Virtual Machines running in the background using Vmware Server, Virtual box, whatever you want to use.  But thanks to someone's new idea of having every Windows Application being able to run with Gnome (Like in the background and what not) as seen here, [http://element14.wordpress.com/2007/07/05/10-minutes-to-run-every-windows-app-on-your-ubuntu-desktop/m](http://element14.wordpress.com/2007/07/05/10-minutes-to-run-every-windows-app-on-your-ubuntu-desktop/m) and in my last post(giving you screen shots of it in practice).

Instead of using a file for the Virtual Machine, why not just use the partition.  Practically having Two operating systems working together.  

The advantage of this (if it works) is that you would be able to install a Windows App while running Ubuntu(Yes of course Wine does this).  Also, if it works,  if you install the app.  When you actually load windows the Application is there ready to run, even though you have installed it Via a virtual machine and via Ubuntu.

Makes a lil more sense?

---

### Post by evolving_monkey on 2007-07-06
I checked out the link Benzies dropped in the beginning. I am using Feisty 7.04 and there is no vmware server console listed in Synaptic. Without it it seems I can't get it to work.
 Is it just that the instructions are wrong and I need to compile software downloaded from VMWare's website?

---

### Post by evolving_monkey on 2007-07-06
You know what's funny. When you answer your own question just after you post it. It is actually addable from add/remove programs ...........so there you go.

---

### Post by dabl on 2007-07-06
YES, I have both dual boot and virtual Win XP machine.

Dual boot is one thing.  Windows in a virtual machine session is a different thing.  Don't confuse them!

I use VMWare Player 2.0  (free as in beer), and got help from here:

[http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

Here's another capability, that makes me like virtual machine better than dual boot:  You can install Samba on your Linux system, and while the Windows virtual machine is running, you can have file sharing between Linux and Windows, on the same machine at the same time.  :guitar:

---

### Post by evolving_monkey on 2007-07-07
I do use this sytem for work sometimes, but it's not my main system. This particular computer I have been using to test how well Ubuntu can be used  in my work environment. So if it goes crash boom it isn't the end of the world. 

I am dual booting XP and Ubunt successfully on this machine. I also want to install a copy of XP with VMWare to see the advantages of doing either. I actually do get the difference. I'm a noob....but not "brick to the head" noob.

---

### Post by evolving_monkey on 2007-07-07
This post actually bled into another. Here is that one [http://ubuntuforums.org/showthread.php?t=494222](http://ubuntuforums.org/showthread.php?t=494222).

Thank you for the site dabl. It helped much

Thanks again

---

### Post by benzies on 2007-07-08
Its kay

I think this post should answer what i need :P

[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

Thanks all.

---

### Post by evolving_monkey on 2007-07-09
Benzies, that's an excellent tutorial.
Thanks to dabl's great site and advice I was able to get an install of windows to work in virtual machine but this is definitely something I wan to try.

Thanks

---

