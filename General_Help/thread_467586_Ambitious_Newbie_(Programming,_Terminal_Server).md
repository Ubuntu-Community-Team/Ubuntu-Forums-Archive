---
title: "Ambitious Newbie (Programming, Terminal Server)"
date: 2007-06-07
forum: General Help
---

### Post by RTucker on 2007-06-07
Hi All,
 
I'm a definate newbie when it comes to Linux, but I'm also the kind of person who likes 'learning to swim by jumping in the deep end'. I'm a very competent Windows user who is about to go for a dual boot with Ubuntu, but I've got some questions...
 
Firstly, I'm a fairly handy VB.Net programmer (good enough to write any programs my workplace/firends/family/self have needed, though not good enough to get paidfor it ;)), and I'd like to know if there are any languages to code for Linux which may be at all similar? Alternatively, what are the 'main' languages people use in the Linux world? From what I've read it seems like python is pretty popular, and theres always C++. I won't be doing anything major, just utility stuff most likley.
 
Secondly, (although I'm not sure if this is appropriate for this thread) I have some questions about using Ubuntu as a Terminal Server. From what I've read, using a thin client is somewhat like a remote desktop session of the terminal server. Everything behaves as if you were sitting in front of the server itself. 
 
So, based on that, is it possible to set up what programs individual or groups of users can run, what they can access, etc? Or is it just whatever is installed on the server?
 
Also, it seems that a lot of 'thin clients' have an OS. Though I thought the point of a Terminal Server set up was to have the clients boot directly from the server via LAN card, with no software installed?
 
Sorry this was a bit long winded, and thanks in advance for any info.

---

### Post by reclusivemonkey on 2007-06-08
One of the quickest and easiest ways to get things done in Linux is through shell scripting; you don't even need to start with a fully fledged programming language, although this may be something you want to do anyway. I'm not a programmer, but I do find shell scripting very useful, so here are a few links for your perusal;

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq](http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq)
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

This is a more general Linux guide, but its handy as to get the most from shell scripting, you need to be aware of all the incredibly useful and robust CLI utilities out there;

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

Good Luck =]

---

### Post by RTucker on 2007-06-08
Thanks for the quick reply.
 
I'll definatley go through those book, as I do know the benefits of being familiar with the CLI. You'd be supprised at the things windows has that can only be accessed through the command prompt. For my purposes though I really need something with a GUI.
 
I just stumbled accross MonoDevelop and it looks like its exactly what I was after :D.
 
Does anyone know what the spread of Mono is like? ie. how many people actually have it, do/how many distros bundle it?.
 
Also, I heard that it was actually bundled in Ubuntu, though some places say otherwise.

---

### Post by Swab on 2007-06-08
> **RTucker said:**
> Hi All,
Secondly, (although I'm not sure if this is appropriate for this thread) I have some questions about using Ubuntu as a Terminal Server. From what I've read, using a thin client is somewhat like a remote desktop session of the terminal server. Everything behaves as if you were sitting in front of the server itself. 
 
So, based on that, is it possible to set up what programs individual or groups of users can run, what they can access, etc? Or is it just whatever is installed on the server?
 
Also, it seems that a lot of 'thin clients' have an OS. Though I thought the point of a Terminal Server set up was to have the clients boot directly from the server via LAN card, with no software installed?
 
Sorry this was a bit long winded, and thanks in advance for any info.

You can setup users on your server and give those users different permissions.  The users login via the thin client machines.

There is no OS on the thin client machines, they boot from the network and don't even require hard drives.

---

### Post by RTucker on 2007-06-08
Ok, cool, thats how I thought the thin clients worked, though I wasn't sure because most of the ones I see for sale say they have some form of OS (eg. Windows CE).
 
Also, as the clients are using the servers OS, would I be better off installing the standard version of Ubuntu for the TS, or getting the server version (which as I understand dosent have a GUI) and installing GNOME/KDE?
 
Again, thanks for the quick replies.

---

### Post by Swab on 2007-06-08
You'd want the standard version with all the GUI apps you want the clients to be able to use.  There is a version of Ubuntu called Edubuntu (aimed at schools) which sets up the server for you.

---

