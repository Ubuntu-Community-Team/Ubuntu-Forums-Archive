---
title: "What are the default folder permissions for the home and user folders?"
date: 2014-11-05
forum: General Help
---

### Post by nickjanoyan on 2014-11-05
I recently installed Plex and after looking around for some tutorials I was able to get it to read my video files, but I had to create a Plex folder that I put in /home and adjust the permissions. I didn't put it in my regular video folder because Plex still can't read from that. It occurred to me today that maybe the reason Plex can't access my files in my user folder is because it doesn't have the permissions for that folder so I changed the permissions for both the home and my username folder and imported my music library. Everything worked fine until there was a kernel panic after browsing through my music library while playing a song. I don't know if this is a bug or because I messed with the permissions, but I removed my music library from Plex and I would like to restore the folders back to their default permissions. This is what I did before to change the permissions so Plex would work.

```
[COLOR=#000000]sudo chown enigma[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]plex [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]R[/COLOR] /home
``` (enigma is my username)

```
sudo chmod 770 -R /home
```

Then I did the same for my user (enigma) folder

```
[COLOR=#000000]sudo chown enigma[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]plex [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]R[/COLOR] /home/enigma
```

```
sudo chmod 770 -R /home/enigma
```

As I mentioned above, I just want to restore the folder permissions to their default values, so if someone could tell me what to type in the terminal to do that, I would really appreciate it.

---

### Post by Impavidus on 2014-11-05
For the /home directory and your own home directory it would be```
sudo chown root:root /home
sudo chmod 755 /home
#I think you don't really need sudo for these two
sudo chown enigma:enigma /home/enigma
sudo chmod 755 /home/enigma
#Finally the owner of your own files
chown -R enigma:enigma /home/enigma
```
The contents of your home directory are a bit more complicated, and you did a recursive chmod so now everything has the same permissions. Best practice is to have execute permissions on your directories, but not on your files, except for your trusted executables.```
drwxrwxr-x directory
-rw-rw-r-- ordinary file
-rwxr-xr-x executable file
```Group permissions don't matter very much most of the time. Someone may come up with a nice command to fix this.

---

### Post by nickjanoyan on 2014-11-05
I don't know if this is important, but after I ran the last command, it showed this.
```
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/b/b9d1b610.jpg’: Input/output errorchown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/8/8e5e354d.jpg’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/a/ade0a421.jpg’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/0/0bef139d.png’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/7/78225774.jpg’: Input/output error
```
Other then that error message, it seems like it worked. I have a question though. 
> The contents of your home directory are a bit more complicated, and you did a recursive chmod so now everything has the same permissions. Best practice is to have execute permissions on your directories, but not on your files, except for your trusted executables.
I didn't quite understand what you said. Did the commands you listed fix that or are all my files executable and if so, is that dangerous? Also do you think it messed up any configuration files in my user folder that would affect my programs? I want to make sure I didn't break something.

---

### Post by Impavidus on 2014-11-06
> **nickjanoyan said:**
> 
I didn't quite understand what you said. Did the commands you listed fix  that or are all my files executable and if so, is that dangerous? Also  do you think it messed up any configuration files in my user folder that  would affect my programs? I want to make sure I didn't break  something.
No, those commands didn't fix the permissions on your files in your home directory. Having execute permissions can be dangerous if you already had malware, that now has execute permissions, but that is not very likely (although certainly possible). Some programs may also get confused because files don't have the correct permissions now – speaking of which, these two might be important:```
chmod 600 .Xauthority
chmod 600 .ICEauthority
```Someone may come up with a nice command to remove execute permissions from all files, but not the directories. There are no executable files in your home directory unless you put them there yourself, so you should know them. Directories need execute permissions, else you can't access their contents.
> I don't know if this is important, but after I ran the last command, it showed this.
```
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/b/b9d1b610.jpg’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/8/8e5e354d.jpg’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/a/ade0a421.jpg’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/0/0bef139d.png’: Input/output error
chown: changing ownership of ‘/home/enigma/.plexht/userdata/Thumbnails/7/78225774.jpg’: Input/output error
```
Other then that error message, it seems like it worked. I have a question though.
That suggests a totally different cause for your original plex issue. File system I/O errors often indicate a faulty hard drive, like a bad sector in your inode table. Do you have backups? If not, make them now. Then check the health of your hard drive.

---

### Post by oldfred on 2014-11-06
I use these for my data partitions.

 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

      
 Seems like a better way as you have more control over what is executable. See post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

I have also done this to remove some executable bits.

 Removed executable
fred@fred-Precise:~$ sudo chmod -R -x ~/Documents/*
But folders have to have executable set
fred@fred-Precise:~$ sudo chmod -R a+rwX,o-w ~/Documents

---

### Post by nickjanoyan on 2014-11-06
I backed up my home directory via SSH using Ubuntu's default backup program a couple days ago. If it's potentially dangerous then I should probably do a full restore. Also, I noticed my hard drive is close to failing which is why I've been making backups. I don't know how much longer my hard drive is going to last, so I'll have to buy a new one when I get some money.

---

