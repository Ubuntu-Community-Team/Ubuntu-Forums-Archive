---
title: "Curious non-behavior of LD_LIBRARY_PATH"
date: 2022-05-29
forum: General Help
---

### Post by mark allyn on 2022-05-29
Hello everyone,

In /home/mark/myso I have placed libtest2.so with a symlink to libtest2.so.1.0 and a symlink from libtest2.so.1 to libtest2.so.1.0.  This is a conventional arrangement of shared libraries, as everyone will note.  Note also that I have not placed these files in /usr/local/lib.  In addition, I have LD_LIBRARY_PATH set to /home/mark/myso.  Now here is the curious part:

If I attempt to link callshare.o to the files in myso using:

  gcc -o callshare callshare.o -ltest2,

 the system replies that there is no file libtest2.so, in spite of the fact that  LD_LIBRARY_PATH has been  set to the appropriate path.  But, if I issue the following command:

  gcc -o callshare -L./myso callshare.o -ltest2,

the executable is built and runs correctly.

So, can someone tell me why the linker can't find the file in myso even though the library path is set to the right value?

Thanks,
Mark Allyn

---

### Post by TheFu on 2022-05-29
Please prove all you have claimed.  Use commands and the output from those commands, so we don't have to trust the claims.  

Use forum code tags for things typed into and show inside the terminal. I see you tried to show the gcc commands, but there is all sorts of important missing information, like the PWD, which would be shown by the default prompt.  Also, the trailing ',' for commands is wrong.

I'd like to see the ACTUAL LD_LIBRARY_PATH, not what you claim it is.
I'd like to see the file permissions AND the PWD for the files involved.
And if you have a Makefile, it would be helpful.

BTW, this is not general help. It is definitely programming and should be in the Development sub-forum. Building code would scare most Ubuntu users.

---

### Post by mark allyn on 2022-05-29
Hiya Fu,

I'm going to repost this on the Development subforum, as you suggest.

Comments on your comments.

First, I don't understand your desire to have me "prove" my claims.  An odd request in my view.

PWD is /home/mark --- as shown by my original post.
Comma in command  -- if you followed my use of the language you should realize that the comma was there to complete a thought, not part of the command.

Third, the file permissions are correct and no point in providing you with them.

I'm not using a Makefile.  I'm using a BASH script.  I've been through the script god knows how many times.  There is nothing wrong with it.  It works.  You can see this by virtue of the second gcc command I posted (don't pay attention to the comma; it merely is there for grammatical purposes as required by the English language).  What doesn't work is LD_LIBRARY_PATH.

Mark

---

### Post by Holger_Gehrke on 2022-05-29
LD_LIBRARY_PATH is for ld.so - the run-time shared object linker - and allows the user to add directories to override the default locations searched for libraries when running a program. If you look at the ENVIRONMENT section of the manual page for gcc you'll find that this variable is not mentioned. A variable that is mentioned is LIBRARY_PATH which - unless I misread the description - should do what you want.

Holger

---

### Post by TheFu on 2022-05-29
A moderator will likely move this thread, so you shouldn't repost. That would be a duplicate.

I asked for for proof to ensure some simple thing wasn't the issue. Since that isn't coming, I cannot help. There are some things that seem odd to me, but without more details, I cannot ensure those aren't wild guesses.  Good luck.

---

### Post by mark allyn on 2022-05-29
Hi Holger and TheFu,

Holger:  your solution fixed my problem, near as I can tell.  What is now mysterious to me is what purpose LD_LIBRARY_PATH serves, since the simpler syntax does everything I thought the more complex "LD_" was designed to do and which is much more often mentioned in the literature.  Perhaps you could elaborate.

TheFu:  From above you can see that no moderation needs to occur.  I do thank you however for clarifying which forum my question was designed to answer.  Best of luck to you too.

Thanks to both of you!

Mark

---

### Post by Holger_Gehrke on 2022-05-29
LD_LIBRARY_PATH is used at run-time, not during compilation. It's mostly a kludge to point the loader for dynamic libraries at a custom, application specific library or set of libraries. It's useful for getting old program for which source is not available to run, provided you can find the old libraries they were compiled against. Another use-case would be programs which need newer versions of one or more libraries than are available for your distribution. You could compile the libraries yourself, put them with the program and point LD_LIBRARY_PATH at the directory where the program and the library/ies are.

Holger

---

