---
title: "So I was messing with the permissions..."
date: 2007-12-24
forum: General Help
---

### Post by buckeyefan on 2007-12-24
I will try to describe this as best as possible...

I downloaded a folder (an icon set), well I understood that I was to copy the files into the file system...

/usr/share/icons/     I believe...

well when I tried to drag the folder into the directory, it told me I didn't have permission to write files there, so i right clicked>permissions in that directory. Well the permissions were set so that only root could write files there...

So I logged in as root, and instead of just dragging them in and being happy, I decided to make it so I could install icons from my normal user account so I right clicked>permissions in the file system directory.

I can't remember what all I did, but I changed all the abilities from root to my user account name... now when ubuntu tries to load (sorry this is vague and probably incorrect, I am obviously a n00b), one of the lines says fail and then gnome never loads, leaving me with the command line.

thanks in advance for any help, hopefully I don't have to reinstall, I had all my compiz settings just how I liked it!

---

### Post by taurus on 2007-12-24
So what are the permissions and who owns that directory, /usr/share/icons?

```
ls -la /usr/share/icons
```

---

### Post by ~LoKe on 2007-12-24
I'm not entirely sure, but this should do it....

```
sudo chown -R root /usr/share/icons
```

---

### Post by buckeyefan on 2007-12-24
both of those returned as permission denied when I booted into recovery mode...

I tried to boot into normal ubuntu (7.10) and i wrote down the error

for the one that [fail]ed, 

kernel log daemon
unable to start /sbin/klogd

---

### Post by ~LoKe on 2007-12-24
Christ...did you change the permission on the entire root filesystem?

```
chmod 755 /
```
In the recovery mode might do it...

**DON'T DO IT** until someone else has come along and ok'd it.  I'm **NOT** sure, at all, if that will work without causing a different problem.

---

### Post by buckeyefan on 2007-12-24
> Christ...did you change the permission on the entire root filesystem?

that'd be a yes, obviously a complete noob move but hey, it's easier to make those mistakes on a machine that cost 30 bucks that you don't really have to worry about :)


thanks again for the help

---

### Post by taurus on 2007-12-24
You can boot your machine to recovery mode, right?  What happens if you run these commands?

```
chmod -R 755 /usr/share/icons
chown -R root:root /usr/share/icons
```

---

### Post by ~LoKe on 2007-12-24
If you're not really worried, go ahead and give it a shot...
```
chmod 755 /
```

---

### Post by buckeyefan on 2007-12-24
> If you're not really worried, go ahead and give it a shot...

this is definitally a learning machine more than anything, i'll go ahead and give it a shot

---

### Post by buckeyefan on 2007-12-24
you guys are awesome, it did the trick (posting on ubuntu right now)

lesson learned, now off to make my next mistake :)

thanks again

---

### Post by ~LoKe on 2007-12-24
Happy to help.  Good luck with whatever you mess with next. :lolflag:

---

