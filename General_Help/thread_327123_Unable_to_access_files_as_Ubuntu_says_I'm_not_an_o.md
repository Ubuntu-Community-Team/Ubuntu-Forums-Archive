---
title: "Unable to access files as Ubuntu says I'm not an owner."
date: 2006-12-28
forum: General Help
---

### Post by pockey on 2006-12-28
I'm the only user on my system, and I can use sudo commands, but when I try to change a file it won't let me because it's write-protected. So, I went to change that property but it says I'm not an owner so everything is greyed.

Is there a way I can get Ubuntu to let me edit these files? I appreciate any help!

---

### Post by reiki on 2006-12-28
sudo gedit filename

---

### Post by pockey on 2006-12-28
So the only way to do this is through the terminal?

---

### Post by melancholeric on 2006-12-28
sudo nautilus will start nautilus with root privileges. Be careful with that.

---

### Post by pockey on 2006-12-28
Ahh, sudo nautilus was what I was looking for. Thanks to you both!

---

### Post by ashmew2 on 2006-12-31
Hey Melancholeric , why do you say Be careful when using sudo nautilus ?
Thanks

---

### Post by adamonline on 2006-12-31
> **melancholeric said:**
> sudo nautilus will start nautilus with root privileges. Be careful with that.

Ahhh, I theoriized that just earlier today!  Good to have it confirmed... I'm so used to the CLI now tho... :)

Ashmew, using SUDO allows you to act as the root user to initiate commands.  "They" say that it's bad to be logged in as root, because one wrong move and you could easily damage something, not to mention it can leave you open to rootkits (grossly read: viruses)...  It sounds like a lot of FUD to me, and I feel like getting this machine up to par over the last couple weeks I've practically LIVED on sudo! ... But really, this is just a quick answer to hold you over until someone with a GOOD answer comes by ;)  I believe it's just a matter of security, from a local *and* remote standpoint.  It allows you to change stuff that's important enough to be protected in the first place.

---

### Post by HadroLepton on 2006-12-31
please don't abuse the sudo powers (or root powers for that matter). it is the main reason why windows is so insecure, but that is another story...

sudo nautilus is dangerous because you start nautilus with root powers. that means you can delete move or rename any file you like, including system critical files. it also means that any new files or folders you create will belong to root, even it is in your home, and that means that you cannot access them when starting nautilus without sudo.

please also read this thread
[http://www.ubuntuforums.org/showthread.php?t=315177&highlight=sudo+abuse](http://www.ubuntuforums.org/showthread.php?t=315177&highlight=sudo+abuse)

---

### Post by ashmew2 on 2007-01-01
lolz :P
Thanks for the answers , pretty satisfying :D

---

### Post by moshuptrail on 2007-01-01
If you DO get files that you think YOU should own, for example in your home directory, but they are owned by root, then do the following:

sudo chown <yourname> <filename>
sudo chgrp <yourname> <filename>

This changes owner and group on each file named.
you can use wildcards (*) in <filename> to do a whole bunch at a time, 

But be careful with this too!  I suggest only in your home directory (or sub-directory)

---

### Post by DnasTheGreat on 2007-01-01
Be careful is an understatement. :)

I cannot think of any files that a normal user should ever own that are not in either /tmp  or your home directory. And /tmp you should never have to fuss with.


I think a quick primer might be in order, since it seems a couple in this thread come from a Run-As-Admin mindset from Windows. (Not a bad thing. Many of us had to start with that junk sometime in our lives.) This stuff isn't really required to know (you shouldn't really have to mess with it much.... In Ubuntu, I think I've yet to play with file permissions manually) but it's good to have an overall picture, so maybe skim over the following.

UNIX (and thus Linux as well) is designed to be a multi-user system. (Contrasting to Windows, which, before NT, was solely single user... they've been trying to get it closer to a multi-user system... XP hasn't quite gotten decent defaults yet... don't know if Vista's any good.) A system has several users, one for each human user which accesses the system, some for daemons that should have lower permissions (security), other minor ones you should care about, and most importantly, root.

root is the superuser. It has total control over every part of the system. Permissions more-or-less do not apply.

Each file has an owner, and each process has an owner. [SIZE="1"](Well, actually there's an effective user id and a real user id, but you don't need to know about that. :))[/SIZE] A processes owner limits what it can do with the files.

Each file also has a set of permissions. I'll gloss over the groups bit to avoid complication, but basically, there are a combination of read/write/execute permissions for each file for the owner of the file, and for others.

The ownership and permissions info of a file can be viewed in the Permissions tab of the file properties in Nautilus. (Or ls -l, which is cooler. ;))

Files in your home directory usually are owned by you and have read/write permissions for you and read permissions for everyone else. System files are usually owned by root.

As a result, only root can mess with the system itself. If you need to act as root, you must escalate your privilegdes. This, in Ubuntu, is done with the sudo command.

This has two advantages.
1. If your system is truly multiuser, a normal user cannot do anything that messes up the system or anything that effects anyone other than himself. (Ideally anyway. He can, of course, hog all the CPU or disk space, which may be subject to a quota system, but meh.)
2. You, as a user, develop a discipline not to mess with system files on a daily basis, unless necessary.

This is useful for many reasons. First, you're less likely to accidentally break something. Second, no application is perfect. Some may have security holes. Sometimes these holes may be compromised. If you are compromised with a normal application, the damage is limited to your files. Bad, yes, but nowhere near as bad as it spreading to the entire system. (As is common in Windows)

If a root-owned application is compromised, all bets are off. (This is also why, for example, the apache webserver is run under its own user, etc. To contain possible damage.)

As to why running sudo nautilus isn't very good, it makes it very easy to drop this discipline. Also, the more complicated an app, the more likely it is to be buggy and the easier it is to compromise. The GNOME programs are rather complex. And any process spawned by another inherits its priviledges. So any program you run from the sudo'ed nautilus is run as root... this isn't particularly good. :) And nautilus is rather complex and it can connect to the Internet, etc.

Also, gedit, for example, is more complex than it's command-line counterparts like nano or vim, since it has to open a window, it hooks into the GNOME libs, etc. This is why a lot of administration is done in the terminal. (Well, also because admins are often computers-y and appreciate the speed and power the terminal gives you.) But you shouldn't have to learn a command-line editor unless you want to. gedit should be fine.

But I do reccommend you setup the Edit as root menu in nautilus instead of running nautilus itself as root. (I don't know why Ubuntu removed this... I think plain GNOME 2.16 has it? Probably because you don't want to do this with things like audio files... might want to consider replacing gnome-open with gedit then.) [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_open_files_as_root_user_via_right_click](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_open_files_as_root_user_via_right_click) This is similar to the sudo gedit, etc., but it's with a GUI. This way your nautilus process doesn't gain the priviledges and only the desired app does.

Anyways... welcome to Linux! I hope you enjoy it.

(Wow, this post ended up being long.)

---

### Post by xardas on 2007-01-02
Good post man! I'm getting this "read only file system" error. Everything in my home directory seems to be not changeable. I cant change the file permissions either through the sudo chown command. The read only file system error crops up again. I'm using edgy on my laptop and my gnome is also very very slow. Any suggestions?

---

### Post by adamonline on 2007-01-02
Nicely said, DnasTheGreat!

---

