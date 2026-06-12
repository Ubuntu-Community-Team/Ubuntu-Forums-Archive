---
title: "PsyBNC requires older version of glibc.  How to get around problem?"
date: 2007-06-12
forum: General Help
---

### Post by madmonk3y on 2007-06-12
PsyBNC is terrible, out-of-date code.  However, there is no other IRC BNC that allows for multi-network-per-single-user-and-single-irc-client-connection, and is multi-user and offers oidentd support.  Because of the lack of alternatives, many of my users still want to run PsyBNC.

PsyBNC has a well-known "stop error".  The stop error means that PsyBNC will compile (with many warnings) successfully, and the process will start, but the performance will degrade (usually over the course of 12-24 hours) until it stops accepting client connections, but the process will continue to run.  When this happens, you have to manually kill -9 the process and restart it.

The compile warnings and stop error are likely because of PsyBNC not being updated to work with any recent versions of glibc.

I was wondering if it was possible to build a static version for ubuntu of the latest version of PsyBNC ([http://www.psybnc.at/download/beta/psyBNC-2.3.2-7.tar.gz](http://www.psybnc.at/download/beta/psyBNC-2.3.2-7.tar.gz)) using an old version of glibc?  Can someone help me figure out a way to do this, please?

Here is some sample output including compile warnings, when I try to compile:

```

src/psybnc.c:225: warning: passing argument 3 of â__pmallocâ discards qualifiers from pointer target type
src/psybnc.c:256: warning: passing argument 2 of âstrmncpyâ discards qualifiers from pointer target type
src/match.c:297: warning: incompatible implicit declaration of built-in function âstrlenâ
src/match.c:310: warning: incompatible implicit declaration of built-in function âstrcpyâ

```

There are hundereds of pmalloc strmncpy strlen and strcpy warnings like the above.

I've attached the entire output from the compile.

Here's a discussion that might help:

```

<1> i have no idea how to build it on ubuntu... building psybnc on sarge was easy though, but...
<2>  do you want to use it just for yourself?
<1>  no that's the problem.  the static binaries available are not oidentd-capable, so they are not usable for multi-user
<2>  well ok for a multiuser env. there is no real alternativ - i would have suggested to use irrsi-proxy for just yourselfe - but thats not possible.
<1> closest alternative is ezbounce.
<1> but that means multiple irc client connections per user (one per network)
<1> there are about 12 other BNCs, of which 2 or 3 are actively maintained, and none of which can do what psybnc does.
<2> I am using glibc-2.3.2.ds1-22sarge6
<1> how do I tell what version of glibc I have installed on ubuntu?
<1> n/m - apt-cache search glibc ----> aptitude show libc6 (tells me) Provides: glibc-2.3.5-3, glibc-2.3.6-2
<2> sudo /lib/libc.so.6
<2> show info about your glibc
<1>  neat - GNU C Library development release version 2.4
<1>  I wish I knew how to statically compile psy.  I'd install vmware and an old version of debian and make a statically-linked binary.
<2> well in any case if you really have to install psybnc you can download an old version of the glibc compile it and install it to some local folder... after that point the makfile to these libarys and it should work.
<1> please walk me through this
<2> i just unpacked psybnc it doesnt even use automake :) and honestly its nothing you can talk someone through .. that a lot of work :/
<2> well i justed looked throught the makefile try 'set CFLAGS=-static' and build it after that (on the old debian)
<2> but it has a static makefile and if thats doesnt work you would have to manually change the ld calls...
<2> also psybnc compiles options into its binary... afaik. that'll make it pretty hard to maintain on another system.
<1>  hrm any other ideas?
<2> nothing that doesnt require major work.. sry. but there still might be an easy option i cant think of right now.
<2> psybnc doesnt have that much code... and probably there is a newer makefile somewhere on the net or something.
<1> I know gentoo has it in their portage tree, so they made an ebuild for it.
<2> might be worth a try... i know a lot of ppl still sell bouncers with psybnc on it... i mean they might be just using sarge. but maybe someone modet it, dont really know
<1> thanks anyway for your help
<2> good luck, hope you get it compiled
<1> thanks - I hope so too

```

---

### Post by whizbaby on 2007-06-12
Cant say something really useful, but shouldnt all those a's with a chinese hat on it be quote marks ? (does everybody see the a's like me?)

---

### Post by madmonk3y on 2007-06-12
Probably.  But this is, as you've already acknowledged, probably not useful in solving the problem or addressing the question.

---

