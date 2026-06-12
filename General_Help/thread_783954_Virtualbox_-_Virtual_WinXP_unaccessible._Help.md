---
title: "Virtualbox - Virtual WinXP unaccessible. Help??"
date: 2008-05-06
forum: General Help
---

### Post by bioburg on 2008-05-06
Hello everyone ;)

This morning I tried to run my virtual winXP via Virtualbox which is installed in Ubuntu 7.10 AMD64. And I got this error message.

[[IMG]http://img253.imageshack.us/img253/8716/virtualboxerrorblb9.png[/IMG]](http://imageshack.us)
Does anyone encountered this before?

I hope I just have to edit a XML file, but I'd like some conformation of this, since I don't want to screw up the virtual XP (took me quit some time to install it properly).

Does anyone know how to fix this?

Kind regards,

Bioburg

---

### Post by Ameneon on 2008-05-06
What it seems to say is that the vbox HDD for the installation still is attached to a machine and cannot be mounted on this one. I don't know the exact error but I would think that perhaps the machine wasn't shut off properly last time leaving some state file intact, but that'd be a guess of course. Not at home so I don't have access to vbox here but I'd look in that direction at least..

---

### Post by bingoUV on 2008-05-06
1. Was any other virtual machine running when you got this error? Closing that machine might help. 
2. Copy the hard disk image file of the machine that you want to run to another file, and create a new machine using this copied hard disk image. You will lose state that your machine was in but otherwise it should work fine.

---

### Post by bioburg on 2008-05-06
tnx for your answers :)

> **Ameneon said:**
> What it seems to say is that the vbox HDD for the installation still is attached to a machine and cannot be mounted on this one. I don't know the exact error but I would think that perhaps the machine wasn't shut off properly last time leaving some state file intact, but that'd be a guess of course. Not at home so I don't have access to vbox here but I'd look in that direction at least..

Sometimes Vbox shows that the virtual XP hasn't been shut off proparly --> aborted or something, but I can always just simply start it again and nothings wrong. I do close winXP properly tho....(shut down etc)

This time I can't start it ... 

I think I just have to change something in the XML files.
There is one in the /home/usernam/.Virtualbox folder and one in the /home/usernam/.Virtualbox/VDI/winXP - LOB b folder.
I couldn't find one in the /home/usernam/.Virtualbox/Machines folder.

I think I need to figure out which code represents my latest snapshot and both XML files have to represent the same {....lots of numbers.....}. I'm not sure how to locate that last snapshot.

Am I thinking correctly?

added note = lastnight it still worked and this morning it gave me the message :rolleyes: and after 3 restarts it still gave me the same message :/

*edit:* I guess we posted simultaniously ^^
> **bingoUV said:**
> 1. Was any other virtual machine running when you got this error? Closing that machine might help. 
2. Copy the hard disk image file of the machine that you want to run to another file, and create a new machine using this copied hard disk image. You will lose state that your machine was in but otherwise it should work fine.

1. Yesterday when I closed it there was a nother VM running.
This morning when I started it, there wasn't.
2. I'll give that one a try. I don't car much about the current state, I do care about the latest snapshot I've taken. 

tnx for the advice guys :D

---

### Post by bioburg on 2008-05-06
I found the problem. 

Thre are no snapshots in my machine folder of the virtual XP which gives the error. I think I messed up lastnight by creating the last snapshot of the completed version. I named it the same as the one before and I deleted the older version.

I think both versions were deleted because they had the same name ](*,)

I'm copying now and will post the result of the attempt.

result = doesn't work --> doing a clean install again :rolleyes:

---

