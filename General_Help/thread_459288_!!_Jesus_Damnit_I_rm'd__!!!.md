---
title: "!! Jesus Damnit I rm'd * !!!"
date: 2007-05-30
forum: General Help
---

### Post by loathsome on 2007-05-30
[B][FONT="Fixedsys"][COLOR="DarkSlateGray"]loathsome@drippindevil:~$ sudo rm -R * '/usr/local/lib/tcl8.4' [/COLOR][/FONT]
[/B]

I DID IT THE WRONG WAY. :(

Any possible way for me to restore what I just did? CRAP!
My whole desktop + home folder is GONE!

---

### Post by blazercist on 2007-05-30
ha, no ur FUBAR... lol I heard about this happening but I thought people would be more cautious.

---

### Post by loathsome on 2007-05-30
> **blazercist said:**
> ha, no ur FUBAR... lol I heard about this happening but I thought people would be more cautious.
Yeah, thanks for that.

I just did a freaking mistake, please tell me I can get my stuff back.

:(

---

### Post by austin on 2007-05-30
what directory where you in?

---

### Post by loathsome on 2007-05-30
/home/loathsome

---

### Post by loathsome on 2007-05-30
Where's the rmtrash when you need it?

Is there ANY way of restoring my **precious** files?

---

### Post by aysiu on 2007-05-30
No, you're screwed.

This is why I always recommend people use ```
gksudo nautilus
``` or ```
kdesu konqueror
``` instead of ```
sudo rm
```

---

### Post by loathsome on 2007-05-30
> **aysiu said:**
> No, you're screwed.

This is why I always recommend people use ```
gksudo nautilus
``` or ```
kdesu konqueror
``` instead of ```
sudo rm
```

Yes, yes, I know I did a stupid thing.


S..crewed? NO OTHER POSSIBILITIES? What about those «recover your files» programs?

[COLOR="LemonChiffon"]F*CK SONOFABI*CH[/COLOR]

---

### Post by aysiu on 2007-05-30
> **loathsome said:**
> Yes, yes, I know I did a stupid thing.


S..crewed? NO OTHER POSSIBILITIES? What about those «recover your files» programs?

[COLOR="LemonChiffon"]F*CK SONOFABI*CH[/COLOR]
Well, if there is a chance of recovering files, the first thing you should do is shut down your computer... or reboot it with a live CD.

The longer you have it running, the less a chance you have of recovering things.

One of these links may help you:
[http://www.sage.org/lists/sage-members-archive/2007/msg00402.html](http://www.sage.org/lists/sage-members-archive/2007/msg00402.html)
[http://www.linuxquestions.org/questions/showthread.php?t=441914](http://www.linuxquestions.org/questions/showthread.php?t=441914)
[http://www.csummers.org/index.php/2005/12/20/undelete-text-files-on-linux-ext3-partition/](http://www.csummers.org/index.php/2005/12/20/undelete-text-files-on-linux-ext3-partition/)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/38807-query-recovering-deleted-files.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/38807-query-recovering-deleted-files.html)
[http://ubuntuforums.org/showpost.php?p=2194002&postcount=8](http://ubuntuforums.org/showpost.php?p=2194002&postcount=8)
[http://kerneltrap.org/node/6562](http://kerneltrap.org/node/6562)

---

### Post by kevinlyfellow on 2007-05-30
> Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

If you use ext3, you've pretty much got no hope.

you could do this to save yourself in the future

```
sudo su
echo "alias rm='rm -i'" >> /root/.bashrc
exit
echo "alias rm='rm -i'" >> ~/.bashrc
```

---

### Post by loathsome on 2007-05-30
> **kevinlyfellow said:**
> If you use ext3, you've pretty much got no hope.

you could do this to save yourself in the future

```
sudo su
echo "alias rm='rm -i'" >> /root/.bashrc
exit
echo "alias rm='rm -i'" >> ~/.bashrc
```
What does that alias-thingy do, **kevinlyfellow?**

---

### Post by kevinlyfellow on 2007-05-30
It sorta creates a new command.  Like alias hello='echo "hello world"' would give you the command hello, which would act just like you typed in echo "hello world"

its very handy

```
kevinly@Argool:~$ alias hello='echo "hello world"'
kevinly@Argool:~$ hello
hello world
```

Edit: Here are some more examples that I find useful
alias dspace='df -h --type=ext3'
alias back='cd $OLDPWD'
alias temperature='cat /proc/acpi/thermal_zone/THRM/temperature'
alias musicnorm='vorbisgain -frs /home/kevinly/music*'
alias gksudo='gksudo -k'
alias iwscan='iwlist scan'

---

### Post by loathsome on 2007-05-30
Ah, sweet - thanks for the tip! ;)

---

