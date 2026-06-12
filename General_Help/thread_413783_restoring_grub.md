---
title: "restoring grub"
date: 2007-04-19
forum: General Help
---

### Post by Mateo on 2007-04-19
i had to restore my windows because i had a problem. after doing so, grub didn't load up any more.  but luckily my partition didn't get erased, so my ubuntu is fine, i just can't get into it.  however i have the livecds so i should be able to get into it and mount the partition.  but how do i restore grub so that it starts when i start my computer.  thanks.

---

### Post by zeekay on 2007-04-19
Try [this help]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation").

Also, if you got a SATA disk, it will instead of returning (hd0), you'll most likely receive (sda0)

---

### Post by Mateo on 2007-04-19
i have several live cds, the old dapper one, a xubuntu one... does this really matter though?   I was just going to use the livecd to access my partition...

---

### Post by zeekay on 2007-04-19
Just take a look on the help I sent then, it teaches what to do if you already got a live cd. :)

---

### Post by Mateo on 2007-04-19
ok, i am trying but a livecd takes FOREVER to load, and what's worse I can't even know what the progress is because my monitor will not display in anything lower than 1024x768.  so until it's completely loaded, i'm clueless as to what's going on.  i tried the xubuntu cd but it stopped working for some reason.  now i'm trying the regular ubuntu dapper cd, i hope this works.

---

### Post by Mateo on 2007-04-19
ok, so i dragged up an old monitor and hooked it up.  it's saying "buffer i/o error on device hdb", said the same thing with the xubuntu livecd.  this is frustrating.

---

### Post by Mateo on 2007-04-19
don't work.  when I type:

find /boot/grub/stage2

says file not found.  i know for a fact that the file exists, however

---

### Post by Mateo on 2007-04-19
bump

---

### Post by zeekay on 2007-04-19
Interesting, you might have the same problems I had a couple of days ago. I couldn't get my Ubuntu working again after that, so I backuped it to a pen-drive and by network transfer and re-installed my Ubuntu, this time a Feisty.

To see the content of your hard disk, try this:
go to the terminal and type
```

# sudo fdisk -l (the parameter is a small L by the way)
<Then it will list all the partitions you got on your HD, so you check up the name of it, if
it's hd2 or sda2 or something like it. You can tell which one it is by taking a look on the 
sizes.>
# cd /media
# sudo mkdir mydisc

# sudo mount /dev/nameofthepartition /media/mydisc (replace "nameofthepartition" 
for the real name of it, in your case could be sda3 or hd2, the one you identified on 
the first command)

```

Then you'll be able to access your hard disc normally, you can backup the data you want from it and even try running the GRUB recovery tutorial again.

---

### Post by Mateo on 2007-04-19
just to let you know that I got it to work.  thanks for your help.  i'll write about how I did it a little bit later.

---

### Post by Mateo on 2007-04-19
wow, what an ordeal.  it was really a problem because my monitor won't display anything below 1024x768.  So during the boot process I can't see anything. This has always been the case.  But usually it's no big deal.  But with the livecds that take forever, it's frustrating because i have no idea what's going on.

So I went to the basement and got an old monitor.  I should say old and **heavy**.  bought broke my back hauling it to the computer room and set it up.  I didn't have any room to put it, so I put it in my chair and sit on the floor, while trying to use the keyboard that's on the desk and look at the monitor sitting in the chair.  the monitor is really old it doesn't display well anyways.  I then discovered that i was getting some i/o error so I tried the xubuntu cd and the same thing happened.  then I tried fluxbuntu and it loaded.  But for some reason I could execute the commands.  By this point I was so uncomfortable and my eyes hurting from sitting right next to a monitor (on the floor), that i moved the desk monitor and put the old one there so I could at least be semi-comfortable while i tried to fix the problem.  so then I popped back in the xubuntu cd and it loaded finally with the error.  Then I tried the fix a couple of times, a couple of different ways and it never worked.  Frustrated I turned it off and went and did some errands.  I even put the old monitor away.  Later I came back and loaded xubuntu livecd and tried the fix again, this time it worked (why I don't know).

all in all, one of the least comfortable computer experiences of my life.

---

### Post by komputes on 2008-01-08
This worked very well for me. I love the fact that you can tab in grub to see whats available, very handy...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

