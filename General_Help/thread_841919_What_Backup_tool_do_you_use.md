---
title: "What Backup tool do you use?"
date: 2008-06-26
forum: General Help
---

### Post by kwilliam on 2008-06-26
I'm thinking about writing a GUI that works with multiple backup tools, and am curious as to what backup tools most Ubuntu users use. Let me know if I haven't listed a backup application you use, and I'll add it to the poll.

---

### Post by todak on 2008-06-26
Remastersys.

```
http://www.remastersys.klikit-linux.com/
```

---

### Post by kwilliam on 2008-06-26
> **todak said:**
> Remastersys.

```
http://www.remastersys.klikit-linux.com/
```

Oops, the poll wasn't up yet. You can vote now.

---

### Post by Taxman415a on 2008-06-26
I use Simple backup (sbackup is the package) but what I would really like is something that makes it really easy to split up the files I want to backup into 4.5Gb chunks in order to make it easy to burn them to DVDs. Currently I use sbackup basically jsut to automate config files and my home directory and I manually create 4.5Gb backup folders for the rest. It's rather a pain and strangely none of the various backup tools seem to address that. 

A well written easy to use backup GUI that covers most people's use cases is way up on the Ubuntu brainstorm site, so kwilliam, you'd be lots of people's hero if you wrote a good tool or improved an existing one.

---

### Post by kwilliam on 2008-06-26
> **Taxman415a said:**
> A well written easy to use backup GUI that covers most people's use cases is way up on the Ubuntu brainstorm site, so kwilliam, you'd be lots of people's hero if you wrote a good tool or improved an existing one.

I'm not looking to be a hero! It just seems to me that there have been SOOOOO many attempts to make a simple GUI backup tool for Linux users, yet none have really "caught on" in a big way, that there must be some underlying problem. My hypothesis is that each GUI only supports one method of making backups, and that people want something more flexible. E.g., a program that could make backups to CDs OR remote servers, do scheduled backups OR do them only on demand, use rsync OR rdiff-backup OR tar as a backend, etc. But writing "one-GUI-to-rule-them-all" would be really hard, which is why I'm curious to know what backends at a minimum such a GUI should support.

In particular, what CD/DVD burning backends are popular? I don't know of many good ones.

(I'm not concerned about partition based backups, like partimage, because those are usually run from a Live CD.)

---

### Post by Cotopaxi on 2008-06-27
Actually I just use copy and paste, from my computer's Hard Disk to an external USB Hard Disk. Actually I only "bak up" data files. Should I have a serious system crash, something that did not happen since I migrated to Linux (Kubuntu), I would make a clean re-installation and then draw the "baked up" data-files back into "Home".

All my data files are stored in any subdirectory within "Home". Also my browser files (Opera, which I love) are stored within "Home".

Primitive, but for a single user and under a STABLE Linux (not Windows rubbish), quite effective.):P

---

### Post by Taxman415a on 2008-06-27
> **kwilliam said:**
> My hypothesis is that each GUI only supports one method of making backups, and that people want something more flexible. E.g., a program that could make backups to CDs OR remote servers, do scheduled backups OR do them only on demand, use rsync OR rdiff-backup OR tar as a backend, etc. But writing "one-GUI-to-rule-them-all" would be really hard, which is why I'm curious to know what backends at a minimum such a GUI should support.
I think your hypothesis is spot on. There is a big need, but none of them have so far fit the bill of being flexible and powerful, yet with sensible defaults. Good software does that of course, lets you do what you want but suggests options if you don't know better.

> In particular, what CD/DVD burning backends are popular? I don't know of many good ones.
I'm not sure what others are common if any, but the backends to K3b and Brasero such as cdrtools, cdrkit, and cdrdao are probably the ones. I checked a few other burning GUI programs available in the repositories and didn't find any other main backends.

---

### Post by kpkeerthi on 2008-06-27
tar for /
rsync for my /home and /data

---

### Post by dlmoak on 2008-06-27
I use linbaku, which creates a tar file of my entire system and saves it to an external drive.  I use Simple Backup inbetween complete backups.

---

### Post by Bliepo32 on 2008-06-27
I just use the command line with tar and bzip. See [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) for more info on that.

---

### Post by issih on 2008-06-27
Slightly off topic, but I recently threw this little app together for my mother to use. Its a bit simplistic, and I know I will probably be tweaking it to make it do something more useful. e.g. incremental backups rather than just full ones, some kind of viewer to get a list of the different file versions stored etc, any ideas welcome.

I am well aware that there are many tools already in existence that do this kind of thing, but this was made for a specific use (namely living on an external hard drive and being usable on any pc its attached to, hence java and the profiles). I'm now fiddling with it because thats what programmers do :)

Feel free to play with it if you want, its released under the "do what the smeg you feel like" license.

Anyway, I guess I use this, or at least I will if I ever stop fiddling with it.

P.S. I know zipping a jar file is pointless, but the forum doesn't like jar files :s

---

