---
title: "Installing IRC on an Ububtu Server."
date: 2008-05-20
forum: General Help
---

### Post by SkelDave on 2008-05-20
Not sure if i've come to the right place, sorry if i'm wrong.

[B]I decided to learn how to set up an irc server using UnrealIrcd and Anope services, and i successfully got it running on my computer (I have MSxp).

One of my friends gave me access to the root of his server and told me i could set up an irc on that, for learning purposes.

I know how to configure it and everything (From online guides), i also made sure the gcc compiler was installed but once i have configured it, it says this:
[/B]

> ./configure --with-showlistmodes --enable-hub --enable-prefixaq --with-listen=5 --with-dpath=/root/Dave/Unreal3.2.7 --with-spath=/root/Dave/Unreal3.2.7/src/ircd --with-nick-history=2000 --with-sendq=3000000 --with-bufferpool=18 --with-hostname=ubuntu --with-permissions=0600 --with-fd-setsize=1024 --enable-dynamic-linking
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


[B]I asked about it on an irc server which i use and all i got out of them was that i needed to create a 'user account' and install it on there. So i did 'adduser Dave' and it asked for my password and things. But what do i do now? How do i start using that user account? How do i access the config.log?

I'd appreciate it if someone could help me, Thanks alot![/B]

---

