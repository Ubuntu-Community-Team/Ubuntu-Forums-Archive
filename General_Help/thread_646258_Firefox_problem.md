---
title: "Firefox problem"
date: 2007-12-21
forum: General Help
---

### Post by _Frank_ on 2007-12-21
I'm on ubuntu 7.10 and my firefox freezes a lot, often when i use flash. I have to quit it and start a new session cause nothing responds. I see that a lot of people seems to have problems with firefox on ubuntu but personnally my firefox doesn't turn grey like other people. Is it the same problem? How do i fix that?

Thanks a lot

---

### Post by TidusBlade on 2007-12-21
I think firefox only turns gray when using Compiz, so depends, I find firefrox crashing alot more using Compiz Fusion for some reason. You might wanna try out the official firefox package instead of the one from ubuntu repos, it's 2 different things actually, I found the official firefox from [here](http://www.mozilla.com/en-US/firefox/?from=getfirefox) to work better...

---

### Post by _Frank_ on 2007-12-21
i'm very newb, it's my first time ever with ubuntu and i've never install a tar.gz file. Now i've done it but were do i extract it? where do i put the file? thanks

---

### Post by _Frank_ on 2007-12-21
up

---

### Post by p_quarles on 2007-12-21
There's actually a separate project called Swiftweasel ([link]("http://sourceforge.net/projects/swiftweasel/")) that pre-compiles the Firefox source code for Linux. You can install this easily, without needing to compile anything yourself. 

That said, there's no guarantee that this will solve your problem. The problem is that with many video cards, Compiz Fusion has trouble dealing with multimedia playback. So, the bug consists of the interaction between Flash and Compiz, and most likely has little to do with Firefox itself. You can, of course, disable Compiz altogether, and you'll probably have fewer problems with video playback.

---

### Post by _Frank_ on 2007-12-22
that sucks a lot. I've been told that ubuntu worked great and was more user friendly for newcomers. Now i have to close my firefox sessions 5-6 times a day because of a bug that should clearly be fix. 

In fact this bug happens when i'm running java and flash. More often with java.  And i have to use it every day. 

There's really no real way to fix that bug?

---

### Post by p_quarles on 2007-12-22
> **_Frank_ said:**
> that sucks a lot. I've been told that ubuntu worked great and was more user friendly for newcomers. Now i have to close my firefox sessions 5-6 times a day because of a bug that should clearly be fix. 

In fact this bug happens when i'm running java and flash. More often with java.  And i have to use it every day. 

There's really no real way to fix that bug?
Yes, there's a pretty easy way to fix the bug, and it's already been suggested by both TidusBlade and myself: turn off Compiz Fusion. If you're not sure how to do this, just ask.

---

### Post by _Frank_ on 2007-12-22
you seem to say that this will maybe make firefox run better. I'll give it a try, and i'll come here if it's not better.

so how do i turn off compiz fusion? What is it exactly, and what will i lose by doing this?

thanks

---

### Post by p_quarles on 2007-12-22
Compiz is the desktop effects program -- it gives you the 3D eyecandy that you may have noticed. It's nice, but it's probably not worth the frustration of Firefox crashing all the time. 

You can get to your display settings by right-clicking on the desktop. I believe the Compiz settings are in the right-most tab of that menu. You should be able to disable it from that menu. (I say "should" because I don't use it frequently, and can't remember all the precise details).

---

### Post by pyronaut on 2007-12-22
go to the system preferences menu and there you'll see appearance ... when you lcick on that th first tab will be themes in the menu.. one of the tabs is settings clikc on it and it should have four options for the type of desktop setting you want. you can dowlaod a tar.gz file to any directory you want. the better option would be to search to search for a deb file for the package since it can be autmatically installed :)

---

### Post by _Frank_ on 2007-12-22
bad news, it's already disable cause my graphic card doesn't support that. So compiz fusion is obviously not the problem.....

any other suggestion?

---

### Post by p_quarles on 2007-12-22
To try and find the source of the problem, you can run Firefox from the terminal. Just open up a term, and type "firefox" (nb: it's case sensitive). Go to YouTube or something so you can try to get it to crash, and make a note of the terminal output at the time of the crash.

---

### Post by euthyfro on 2007-12-22
i'm having the same problem, & running firefox from the terminal gives me
"segmentation fault (core dumped)"
when the crash occurs.

also, nothing i download is showing up in the downloads history in tools(or even causing the download window to open when i get it), it gets saved to the area specified but when i go to use the file (an .lhz in gnomekiss is the case right now) it doesn't show up.  it did the same thing when i downloaded a gutsy install disc & tried to burn it in k3b.

---

### Post by euthyfro on 2007-12-22
the 2nd problem i mentioned was fixed by switching from the custom 3rd-party theme i had been using.  i've yet to find 1 i like that doesn't screw something like this up

---

### Post by _Frank_ on 2007-12-23
so is there a way to fix that problem? It's so a big glitch i'm amazed it's not fix yet.

---

### Post by euthyfro on 2007-12-24
i spoke too soon, i'm still not getting anything to download successfully in firefox...ugh

---

