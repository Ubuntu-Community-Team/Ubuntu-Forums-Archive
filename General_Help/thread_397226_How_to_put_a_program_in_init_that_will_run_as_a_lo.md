---
title: "How to put a program in init that will run as a local user?"
date: 2007-03-30
forum: General Help
---

### Post by tymanthius on 2007-03-30
I finally found hellanzb, and I think I'm in love.   :lolflag: 

What I would like to do is start hellanzb at boot in daemon mode (hellanzb -D) so that it's just always running.  But I may need it to run as me, not root, to get the file permissions on the downloads correct.  I'm not sure about that, but I have had other programs that when run as daemon's, or started by root, set the downloaded files as owned by root.  Annoying to have to fix.

Any ideas would be appreciated.

Thanks!

Tymanthius

---

### Post by WakkiTabakki on 2007-03-30
Run it as part of you session!
Open Session under Preferences-menu (this applies to Gnome) and just add it there and it'll start when you log in...

/N

---

### Post by tymanthius on 2007-03-30
I don't always log in to my session.  My kids occasionally use this pc (theirs always seems to be broken . . . ), so sometimes they log in first.  But I want hellanzb to 'just be there' so that if I remote in, or steal the kybrd & drop to a terminal, I can just have it work.  

Thanks for the idea tho.

Tymanthius

---

### Post by WakkiTabakki on 2007-04-04
Well, ok 8-[... Rrrright, then... I can think of two ways to go about it. It's quite likely that both of'em would be considered as McGyver-solutions, and also, I don't actually know how to do any of them exactly, sorry... But at least it may provide you with a direction in which to go looking.  

** Using SUID
You could accomplish what you're after by suid:ing the executable (**not** sudo!). 
Works like this: When an executable has the setuid-bit set, it's gets run with the privileges of the owner of the executable, regardless of who actually ran the program. So if you set yourself as the owner of the executable, set the suid-bit on it and then have it run as daemon on start-up as you originally did, the process should be run with *your* credentials...
**Note,** this is not the best idea from a security perspective, but I guess you're not storing any nuclear missile launch codes on the comp, right?
(check wiki for a better explaination:  [http://en.wikipedia.org/wiki/Suid](http://en.wikipedia.org/wiki/Suid) )

** Mounting with suid 
This is another suid, actually, but really the same principle only applied to a file-system instead...
You could add the target download folder (the one where you would've had all the root-owned files) as a mount in to your [FONT="Courier New"]/etc/fstab[/FONT] and set it to mount using the options [FONT="Courier New"]suid/guid[/FONT] and [FONT="Courier New"]umask[/FONT].
When mounting with suid/guid you can set that anyone accessing the mount will do it as the specified user/group hence, even if your hezbollah-program is executing as root when writing to the mount, the files would turn up as owned by the user (as specified by the suid/uid-option) and/or group (guid/gid).
With the umask-option you can tell the file system to remove permissions to all files written to the mount. So if you mount with umask=0000 (i.e remove no permissions) all files written to the mount would get 777 (rwxrwxrwx) permissions, i.e accessible by all, but still owned by root in your case.
Note, using this strategy, the program must write to the mount, not the actual folder, e.g.
[INDENT]If you have your download folder in [FONT="Courier New"]/home/schwoop/stuff [/FONT]and you mount that folder (using a line in [FONT="Courier New"]/etc/fstab[/FONT] with all the correct options) as [FONT="Courier New"]/mnt/StuffAndSuch[/FONT] you'll have to have your hezwhatever-program write to [FONT="Courier New"]/mnt/StuffAndSuch[/FONT] and not to [FONT="Courier New"]/home/schwoop/stuff [/FONT]
[/INDENT]

Good luck (you may need it :) )
/N

---

### Post by mbeierl on 2007-04-04
I use the following in my rc.local:
```

/bin/su - target_username -c program_to_run &

```
Where, of course, target_username is your user name and program_to_run to the program that you want to run.

That should do the trick.

---

### Post by WakkiTabakki on 2007-04-06
Hi mbeierl
But, doesn't that require the user to interactively type in the password?

/N

---

### Post by tymanthius on 2007-04-07
That was close to the way I solved it.  Put a script in to run at start up that was just a command to run hellanzb as me (no password) and use my home directory.  

I can't look the command up right now b/c I think I hosed Xorg or my nvidia drivers.  But it's working great.  :)

<edit>
Got my video issue fixed - kdm & gdm were fighting.
the command in my script is 'sudo -H -u <username> hellanzb -D'

---

### Post by cookfromfrozen on 2007-04-07
> **WakkiTabakki said:**
> Hi mbeierl
But, doesn't that require the user to interactively type in the password?

/N
In general, yes, but not if su is invoked by root.

The suid flag on the executable may be a cleaner solution though.

---

