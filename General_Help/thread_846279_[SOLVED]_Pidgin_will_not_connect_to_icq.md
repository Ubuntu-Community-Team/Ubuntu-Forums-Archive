---
title: "[SOLVED] Pidgin will not connect to icq"
date: 2008-07-01
forum: General Help
---

### Post by zarqoon on 2008-07-01
I am using gutsy and since getting back from work pidgin will not connect to icq anymore. I get this error:
```
The client version you are using is too old. Please upgrade at http://pidgin.im/
```
This morning it worked fine. Xmpp still works.

Until now i used the version 2.2.1 available at the gutsy repository.
Now i downloaded the current 2.4.2 sourcecode. It compiled and startet it without major problems but still will not connect to icq and shows the same error message.

I do not like being unable to use icq

---

### Post by Pablo89 on 2008-07-01
I have the same! I wrote to the icq team, but I don't trust it could help. Licq didn't work as well. I use icq2go temporarily, but it sucks a little bit. It seems to be something against any non-official clients...

---

### Post by zarqoon on 2008-07-01
If only offical clients will work in the future. I will not use icq anymore. As i am sure a lot of others will not either. Icq 6 sucks bigtime and i think there is no linux version. It does not even work on a lot of windows machines. I have not been able to get it running on my sisters xp machine.

---

### Post by Pablo89 on 2008-07-01
There is no Linux version of an official client, and it would be great not to need icq! But, unluckily, some my friends use it and I don't expect them to change easily... Maybe some patch informing "I'm not pidgin, I'm the newest candy-like official icq client!" would solve it? I mean the version information sent to the server...

It's the first day of a month... probable time for such changes. It sucks much...

---

### Post by zarqoon on 2008-07-01
If this does not get resolved i will have to try to get my friends to use xmpp. It should make things a lot more easy if only icq6 will work. I have not met anyone yet who likes it.

---

### Post by Pablo89 on 2008-07-01
If it was so easy...
By the way, is this some problem of my provider, or is [www.pidgin.im](www.pidgin.im) website dead at the moment?

---

### Post by zarqoon on 2008-07-01
Its very slow from here. And often even times out. Something seems to be wrong with the server. Maybe its too many people trying to download 2.4.2 even though it does not work either.

---

### Post by Pablo89 on 2008-07-01
It's not a surprise that icq networks admins know nothing about pidgin versions... the message is automatically generated at client side. Licq dies with "unknown error"...
And stupid icq2go has already crashed my Firefox few times!

---

### Post by zarqoon on 2008-07-01
Why do they do this?
OK they do not get advertising revenue from people using 3rd party clients but they get a much higher userbase that will keep more people using their service.
If they restrict use to icq6 a lot of people will stop using icq altogether.
A lot of people may switch to icq6 too but i am sure at least some will be persuaded to use something else by their friends who are unable or unwilling to use icq6

---

### Post by kendon on 2008-07-01
this really sucks big time. i got the 2.4.1 in gutsy from some third-party repo, still the same, 2.4.2 debs won't install, and as i read here it wouldn't help anyway. i would like to quit using icq, but that is not an option as my contact lists consists of icq contacts only...

does anybody have an idea how long we're gonna be stuck with icq2go here?

---

### Post by jimv on 2008-07-01
Holy crap, ICQ is still around?

---

### Post by Pablo89 on 2008-07-01
zarqoon: You know it and I know it. [IRONY]Tell icq admins, will see if they understand.[/IRONY]

---

### Post by Rumo on 2008-07-01
Not surprisingly, it doesn't work with kopete either. 

Don't worry too much, tough. It will probably take just a few days till the patch is out. This has happened already several times in the past...

---

### Post by Pablo89 on 2008-07-01
I would like to compile it immediately when thee patch exists! Please, folks - write here when such patch appears!

By the way, maybe SOME client works? I shall try ysm - the most advanced one, which is, anyway, more useful than icq2go :-).

EDIT: Ysm seems to work! It seems to be a protocol support problem everywhere else, not version string :(.

---

### Post by ales on 2008-07-01
Hi,

Same problem here. I use ICQ too, but most my friends use also Skype or compatible Fring. If it won't work, I will stop using it. It's simple. :) 
Maybe they changed the communication protocol to disable the 3rd party software...

---

### Post by Pablo89 on 2008-07-01
ysm works, so the protocol hasn't changed today. Just, support in popular clients is outdated...

Do you know some nicer working clients? Maybe qip on wine :confused:? Miranda on wine?

---

### Post by keyme on 2008-07-01
Just compiled 2.4.2 from source. Doesn't help.
ICQ is my primary IM client. Damn, I'd really hate installing ICQ 6 on a VirtualBox'd Windows.
WINE doesn't seem to support it (or so their AppDB says).
Guess I'll try qip ( [http://www.qip.ru](http://www.qip.ru) ). Worth a try.


Edit:
Just tried an old mobile client called Jimm (for Java MIDP2.0 devices), it works. Maybe this isn't a protocol problem after all?

---

### Post by ales on 2008-07-01
Hmm, no I don't know. I use QIP on my WM5 Smartphone for now. But I like Pidgin so I'll wait a week and hope it will be solved soon.

---

### Post by Pablo89 on 2008-07-01
keyme: If only works. Please write here when you check if 1) qip works today 2) qip works with wine :)...

ales: not everyone is able to live without icq for a week :(

---

### Post by jrings on 2008-07-01
Until pidgin works again, [www.meebo.com](www.meebo.com) is way better than icq2go...

/edit: Ouch, it doesn't work either...should have checked that first...

---

### Post by zarqoon on 2008-07-01
Just checked out the ysm site. It was not updated for almost 2 years. Does not seem to be a too old problem. If it really works that is. I do not like that it only supports icq

---

### Post by aazikov on 2008-07-01
I found that SIM-IM works normally. (sim-im.org)

---

### Post by Pablo89 on 2008-07-01
zarqoon: Exactly, "that is". But some users don't feel comfortable with CLI :D.

aazikov: Thanks for info! I shall check it out...

Btw, QIP doesn't work for me with wine-1.0-rc1 on debian :(

---

### Post by nicweb on 2008-07-01
There's a security bug in pidgin that may affect icq too... so perhaps icq is blocking pidgin versions to require a fix.

[http://secunia.com/advisories/30881/](http://secunia.com/advisories/30881/)

---

### Post by msundman on 2008-07-01
OK, so ICQ is out. Does anyone know of any XMPP server that:
[LIST=1]
[*]will most likely be running for years and years,
[*]doesn't go offline for a while several times a month, and
[*]delivers all messages?
[/LIST]
I'm currently using jabber.org, but it fails point 2 above. Google Talk fails point 3 (at least between two pidgins where one uses Google Talk and the other uses XMPP with some other server).

---

### Post by Pablo89 on 2008-07-01
msundman made me have an idea: maybe icq jabber transport works somewhere? Anyone?

---

### Post by zarqoon on 2008-07-01
I've been using jabber.org for some time now. And yes it goes offline a lot.
I've been thinking of setting up my own xmpp server but it will most likely fail point 1 and 2

---

### Post by keyme on 2008-07-01
Couldn't download QIP, there seems to be some problem with their site.
However, there is another client called Miranda IM ( [http://www.miranda-im.org/download/](http://www.miranda-im.org/download/) ) that works, and works on WINE. Looks like I'll be using this for a while.

---

### Post by Pablo89 on 2008-07-01
Use google to find some mirror for qip8060.exe if you want. But for me it failed on wine.
Much better option is SIM, like aazikov suggested. It really works!

---

### Post by noof on 2008-07-01
"The topic for #pidgin is: There are issues with ICQ - ignore the message to upgrade and wait"

[http://launchpadlibrarian.net/15741199/pidgin-2.4.2-icq.patch](http://launchpadlibrarian.net/15741199/pidgin-2.4.2-icq.patch)
Should work.

---

### Post by 2GooD on 2008-07-01
Subscribe to [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/) to get notified of progress on this issue. (But please don't spam the bug report with "me too" messages.)

---

### Post by zarqoon on 2008-07-01
just compiled again and the patch noof posted works.
I am online again.

---

### Post by Pablo89 on 2008-07-01
Compiling... will see :)

UPDATE: It really works! Will see if changing that line in my "normal" Pidgin 2.3.1 sources on Debian Etch will solve that...

---

### Post by xlinuks on 2008-07-01
Gee today is like the end of days, my ISP kept telling me for some reason that I'm not authorized to use internet, my local torrent portal says my IP is banned for no reason, the elitetorrents.org seems to be hacked, ICQ stopped working.. what's going on people! :)

---

### Post by LinuX-M@n1@k on 2008-07-01
How do I apply the patch? In which directory must I be?

```
pidgin-2.4.2$ patch -p1 < pidgin-2.4.2-icq.patch can't find file to patch at input line 11
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|#
|# old_revision [dba36543cdde6db127857b0edfdc3ad1969bbd39]
|#
|# patch "libpurple/protocols/oscar/oscar.h"
|#  from [a40e3332eade975c73e344e17bd06d4b99cae751]
|#    to [7853a27f5f8735092ebefef567aaeeccad2a057c]
|#
|============================================================
|--- libpurple/protocols/oscar/oscar.h	a40e3332eade975c73e344e17bd06d4b99cae751
|+++ libpurple/protocols/oscar/oscar.h	7853a27f5f8735092ebefef567aaeeccad2a057c
--------------------------
File to patch: 

```
Which file ?

---

### Post by Pablo89 on 2008-07-01
LinuX-M@n1@k: Use "patch -p0".

---

### Post by Joe_CoT on 2008-07-01
If you have Hardy, x86, and are trusting, I have the binary built with the patch. Straight from apt-get source, with the patch

[http://joeterranova.net/code/pidgin-2.4.1-icqfix.tar.gz](http://joeterranova.net/code/pidgin-2.4.1-icqfix.tar.gz)

The file will stay up til there's an update, or you take my server down.

---

### Post by zarqoon on 2008-07-01
just do it manually
find the file libpurple/protocols/oscar/oscar.h in your source
Open it with some editor
go to line 301
change the 
```
0x010a, \
```
to
```
0x010b, \
```

the patch file does nothing else

compile again

---

### Post by Pablo89 on 2008-07-01
zarqoon is right. One char is not worth downloading the whole updated tarball :-)

---

### Post by Mayfoev on 2008-07-01
Here is (for hardy) a very small bsdiff (binary diff) for this 1-byte change to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0

---

### Post by debuntu on 2008-07-01
right now sim works without problem.

---

### Post by Zappes on 2008-07-01
> **Mayfoev said:**
> Here is (for hardy) a very small bsdiff (binary diff) for this 1-byte change to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0

Absolutely great, works like a charm. Thanks a lot!

---

### Post by 2GooD on 2008-07-01
> **Mayfoev said:**
> Here is (for hardy) a very small bsdiff (binary diff) for this 1-byte change to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0

Great, that's much easier than what I just did: changing it manually with khexedit! :-)

For /usr/lib/purple-2/liboscar.so.0.0.0 with MD5 sum 30762493114a1affa209d8bb41e7afe4, change byte at offset 0x2d1bf from 0x0a to 0x0b.

---

### Post by keyme on 2008-07-01
Patched, works great. Thanks everybody.

Now why in the name of science does pidgin check a value that is of use only to the official client?

---

### Post by khurtsiya on 2008-07-01
Hi,

can anybody please write what exactly I need to do to solve this problem?

I am noob in linux and can not understand above suggestions.

Please make it like 1) do this, 2) do that, 3) do other...

Thaks!

---

### Post by camel1cz on 2008-07-01
Hi,

does anyone have a solution for Gutsy? I cannot compile on my laptop (there is too much libraries missing :-( )

Thanks for help!

---

### Post by Mayfoev on 2008-07-01
> **camel1cz said:**
> Hi,

does anyone have a solution for Gutsy? I cannot compile on my laptop (there is too much libraries missing :-( )

Thanks for help!

As for hardy i386 in a previous post, here is another bsdiff (binary diff) for gutsy i386 to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0
Not tested on gutsy, however, but it should work.

---

### Post by fibbs on 2008-07-01
hey, anybody with x86_64 version who got it working already?

---

### Post by camel1cz on 2008-07-01
> **Mayfoev said:**
> As for hardy i386 in a previous post, here is another bsdiff (binary diff) for gutsy i386 to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0
Not tested on gutsy, however, but it should work.

Works great! Thank you!

---

### Post by Pitufin on 2008-07-01
> **khurtsiya said:**
> can anybody please write what exactly I need to do to solve this problem?

I am noob in linux and can not understand above suggestions.

Please make it like 1) do this, 2) do that, 3) do other...

Close Pidgin program (not only the window).

Download the patch and uncompress it

Open a terminal and:

cd */directory/where/there/is/the/uncompressed/patch*
sudo mv /usr/lib/purple-2/liboscar.so.0.0.0 /usr/lib/purple-2/liboscar.so.0.0.0.original
sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ./pidginicqbsdiff

Too much thanks for the patch!

---

### Post by iacchi on 2008-07-01
> **2GooD said:**
> Great, that's much easier than what I just did: changing it manually with khexedit! :-)

For /usr/lib/purple-2/liboscar.so.0.0.0 with MD5 sum 30762493114a1affa209d8bb41e7afe4, change byte at offset 0x2d1bf from 0x0a to 0x0b.

Hi, I'm running Pidgin 2.4.2 on Debian lenny (amd64). How did you discover the exact offset in which you should change the byte? I'd like to do a similar thing, since I don't want to recompile everything.

---

### Post by khurtsiya on 2008-07-01
> **Pitufin said:**
> 
sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ./pidginicqbsdiff

This command returns 

> michael@michael-laptop:~/Desktop$ sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ./pidginicqbsdiff
sudo: bspatch: command not found


What I am doing wrong?

Thanks!

---

### Post by lancelight on 2008-07-01
> **iacchi said:**
> Hi, I'm running Pidgin 2.4.2 on Debian lenny. How did you discover the exact offset in which you should change the byte? I'd like to do a similar thing, since I don't want to recompile everything.

MM yes I'd be interested in the same thing.  I run PCLinuxOS and the offset discovery method would help a lot.  I tried DLing the source and changing the line by hand but it did not fix anything.  I got the source right from the pidgin sourceforge site, the line was like 304 or something like that but changing the a to b did nothing.

---

### Post by iacchi on 2008-07-01
> What I am doing wrong?

Did you install the bsdiff package?

---

### Post by DerJo on 2008-07-01
For amd64 change liboscar.so.0.0.0 at offset 0x2E8B8 from 0x0A to 0x0B
worked for me

---

### Post by Ampulse on 2008-07-01
Thanks for the patch!

---

### Post by iacchi on 2008-07-01
> **DerJo said:**
> For amd64 change liboscar.so.0.0.0 at offset 0x2E8B8 from 0x0A to 0x0B
worked for me

How do you find these offset?

---

### Post by DerJo on 2008-07-01
trial and error
i searched for 0x010a (seen [here]("http://launchpadlibrarian.net/15741199/pidgin-2.4.2-icq.patch")) in liboscar.so.0.0.0
didn't come up too often, so i tried until i found the right one

---

### Post by lancelight on 2008-07-01
I dont know how they are finding them but my guess is they compile the patch then just diff the binary file to get the offset which would mean the first guy is just trying to sound 'cool' saying he did the offset first which is kinda backwards.  If theres another way, then I'd surely like to hear it because I could use it also since compiling this patch does nothing with the 2.4.2 sourceforge version.

---

### Post by wurdulak on 2008-07-01
Thanks to all for the help!

---

### Post by iacchi on 2008-07-01
> **DerJo said:**
> trial and error
i searched for 0x010a (seen [here]("http://launchpadlibrarian.net/15741199/pidgin-2.4.2-icq.patch")) in liboscar.so.0.0.0
didn't come up too often, so i tried until i found the right one

With which program? I've tried searching 010a with khexedit but it didn't find anything...

---

### Post by Pitufin on 2008-07-01
> **khurtsiya said:**
> What I am doing wrong?

Execute this and retry:

sudo apt-get install bsdiff

---

### Post by DerJo on 2008-07-01
> **lancelight said:**
> I dont know how they are finding them but my guess is they compile the patch then just diff the binary file to get the offset which would mean the first guy is just trying to sound 'cool' saying he did the offset first which is kinda backwards.  If theres another way, then I'd surely like to hear it because I could use it also since compiling this patch does nothing with the 2.4.2 sourceforge version.

this has nothing to do with being cool ;-)
i've just been too lazy to compile, so i used the info from the patch und searched a bit

although it might slightly be cool to be the first one having an offset ;-)

---

### Post by DerJo on 2008-07-01
> **iacchi said:**
> With which program? I've tried searching 010a with khexedit but it didn't find anything...

did it with ghex2
if you find it by looking at the offset manually there's something wrong with your way to search

---

### Post by blauer-affe on 2008-07-01
i found 0x2E8B8 in liboscar.so.0.0.0 how do i change the value? (i use bless as hex editor just installed it and no idea how to use it...)

---

### Post by tuffff on 2008-07-01
Debian Lenny,
md5sum of liboscar.so.0.0.0.bak: 0a66815636ffa48b2883114c9028938d

offset: 0x2cd000
old value: 0x0a
new value: 0x0b

I am sooo happy :D

---

### Post by DerJo on 2008-07-01
> **iacchi said:**
> Hi, I'm running Pidgin 2.4.2 on Debian lenny (amd64). How did you discover the exact offset in which you should change the byte? I'd like to do a similar thing, since I don't want to recompile everything.

I just saw you're not using Ubuntu.
You probably have an other version of liboscar.so.0.0.0
Use the values tuffff posted

---

### Post by lancelight on 2008-07-01
Well surprisingly the search method actually returned 1 result.  I changed it to b, saved, and it STILL doesnt like me.  It just will not let me login to icq because of the version error.  I'm not getting why it works for others yet when I change the exact same value it still decides I dont need to be logged into ICQ.  I'm guessing that searching for the value with a Hexed probably isnt a good idea.  But changing it in the source didnt work either so something isnt right either with the sourceforge version of pidgin or the patch.

---

### Post by blauer-affe on 2008-07-01
plz can you tall a noob how to chnge these values? 
all i see is a FF at the position that is marked if i go to the offset...

---

### Post by DerJo on 2008-07-01
> **lancelight said:**
> Well surprisingly the search method actually returned 1 result.  I changed it to b, saved, and it STILL doesnt like me.  It just will not let me login to icq because of the version error.  I'm not getting why it works for others yet when I change the exact same value it still decides I dont need to be logged into ICQ.  I'm guessing that searching for the value with a Hexed probably isnt a good idea.  But changing it in the source didnt work either so something isnt right either with the sourceforge version of pidgin or the patch.

alright
i'm sorry!
it's 0x0A01, NOT 0x010A you have to search for
change to 0x0B01!
if you're on Ubuntu Hardy with latest packages you should see it at the offset

my fault

---

### Post by eustace on 2008-07-01
There's a patched version of Pidgin in Philipp Dreimann's PPA: 

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/comments/21](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/comments/21)

Instead of hacking with hexedit/bsdiff you can simply install patched pidgin from there. 

BTW, it's enough to just download and install the appropriate .deb for libpurple.

---

### Post by iacchi on 2008-07-01
> **tuffff said:**
> Debian Lenny,
md5sum of liboscar.so.0.0.0.bak: 0a66815636ffa48b2883114c9028938d

offset: 0x2cd000
old value: 0x0a
new value: 0x0b

I am sooo happy :D

mmm... my md5sum is c8142f000df0faeb5d922c0013e1b722

working with ghex2: I went to Edit -> Find (I have it in italian so the translation may differ a little), then in the left part of the windows I insert: "01 0A" and clicked on Find next, but it says it can't find any string like that... Where I'm wrong?

---

### Post by lancelight on 2008-07-01
MMM  I'll try that instead.  6 results for that one, so hopefully one of them works.  If it does I'll be a happy camper :P

---

### Post by DerJo on 2008-07-01
> **blauer-affe said:**
> plz can you tall a noob how to chnge these values? 
all i see is a FF at the position that is marked if i go to the offset...

- make backup of liboscar.so.0.0.0
- grab your favorite hex editor
- jump to offset
- change 0A to 0B
- save
- start pidgin and try

---

### Post by Borlag on 2008-07-01
> **eustace said:**
> There's a patched version of Pidgin in Philipp Dreimann's PPA: 

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/comments/21](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/comments/21)

Instead of hacking with hexedit/bsdiff you can simply install patched pidgin from there. 

BTW, it's enough to just download and install the appropriate .deb for libpurple.

Thank you, the deb package from this link worked perfectly for my amd64 system.

---

### Post by khurtsiya on 2008-07-01
> **iacchi said:**
> Did you install the bsdiff package?

Now I do. And that line returns

> sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ./pidginicqbsdiff
bspatch: fopen(./pidginicqbsdiff): No such file or directory

I guess I downloaded patch file not right. When I follow this link [http://nosnilmot.com/pidgin/pidgin-2.4.2-icq.patch](http://nosnilmot.com/pidgin/pidgin-2.4.2-icq.patch) it shows text
> An earlier patch was based on a random change by a random person in an IRC
channel. It may not be correct and probably is not advisable to use it.

This patch makes libpurple mimic the exact version numbers sent by the
official ICQ6 client, but is not thoroughly tested.

#
# old_revision [dba36543cdde6db127857b0edfdc3ad1969bbd39]
#
# patch "libpurple/protocols/oscar/oscar.h"
#  from [a40e3332eade975c73e344e17bd06d4b99cae751]
#    to [ab1fe743aec4287710fdb56eb412ee30f43ff318]
#
============================================================
--- libpurple/protocols/oscar/oscar.h	a40e3332eade975c73e344e17bd06d4b99cae751
+++ libpurple/protocols/oscar/oscar.h	ab1fe743aec4287710fdb56eb412ee30f43ff318
@@ -258,6 +258,15 @@ struct _ClientInfo
 	"us", "en", \
 }
 
+#define CLIENTINFO_ICQ6_6_0_6059 { \
+	"ICQ Client", \
+	0x010a, \
+	0x0006, 0x0000, \
+	0x0000, 0x17ab, \
+	0x00007535, \
+	"us", "en", \
+}
+
 #define CLIENTINFO_ICQBASIC_14_3_1068 { \
 	"ICQBasic", \
 	0x010a, \
@@ -302,9 +311,9 @@ struct _ClientInfo
 #define CLIENTINFO_PURPLE_ICQ { \
 	"Purple/" VERSION, \
 	0x010a, \
-	0x0014, 0x0034, \
-	0x0000, 0x0bb8, \
-	0x0000043d, \
+	0x0006, 0x0000, \
+	0x0000, 0x17ab, \
+	0x00007535, \
 	"us", "en", \
 }
 

So how can I download patch file?

Thanks!

---

### Post by blauer-affe on 2008-07-01
well thx semms the problem is that i hav another version... at offset 0x2E8B8 the value is FF not 0A

i use pidgin 2.4.2 on Hardy 64

---

### Post by iacchi on 2008-07-01
> **tuffff said:**
> Debian Lenny,
md5sum of liboscar.so.0.0.0.bak: 0a66815636ffa48b2883114c9028938d

offset: 0x2cd000
old value: 0x0a
new value: 0x0b

I am sooo happy :D

Ok, it worked. But the offset is 0x2cd00, you added too much zeroes ;)

---

### Post by DerJo on 2008-07-01
> **khurtsiya said:**
> Now I do. And that line returns



I guess I downloaded patch file not right. When I follow this link [http://nosnilmot.com/pidgin/pidgin-2.4.2-icq.patch](http://nosnilmot.com/pidgin/pidgin-2.4.2-icq.patch) it shows text

So how can I download patch file?

Thanks!

name the file pidginicqbsdiff
the file starts with the first #
not with the text at the beginning
so cut that off

---

### Post by lancelight on 2008-07-01
Well I see what the problem with the source file was.  The guy who posted the original patch had it wrong and then instead of renaming it, he simply fixed the patch file.  Before it was just change 1 line, now its change 4 lines.  Going to try the source route again.  Hex route didnt have any dice for me.

---

### Post by tuffff on 2008-07-01
> **iacchi said:**
> Ok, it worked. But the offset is 0x2cd00, you added too much zeroes ;)

I think most Hexeditors do - like khexedit does - cut of the offset's last digit and show 16 values in that line. Assuming that, 0x2cd000 is right. ;)

---

### Post by debuntu on 2008-07-01
debian sid - amd64 on 32 userland
pidgin - 2.4.2

md5sum of liboscar.so.0.0.0.bak: 0a66815636ffa48b2883114c9028938d

offset: 0x2CD00
old value: 0x0A
new value: 0x0B

worked.

thanx

---

### Post by blauer-affe on 2008-07-01
Works!!!
like DerJo descriped
i searched for 010A and found it about 11 times so i tried to change them to 0B  and found the right one at **offset: 0x2e2fc**

Perhaps this helps someone...

I use Pidgin 2.4.2 on Ubuntu Hardy 64bit

---

### Post by DerJo on 2008-07-01
> **blauer-affe said:**
> Works!!!
like DerJo descriped
i searched for 010A and found it about 11 times so i tried to change them to 0B  and found the right one at **offset: 0x2e2fc**

Perhaps this helps someone...

I use Pidgin 2.4.2 on Ubuntu Hardy 64bit

just to mention:
i hope you changed the ones that didn't work back to 0A or you might get problems with Pidgin crashing ;-)

---

### Post by blauer-affe on 2008-07-01
sure i did ;)

---

### Post by madman-sf on 2008-07-01
c8142f000df0faeb5d922c0013e1b722  liboscar.so.0.0.0

offset 0x002CD00


if you are still searching search for 0A01

---

### Post by DarkDemon[Rus] on 2008-07-01
I thank you guys, as well as i thank you on behalf of my russian comrades, who also use Linux and pidgin :) 
My liboscar.so.0.0.0 MD5sum: 7f6be50c7bd964926aca7fc488142fab
offset: 0x3C508

---

### Post by Greylopht on 2008-07-01
Both of mine were at 0x2CD2B on both laptops.  That is i386 Hardy, with pidgin 2.4.2 and libpurple 2.4.2  changed B0 0A 01 to B0 0B 01  and things worked flawlessly since.

Thanks for all the help tho guys!

---

### Post by hgradeca on 2008-07-01
Hi!
I hope that you will not crucify me ;), but I am using windows and I was wondering whether there is any chance to manually alter the necessary files in order to get Pidgin working again?
Thanks in advance for replying! :)

---

### Post by nowshining on 2008-07-01
If you want a quick fix or you don't want to download and install a whole pidgin deb file, etc.. (updates from your distro should be out soon if it's still receiving security updates, etc..):

& or

if you can't find it:

for khex - u may need to find offset - red numbers, etc.. on left side: 0002:fe00

change 0a to 0b and make sure the cursor isn't a square, ie: u pushed the insert button or else the right letters/numbers will get replaced as u type them

or download and use the liboscar I have uploaded: it's from the pidgin 2.4.2 source

instructions:

in terminal:
```

Exit Pidgin:

(IF need be use locate to find liboscar.so.0.0.0)

sudo cp /usr/local/lib/purple-2/liboscar.so.0.0.0 #to a safe place & not the same place u used to save the attached one.

or

/usr/lib/purple-2/liboscar.so.0.0.0

depending on where you installed pidgin & where liboscar.so.0.0.0 is.

Now for the one you downloaded to hopefully to the desktop.

in terminal:

cd Desktop/

chown root:root liboscar.so.0.0.0

now

in terminal:

sudo mv liboscar.so.0.0.0 /usr/local/lib/purple-2/

or

sudo mv liboscar.so.0.0.0 /usr/lib/purple-2/

depending on where you installed pidgin & where liboscar.so.0.0.0 is.
```

---

### Post by rubzo on 2008-07-01
Hi,

Running the pidgin that comes with eeeXubuntu, version 2.2.1
md5sum for liboscar.so.0.0.0: 14657443b7ae1972c686f25838bf9955

changing 0A to 0B at offset 0x2E83A with hexedit worked a charm for me.

Thanks for your help in making this a quick fix.

-R

---

### Post by dimnix on 2008-07-01
Attached Files
File Type: zip 	liboscarfixedicq.zip (108.7 KB, 3 views)

Ubuntu Hardy i386 Pidgin 2.4.1
Overwrite this file after backup and it's ok. It is work. Very big thanks. 

PS: Sorry for my english.

---

### Post by nowshining on 2008-07-01
> **dimnix said:**
> Attached Files
File Type: zip 	liboscarfixedicq.zip (108.7 KB, 3 views)

Ubuntu Hardy i386 Pidgin 2.4.1
Overwrite this file after backup and it's ok. It is work. Very big thanks. 

PS: Sorry for my english.

Thank's for confirming. :) & ur welcome.

---

### Post by conscious on 2008-07-02
By the way, the fix from Pidgin (v. 2.4.3) is already out.

---

### Post by khurtsiya on 2008-07-02
> **DerJo said:**
> name the file pidginicqbsdiff
the file starts with the first #
not with the text at the beginning
so cut that off
Thanks for helping me!
This brings another error.

> michael@michael-laptop:~/Desktop$ mv pidgin-2.4.2-icq.patch pidginicqbsdiff
michael@michael-laptop:~/Desktop$ sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ./pidginicqbsdiff
[sudo] password for michael:
bspatch: Corrupt patch

michael@michael-laptop:~/Desktop$

---

### Post by borlosky on 2008-07-02
after installing patch, pidgin no longer opens. had to completely remove pidgin, then reinstall, so i'm back to square one with being unable to login to icq.

---

### Post by 808y on 2008-07-02
> **khurtsiya said:**
> Thanks for helping me!
This brings another error.

you got the wrong file, get the one posted by #40 called : 
"pidginicqbsdiff.gz"

extract that file to your desktop.
you will get a file called "pidginicqbsdiff on your desktop"
open a terminal and use:
"sudo bspatch /usr/lib/purple-2/liboscar.so.0.0.0.original /usr/lib/purple-2/liboscar.so.0.0.0 ~/Desktop/pidginicqbsdiff"

---

### Post by cwhisperer on 2008-07-02
> **Mayfoev said:**
> Here is (for hardy) a very small bsdiff (binary diff) for this 1-byte change to apply with bspatch on /usr/lib/purple-2/liboscar.so.0.0.0

works fine for me ;)

---

### Post by q11q11 on 2008-07-02
patching didn`t work for me, but thanks to **Joe_CoT** and his patched compiled version at [http://joeterranova.net/code/pidgin-2.4.1-icqfix.tar.gz](http://joeterranova.net/code/pidgin-2.4.1-icqfix.tar.gz)

---

### Post by benste on 2008-07-02
One question for normal users, when will 2.1.4 be realesed via updatemanager???
this is an important part of ubuntu or???

---

### Post by el_noobe on 2008-07-02
Erm, I am a little confused now. I had the same problem with Pidgin and ICQ yesterday, but did not have enough time until today in order to check possible solutions. When I found that Pidgin 2.4.3 was released today (including the ICQ fix), I downloaded the source code and compiled it locally. Now, I am still experiencing the same error "Client version is too old..."! What have I done wrong?:confused:

---

### Post by Gunman1982 on 2008-07-02
You probably have still the pidgin package of ubuntu installed. remove the pidgin package via synaptiv or apt-get and then reinstall it via the source (don't forget to do the 'sudo make install' in the end). Or you wait until the maintainer uploads the newest version to the ubuntu repos.

---

### Post by ghoulsblade on 2008-07-02
i compiled from source, and it worked when starting
/usr/src/pidgin-2.4.3/pidgin/pidgin manually,
i did deinstalled the old pidgin and run "sudo make install", but no idea where that actually installed it, i'm not that comfortable with configure options, and already had to go through it a dozen times because of missing libs or something, so maybe it got some path wrong.
i hope there'll be a package soon =)

---

### Post by Gunman1982 on 2008-07-02
If you do the 'sudo make install' it installs it in your system folders, just execute pidgin, it should find the command like it did when you installed it through synaptic/apt-get.

---

### Post by zavizionov on 2008-07-02
I have solved this issue for Gutsy version of Pidgin [http://zavizionov.blogspot.com/2008/07/pidgin-connect-problem.html](http://zavizionov.blogspot.com/2008/07/pidgin-connect-problem.html)

---

### Post by heatblazer on 2008-07-02
I`ve downloaded a pakage from this thread pidgin-2.4.1-icqfix and reinstalled from there. Nothing happens. I am using hardy?

---

### Post by heatblazer on 2008-07-02
> **nowshining said:**
> If you want a quick fix or you don't want to download and install a whole pidgin deb file, etc.. (updates from your distro should be out soon if it's still receiving security updates, etc..):

& or

if you can't find it:

for khex - u may need to find offset - red numbers, etc.. on left side: 0002:fe00

change 0a to 0b and make sure the cursor isn't a square, ie: u pushed the insert button or else the right letters/numbers will get replaced as u type them

or download and use the liboscar I have uploaded: it's from the pidgin 2.4.2 source

instructions:

in terminal:
```

Exit Pidgin:

(IF need be use locate to find liboscar.so.0.0.0)

sudo cp /usr/local/lib/purple-2/liboscar.so.0.0.0 #to a safe place & not the same place u used to save the attached one.

or

/usr/lib/purple-2/liboscar.so.0.0.0

depending on where you installed pidgin & where liboscar.so.0.0.0 is.

Now for the one you downloaded to hopefully to the desktop.

in terminal:

cd Desktop/

chown root:root liboscar.so.0.0.0

now

in terminal:

sudo mv liboscar.so.0.0.0 /usr/local/lib/purple-2/

or

sudo mv liboscar.so.0.0.0 /usr/lib/purple-2/

depending on where you installed pidgin & where liboscar.so.0.0.0 is.
```


Thanx a lot. This helped! KUDOS 4 U!!

---

### Post by aev on 2008-07-02
> **DerJo said:**
> For amd64 change liboscar.so.0.0.0 at offset 0x2E8B8 from 0x0A to 0x0B
worked for me

Worked for AMD64 - THANKS! :D

---

### Post by zavizionov on 2008-07-02
My Pidgin's version is 1:2.2.1-1ubuntu4.1 Gutsy
/usr/lib/purple-2/liboscar.so.0.0.0

offset 0002:e83a

---

### Post by jimmal on 2008-07-02
Meine Pidgin Version is 1:2.2.1-1ubuntu4.1 Gutsy

offset 0x2DF51 -> 0A zu 0B

**Schritte:**

/usr/lib/purple-2# md5sum liboscar.so.0.0.0 
06f846ee32732d56ec8ada13590d9509  liboscar.so.0.0.0


/usr/lib/purple-2# ghex2 liboscar.so.0.0.0

Bearbeiten -> gehe zu Byte 0x2DF51 -> 0A zu 0B. 
Datei -> speichern

pidgin geht.

---

### Post by aev on 2008-07-03
> **2GooD said:**
> Great, that's much easier than what I just did: changing it manually with khexedit! :-)

For /usr/lib/purple-2/liboscar.so.0.0.0 with MD5 sum 30762493114a1affa209d8bb41e7afe4, change byte at offset 0x2d1bf from 0x0a to 0x0b.

Editing with hexedit seems sooo much easier than patches for small things. Thanks for pointing out the right offsets :)

---

### Post by conscious on 2008-07-03
The update is available in hardy-proposed now.

---

### Post by Sim777 on 2008-07-03
I'm sorry for being such a nooob. 


What exactly do I modify in liboscar.so.0.0.0? I opened file in hexedit. Now what do I search for and what do I modify?


Here's one of lines.... 
0002D1B0   49 89 C5 74  35 45 85 F6  7E 30 48 89  DD 45 31 E4  I..t5E..~0H..E1.

I'm on gutsy 64. pidgin is 2.2.1

---

### Post by conscious on 2008-07-03
Try offset 0x2E8B8 as suggested in [post #55]("http://ubuntuforums.org/showpost.php?p=5300296&postcount=55").

---

### Post by Sim777 on 2008-07-03
> **conscious said:**
> Try offset 0x2E8B8 as suggested in [post #55]("http://ubuntuforums.org/showpost.php?p=5300296&postcount=55").

```

0002E8B0   FD FF EB 02  31 ED 48 89  E8 48 8B 5C  24 08 48 8B  ....1.H..H.\$.H.

```
The first two characters in third column "E8" = 0x2E8B8 / 0x42E08 

What does it mean "offset" and how do I do it.

---

### Post by conscious on 2008-07-03
This string:
> **Sim777 said:**
> ```

0002E8B0   FD FF EB 02  31 ED 48 89  E8 48 8B 5C  24 08 48 8B  ....1.H..H.\$.H.

```

means that there is "FD" at offset 0002E8B0, "FF" at offset 0002E8B1, ..., "8B" at offset 0002E8BF (all numbers here are hexadecimal).

It looks like at both offsets posted above, there is no "0A" in your file (you must have a different binary). There is still a couple of options for you: you can search for "0A01" if the binary. There will probably be several matches, so you can backup the file and try changing them one "0A" to "0B" at a time like the posters above did. This looks risky though, so alternatively you can install an update from gutsy-proposed ([they say]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591") it's already there).

---

### Post by Sean Heron on 2008-07-03
> **conscious said:**
> The update is available in hardy-proposed now.

I just wanted to say thank you to you for that hint, my Pidgin now happily works again :D. For clarification for other users: add the line 

```
deb http://en.archive.ubuntu.com/ubuntu/ hardy-proposed main 
```

in the text file: /etc/apt/sources.list 
(or if you prefer, use the graphical "source manager" and add the line to the third-party software). 

If you have problems doing either of these, you might go to the documentation wiki and search for "SoftwareRepositories" and then look for how to add these (which is what your doing in adding the above line to the text file.

I'm only explaining all this, because I had to remind myself, and thought that some people might not know :D (also //de.archive... did not yet have the update).
Regards
         Sean

---

### Post by Sim777 on 2008-07-03
Found it. 

000261E0   E0 **0A 01** 00  48 8D 3D 16  02 01 00 48  89 C3 BA 05  ....H.=....H....  

requires change to **0B**

---

### Post by StOoZ on 2008-07-03
> **Sean Heron said:**
> I just wanted to say thank you to you for that hint, my Pidgin now happily works again :D. For clarification for other users: add the line 

```
deb http://en.archive.ubuntu.com/ubuntu/ hardy-proposed main 
```

in the text file: /etc/apt/sources.list 
(or if you prefer, use the graphical "source manager" and add the line to the third-party software). 

If you have problems doing either of these, you might go to the documentation wiki and search for "SoftwareRepositories" and then look for how to add these (which is what your doing in adding the above line to the text file.

I'm only explaining all this, because I had to remind myself, and thought that some people might not know :D (also //de.archive... did not yet have the update).
Regards
         Sean

can I use this on gusty?

---

### Post by neosofti on 2008-07-03
All is working with the packages from [http://getdeb.net/release/2884](http://getdeb.net/release/2884).

:lolflag:

---

### Post by conscious on 2008-07-04
> **StOoZ said:**
> can I use this on gusty?

The patch is already in gutsy-updates. You will receive it if you have "recommended updates" enabled in System -> Administration -> Software Sources.

---

### Post by Fonsis on 2008-07-04
pls delete

---

### Post by nowshining on 2008-07-04
by the way when using hexedit on the one I had - there was about only 7 0a01's :P the third from the last was the one if i rem. correctly.

---

### Post by borlosky on 2008-07-05
comfirmed, update from update manager solved issue. just run System > Administration > Update Manager:)

---

### Post by TransplantedCanuck on 2008-07-06
Is there a quick / easy way to fix this with funpidgin? (I don't like a tiny chatbox).

---

### Post by fraktalek on 2008-07-08
I have recommended updates in gutsy, but I still didn't receive the update. Even after repository reload.
Where should I look for the problem?

---

### Post by conscious on 2008-07-10
> **TransplantedCanuck said:**
> Is there a quick / easy way to fix this with funpidgin? (I don't like a tiny chatbox).
Doesn't funpidgin release updates? Anyway, I believe it uses the same libpurple, so you should be able to fix it by looking for the characteristic byte sequence and changing it (described above).

> **fraktalek said:**
> I have recommended updates in gutsy, but I still didn't receive the update. Even after repository reload.
Where should I look for the problem?
Regional mirrors are sometimes slow (could it be this slow?) Are you sure you are using the central server for updates?

---

### Post by fraktalek on 2008-07-13
Well, still no update even after I switched from a regional mirror to the main server :-/

---

