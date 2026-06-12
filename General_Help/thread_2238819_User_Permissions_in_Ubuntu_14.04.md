---
title: "User Permissions in Ubuntu 14.04"
date: 2014-08-10
forum: General Help
---

### Post by AmagicalFishy on 2014-08-10
Hi, everyone

I just upgraded to Ubuntu 14.04 and am having an slightly inconvenient issue. In Ubuntu 12.04, there were naturally certain actions I had to *sudo *in order to perform. In Ubuntu 14.04, it seems I have to *sudo *to do much of anything. This is causing a lot of various little annoyances (I decided to *sudo -*while compiling/making a bunch of stuff that I did not previously have to *sudo*, and ended up installing things to a /tmp/root folder instead  of a /tmp/[username] folder, for example).

Is there some user-permission change I can do to get permission-stuff back to how it was in 12.04? I don't want my default user account to be as powerful as root, but I also don't want to have to type in *sudo *before I do anything, all the time.

Thanks for any help you guys can offer :)

---

### Post by steeldriver on 2014-08-10
Examples... ?

If you need sudo while compiling/making, that's nothing to do with the command (or any changes in sudo behavior) - it's just a matter of where the files are (a system directory versus your home directory). Or perhaps you used 'sudo' unnecessarily at some point and now subsequent 'configures' or 'makes' can't overwrite the files because they are owned by root?

---

### Post by AmagicalFishy on 2014-08-10
Examples include having to type in sudo before mv, rm, edditting with vim, making/configuring files that never before necessitated sudo, etc.

I'm reinstalling things that were installed in my 12.04 in the same folders/same way that I installed the before (I did a clean install when I upgraded). 

The using 'sudo' unnecessarily is an interesting point, actually, this might be the case&#8212;but if it is, then that opens up some new problems, I think. For example, the stuff I'm making won't make successfully unless I sudo, forcing it into root, (while, when I installed it before, it making it w/o sudo was fine). 

There isn't some kind of user-status that would be something like an elevated user, but one that doesn't actually have all the powers of a root user?

---

### Post by whitesmith on 2014-08-10
There's no named equivalent of a Windows Power User in Ubuntu, just users and root. All privileges are controlled by permissions here.

---

### Post by AmagicalFishy on 2014-08-10
Hm. What could have made the change between 12.04 and 14.04? There is, most definitely, a noticeable difference&#8212;unfortunately, I'm not very familiar w/ Windows Power User.

---

### Post by steeldriver on 2014-08-10
Can you give **specific** examples (including full directory paths) of commands that now require sudo but didn't previously?

---

### Post by AmagicalFishy on 2014-08-10
javi@Guantanamo-Bay:~$ mkdir test
javi@Guantanamo-Bay:~$ mv test ..
mv: cannot move &#8216;test&#8217; to &#8216;../test&#8217;: Permission denied
javi@Guantanamo-Bay:~$

javi@Guantanamo-Bay:~/LabWork/simulation/offline/make$ ./configure
./configure: line 1831: config.log: Permission denied
./configure: line 1841: config.log: Permission denied
javi@Guantanamo-Bay:~/LabWork/simulation/offline/make$

Are a couple, the most relevant right now. These commands worked fine before the upgrade without having to sudo.

(What would these examples provide that I hadn't said already? [In the case that I'm missing something that I could be looking for in the future])

---

### Post by steeldriver on 2014-08-10
Well if you are creating the directory 'test' in the top level of your home directory, and then trying to move it up to /home, that would normally require sudo (root owns /home). If that was different on you old system, then you must have set up non-standard directory permissions/ownership previously.

In the second case, either the ownership/permissions got messed up when you copied the files, or you ran the configure script initially with sudo, causing the log file (and possibly others - such as any Makfiles that may have been generated) to become owned by root. It should just be a case of fixing those ownerships/permissions.

---

### Post by AmagicalFishy on 2014-08-10
Ah! Alright.

My old system was the first time I consistently used Ubuntu, so I probably had some weird novice-fueled settings. I think I'll reinstall everything from scratch for the second issue&#8212;stuff may have been put into a folder with 'root' instead of 'javi'.

Thanks very much for your help. :)

---

### Post by whitesmith on 2014-08-10
> **AmagicalFishy said:**
> Hm. What could have made the change between 12.04 and 14.04? There is, most definitely, a noticeable difference—unfortunately, I'm not very familiar w/ Windows Power User.

[http://en.wikipedia.org/wiki/Power_user](http://en.wikipedia.org/wiki/Power_user)

---

