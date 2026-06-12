---
title: "I accedently added extra file extensions to every file in my home folder"
date: 2007-10-10
forum: General Help
---

### Post by onesojourner on 2007-10-10
This is from another thread. I solved one problem and created a bigger one. I was trying to ad some file extensions to a folder. Now I have that file extensions (.smc) on every single file in my home directory. It really screwed up a few programs including FF.  I ran the code   rename 's/.smc/\ /g' *

here is what I get with that command

Unknown option: {
Unknown option: m
Unknown option: i
Unknown option: i
Unknown option: o
Unknown option: a
Unknown option: .
Unknown option: o
Unknown option: r
Unknown option: g
Unknown option: }
Unknown option: bbl.mp3.smc
Usage: rename [-v] [-n] [-f] perlexpr [filenames]

all the files still have the .smc extension on them.

---

### Post by Old *ix Geek on 2007-10-10
I'm not sure I'm clear on how the files are named now.  Would you post the results of **ls** please?

---

### Post by onesojourner on 2007-10-10
I am at work now but I can do it when I get home. I can give you an example of how the files are named though.

I have a video on my desktop for example that should be named dexter.mov - now it is dexter.mov.smc I have what used to be dogtalktheradioshow.mp3 that is now dogtalktheradioshow.mp3.smc . basically every file has an extra .smc at the end. The problem seems to go for everything in my home folder at the moment.

---

### Post by bodhi.zazen on 2007-10-10
> bodhi@VirtualUbuntu:~/test$ touch dexter.mov.smc
bodhi@VirtualUbuntu:~/test$ touch dogtalktheradioshow.mp3.smc
bodhi@VirtualUbuntu:~/test$ ls
[color=red]dogtalktheradioshow.mp3.smc  dexter.mov.smc[/color]

bodhi@VirtualUbuntu:~/test$[color=blue]**rename 's/.smc/\ /g' ***[/color]
bodhi@VirtualUbuntu:~/test$ ls
[color=blue]dexter.mov   dogtalktheradioshow.mp3[/color]

Be sure you do not have a typo in that command

EDIT: Sorry, that command will add a space at the end of the file names.

USE THIS:

```
for i in *.smc;do mv ${i} ${i%%.smc*};done
```

---

### Post by bashologist on 2007-10-10
Why would you add a space to the end of the filename, and why would you not use an anchor? This should fix it.
```
rename 's/.smc$//' *
```
If you did it to your hidden filenames too then you could use one of these.
```
find -mindepth 1 -maxdepth 1 -exec rename 's/.smc$//' {} +
rename 's/.smc$//' * .!(.|)
```

---

### Post by bodhi.zazen on 2007-10-10
> **bashologist said:**
> Why would you add a space to the end of the filename, and why would you not use an anchor? This should fix it.
```
rename 's/.smc$//' *
```

Thanks , that works as well. My mistake, I thought I was escaping the space and inserting a null.

Please, what is an anchor (I assume that refers to the $)?

EDIT, my updated command works for . files as well :)

---

### Post by bashologist on 2007-10-10
You forgot to double quote the variables in your for loop. Hehe. n_n
> **bodhi.zazen said:**
> Thanks , that works as well. My mistake, I thought I was escaping the space and inserting a null.
Spaces don't need to be escaped in perl unless you're using x, and wasn't onesojourner the first one to escape it?
> **bodhi.zazen said:**
> Please, what is an anchor (I assume that refers to the $)?
An anchor is commonly used to match the end or beginning of a string, although it has other uses like matching beginnings of words I think.

---

### Post by bodhi.zazen on 2007-10-10
> **bashologist said:**
> You forgot to double quote the variables in your for loop. Hehe. n_n

Spaces don't need to be escaped in perl unless you're using x, and wasn't onesojourner the first one to escape it?

An anchor is commonly used to match the end or beginning of a string, although it has other uses like matching beginnings of words I think.

Once again, thanks.

My mistake again it seems, I did not think I needed to " the variables as I used the {} to pattern match.

---

### Post by onesojourner on 2007-10-10
ok I tried some of these and nothing seems to be working. here is the output 

peter@peter-desktop:~$ for i in *.smc;do mv ${i} ${i%%.smc*};done
mv: cannot stat `*.smc': No such file or directory
mv: cannot move `drive' to `XBMC/drive': Permission denied
peter@peter-desktop:~$ find -mindepth 1 -maxdepth 1 -exec rename 's/.smc$//' {} +
./.Xauthority.smc not renamed: ./.Xauthority already exists
./.sudo_as_admin_successful.smc not renamed: ./.sudo_as_admin_successful already exists
./.bash_history.smc not renamed: ./.bash_history already exists
./.gksu.lock.smc not renamed: ./.gksu.lock already exists
./.ICEauthority.smc not renamed: ./.ICEauthority already exists
./.mcoprc.smc not renamed: ./.mcoprc already exists
./.gtkrc-1.2-gnome2.smc not renamed: ./.gtkrc-1.2-gnome2 already exists
./.xsession-errors.smc not renamed: ./.xsession-errors already exists
./.lesshst.smc not renamed: ./.lesshst already exists
./.dmrc.smc not renamed: ./.dmrc already exists
./.esd_auth.smc not renamed: ./.esd_auth already exists
./.recently-used.xbel.smc not renamed: ./.recently-used.xbel already exists
peter@peter-desktop:~$ for i in *.smc;do mv ${i} ${i%%.smc*};done
mv: cannot stat `*.smc': No such file or directory
mv: cannot move `Desktop' to a subdirectory of itself, `XBMC/Desktop'
mv: cannot move `drive' to `XBMC/drive': Permission denied
peter@peter-desktop:~$ sudo for i in *.smc;do mv ${i} ${i%%.smc*};done
bash: syntax error near unexpected token `do'
peter@peter-desktop:~$

---

### Post by onesojourner on 2007-10-10
oh and I do have .smc at the end of all my hidden files in my home folder too.

---

### Post by bodhi.zazen on 2007-10-10
After running all those commands, what do we have ?

---

### Post by onesojourner on 2007-10-10
#1

peter@peter-desktop:~$ rename 's/.smc/\ /g' *
peter@peter-desktop:~$ 


#2

peter@peter-desktop:~/Desktop$ ls
peter@peter-desktop:~/Desktop$ find -mindepth 1 -maxdepth 1 -exec rename 's/.smc$//' {} +
peter@peter-desktop:~/Desktop$ rename 's/.smc$//' * .!(.|)
bash: !: event not found
peter@peter-desktop:~/Desktop$ 

#3

peter@peter-desktop:~$ rename 's/.smc$//' *
peter@peter-desktop:~$ 

#4

peter@peter-desktop:~$ find -mindepth 1 -maxdepth 1 -exec rename 's/.smc$//' {} +
./.Xauthority.smc not renamed: ./.Xauthority already exists
./.sudo_as_admin_successful.smc not renamed: ./.sudo_as_admin_successful already exists
./.bash_history.smc not renamed: ./.bash_history already exists
./.gksu.lock.smc not renamed: ./.gksu.lock already exists
./.ICEauthority.smc not renamed: ./.ICEauthority already exists
./.mcoprc.smc not renamed: ./.mcoprc already exists
./.gtkrc-1.2-gnome2.smc not renamed: ./.gtkrc-1.2-gnome2 already exists
./.xsession-errors.smc not renamed: ./.xsession-errors already exists
./.lesshst.smc not renamed: ./.lesshst already exists
./.dmrc.smc not renamed: ./.dmrc already exists
./.esd_auth.smc not renamed: ./.esd_auth already exists
./.recently-used.xbel.smc not renamed: ./.recently-used.xbel already exists


no .smc has been removed as of yet.

---

### Post by onesojourner on 2007-10-10
now every file on my desktop seems to be gone??

---

### Post by bodhi.zazen on 2007-10-10
> **onesojourner said:**
> peter@peter-desktop:~$ find -mindepth 1 -maxdepth 1 -exec rename 's/.smc$//' {} +
./.Xauthority.smc not renamed: ./.Xauthority already exists
./.sudo_as_admin_successful.smc not renamed: ./.sudo_as_admin_successful already exists
./.bash_history.smc not renamed: ./.bash_history already exists
./.gksu.lock.smc not renamed: ./.gksu.lock already exists
./.ICEauthority.smc not renamed: ./.ICEauthority already exists
./.mcoprc.smc not renamed: ./.mcoprc already exists
./.gtkrc-1.2-gnome2.smc not renamed: ./.gtkrc-1.2-gnome2 already exists
./.xsession-errors.smc not renamed: ./.xsession-errors already exists
./.lesshst.smc not renamed: ./.lesshst already exists
./.dmrc.smc not renamed: ./.dmrc already exists
./.esd_auth.smc not renamed: ./.esd_auth already exists
./.recently-used.xbel.smc not renamed: ./.recently-used.xbel already exists

those *.smc files can likely be deleted. They are config files and were re-generated automagically :)

Also, to run a complex command as root "sudo for i in *.smc;do mv ${i} ${i%%.smc*};done"

You need to :

```
sudo sh -c "sudo for i in *.smc;do mv ${i} ${i%%.smc*};done"
```

* Be careful with that as you can easily do systemic damage ;)

---

### Post by bashologist on 2007-10-10
> **onesojourner said:**
> peter@peter-desktop:~/Desktop$ rename 's/.smc$//' * .!(.|)
bash: !: event not found

[indent]Extglob will make this command work, but it doesn't matter since it'll give you the same results as you got with the find command.
```
shopt -s extglob
rename 's/.smc$//' * .!(.|)
```[/indent]

> **bodhi.zazen said:**
> sudo sh -c "sudo for i in *.smc;do mv ${i} ${i%%.smc*};done"
[indent]Braces do not protect against word splitting. This is what your command would look like fixed.
```
sudo sh -c 'for i in *.smc; do mv "$i" "${i%%.smc*}"; done'
```
[/indent]

> **onesojourner said:**
> now every file on my desktop seems to be gone??
[indent]After the commands everything disappeared? What path are you looking at? What command did you run to get these filenames ending with smc? Can you give the output of "ls -la ~" in a code tag?[/indent]


I'm gonna go to bed for the night. Can't wait to see how this ends! Good luck guys, and goodnight.

---

### Post by bodhi.zazen on 2007-10-10
Thanks, so noted on " "

I needed the asterisk because, in my test runs with variations on *.smc I could not get the proper format without it ...

Now I can not re-create it , so it must have been a problem between chair and keyboard :lolflag:

---

### Post by onesojourner on 2007-10-11
sorry I am not sure how to do a code tag. I will edit this post when I figure it out:

```
peter@peter-desktop:~$ ls -la ~
total 560
drwxr-xr-x 51 peter peter  12288 2007-10-10 17:06 .
drwxr-xr-x  3 root  root    4096 2007-04-17 10:51 ..
-rw-r--r--  1 peter peter    143 2007-05-27 13:13 .audacity
drwxr-xr-x  2 peter root    4096 2007-10-09 17:43 .automatix
drwxr-xr-x 10 peter peter   4096 2007-10-09 17:42 .azureus
-rw-------  1 peter peter   1397 2007-10-10 17:04 .bash_history
-rw-------  1 peter peter   1557 2007-10-08 20:09 .bash_history.smc
-rw-r--r--  1 peter peter    220 2007-04-17 10:51 .bash_logout
-rw-r--r--  1 peter peter   2298 2007-04-17 10:51 .bashrc
drwxr-xr-x  4 peter peter   4096 2007-04-18 10:41 .config
drwx------  2 peter peter   4096 2007-10-09 17:43 .cups
drwxr-xr-x  2 peter peter   4096 2007-10-10 15:40 Desktop
-rw-------  1 peter peter     26 2007-10-09 19:18 .dmrc
-rw-------  1 peter peter     26 2007-04-17 15:56 .dmrc.smc
drwxr-xr-x  2 root  root    4096 2007-08-31 19:41 drive
-rw-------  1 peter peter     16 2007-10-09 19:18 .esd_auth
-rw-------  1 peter peter     16 2007-04-17 15:56 .esd_auth.smc
drwxr-xr-x  7 peter peter   4096 2007-10-09 19:06 .evolution
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:42 .fontconfig
drwx------  4 peter peter   4096 2007-10-09 17:42 .gaim
drwx------  4 peter peter   4096 2007-10-10 07:52 .gconf
drwx------  2 peter peter   4096 2007-10-11 08:17 .gconfd
drwxr-xr-x 21 peter peter   4096 2007-10-09 17:43 .gimp-2.2
-rw-r-----  1 peter peter      0 2007-10-10 17:04 .gksu.lock
-rw-r-----  1 peter peter      0 2007-10-09 16:34 .gksu.lock.smc
drwxr-xr-x  2 peter peter   4096 2007-04-17 20:55 .glchess
drwxr-xr-x  4 peter peter   4096 2007-04-18 13:31 .gnome
drwx------ 14 peter peter   4096 2007-10-09 22:06 .gnome2
drwx------  2 peter peter   4096 2007-04-17 15:56 .gnome2_private
drwx------  3 peter peter   4096 2007-06-29 16:15 .google
drwx------  5 peter peter   4096 2007-10-09 17:42 .googleearth
drwxr-xr-x  2 peter peter   4096 2007-10-09 19:18 .gstreamer-0.10
-rw-r--r--  1 peter peter     87 2007-10-09 19:18 .gtkrc-1.2-gnome2
-rw-r--r--  1 peter peter     87 2007-04-17 15:56 .gtkrc-1.2-gnome2.smc
-rw-------  1 peter peter    173 2007-10-10 07:52 .ICEauthority
-rw-------  1 peter peter   1303 2007-10-09 16:30 .ICEauthority.smc
drwxr-xr-x  2 peter peter   4096 2007-04-18 10:40 .icons
drwxr-xr-x  3 peter peter   4096 2007-04-24 17:11 .java
drwx------  3 peter peter   4096 2007-04-18 12:01 .kde
-rw-r--r--  1 peter peter   2673 2007-08-16 17:12 .kinorc
-rw-------  1 peter peter     35 2007-10-10 17:05 .lesshst
-rw-------  1 peter peter     35 2007-10-09 17:03 .lesshst.smc
drwxr-xr-x  3 peter peter   4096 2007-04-18 09:03 .local
drwx------  3 peter peter   4096 2007-04-18 13:31 .loki
drwx------  3 peter peter   4096 2007-04-18 11:12 .macromedia
-rw-r--r--  1 peter peter   3156 2007-07-09 07:12 .mailcap
drwxr-xr-x  3 peter peter   4096 2007-10-09 20:35 .mcop
-rw-------  1 peter peter     31 2007-10-09 20:35 .mcoprc
-rw-------  1 peter peter     31 2007-04-18 14:00 .mcoprc.smc
drwx------  3 peter peter   4096 2007-04-17 15:56 .metacity
drwx------  3 peter peter   4096 2007-04-17 15:59 .mozilla
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:42 .mplayer
drwxr-xr-x  3 peter peter   4096 2007-10-09 22:06 .nautilus
drwx------  2 peter peter   4096 2007-06-04 20:41 .nero
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:40 .neverball
drwx------  3 peter peter   4096 2007-10-07 20:44 .openoffice.org2
-rw-r--r--  1 peter peter    566 2007-04-17 10:51 .profile
drwxr-xr-x  2 peter peter   4096 2007-10-09 20:29 .qt
-rw-------  1 peter peter  34548 2007-08-14 17:17 .realplayerrc
-rw-------  1 peter peter 138717 2007-10-08 20:32 .recently-used
-rw-r--r--  1 peter peter   1515 2007-10-10 17:06 .recently-used.xbel
-rw-r--r--  1 peter peter  46379 2007-10-08 20:32 .recently-used.xbel.smc
-rw-------  1 root  root    1024 2007-05-03 21:05 .rnd
drwxrwx---  3 peter peter   4096 2007-04-24 16:35 .sane
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:43 .serpentine
-rw-r--r--  1 peter peter      0 2007-10-09 19:06 .sudo_as_admin_successful
-rw-r--r--  1 peter peter      0 2007-04-17 15:57 .sudo_as_admin_successful.smc
drwxr-xr-x  3 peter peter   4096 2007-04-18 10:41 .themes
drwx------  4 peter peter   4096 2007-04-17 16:45 .thumbnails
drwxr-xr-x  3 peter peter   4096 2007-10-09 17:42 .tomboy
-rw-r--r--  1 peter peter   1179 2007-08-15 15:55 .tomboy.log
drwx------  2 peter peter   4096 2007-10-09 18:22 .Trash
drwx------  2 peter peter   4096 2007-10-09 17:42 .tsclient
drwxr-xr-x  2 peter peter   4096 2007-10-10 17:04 .update-manager-core
drwx------  2 peter peter   4096 2007-10-09 17:42 .update-notifier
drwxr-xr-x  3 peter peter   4096 2007-10-09 17:43 .vlc
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:43 .vmware
drwxr-xr-x  2 peter peter   4096 2007-08-15 15:55 .wapi
-rw-------  1 peter peter    124 2007-10-10 07:52 .Xauthority
-rw-------  1 peter peter    124 2007-10-09 16:30 .Xauthority.smc
drwxrwxrwx 11 peter peter   4096 2007-10-10 15:39 XBMC
drwxr-xr-x  2 peter peter   4096 2007-10-09 18:22 .xine
-rw-r--r--  1 peter peter   3127 2007-10-10 22:53 .xsession-errors
-rw-r--r--  1 peter peter  20333 2007-10-09 19:04 .xsession-errors.smc
drwxr-xr-x  2 peter peter   4096 2007-10-09 17:42 .zsnes
peter@peter-desktop:~$
```

---

### Post by bodhi.zazen on 2007-10-11
Looks like problem solved. Any remaining files with .smc can be either left alone or deleted.

FYI : like this :

[noparse]```
<insert_text>
```[/noparse]

---

### Post by onesojourner on 2007-10-11
all that has happened is all the files on my desktop were deleted. The same goes for the files in the home folder. I really need to find those. All the files in the hidden files in my home folder are still .smc.

---

### Post by onesojourner on 2007-10-11
I think that sounded a little whiny sorry. I appreciate every one who is trying to help me figure this out.

---

### Post by onesojourner on 2007-10-12
this seems to effect every program in my home directory.

---

### Post by bodhi.zazen on 2007-10-12
what command did you use to create this situation ?

---

### Post by onesojourner on 2007-10-12
honestly I am not sure. it was one of the commands you or some one else gave me in the first thread. I just kept trying them until one worked.

---

