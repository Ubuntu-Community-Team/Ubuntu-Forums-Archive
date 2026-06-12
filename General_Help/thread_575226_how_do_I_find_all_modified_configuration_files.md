---
title: "how do I find all modified configuration files?"
date: 2007-10-13
forum: General Help
---

### Post by kosmos on 2007-10-13
Sorry if this is a dumb question, but I've looked at dpkg, dpkg-query, dlocate, and I don't see an easy answer. I've looked in /var/lib/dpkg/info/* and I see the *.conffiles lists, which is a start, but I don't think the md5sums of conffiles are listed in the *.md5sums files. So how do I get a simple list of modified configuration files? 

Thanks.

---

### Post by geirha on 2007-10-14
One thing you could do, is compare the /etc dir on the livecd with the /etc dir on your system. Not all configuration is stored in /etc, but most of it should be.

First of all, make a note of where your /etc is mounted: ```
df /etc
```

Then boot with your livecd and mount your system partition. In a terminal:
```

sudo mount /dev/hda1 /mnt
sudo diff -ur /etc/ /mnt/etc/

```
change /dev/hda1 with the actual partition on your system.

the diff command may give a lot of output, so either (1) pipe it to less, or (2) write the output to a file:
```
sudo diff -ur /etc/ /mnt/etc/ | less          # (1)
sudo diff -ur /etc/ /mnt/etc/ > /tmp/diff.txt # (2)
```

---

### Post by kosmos on 2007-10-14
Thanks for your reply. I do not have a live cd. 

This is a system on which I did not do the initial configuration. This is why I would very much like to find all the modified config files to make sure I have not missed anything.

I'd be surprised if there wasn't a command to find modified config files. It was pretty simple to do with rpm back when I ran a redhat system. And everyone tells me deb is better! :)

I have noticed that during a system upgrade, the process tells you if there are modified config files and allows you to keep them or overwrite them with new ones. So the information must be there somewhere, I just need to know how to get it.

---

### Post by japhy on 2008-01-15
You might try doing it with debconf:

[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Warning:  I haven't yet tried this myself.

---

### Post by kosmos on 2008-01-18
> **japhy said:**
> You might try doing it with debconf:

[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Warning:  I haven't yet tried this myself.

The referenced page shows a method of finding files newer than a certain date, which I am already familiar with (the "find" command can easily do this, for instance). The problem is that this doesn't seem to give good results on my system, I end up with far too many "hits" of files that have been touched by various system processes, but not by me, as it includes things like /etc/mtab, and so on. 

As for debconf, I don't understand how to use it to find modified config files.

---

