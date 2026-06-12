---
title: "&quot;GDM could not write&quot; error after messing with partitions"
date: 2007-04-10
forum: General Help
---

### Post by rapper97 on 2007-04-10
Alright, I've looked around at some of the other "GDM could not write to your authorization file" threads, but none seem to cover this, and I thought you might need a little backstory. So I apologize if this has been answered before; if so, by all means, please point me in the right direction.

I had two ext3 partitions, hda3, which was / (root, where it booted from) and hda4, which was a backup of some old files. My plan was to copy the files over to hda3 and then erase the hda4 partition, "growing" hda3 into its place. I did that, using Gparted off the live CD, then rebooted. When booting, I would then get an error which I didn't really understand, but I inferred Linux was looking for hda4; it would then kick me back to a root prompt. My friend told me to edit fstab, so I just erased the line about hda4. Now I can get to the Gnome login screen, but when I attempt to log in, it gives me the message
"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

I click OK (because I have no choice) and then get to "GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator"

After I expanded the hda3 partition to take up the space of the erstwhile hda4, Gparted showed hda3 as being pretty full, as if the files from hda4 were still there, even though the partition wasn't. I didn't think anything of it at the time, but now think those files are taking up space - even though there's no more hda4 and, as far as I can see, the files themselves aren't there. How do I get back into the GUI and put this behind me??

---

### Post by rapper97 on 2007-04-10
Also, it just occurred to me that I mounted the drive last night through the live CD, and I didn't have the Internet in front of me to double-tjeck commands, so I may have done something stupid with [FONT="monospace"]chmod[/FONT] or [FONT="monospace"]chown[/FONT]? Hmmm.....  :-|

---

### Post by phidia on 2007-04-10
Maybe the simplest thing to do is to create a new user. If that works you can either copy the profile and hidden dot files over to your old user account or just transfer all files to the new user. (Edit: actually it's better if you use the new account to figure out what's wrong with the old one-in ubuntu I believe only the 1st account created can do sudo.)
Check out man adduser.

---

### Post by spankymasterc on 2007-04-10
Had this command happen to me had to reinstall ubuntu lol tried 3 pages of commands none worked and when one worked gave me other error lol 

Sorry for non answer

---

### Post by rapper97 on 2007-04-11
> **phidia said:**
> Maybe the simplest thing to do is to create a new user.
:!:*Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.*
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "vinyl"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
```

So, basically same problem, different error message.

I'm a little bit leery of doing anything from the command line, although I would if I knew what I was doing
although in that case I don't think I'd need a new user

---

### Post by dreadlord_chris on 2007-04-11
This should right you permissions problems. Boot into Recovery Mode, and at the command prompt enter:
```

chown -hR <NAME>:<NAME> /home/<NAME>

```
Replacing <NAME> with your user name. This will change both the *user & group* for all files & folders in your Home folder to your user name & group.

---

### Post by rapper97 on 2007-04-13
Good looking out, Chris. My homie had me do something similar, (without the [FONT="monospace"]-h[/FONT], I think) and that solved the permissions nightmare I'd created, insomuch as I'm only having [the problem the new user I created had]("http://ubuntuforums.org/showthread.php?t=406297/#post2434240"). Now my only problem, I think, is [this]("http://ubuntuforums.org/showthread.php?t=406793")

---

### Post by rapper97 on 2007-04-15
My homie said to show him the results of [FONT="monospace"]fsck /dev/hda3[/FONT]
```
ubuntu@ubuntu:~$ sudo fsck /dev/hda3 
fsck 1.38 (30-Jun-2005) 
e2fsck 1.38 (30-Jun-2005) 
/dev/hda3: clean, 134535/2133728 files, 4005364/4261241 blocks
```

---

