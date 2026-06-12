---
title: "Trouble compiling SMAUG files"
date: 2008-03-30
forum: General Help
---

### Post by Raumz on 2008-03-30
Hi.  I am trying to create a MUD so I loaded Ubuntu onto a old desktop I have.  I chose SMAUG as the code base so I found a tutorial on how to load up and start a SMAUG based MUD (tutorial here [http://www.cs.utk.edu/~london/smaug/]("http://www.cs.utk.edu/~london/smaug/")).  I downloaded the code and followed the steps until I needed to compile using the "make all" command.  This is a sample of the error messages I got:


act_comm.c:2918: warning: incompatible implicit declaration of built-in function ‘sprintf’
act_comm.c:2923: error: ‘CHAR_DATA’ has no member named ‘deaf’
act_comm.c:2924: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c: In function ‘knows_language’:
act_comm.c:2941: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2943: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2943: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c:2945: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2945: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c:2953: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2953: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2959: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2969: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c: In function ‘can_learn_lang’:
act_comm.c:2982: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:2986: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c: In function ‘do_speak’:
act_comm.c:3053: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c:3062: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:3064: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c: In function ‘do_languages’:
act_comm.c:3080: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:3125: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:3125: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:3126: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c:3128: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c:3128: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c:3135: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c:3144: error: ‘CHAR_DATA’ has no member named ‘practice’
act_comm.c:3150: error: ‘CHAR_DATA’ has no member named ‘practice’
act_comm.c:3155: error: ‘CHAR_DATA’ has no member named ‘speaks’
act_comm.c:3176: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c:3177: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c:3177: error: ‘CHAR_DATA’ has no member named ‘speaking’
act_comm.c: In function ‘do_traffic’:
act_comm.c:3190: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c: In function ‘do_wartalk’:
act_comm.c:3201: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c: In function ‘do_racetalk’:
act_comm.c:3212: error: ‘CHAR_DATA’ has no member named ‘act’
act_comm.c: In function ‘add_profane_word’:
act_comm.c:3251: warning: incompatible implicit declaration of built-in function ‘strlen’
act_comm.c:3342: warning: incompatible implicit declaration of built-in function ‘strcat’
make[1]: *** [act_comm.o] Error 1
make[1]: Leaving directory `/home/raumz/Desktop/smaug/src'
make: *** [all] Error 2

I tried all the tips it listed on the site and I still can't get this to work.
I was wondering if anyone here is familiar with this and if they can help me out.
Thanks for your time.

---

