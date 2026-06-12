---
title: "[SOLVED] OMG, I sent /home/user folder to /Trash..."
date: 2013-07-10
forum: General Help
---

### Post by LinuxNubian on 2013-07-10
I tried to move a /home/user folder from an external harddrive to my internal /home folder running Xubuntu 12.04. I received an error indicating an .iso could not be copied, so I cancelled the operation and attempted to send the newly copied partial folder to /Trash in order to try, again; but I sent my internal /home/user folder, instead. To add to the tragedy, I panicked and cancelled the move to /Trash. Now, all that I can find in /home is the partial /home/user that I attempted to move from the external harddrive. I fear that I have lost the folder for good and that is very bad.

I, hereby, nominate myself for stupid user of the millenium.

I have found info on recovering lost partitions, but nothing that addresses my idiotic mistake (nothing is in lost+found). Is there a way to recover a lost folder that did not make it to /Trash or am I just plain out of luck?

I wish to extend my humble gratitude to all who may consider this most regrettable dilemna.

---

### Post by jamesisin on 2013-07-11
Can you just restore anything that happens to be in the trash?

---

### Post by alan9800 on 2013-07-11
you might try to run the following command```
restore-trash *
```in a Terminal window; see [http://manpages.ubuntu.com/manpages/precise/man1/restore-trash.1.html](http://manpages.ubuntu.com/manpages/precise/man1/restore-trash.1.html).

---

### Post by LinuxNubian on 2013-07-11
Thank you, both, for responding. I forgot to mention that "user" (actually it was "luke") was root and the only user w/sudo privies, so I had to use chroot to get root w/: 
root@r2d2$ adduser help sudo 

Unfortunately, nothing is found in /Trash & restore-trash * seemed to only look for files in the current directory so I made a /home/luke directory, but no love:

help@r2d2:~$ restore-trash *
No files trashed from current dir ('/home/help')
help@r2d2:~$ cd /home/luke
bash: cd: /home/luke: No such file or directory
help@r2d2:~$ mkdir /home/luke
mkdir: cannot create directory `/home/luke': Permission denied
help@r2d2:~$ sudo mkdir /home/luke
help@r2d2:~$ cd /home/luke
help@r2d2:/home/luke$ restore-trash *
No files trashed from current dir ('/home/luke')
help@r2d2:/home/luke$ restore-trash luke
No files trashed from current dir ('/home/luke')

Btw, the /home/luke folder was 100GB.

I am looking into scalpel, now that I am able to execute commands as root, but it's gonna take some time to get familiar with it; the scalpel.conf is a challenge. I hope there is a simpler way to recover lost folders.

Thank you, again, for responding...I lost a bunch of my sister's files & she's gonna kill me, if she finds out!

---

### Post by Azdour on 2013-07-11
Hi,

Have you checked in roots trash for your files - /root/.local/share/Trash/files?

---

### Post by oldos2er on 2013-07-11
> **LinuxNubian said:**
> I tried to move a /home/user folder from an external harddrive to my internal /home folder running Xubuntu 12.04. 

Did you move files in the terminal, or graphically? If you use the terminal, **history** should show the exact command you used, and if you post it here it should be easy to create a "reverse" command to undo the damage.

I don't understand when you refer to /Trash, did you create a folder named Trash in the root folder / ? Your user's trash folder by default is located in /home/user/.local/share/Trash/

---

### Post by LinuxNubian on 2013-07-11
> **Azdour said:**
> Hi,

Have you checked in roots trash for your files - /root/.local/share/Trash/files?

BINGO! Thank you! That's exactly where it went. For the record, I had to check Files=>Show Hidden Files to find it with nautilus, which is what I used to delete the folder. 

I copied the misplaced file back into /home & I can't login to the 'luke' profile, but I can live with the new user profile...really just wanted the files back.

Thank you, again, for the help everyone.:) I was really worried that interupting the Send To Trash process might have been fatal to it's contents.

---

### Post by VMC on 2013-07-12
LOL. I have to admit that your first post made my day. Not at you expense, but I was laughing because I have all been there many times. I have done even more unbelievable stunts.

Regarding 'luke'. You can use either root or sudo to change luke's password, unless or course your not 'luke'. Here's a [link]("http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password") that may help luke :)

---

### Post by alphaamanitin on 2013-07-12
> **VMC said:**
> LOL. I have to admit that your first post made my day. Not at you expense, but I was laughing because I have all been there many times. I have done even more unbelievable stunts.

Regarding 'luke'. You can use either root or sudo to change luke's password, unless or course your not 'luke'. Here's a [link]("http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password") that may help luke :)

I once went to delete a lib/ of a program.  Meant to do ```
rm -rvf lib/
```I accidentally put in ```
rm -rvf /lib/
```

It was pretty dishearting watching everything fly through the command line on its way to extinction.

~AlphaA

---

### Post by alan9800 on 2013-07-13
just a tip, that might seem silly but it isn't: remember to always use```
rm -i <what you wish to delete>
```so you're able to see what is going to be deleted before it's removed from your HD.

---

