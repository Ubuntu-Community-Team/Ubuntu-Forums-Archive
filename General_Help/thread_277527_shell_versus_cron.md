---
title: "shell versus cron"
date: 2006-10-14
forum: General Help
---

### Post by evaristegalois on 2006-10-14
Here is my problem: I am trying to use cron for all sorts of things, and I keep running into difficulties where a command run from the command line cannot be executed by cron. For example, the command

lame /home/evaristegalois/home.wav /home/evaristegalois/home.mp3

will run without trouble on the command line (or from a simple shell script with that command as my only line) but

0 9 14 10 * lame /home/evaristegalois/test.wav /home/evaristegalois/test.mp3 
5 9 14 10 * echo "this at least is working" > /home/evaristegalois/test.txt

will not create an mp3 file from the existing wav file even though five minutes later the echo command works perfectly well. I tried putting the command

lame /home/evaristegalois/home.wav /home/evaristegalois/home.mp3

into a shell script with name lame.sh and then watch cron as it again fails on

0 9 14 10 * sh /home/evaristegalois/lame.sh

What is the issue? Is it permissions (my hunch)? Which permissions does cron need to execute its commands? lame, for example, is in /usr/local/bin, and its permission there is -rwxr-xr-x, with root being the owner. But again, on my run-of-the-mill command line, the command works just swell.

Your help would be appreciated. lame is not the only command doing this to me. mplayer, when I try to convert .ram files into .wav files, or id3tool when I try to tag my mp3 files, do the same thing to me. Which permissions do you need for the files being worked on? It's confusing, I've tried a lot of things. Are there special characters in cron that I need to escape? That doesn't seem to be the case.

--evaristegalois

---

### Post by evilghost on 2006-10-14
Perhaps cron isnt' expanding the local environment and you need to use "/usr/local/bin/lame" instead of just "lame" in your crontab?

---

### Post by kidders on 2006-10-14
Hi there,

Technically, you can run cron jobs as anyone you like, but here's an easy thing you can do to see who the default is...

Do **mkdir ~/crap && chmod 777 ~/crap**
Then get cron to **touch /home/<wherever>/crap/somefile**

The file will be owned by the user that cron created it with. Low-tech, I know, but at least you'll have your answer! :-)

> lame, for example, is in /usr/local/bin, and its permission there is -rwxr-xr-x, with root being the owner. But again, on my run-of-the-mill command line, the command works just swell.That's precisely what you'd expect, since the "world execute" bit (the last 'x') is switched on.

**Edit:** From what you've posted, there are too many reasons why your cron task might be failing. Perhaps the most likely is that it either can't read your source file, or write the destination one.

---

### Post by chalex on 2006-10-14
I would think that the user that the cron daemon runs as does not have write permissions to your home directory.

For example, if you change the destination to /tmp, it will work fine.

---

### Post by evilghost on 2006-10-14
> **chalex said:**
> I would think that the user that the cron daemon runs as does not have write permissions to your home directory.

For example, if you change the destination to /tmp, it will work fine.

Why wouldn't it, AFAIK, cron is running as root.

---

### Post by evaristegalois on 2006-10-15
Thank you. Writing "lame" instead of "/usr/local/bin/lame" was the problem. Not only does one have to use the expanded filename but also the expanded command name. Wouldn't have occurred to me without you all's help. 

Cheers,

--evaristegalois

---

### Post by evilghost on 2006-10-15
> **evaristegalois said:**
> Thank you. Writing "lame" instead of "/usr/local/bin/lame" was the problem. Not only does one have to use the expanded filename but also the expanded command name. Wouldn't have occurred to me without you all's help. 

Cheers,

--evaristegalois

Always glad to help :)

---

