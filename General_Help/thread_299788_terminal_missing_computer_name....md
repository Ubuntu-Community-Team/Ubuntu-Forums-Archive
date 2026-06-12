---
title: "terminal missing computer name..."
date: 2006-11-14
forum: General Help
---

### Post by ephman on 2006-11-14
hello,

this is really strange for some reason when i go into a terminal instead of getting ephman@wintermute:, i get ephman@(none):  same thing for root i get root@(none):  this just recently started and i can't seem to figure out what it could be?  is anybody else noticing this?  i do not believe i've changed anything for my system...  any help would be really appreciated.  thank you.

ephman

---

### Post by ciscosurfer on 2006-11-14
Check your .bashrc file under ~/.bashrc and go to the PS1= line.

You can modify this line to your liking.

---

### Post by scxtt on 2006-11-14
and look at:

[indent]/etc/hosts
/etc/hostname[/indent]

---

### Post by ciscosurfer on 2006-11-14
> **scxtt said:**
> and look at:
[INDENT]/etc/hosts
/etc/hostname[/INDENT]Yeah, that'd be a good place to start, to even see if your hostname is set.  Good suggestion, scxtt.

---

### Post by ephman on 2006-11-14
hi,

this is the PS1= line.  where in this line do i put my computer name?

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

also both /etc/hosts /etc/hostname are empty?  how would i now set the hostname?

thank you so much,

ephman

---

### Post by LenzM on 2006-11-14
/etc/hostname should contain the name of your computer as the only contents of the file

---

### Post by ephman on 2006-11-14
:)  thank you people very much.  i added my hostname into that file and life is now good.  no idea how that file could have been played with.  cool learned something great!

thanks,
ephman

---

### Post by CatKiller on 2006-11-14
Unless you changed your /etc/hosts file as well as your /etc/hostname file, you could now have problems when you try to run any programs that require root permissions.

If this turns out to be the case, you will have the problem that you need root permissions to fix the problem, but the problem stops you getting root permissions.

Not to worry though - if you restart your computer and press Esc to get the GRUB menu, you can enter the recovery console. This will have you logged in as root without having to worry about the /etc/hosts file being broken.

I believe that the file should start ```
127.0.0.1 localhost *computername*
``` where *computername* is the name specified in /etc/hostname.

---

### Post by syxbit on 2006-11-14
so to change your computer name you just change it in those 2 places and that's it?
is there a way to do this graphically? (just curious)

---

### Post by CatKiller on 2006-11-14
> **syxbit said:**
> so to change your computer name you just change it in those 2 places and that's it?

It's scary enough that you have to change it in two places at once - you think there should be **more**? :mrgreen: 

> is there a way to do this graphically? (just curious)

System -> Administration -> Networking -> General -> Host name.

---

### Post by scxtt on 2006-11-14
there's also the **hostname** command,  but i don't know if it's persistent ...

---

### Post by ephman on 2006-11-15
when i was doing some research on this i found that the hostname command is not persistant.

even if you change the hostname in the via the gui, you still need to add it to the /etc/hosts with 127.0.0.1 localhost hostname

thanks,
ephman.

---

