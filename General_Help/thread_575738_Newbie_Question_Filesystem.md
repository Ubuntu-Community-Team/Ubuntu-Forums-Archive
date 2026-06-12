---
title: "Newbie Question: Filesystem"
date: 2007-10-14
forum: General Help
---

### Post by rohedin on 2007-10-14
:) Hi there over the past day or so Ive been looking at Wubi. I'm convinced and Im gonna download it.
 
However, before I do so, there's one thing that's been bugging me. Ive heard that hard-rebooting on Wubi can damage the file system. By this does it mean, just the virtual disk filesystem or the actual hardisk with Windows on it?

If you could answer this, I would be greatfull.

---

### Post by ryanVickers on 2007-10-14
Could you not just use the live CD?  A lot of people have problems with Wubi, and by what I've read in my time, it doesn't seem like a very good ides if your not sure what your doing.  I would really recommend [getting]("http://gparted.sourceforge.net/download.php") the [gparted live CD]("http://gparted.sourceforge.net/features.php"), partitioning giving windows half or something, and the other have to Ubuntu and 1GBof swap ;)

---

### Post by ajgreeny on 2007-10-14
I agree with ryanVickers.  Much the better way.

---

### Post by rohedin on 2007-10-14
After a slight incident with partitioning a few months ago that rendered my PC trashed for life, i've been a bit wary about partitioning. Also, you haven't answered my question, will it or won't affect the Windows filesystem?

---

### Post by ryanVickers on 2007-10-14
Well, I don't know anything about it ;), but what I've gathered, I think it is a way to install Ubuntu but run the installer like a windows app.  Now, does it actually create an Ubuntu install on the HD, or does it run like a VM, or does it have it's "virtual Disk" inside of windows while running like a real OS?

---

### Post by Frak on 2007-10-14
Are you running XP or Vista.

@ryanVickers, its a Virtual Disk used as a Real Disk within the Windows Filesystem.

---

### Post by ryanVickers on 2007-10-14
oh, well then the chances of corrupting windows are quite slim I think, but always present.

I would still strongly recommend a real installation over this, but...

---

### Post by rohedin on 2007-10-14
Im using XP.

---

### Post by ryanVickers on 2007-10-14
that's good then ;)

God only knows what Vista would have done!  M$ probably implanted some secret code to bomb your computer if it detects your installing Linux ;)

---

### Post by rohedin on 2007-10-14
> **ryanVickers said:**
> that's good then ;)

God only knows what Vista would have done!  M$ probably implanted some secret code to bomb your computer if it detects your installing Linux ;)

Hehe, you thought you were joking. A while back I saw a video on youtube, when this guy booted up vista it formatted his Linux partition. :shock:

---

### Post by ryanVickers on 2007-10-14
oh dear - they need to die! :p

---

### Post by Frak on 2007-10-14
> **rohedin said:**
> Im using XP.
I was thinking of something else when I posted that, but now that I actually re-read your first post, if you hard boot ANY system, it has a chance of corrupting the file system.

But, the chance of it happening, is pretty slim. If it does, pop in your XP CD and choose repair and it will fix it back for you.

---

### Post by ryanVickers on 2007-10-14
yup, it'll run that windows check disk:

checking or fixing some files
checking or fixing some more files
checking or fixing some more files
checking or fixing some more files
1 or more files were checked/fixed

or if there's an error
1 or more unrecoverable errors were encountered
:p

---

### Post by rohedin on 2007-10-14
OK, thanks everyone. I'll install Wubi tommorow.

---

### Post by PGHammer on 2007-10-18
> **Frak said:**
> Are you running XP or Vista.

@ryanVickers, its a Virtual Disk used as a Real Disk within the Windows Filesystem.

I did my Feisty Fawn from within Vista (Ultimate in particular).  Most of my posts since then have been from that Feisty install (only one post, elsewhere, was not).

I've done *native* Feisty Fawn installs (in fact, on this hardware), and the lack of partition fiddlng (though I know how to do it, I hate it) is a major advantage for Wubi, to put it bluntly.

Now I'm really curious - how will it install and perform on a Core 2 Quad?

---

### Post by ago on 2007-10-18
> **PGHammer said:**
> Now I'm really curious - how will it install and perform on a Core 2 Quad?

In 7.10 wubi will install the 64 bit version... Which means no proprietary flash player... :P

---

### Post by Frak on 2007-10-18
> **ago said:**
> In 7.10 wubi will install the 64 bit version... Which means no proprietary flash player... :P
nspluginwrapper runs flash just fine.

---

### Post by ago on 2007-10-18
> **Frak said:**
> nspluginwrapper runs flash just fine.

Didn't know about that! I am a purist myself and could happily live with the opensource flash plugin, but my sons have a non-negotiable requirement for teletubby games... So thanks a lot!

---

