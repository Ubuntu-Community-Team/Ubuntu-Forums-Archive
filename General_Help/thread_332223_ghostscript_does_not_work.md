---
title: "ghostscript does not work?"
date: 2007-01-05
forum: General Help
---

### Post by monkblah on 2007-01-05
Hi, I have Dapper on my machine & want to use ghostscript to print postscript files from the command line.

I have a test file called test2.ps. I can open it with ghostview and it displays properly; I can tell ghostview to print it via lpr and it prints properly.

But when I try to run gs on it to send it directly to print or stdout, it fails, just spewing out a lot of garbage.

I have tried commands like 

cat test2.ps | gs -dSAFER -dNOPAUSE -sDEVICE=ljet4 -sOutputFile=- | lpr 

and

cat test2.ps | gs -dSAFER -dNOPAUSE -sDEVICE=ljet4 -sOutputFile=-

and

cat test2.ps | gs -sOutputFile=-

but regardless, it just spews or prints out garbage, like:

```

$ cat test2.ps | gs -sOutputFile=-
ESP Ghostscript 815.02 (2006-04-19)
Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS<2>GS<4>GS<6>GS<8>GS<10>GS<12>GS<14>GS<16>GS<18>GS<20>GS<22>GS<24>GS<26>GS<28>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS>GS<1>GS<3>GS<2>GS>GS<1>GS>GS>GS<1>GS>GS<1>GS>GS>GS<1>GS>GS<1>GS>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   2   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1   4   %oparray_pop   --nostringval--   1   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:36/191(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 17
GS<1>GS<2>GS<1>GS<2>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<2>GS<1>GS<2>GS<1>GS<1>GS<3>GS<1>GS<3>GS<1>GS<3>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<2>GS<1>GS<2>GS<1>GS<3>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<2>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<1>GS<3>GS<1>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   3   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   2   4   %oparray_pop   --nostringval--   2   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:73/191(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 17
GS<2>GS<3>GS<2>GS<3>GS<2>GS<2>GS<3>GS<2>GS<3>GS<2>GS<3>GS<2>GS<3>GS<2>GS<3>GS<2>GS<3>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<2>GS<10>GS<18>GS<26>GS<34>GS<42>GS<50>GS<58>GS<66>GS<74>GS<82>GS<90>GS<98>GS<103>GS<112>GS<122>GS<130>GS<2>GS<2>GS<3>GS<2>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   4   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   3   4   %oparray_pop   --nostringval--   3   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:92/191(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 17
GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<4>GS<3>GS<4>GS<3>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<4>GS<5>GS<5>GS<3>GS<3>GS<3>GS<3>GS<3>GS<4>GS<3>GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<3>GS<4>GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<4>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<4>GS<5>GS<3>GS<4>GS<5>GS<3>GS<4>GS<5>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>Loading NimbusSanL-Bold font from /var/lib/defoma/gs.d/dirs/fonts/n019004l.pfb... 2309412 917938 1870204 552250 4 done.
GS<3>GS<3>Loading NimbusRomNo9L-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n021003l.pfb... 2346172 1040085 1870204 557830 4 done.
GS<3>GS<3>GS<3>Loading NimbusRomNo9L-ReguItal font from /var/lib/defoma/gs.d/dirs/fonts/n021023l.pfb... 2483412 1175756 1870204 564554 4 done.
GS<3>GS<3>GS<3>Loading NimbusRomNo9L-Medi font from /var/lib/defoma/gs.d/dirs/fonts/n021004l.pfb... 2620652 1310619 1870204 572349 4 done.
GS<3>GS<3>Loading NimbusMonL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n022003l.pfb... 2757892 1432143 1890300 581317 4 done.
GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>GS<3>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   5   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   4   4   %oparray_pop   --nostringval--   4   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:149/191(L)--
Current allocation mode is local
Current file position is 4
GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>GS<4>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   6   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   5   4   %oparray_pop   --nostringval--   5   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:149/191(L)--
Current allocation mode is local
Current file position is 4
GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>GS<5>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   7   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   6   4   %oparray_pop   --nostringval--   6   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:149/191(L)--
Current allocation mode is local
Current file position is 4
GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>GS<6>ERROR: /invalidrestore in --restore--
Operand stack:
   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   8   4   %oparray_pop   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   7   4   %oparray_pop   --nostringval--   7   4   %oparray_pop   --nostringval--
Dictionary stack:
   --dict:1119/1686(ro)(G)--   --dict:0/20(G)--   --dict:81/200(L)--   --dict:149/191(L)--
Current allocation mode is local
Current file position is 5

```

I have the following gs- packages installed.
```

$ dpkg-query -l | grep gs-
ii  gs-common                              0.3.9ubuntu1                            Common files for different Ghostscript relea
ii  gs-esp                                 8.15.2.dfsg.0ubuntu1-0ubuntu1           The Ghostscript PostScript interpreter - ESP
ii  gs-gpl                                 8.15-4ubuntu3                           The GPL Ghostscript PostScript interpreter

```

Why is this happening and how can I fix it?  Thanks for any help.

---

### Post by DigitalAxis on 2007-01-22
Uh, maybe try running **gs** with the **-q** option as well?  That should make its output quiet...

Regardless, I *think* UNIX printer drivers can print postscript files directly, at least if they've been configured with CUPS.  In that case, you can just type **lpr test2.ps** directly.

That is, unless you're using Ghostscript because CUPS didn't work with your printer, in which case I have no idea.

---

### Post by monkblah on 2007-01-27
> **DigitalAxis said:**
> Uh, maybe try running **gs** with the **-q** option as well?  That should make its output quiet...


I'm not sure you intended this, but your tone comes across as quite patronizing. That sort of attitude is never helpful, and seems particularly uncalled for since your suggestions are useless.

The problem isn't that I don't like watching ghostscript error messages, the problem is that ghostscript doesn't work.

> **DigitalAxis said:**
> 
Regardless, I *think* UNIX printer drivers can print postscript files directly.... you can just type **lpr test2.ps** 


You think wrong, that outputs garbage. My printer isn't postscript, that's why I wanted to use ghostscript.

> **DigitalAxis said:**
> 
That is, unless you're using Ghostscript because CUPS didn't work with your printer, in which case I have no idea.

Yes, you do have no idea. Which is fine, it's just odd that you felt the need to post a patronizing reply.

For anyone having the same problem with broken ghostscript on Ubuntu: I decided to use a program called enscript, which works well for my purposes.

---

