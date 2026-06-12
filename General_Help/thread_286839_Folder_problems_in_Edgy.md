---
title: "Folder problems in Edgy"
date: 2006-10-28
forum: General Help
---

### Post by NZ-Wanderer on 2006-10-28
Anyone else come across this type of problem in Edgy??

[[IMG]http://img170.imageshack.us/img170/3960/screenshotjw7.th.jpg[/IMG]](http://img170.imageshack.us/my.php?image=screenshotjw7.jpg)

That "supposedly" is my "home/john" directory, notice anything weird??
At the moment I am using a brand new "home/john" (the old one is on another partition backed up in hopes it can be restored..

BUT I have just noticed with this brand new install, I goto network servers, click on "windows network" folder, up comes "mshome" sometimes as a folder, sometimes as a normal icon such as you see in that screenshot above..

I am very concerned with what is happening here, and I have no idea what to do to fix it...

---

### Post by Who on 2006-10-28
> **NZ-Wanderer said:**
> Anyone else come across this type of problem in Edgy??

[[IMG]http://img170.imageshack.us/img170/3960/screenshotjw7.th.jpg[/IMG]](http://img170.imageshack.us/my.php?image=screenshotjw7.jpg)

=That "supposedly" is my "home/john" directory, notice anything weird??
At the moment I am using a brand new "home/john" (the old one is on another partition backed up in hopes it can be restored..



Do these 'normal icons' that are really folder behave like folders when you click on them? maybe try changing icon theme in system-->preferences-->theme.

If not...

I really don't know, but it looks like what I've seen when mounting disks as the wrong type using mount or fstab - perhaps edgy detected something wrong (though this wouldn't explain why smb doesn't work? 

If you want to check this then look at /etc/fstab (sudo gedit /etc/fstab) and see that the third item in the line for the affected disk is the correct filesystem type - like 'ext3'

as an example, one of my lines for ext3 looks like this

UUID=7c528538-e560-4916-ae58-5ea9cf7cff4f /media/hdc5 ext3 defaults 0 2

Good luck

---

### Post by NZ-Wanderer on 2006-10-28
Thanks for the reply...

Alas no, these normal icons' that are really folders, Do NOT behave like folders, clicking on properties of google-earth for instance the type is "unknown", as is the size, and the permissions, well that says "The permissions of Google-earth could not be determined"

I looked at fstab, and all partitions are as they should be, it has even got the backup home partition I made as EXT3...

---

### Post by NZ-Wanderer on 2006-10-28
Anyone got any ideas to my strange problem? - I never had anything like this happen on Dapper or Breezy, nor did it happen on RC1 of Edgy..
If it wasn't soo much hassle I would reinstall one of those to see if my folders came back, but I hoping one of you real bright people can give me some ideas :D :D

Update:

I have given up and gone back to Dapper.. there are too many things in Edgy that make it unusable to me.
1) It eating my original home and trashing my directories
2) problems getting smb to work properly
3) unable to get vmware working
4) no more "disks" in system/admin

are the main ones...

I'm sorry, but IMHO this is the worst Ubuntu I have seen released so far...

---

