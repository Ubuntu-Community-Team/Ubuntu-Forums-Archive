---
title: "Can't boot ubuntu after wubi install - can't access tty"
date: 2007-06-02
forum: General Help
---

### Post by ezekielnin on 2007-06-02
Hi guys,

This may be the best appropriate place to post for my problem. (i already posted somewhere else on this forum [http://ubuntuforums.org/showthread.php?t=461963](http://ubuntuforums.org/showthread.php?t=461963))

[INDENT]I installed ubuntu 2 days ago using the wubi installer (which i think is a great idea btw) but unfortunately ubuntu doesn't want to load on my system. I don't receive any error while wubi installs nor in ubuntu installation.

When I but ubuntu the ubuntu logo shows with a loading bar which gets stuck at the very beginning. it stays there for 5 minutes then I get back to a black screen and the following test appears:

Busybox v1.1.3 Built in shel(ash)
can't access tty
job control turned off
(initramfs):_

Anybody knows what that means? I'd really like to use ubuntu everybody says it's great!

My hardware is the following : intel p4 2.8ghz, 512 mb ram, 56gb IDE HD, video card 128mb. Toshiba Satellite A30.

Personnaly I don't think this has anything to do with wubi but tell me if I'm wrong. Thanks![/INDENT]

thanks again for your help!

Alex

---

### Post by ago on 2007-06-02
Is that Wubi-Test3? If not please download it from the website and try again

---

### Post by ezekielnin on 2007-06-02
Hi,

yes I forgot to say this is happening with wubi test 3. I previously tested it with wubi test 1 when it came out and I had the same issue one time. Then I re-installed and ubuntu always froze when it was loading its components (just after logging in). 

hope this can help! 
Alex

---

### Post by ezekielnin on 2007-06-02
I  uninstalled and re-installed wubi. I got further in the loading process but after logging in it simply does nothing. HD doesn't seem to load anything... waited 30 minutes. Now I try to reboot and wheter I select ubuntu or windows XP the computer reboot completely .... sooooo I can<t load any OS anymore :( :( :( 

Is this easy to fix? Right now I'm using Knoppix live cd 5 ... I'm so happy i had this... i don't want to format ... i got some unsaved work. If possible i'd like to repair this.

thks

---

### Post by ezekielnin on 2007-06-03
Anyone have an idea how to fix this please?

I tried to use the option that says "Disable automatic restart" but it stills reboot right after I choose any of the 2 OS.

:(

I'll try to use windows xp CD recovery console... i hope this will work.

---

### Post by ago on 2007-06-03
There is nothing in wubi that affects xp directly, you'd need to provide some more detailed info. Can it be that XP filesystem was corrupted?

---

### Post by ezekielnin on 2007-06-03
hum, I don't understand either. XP was working fine before. But this happenend just after wubi/ubuntu install so logically it has to do something with it...

Anyways I backed up my files to a external HD and formatted hd and installed XP again. everything is working fine. I'll wait until wubi becomes non-beta before trying ti again.

---

