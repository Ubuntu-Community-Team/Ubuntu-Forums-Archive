---
title: "[SOLVED] Bulk Unzipping?"
date: 2008-03-09
forum: General Help
---

### Post by intense.ego on 2008-03-09
I was not sure where to put this thread, so i put it here. 

Anyway, I have many (like 40) .rar and .zip archives and instead of having to open each one individually and extract, I was wondering whether there was a way of bulk unzipping them or setting up a queue?

---

### Post by insineratehymn on 2008-03-09
Ithink so.... Apparently tar supports regular expressions.

[http://www.gnu.org/software/tar/manual/html_node/tar_107.html](http://www.gnu.org/software/tar/manual/html_node/tar_107.html)

Thats a tutorial, I'm not incredibly skilled at regular expressions, so I cant really help you too much. 

I don't know if unzip does though...

---

### Post by intense.ego on 2008-03-09
> **insineratehymn said:**
> Ithink so.... Apparently tar supports regular expressions.

[http://www.gnu.org/software/tar/manual/html_node/tar_107.html](http://www.gnu.org/software/tar/manual/html_node/tar_107.html)

Thats a tutorial, I'm not incredibly skilled at regular expressions, so I cant really help you too much. 

I don't know if unzip does though...

I don't quite understand. Will this allow me to unzip many different rars at once?

---

### Post by PmDematagoda on 2008-03-09
This thread has been moved to the General Help section.

---

### Post by intense.ego on 2008-03-09
I found this helpful link on UF: [http://ubuntuforums.org/showthread.php?t=248354](http://ubuntuforums.org/showthread.php?t=248354) and I have a few questions:

1) will it still work (the thread is a bit old)?
2) can it be modified so that zips and rars are unzipped?
3) some of the rars/zips are password protected. will it stall on those ones or will it just move on and ignore them?

---

### Post by prshah on 2008-03-09
try (in a terminal):

mkdir unzipped && unzip -v -d unzipped '*.zip'

and

mkdir unrard && unrar ex '*.rar' ./unrard/

If in doubt, man unzip and man unrar will help you out.

Note that ubuntu will handle zip, Zip and ZIP as different files due to case.

If this doesn't help, you can use a simple shell script to do the job for you: see "help for"

Cheers,
PRShah

---

### Post by intense.ego on 2008-03-09
> **prshah said:**
> 

If this doesn't help, you can use a simple shell script to do the job for you: see "help for"


I don't understand, could you please elaborate? Also, do you know how it handles password protected rars?

---

### Post by prshah on 2008-03-09
> **intense.ego said:**
> I don't understand, could you please elaborate? Also, do you know how it handles password protected rars?

```

~$ mkdir unrard 

~$ for varname in `ls | grep -i rar`; do unrar ex "$varname" ./unrard/ ; done

```

If all the archives have the same password:

```

~$ for varname in `ls | grep -i rar`; do unrar ex -ppassword "$varname" ./unrard/ ; done

```

Otherwise, it will ask you for a password when it encounters a password protected archive. If you don't want it to ask for a password and proceed with the others, use:

```

~$ for varname in `ls | grep -i rar`; do unrar ex -p- "$varname" ./unrard/ ; done

```

For zip files:

```

~$ mkdir unzipped

~$ for varname in `ls | grep -i zip`; do unzip -v -d unzipped "$varname" ; done

```

for zip files with all the same passwords:

```

~$ for varname in `ls | grep -i zip`; do unzip -v -d unzipped  -P password "$varname" ; done

```

if you don't give "-P" (note the case), you will be asked for the password while the unzipping is taking place.

Cheers,
PRShah

---

### Post by kostkon on 2008-03-09
> **intense.ego said:**
> I was not sure where to put this thread, so i put it here. 

Anyway, I have many (like 40) .rar and .zip archives and instead of having to open each one individually and extract, I was wondering whether there was a way of bulk unzipping them or setting up a queue?

Assuming that none of them are password protected, you can simply select all the files, right-click and select *Extract Here*.

EDIT: although, even if you have password protected files, you will be asked for a password for every one of them through a pop-up.

---

### Post by intense.ego on 2008-03-09
Thank you prshah, for all your help, but kostkon had the solution I was looking for. I didn't know it was that simple. This is a real noob moment for me.

---

### Post by CrazyAcey29 on 2008-04-01
This might help me out as well.  Although, the files that I have to unZIP and UnRAR are files for use in my Sims2 game, on my laptop computer.  If this works for you guys, then let me know.  If it works for you, it might just work for me, because I have so many files that I need to reinstall, so that I can have certain things in my game, and certain crazy families available for play.  I also don't want to take all the time it would take to manually extract every hair, clothing, skin-color, and whatever other custom content I have, since I have so many files that fall into many categories.  So, please let me know if this wirked for you, the person that originally posted this thread.

---

### Post by CrazyAcey29 on 2008-04-01
I found a place where they may have a tool that can be downloaded that could make it easier for all of those of us that are having trouble with Bulk Unzipping.  You can download the trial version of it from this one site I found, or buy the full version of it.  I just want to make sure, before I post the link, that it's okay to post it here for those interested in it.

---

### Post by intense.ego on 2008-04-04
Sorry for the late reply, but I was away. Anyway, the method that worked with me was to select all the RARs/ZIPs, right click on any one and select "Extract To". Next, just choose a destination and click OK.

---

