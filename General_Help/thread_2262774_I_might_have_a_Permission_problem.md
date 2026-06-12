---
title: "I might have a Permission problem?"
date: 2015-01-27
forum: General Help
---

### Post by moteprime on 2015-01-27
My gedit and 'Image Viewer' can't save. Save and 'Save as' are greyed out, and neither programs offer to save if i make changes til the files i opened.
It happens everywhere, incl. Home directory, sub directories, USB drives and with files I make and changes permission to in other users directories.
The strange thing is that the same files that can't get saved for example with gedit, can be saved if i use 'LO Writer' in stead. Images that 'Image Viewer' will not save. can get saved by Shotwell.
I am the owner of all files, and have Read&Write permission for both user and group.
Other user profiles does not have this problem.

I hope i do not have to reinstall the hole system.

---

### Post by kc1di on 2015-01-27
Check the permission of the program and make sure usr group has permission to read and write.

---

### Post by moteprime on 2015-01-27
Thank you for your reply.
How can i check the programs permissions?

---

### Post by steeldriver on 2015-01-27
Hmm that's a bit of a puzzle - can you provide the following outputs please?

```

id

ls -ld $HOME

ls -l $(which gedit)

find $HOME \( ! -user "$(id -u)" -o ! -group "$(id -g)" \) -ls

```

---

### Post by moteprime on 2015-01-27
```
mads@ThinkPad:~$ id
uid=1000(mads) gid=1000(mads) groups=1000(mads),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)

mads@ThinkPad:~$ ls -ld $HOME
drwxrwx--- 47 mads mads 4096 jan 27 13:03 /home/mads

mads@ThinkPad:~$ ls -l $(which gedit)
-rwxr-xr-x 1 root root 581360 mar 27  2014 /usr/bin/gedit

mads@ThinkPad:~$ find $HOME \( ! -user "$(id -u)" -o ! -group "$(id -g)" \) -ls
16384415    4 -rw-r--r--   1 root     root          277 sep 15 20:12 /home/mads/.config/Trolltech.conf
16384412    4 drwx------   2 root     root         4096 sep 15 20:12 /home/mads/.gvfs
find: `/home/mads/.gvfs': Permission denied
16384422    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Bearded
16384423    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Bearded/.share_info
16384431    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Hedvig\ og\ Far
16384432    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Hedvig\ og\ Far/.share_info
16384428    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Claus
16384429    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Claus/.share_info
16384333    4 drwxr-xr-x   3 root     root         4096 sep 15 20:19 /home/mads/.local/share/Trash/expunged/2642395596/Backup
16384186    4 drwxr-xr-x   2 root     root         4096 sep 15 20:19 /home/mads/.local/share/Trash/expunged/2642395596/Backup/Link\ to\ Documents
16384413    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache
16384425 174084 -rwx------   1 root     root     178257920 sep 15 20:22 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/61325aca22b833817d70ec8bfcee2b60
16384459 51188 -rwx------   1 root     root     52410507 sep 15 20:19 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/987344d2149ca1527244ce54b2619522
16384462  124 -rwx------   1 root     root       124009 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/afdd622e58149ade9ada90a7d8fecc1d
16384426 123908 -rwx------   1 root     root     126877696 sep 15 20:22 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/581b73d017fadc1fe32139a499a79504
16384461   80 -rwx------   1 root     root        78019 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/7d78e7bdd6ec81abfad56391605f3861
16384427  112 -rwx------   1 root     root       112640 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/.copy.cache/2203406366c648ad8427814651086868
16384454    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/m_e_h
16384455    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/m_e_h/.share_info
16384438    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Mette
16384439    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Mette/.share_info
16384452    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/m.e.h
16384453    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/m.e.h/.share_info
16384442    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Palle
16384443    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Palle/.share_info
16384448    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Th\303\270ger\ og\ Far
16384449    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Th\303\270ger\ og\ Far/.share_info
16384436    4 drwxr-xr-x   2 root     root         4096 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Mads
16384437    4 -rwx------   1 root     root            8 sep 15 20:15 /home/mads/.local/share/Trash/expunged/2642395596/Mads/.share_info
16384410    4 drwx------   2 root     root         4096 jan 22 18:16 /home/mads/.cache/dconf
find: `/home/mads/.cache/dconf': Permission denied
16384066    4 drwx------   3 root     root         4096 sep 15 20:12 /home/mads/.dbus
find: `/home/mads/.dbus': Permission denied

```

---

### Post by kc1di on 2015-01-27
[Here i]("https://help.ubuntu.com/community/FilePermissions")s the official permissions document from ubuntu. 

simpler way is to use the terminal and issue one of the following commands```
ls -l <filename> 
``` or ```
stat <filename>
```

I'm using mate at the moment and the image viewer is eye of mate  so the command would be 
```
ls -l /usr/bin/eom or stat /usr/bin/eom
```

Good Luck

---

### Post by kc1di on 2015-01-27
[Here i]("https://help.ubuntu.com/community/FilePermissions")s the official permissions document from ubuntu. 

simpler way is to use the terminal and issue one of the following commands```
ls -l <filename> 
``` or ```
stat <filename>
```

I'm using mate at the moment and the image viewer is eye of mate  so the command would be 
```
ls -l /usr/bin/eom or stat /usr/bin/eom
```

the output look like this:
> $ stat /usr/bin/eom
  File: ‘/usr/bin/eom’
  Size: 557152    	Blocks: 1096       IO Block: 4096   regular file
Device: 806h/2054d	Inode: 1046474     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2015-01-27 07:20:10.431337087 -0500
Modify: 2014-07-22 19:00:25.000000000 -0400
Change: 2015-01-26 06:20:03.286744242 -0500
 Birth: -


this shows that root is the owner and that root can read, write and exicute the file and that usr group can exicute and read but not write. 


Good Luck

---

### Post by moteprime on 2015-01-27
Thank you.
I have some understading about how the filestystem permissions work.
But i'm really sure what you suggest i do. The permissions on the gedit file in /usr/bin are owner: root,access Read&Write, grp root: RO others: RO

At the time this problem started, i set Nautilus to ask to run text files or view them, But set i back to defaul, open as text.
Also i installed encryption for the 'Private' folder. Cant remember the name of it, but it's default Ubuntu stuff.

Are the permission for gedit wrong?
Please help me.

---

### Post by steeldriver on 2015-01-27
So it looks like you have been running stuff that you shouldn't as root (or using sudo) - you shouldn't have all those root-owned files in $HOME, or a root-owned .gvfs mount

Probably the biggest red flag for your current issue is the root-owned .dbus directory, since gedit uses dbus under the hood

Let's see if simply taking back ownership of everything will do the trick:

```

sudo chown -R mads:mads /home/mads

```

---

### Post by moteprime on 2015-01-27
When i was messing with the encryption program "ecryptfs-utils", i did it in a SU terminal. SO probably somewhere along some system things got root as owner?

Taking ownership did not fix it.

The other user a have in my Ubuntu does not have this problem, It's also and Administrative user.

---

### Post by steeldriver on 2015-01-27
Did you log out and back in after taking back ownership? that may be necessary in order to sort out the dbus session-bus

---

### Post by moteprime on 2015-01-27
I restarted after it did not work, but unfortunately it did not make any difference.

---

