---
title: "changing ownership of files"
date: 2013-04-15
forum: General Help
---

### Post by ghostninja on 2013-04-15
Hi There,

Hoping someone can help me, ive tried to search the forums but couldnt find anything specific to my issue. I have a program which is running as the root user, when it creates a file it, of course, gives ownership to root. now my question is, is there a way to automatically change the ownership of the file, as the problem i face is that ftp users cannot delete the files when no longer needed as they dont own it. and the program without major modification to the installation script (which i dont have the skills to do) wont run as anything but root. i would like a way to either set the folder the files are in to automatically chown -R to a particular user, or to chmod - R 777 all files inside the folder as they are created there. is there a command to do such a thing? or would i need to figure out how to create a looping script that chmod - R 777 everything in the folder every few minutes?? Thanking you in advance for your help. Also please give idiot proof instructions if you do happen to know the answer. 

Much Appreciated,

Ghostninja

---

### Post by schragge on 2013-04-15
You can try to set the [set-group-ID]("http://www.gnu.org/software/coreutils/manual/html_node/Directory-Setuid-and-Setgid.html") permission bit on the folder.

---

### Post by ghostninja on 2013-04-15
> **schragge said:**
> You can try to set [set-group-ID]("http://www.gnu.org/software/coreutils/manual/html_node/Directory-Setuid-and-Setgid.html") on the folder.

thanks schragge,  

lets say the folder was /home/user/stuff   

would the command be chmod =777 /home/user/stuff?

---

### Post by schragge on 2013-04-15
No. Please read the info page i linked. The idea is to make the folder be owned by some group:
```
sudo chgrp users /home/user/stuff
``` put users you want to be able to access files there into that group:
```
for user in alice bob; do sudo adduser $user users; done
``` and set the setgid bit on the folder:
```
sudo chmod g+s /home/user/stuff
```

---

### Post by ghostninja on 2013-04-15
thankyou for your help. i will let you know how i go.

---

### Post by rnerwein on 2013-04-15
hi
this is not related to the post - but i have to tell it - for schragge. i follwed a lot of posts from schragge and i think:
for breakfast he has "bash manual", for dinner "regular expressions", for dessert "sed" and last not least for supper "awk".
i am a long time unix/linux user (unix more than 30 years) but i am surprised about his knowledge. :-)   ;-)
have fun
ciao
 richi

---

### Post by CatKiller on 2013-04-15
FWIW, running things as root is a Bad Plan and anything to allow you to do so is a hack. Even if you've solved this particularly issue, not running that program as root is desirable for security reasons.

---

### Post by bab1 on 2013-04-15
> **schragge said:**
> You can try to set the [set-group-ID]("http://www.gnu.org/software/coreutils/manual/html_node/Directory-Setuid-and-Setgid.html") permission bit on the folder.

I think the link you provided can be confusing to a new user.  In the end it shows how to set BOTH SUID and SGID together (6) while not mentioning all  of the other options (i.e setting just SGID (2)).  See [**_[COLOR="#0000FF"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for a more gentle explanation.

---

### Post by Morbius1 on 2013-04-15
Running the application as root introduces other impediments to making this work me thinks.

When I create a folder/file it has permissions of 775/664. When root does this it has permissions of 755/644. If you use setgid and set the group to "users" on the parent folder the file added by root will in fact have "users" as the group but the ordinary user will still not be able to delete the file as required. You would have to change permissions on the parent folder to 775 if all you want to do is allow the ordinary user to delete the file.

If however you want the ordinary user to be able to edit this file and the file is created dynamically by root then you will have to do something extra-ordinary, something like bindfs, to pull that off.

---

### Post by schragge on 2013-04-15
@**Morbius1**
I was not aware that root has tighter umask than regular user on Ubuntu which makes sense actually. I'm on Debian where all users have *umask 022* by default, so the setgid trick won't work anyway, but I was reading somewhere that Ubuntu had changed umask to 002 and assumed it would work then. Thanks for correcting my misconception.

---

### Post by bab1 on 2013-04-15
> **schragge said:**
> @**Morbius1**
I was not aware that root has tighter umask than regular user on Ubuntu which makes sense actually. I'm on Debian where all users have *umask 022* by default, so the setgid trick won't work anyway, but I read somewhere that Ubuntu had changed umask to 002 and assumed it would work then. Thanks for correcting my misconception.

You can always set the umask in the script or in a wrapper script for a binary blob.  The last declared umask is what is used.  In a script or wrapper, the umask should be local to that environment only.  I would be more inclined to use a SGID for a common group with the appropriate umask.

---

### Post by ghostninja on 2013-04-16
thanks guys, tried everything mentioned above and then some. but no luck. seems that as long as root still owns the file no matter whether i change umask, set uid or gid, or sit shouting curses at the screen the user simply cannot delete the files. even after changing file permission to 777 in filezilla wont work.   such a simple thing, yet so stupidly difficult, but ive learnt a hell of a lot trying to make it work.  think i will look into creating a looping script to chown -R the folder every few mins. or will that chew up too much resources? anyone gotta guide for making scripts? only been using linux off and on for the last couple of months so any help would be appreciated.

---

### Post by bab1 on 2013-04-16
> **ghostninja said:**
> thanks guys, tried everything mentioned above and then some. but no luck. seems that as long as root still owns the file no matter whether i change umask, set uid or gid, or sit shouting curses at the screen the user simply cannot delete the files. even after changing file permission to 777 in filezilla wont work.   such a simple thing, yet so stupidly difficult, but ive learnt a hell of a lot trying to make it work.  think i will look into creating a looping script to chown -R the folder every few mins. or will that chew up too much resources? anyone gotta guide for making scripts? only been using linux off and on for the last couple of months so any help would be appreciated.

Sometimes the devil is in the details.  If you have a file the is owned by root:***users*** and the permissions are read/write (rw-) for both the user and the group, the file can be edited or deleted by any user in the group ***users***.  There is no need to constantly run a script to reset the permissions on the data files. 

What is the program you are running?  How about posting the data that the program creates and the directory structure that where the data is placed.

---

### Post by Morbius1 on 2013-04-16
Let me volunteer for the "stupid question". The only ftp server thing I've done was with vsftp and that was a very long time ago but you needed to enable the ftp user to have write ( and delete ) access. With vsftp it was a "write_enable=Yes" ( I think ) that had to be added to the vsftpd.conf file somewhere.

You did do this on whatever ftp package you are using, right?

---

### Post by bab1 on 2013-04-16
> **Morbius1 said:**
> Let me volunteer for the "stupid question". The only ftp server thing I've done was with vsftp and that was a very long time ago but you needed to enable the ftp user to have write ( and delete ) access. With vsftp it was a "write_enable=Yes" ( I think ) that had to be added to the vsftpd.conf file somewhere.

You did do this on whatever ftp package you are using, right?

Not a stupid question at all.  Better to know now rather than at post #153.  ;-)

---

### Post by ghostninja on 2013-04-16
yep can read, write and create, everything except delete.

---

