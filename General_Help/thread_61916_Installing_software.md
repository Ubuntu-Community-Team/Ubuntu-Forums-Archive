---
title: "Installing software"
date: 2005-09-02
forum: General Help
---

### Post by Kameleon on 2005-09-02
Hi there,
Since a few weeks i'm using Ubuntu now, and no matter what i do, i can't seem to install any software. Not with Synaptic and not with the command line.
Now i really like Linux, but i'm getting sick and tired of not being able to install software on any Linux system. I want to learn using Linux but so far my questions have not been answered in a way that makes it possible to install software.
Please help me or i'm forced to go back to Windows, which i really don't want.
Thanks in advance.

---

### Post by KingBahamut on 2005-09-02
Can you output your sources.list file to this forum. 

/etc/apt/sources.list 

I suspect that might be an issue.

---

### Post by Kameleon on 2005-09-02
I'm getting an " access denied" reply...

---

### Post by Kameleon on 2005-09-02
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
It worked now so here it is


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by KingBahamut on 2005-09-02
well the first thing Id do is comment out / remove the CDROM source. 

then uncomment the bottom source list. 

and using the ubuntuguide link in my sig, adding the backports repo as well. 

then retry.

---

### Post by Kameleon on 2005-09-02
I'm sorry but i do not understand your answer. There is nothing wrong with my cd-rom.
I just want to know the commands to install downloaded software or software "installed" by Synaptic. Just a list of steps i should take is all that i want.
Thanks for your quick reaction!

---

### Post by KingBahamut on 2005-09-02
apt-cache search <programname>
apt-get install <programnamefoundinabovesearch>
apt-get remove <name of program installed>

---

### Post by KingBahamut on 2005-09-02
I do note however that on this forum, you have asked only one question. one for which I hope I answer well. 

Where else have you asked questions for which you did not get an answer.

---

### Post by Kameleon on 2005-09-03
Now it worked!  :) 
I have been posting in newsgroups before, but didn't find the answer there.
Your answer is what i was looking for, just: step 1, 2, 3.
Thanks a lot!

---

