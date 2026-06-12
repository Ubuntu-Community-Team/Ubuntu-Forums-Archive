---
title: "HOW TO: Grsync over SSH"
date: 2008-03-31
forum: General Help
---

### Post by TekNullOG on 2008-03-31
OK, I spent the last hour trying to figure out how to use Grsync with SSH and I thought I would explain how I got it to work. It seems so obvious now but I hope it helps others.

Grsync allows you to rsync using a nice GUI and is also available in the Ubuntu repositories. If you're wondering what is rsync? Wikipedia says: "rsync is a software application for Unix systems which synchronizes files and directories from one location to another while minimizing data transfer".

First off, l'll assume you know what most of the options are in rsync so I won't cover that stuff.

I also imagine that you are able to Grsync to a local usb drive. This allows you to know that Grsync and its dependencies is properly installed and working.

It doesn't matter whether your remote computer is your destination or source. What's important is you make sure to have the proper syntax for the remote computer.

For example, it should look like:

> 
remotecomputer:/remote/directory


In order to give you a more concrete example, this might help you more.

> 
192.168.1.1:/home/yourname/directory/


I might be blind but I could not find the option for telling Grsync to use ssh so you'll have to go to:
Advanced options > Additional options > -e ssh

All you need to do is add:
-e ssh

I know this doesn't seem very complicated but it puzzled me and my friends for some time and since we're still kinda newbies with linux, the answer was not easy to find. So voila, I hope it helps someone else.

---

### Post by JasonSilver on 2008-04-02
Very helpful-- I was stuck too.

Another problem tho: how to I explicity tell it to use a different username? It's defaulting to my Ubuntu username.

Thanks,
Jason Silver

---

### Post by JasonSilver on 2008-04-02
Duh, it's simple: username@serveraddress:/file/structure

Thanks!
Jason

---

### Post by TekNullOG on 2008-04-03
Sorry I didn't reply faster, I've been very busy lately. But you seem to have found the solution.

I am happy you found this useful. My knowledge of Ubuntu is sometimes limited so when I find the solution to something that I couldn't easily find, I try to do my part and share it in the forums.

---

