---
title: "Installation problem"
date: 2007-06-07
forum: General Help
---

### Post by matjosquig on 2007-06-07
I decided to install wubi the about a week ago.  I installed it and it worked fine.  For some reason i decided to uninstall it.  Today i decided that I wanted to install it again but when i tryed to boot i got a "error 17 file not found" message.  What do I do to correct this I tried reinstalling it.  I think this would make the 3rd time and they all get that error.

---

### Post by benanzo on 2007-06-07
This is most likely because the */boot/grub/menu.lst* doesn't list the correct partition for your root **/** install.  You may need to boot to an Ubuntu LiveCD and edit that file to point to the correct partition.  Sometimes that can happen across upgrades or other changes.

---

### Post by matjosquig on 2007-06-07
i dont have i live cd were do i get one?

---

### Post by MikeM709 on 2007-06-07
Go to the Ubuntu site and click on the download ubuntu link on the left. then choose what flavor of ubuntu you want and then select the desktop iso, (i.e. don't click the checkbox next to the alternate iso thingy.) then your download should start. burn that iso to a cd using a program that can burn .iso files, because they are not the same as regular files. .iso's are like a photo copy of a cd and when it burns it it unzips it so it knows where to put everything.

---

### Post by ago on 2007-06-07
You can also try [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html) 

We would like to know if that fixes your problem (remove any menu.lst file you may have on C:\ or D:\)

---

### Post by matjosquig on 2007-06-07
Ok i am running linux off the live cd now what?

---

### Post by ago on 2007-06-07
You can choose to install it if you like it. There should be an icon on the desktop.

---

### Post by matjosquig on 2007-06-07
i dont want to delete windows!  Well i don't care about windows but i don't want to delete all my files.

---

### Post by ago on 2007-06-07
Ubuntu will resize your windows partition, without deleting it (unless you choose so). If you want to avoid partitioning try the wubi-minefield link above

---

### Post by matjosquig on 2007-06-07
so if i click install it will partition it right?  And how would i unpartition it if i want to remove it later?

---

### Post by ago on 2007-06-07
That's a bit more involved, but essentially you need to expand the partition with some tool (gparted for instance) and restore the windows bootloader. If you want to avoid partitioning you can use wubi (which does not modify the partitions and can be uninstalled) or keep using the live cd.

---

### Post by MikeM709 on 2007-06-07
i would suggest getting a 1 GB (minimum) flash drive and installing linux on there. there are many sites that offer detailed explinations on how to do it. that way its like a live cd in that it has everything on there that you want, its small, and also you can save things to it like documents unlike a live cd where once its on the cd you cannon modify it.

---

### Post by matjosquig on 2007-06-07
can i still load windows or not?

---

### Post by MikeM709 on 2007-06-07
do you mean now or with my flash drive thing. 

because right now you might not be able to if you have vista because wubi is still going through testing, but look for a thread i started a little down the page. 

if you are talking now and you do not have vista, then you should be able to.just select windows when the screen comes up asking you what to boot when you start your computer.

if youare talking about that flash drive thing, then yea you can boot from there or the hard drive. plus you can use it on any computer like ones at work or friends houses and such.

---

### Post by matjosquig on 2007-06-07
I am trying to use wubi or the flash drive thing but is the flash drive thing going to load faster than the live cd because this live cd version is running really slow.  I have win xp but when i try and but ubuntu that i used wubi to install i get a file not fount error 17

---

### Post by MikeM709 on 2007-06-07
you can get back to windows. and also the flash drive thing is only fast if your flashdrive has fast read/write speeds. if its slow, then it will be no faster then a live cd. it will most likely be just as slow. but if you want to bring linux with you everywhere, then use the flash drive. but for now you can just go back to windows xp by selecting windows from that menu that comes up when you start your compputer. select windows instead of ubuntu.

---

### Post by matjosquig on 2007-06-07
but i need help getting the wubi version to work when i try to boot it i get an error 17 file not found.

---

### Post by ago on 2007-06-08
Did you try [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html) ?

---

