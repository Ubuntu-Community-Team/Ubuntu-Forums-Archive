---
title: "Lightbox  Firefox + Ubuntu"
date: 2007-04-07
forum: General Help
---

### Post by lukemack on 2007-04-07
Hi,

I've noticed that the lightbox javascript script runs incredibly slowly in Firefox on ubuntu.I was wondering if a few people could try the following URL and see if they get smooth animations:

[http://www.huddletogether.com/projects/lightbox2/](http://www.huddletogether.com/projects/lightbox2/)

It would help if you are familiar with this script and know how it is suppose to look. It behaves as it should on my windows machine but on Ubuntu it is very 'jerky'.

thanks for any replies.

<L>

---

### Post by Jump on 2007-04-07
I tried the link and seems to be fine for me. It puts up a white window for about a second and then it plays the animation very smooth on my end.

---

### Post by lukemack on 2007-04-11
thanks. it runs v slowly for me and the cpu goes crazy. am on a P4 with 1GB RAM. anyone got any ideas why that might be?

---

### Post by kerry_s on 2007-04-11
Runs fine here.

What java are you using?

I'm running sun-java6 in feisty.

---

### Post by y-lee on 2007-04-11
It runs great for me, and I have only 512 M memory and an older P4 machine. I use firefox 2.0.0.3 on dapper drake but this script runs better on ubuntu for me than it does in Windows 2000 pro. I have however tweaked my about:config file in FF to improve performance. Since this is a javascript file  I doubt the version of java you have really matters, java is not the same thing as js. I am new to linux so I probably can't help you tho, but perhaps updating firefox will help if you aren't already using the latest version.

---

### Post by lukemack on 2007-04-11
I've got the latest version and java6u1. having done a bit of research, switching java off improves things but only very slightly (i know javascript is nothing to do with java but i guess switching java off affects performance). would be interested to know what performance tweaks you have made in about:config.

a bit of googling shows that others are having similar problems with FF on linux. its not a big deal but i was surprised that a bit of javascript would cause a cpu spike.

---

### Post by y-lee on 2007-04-11
most of the tweaks i did one can find here, [How to speed up firefox]("http://ubuntuforums.org/showthread.php?t=179540"). Ya might want to also read [firefox rocks]("http://www.terminally-incoherent.com/blog/forum/main/topic-4/?recent=64") since one of these tweaks can limit the web pages viewable.

---

