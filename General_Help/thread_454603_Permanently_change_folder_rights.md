---
title: "Permanently change folder rights?"
date: 2007-05-25
forum: General Help
---

### Post by Blofeld on 2007-05-25
How do I make it that all files which get placed in a certain folder are automatically set to certain rights?
I have a shared folder, and I want all files which are placed in that folder to be automatically manipulatable by everyone.  Because I'm tired of having to do a chmod each time I'm shifting files from one computer to another.[-(
I thought I could achieve this by commanding > sudo chmod a+rwx /Thatsharedfolder -R but it didn't work.:(
Is this doable?  Any suggestions, oh you mighty Linux wizards?

---

### Post by maxamillion on 2007-05-25
```
sudo chmod 777 -R testDIR/
```

should work ... it appears to have worked on my machine (though keep in mind i did limited testing as i was just doing it in order to answer this post)

---

### Post by tgm4883 on 2007-05-25
> **maxamillion said:**
> ```
sudo chmod 777 -R testDIR/
```

should work ... it appears to have worked on my machine (though keep in mind i did limited testing as i was just doing it in order to answer this post)

Wouldn't that just apply to everything that was in the folder and all subfolders and files?  What about if you added a file to that directory after you ran that command?  Would it have the correct permissions?  The OP wants to only have to run that command once.

---

### Post by maxamillion on 2007-05-25
Oh! ... hah, yeah ... didn't even think about that ... uhmmm not sure, haven't ever tried.

I will look into that and post back.

---

### Post by fdrake on 2007-05-25
> **tgm4883 said:**
> Wouldn't that just apply to everything that was in the folder and all subfolders and files?  What about if you added a file to that directory after you ran that command?  Would it have the correct permissions?  The OP wants to only have to run that command once.

you would have to run that command each time that you move a file inside that folder. just because you move a file doesn't mean it loses its permissions.

---

### Post by tgm4883 on 2007-05-25
> **fdrake said:**
> you would have to run that command each time that you move a file inside that folder. just because you move a file doesn't mean it loses its permissions.

Thats the point though, what we are trying to accomplish.

What we want is to be able to put a file inside a directory and for it to inherit the permissions of the directory automatically

---

### Post by Blofeld on 2007-05-26
Thanks for your input everyone.  Still no solution, but at least it seems I haven't overlooked anything obvious!
;)
If anyone still has a solution up his sleeve, feel free to extrapolate it here!

---

### Post by aidanr on 2007-05-26
you could make a thunar custom action that moves and sets permissions of selected file(s)

bit busy at work atm, will put something together later

---

### Post by tgm4883 on 2007-05-26
A cron job would be able to do it to no?  But then you would have to wait until it runs.  I suppose you could have it run often, although im not sure how intense that would be on folders with large amounts of files.

---

### Post by fdrake on 2007-05-26
my idea is to create a launcher in the terminal.right click on the desktop and select "Create Launcher".
Type: application in terminal
Name:share  
Command: sudo chmod 777 -R  "directory's url"

make sure u set the permission of the  launcher file to 777, so open the terminal and type:
sudo chmod 777 "launcher's url" the last thing left is to place this launcher somewhere where everybody can access it.What about the home directory? 
sudo mv "launcher's url" /home/share
to make it easier you can make a link on your desktop or on your panel.

this method implies 1 thing that a file can be shared only by its owner.

---

### Post by tgm4883 on 2007-05-26
> **fdrake said:**
> my idea is to create a launcher in the terminal.right click on the desktop and select "Create Launcher".
Type: application in terminal
Name:share  
Command: sudo chmod 777 -R  "directory's url"

make sure u set the permission of the  launcher file to 777, so open the terminal and type:
sudo chmod 777 "launcher's url" the last thing left is to place this launcher somewhere where everybody can access it.What about the home directory? 
sudo mv "launcher's url" /home/share
to make it easier you can make a link on your desktop or on your panel.

this method implies 1 thing that a file can be shared only by its owner.

Doesn't this method also require that the user has sudo privledges?

---

### Post by adampyre on 2007-05-26
I think it means you have to type the password for sudo each time?

---

### Post by fdrake on 2007-05-26
> **tgm4883 said:**
> Doesn't this method also require that the user has sudo privledges?

you right using sudo you need to be a superuser. but i think you don't actually need sudo in this case, because the owner of the file (even if it's not a superuser) can change the permission of any file s/he owns. so just ignore sudo.
Command: chmod 777 -R "directory's url"

---

### Post by xpc on 2007-05-28
Looking for a solution for the exact same problem, I found that activating acl ([SIZE=-1]access control list) can do the trick:

First get acl
[/SIZE]```
sudo apt-get install acl
```then change /etc/fstab for the mountpoint you wish to use acl on, ie:

```
/dev/hda9    /media/share    ext3    defaults,acl    0    2
```note that not all filesystems support acl
umount and mount /media/share to activate acl:

```
sudo umount /media/share
sudo mount -a


```then set the permissions with setfacl:

```
sudo setfacl -R -m d:u::rwx,d:g:users:rw,d:m:rw,d:o:--- /media/share
```that's it! Now all the users of the group users can read and write all the files in the share folder. 

Finally 
```
getfacl /media/share 
```will show you the permissions of that folder

---

