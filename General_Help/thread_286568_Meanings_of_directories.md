---
title: "Meanings of directories"
date: 2006-10-27
forum: General Help
---

### Post by PigCorpse on 2006-10-27
Hi!

Can someone tell me what those directories are for? I mean stuff like:

/usr/bin
/usr/share
/usr/lib
/usr/opt
...

It seems some things are installed in one of these directories, and some are installed into others. Can someone explain what all the directories mean?

Thanks!

---

### Post by black_rob on 2006-10-27
I'm not a unix historian, but traditionally /bin is for programs (short for binary?), /sbin is for special programs that not everyone needs access to -- /sbin usually isn't in a regular users path, just the root users-- like ifconfig is there, because a regular user doesn't need to set up a network connection.  /opt has always been a question mark for me, and I believe that's what it's for "optional" programs.  In my experience, there often isn't much in opt at all, although often kde and openoffice install there instead in /usr.  /lib is for libraries that various programs might need.  

The above directories are for the base system: everyone with a barebones unix install of a specific distribution will have the same thing in their /bin, /sbin, /lib, etc.  All the extra programs go into /usr, all the non-essential programs.  The subdirectories in /usr carry the same purpose as the subdirectories in the root directory, containing libraries and binaries for all the extra programs.

---

### Post by ~LoKe on 2006-10-27
```
loke@x04d:~$ ls /opt/
loke@x04d:~$
```

You can pretty much put whatever you want in /opt/.

---

### Post by po0f on 2006-10-27
PigCorpse,

Well, the /usr directory stands for **us**e**r**, or **U**nix **s**hared **r**esources, depending on who you ask.  Pretty much anything a regular user need to run a program can be found in here.

/usr/bin is where **bin**ary (aka executable) files go.  So, programs that you use.

/usr/share is where data is stored that is **share**d between programs, like /usr/share/icons.  Many programs will use the resources in this directory.

/usr/lib is the **lib**rary folder.  Libraries meaning DLLs, if you are more familiar with Windows.

/usr/opt is a new one on me, usually it's just /opt.  Stuff that is **opt**ional goes in this directory, ie stuff you install outside of core system stuff.  Like maybe a game you downloaded and didn't want to put in the main filesystem.

Hope this helps.

---

### Post by ejket on 2006-10-27
This might help:

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by PigCorpse on 2006-10-28
Awesome!

Thanks to all of you! I now have the answer to one of the most troubling questions I've had about Linux.

---

