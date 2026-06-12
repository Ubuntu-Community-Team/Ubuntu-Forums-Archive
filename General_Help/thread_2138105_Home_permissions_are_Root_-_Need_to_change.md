---
title: "/Home permissions are Root - Need to change"
date: 2013-04-23
forum: General Help
---

### Post by Redalien0304 on 2013-04-23
Reinstalled Ubuntu 12.04 with Root & Home on Different Partitions. Copied over 2 Directories "Documents & Downloads" from my Home Backup (Full partition Backup of Home). tried to change the owner via gksu nautilus but no luck. did not change. Now if change folder inside Downloads Dir say  "Wifi on Dell Latitude D600" (which i did) only changes the Folder properties not the the files inside the folder. I can change the file Properties Individually (which i did). How can change all Files in Downloads & Documents to my current User easily??  I found this would this work [http://askubuntu.com/questions/129745/is-there-a-graphical-method-for-modifying-users-group-memberships](http://askubuntu.com/questions/129745/is-there-a-graphical-method-for-modifying-users-group-memberships) or what is the way to do it in the Terminal? If need more Info let me know. Any info would be Appreciated thanks

---

### Post by Diametric on 2013-04-23
Are you asking how to change the file ownership?

---

### Post by Redalien0304 on 2013-04-23
yes im asking how to change file Ownership preferably gui. bu i will do in the terminal also.

---

### Post by VeeDubb on 2013-04-23
You will need to change the ownership of the files, and it is MUCH easier and more reliable to do it through the console.  I will give you directions, but you MUST be extremely careful, as anything run as root (using sudo) that includes -r can have catastrophic consequences if misused.

Very simply, open up a terminal (boot into single user mode if you have to) and assuming your username for your desktop is steve, 

```
sudo chown -R steve:steve /home/steve
```

That will change the owner and group owner of your home directory and everything in it.  In plain english that more or less means:

As the root user (sudo), change ownership (chown), recursively (-R), to the user named steve and the group named steve (steve:steve), of steve's home directory (/home/steve)

If you're forced to boot into single user root terminal mode, you can skip the sudo.

If any part of that is unclear, PLEASE ask for clarification.

---

### Post by Diametric on 2013-04-23
^^He beat me to it.  And don't forget to go over the man page:

man chown

Cheers.

---

### Post by Redalien0304 on 2013-04-23
Ok i did sudo chown -R craig:craig /home/craig   I get error chown: cannot access `/home/craig/.gvfs': Permission denied back whts going on now?

---

### Post by deadflowr on 2013-04-23
> **Redalien0304 said:**
> Ok i did sudo chown -R craig:craig /home/craig   I get error chown: cannot access `/home/craig/.gvfs': Permission denied back whts going on now?

What does

```
ls -al ~/.gvfs
```

show you.

And do you have any samba or network shares mounted?

---

### Post by Redalien0304 on 2013-04-23
Output of  ls -al ~/.gvfs
dr-x------  2 craig craig    0 Apr 22 16:45 .
drwxr-xr-x 28 craig craig 4096 Apr 22 21:00 ..
 
 No samba or network shares

---

### Post by deadflowr on 2013-04-23
I did find this which gives some info on gvfs

[http://ubuntuforums.org/showthread.php?t=791693](http://ubuntuforums.org/showthread.php?t=791693)


Whether the info is helpful for this or not...

---

### Post by steeldriver on 2013-04-23
That's normal, it's nothing to worry about imho - .gvfs is like a mount point for user-mounted Nautilus network shares, you shouldn't be trying to change the ownership on those anyhow (they are not really part of 'your' home directory). It's always created without read permissions for anyone except the owner (not even root).

---

### Post by grahammechanical on 2013-04-23
I recently had a similar problem. I created a data partition and I had to use gksudo nautilus to create folders on that partition. That gave ownership to "me" with group "root" and "others" only having access not to create and delete files. And so when I copied files into those folders as standard user I could only access those files. I could not write to them.

The answer is to use gksudo nautilus to select the folder, select Properties and change the permissions in the permissions tab. You will find that with gksudo nautilus you get an option to change the permissions of files inside each folder. It can be done one file at a time but this option will change the permission of "group" and "others" for all the files. Look for the button that says "Change permissions for enclosed files."

Regards.

---

### Post by Redalien0304 on 2013-04-23
did gksudo on the 2 folders Documents,  Downloads, it appears might be fixed. i will it a give it a day or so. Ty grammechanical

---

