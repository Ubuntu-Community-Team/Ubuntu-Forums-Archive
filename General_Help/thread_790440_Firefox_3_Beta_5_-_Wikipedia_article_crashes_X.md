---
title: "Firefox 3 Beta 5 - Wikipedia article crashes X"
date: 2008-05-11
forum: General Help
---

### Post by tghe-retford on 2008-05-11
I have an odd problem which occurred when I was doing some research for the British Monarchy on Wikipedia for a forum posting. When I tried to access this page, X immediately crashed and dumped me back to the login screen.

[http://en.wikipedia.org/wiki/Line_of_succession_to_the_British_throne](http://en.wikipedia.org/wiki/Line_of_succession_to_the_British_throne)

I have only seen this problem happen on that page.

Anyone else having this problem when accessing that page? Any suggestions or logs I could check to diagnose the problem and report it?

Thanks in advance.

---

### Post by Coplen on 2008-05-11
Nothing here.

Someone more knowledgeable than I should be by eventually to help you out.

---

### Post by ibuclaw on 2008-05-11
Hmm... that is very interesting indeed.

The reset for me happened when I got 5/6ths of the way down.

I'm just going through the debugging now (dmesg doesn't seem useful):
```

[ 4744.958281] rix 10 (0) bad ratekbps 0 mode 6
[ 5920.507070] rix 9 (0) bad ratekbps 0 mode 6

```
Something to do with my wireless device I think. (I have PCI WPN311).

If you want to debug it:
Wait until the next minute arrives (ie: if it's 7:04 now, don't do this until the clock strikes 7:05...)

When it does, quickly open the page and scroll down till you cause a crash.

Then when you log back in issue the command: (You can press **Alt+F2** and paste this there).
```
gksu cat /var/log/* | grep 19:05 > ~/Desktop/wikipedia.crash.log
```
Your answer is in there (Somewhere).

Regards
Iain

---

### Post by tghe-retford on 2008-05-11
> **tinivole said:**
> If you want to debug it:
Wait until the next minute arrives (ie: if it's 7:04 now, don't do this until the clock strikes 7:05...)

When it does, quickly open the page and scroll down till you cause a crash.

Then when you log back in issue the command: (You can press **Alt+F2** and paste this there).
```
gksu cat /var/log/* | grep 19:05 > ~/Desktop/wikipedia.crash.log
```
Your answer is in there (Somewhere).
I tried your suggestion (replacing the time with 19:18 when I navigated to the page) and all I got was this output:

```
Binary file (standard input) matches
```
and nothing else. :(

---

### Post by papoanaya on 2008-05-11
> **tghe-retford said:**
> 

I have an odd problem which occurred when I was doing some 
[chomp...]
Anyone else having this problem when accessing that page? Any suggestions or logs I could check to diagnose the problem and report it?

Thanks in advance.


I was accessing some pages in Wikipedia and the whole X (or system) froze on me.  I personally removed firefox3 and reverted to firefox 2 (I was also having problems with the certificates on OWA as well).  You may want to try to use epiphany or revert to firefox2.

Luis

---

### Post by ibuclaw on 2008-05-11
Here are my sequence of events:
```

[Sun May 11 19:13:06 2008] 140580kb available for preloading, using 137080kb of it
[Sun May 11 19:13:06 2008] readaheading 379 files
[Sun May 11 19:13:28 2008] 311530kb available for preloading, using 311356kb of it
[Sun May 11 19:13:28 2008] readaheading 1098 files
May 11 19:13:28 fredbuntu gdm[5649]: pam_unix(gdm:session): session closed for user iain
[Sun May 11 19:13:29 2008] client connected from 8105[0:0]
[Sun May 11 19:13:29 2008] 1 client rule loaded
[Sun May 11 19:13:30 2008] client connected from 8105[0:0]
[Sun May 11 19:13:30 2008] 1 client rule loaded

```

Looks like the "readaheading" cache crashes due to a sudden spike (triples in size from loading the page at 19:13:06, to the moment X crashes at 19:13:28 ).

As you can see, my session is closed immediately afterwards, and the following two seconds is X restarting itself.

It could be a safety measure trap to prevent DDOSing (or Linux freezing indefinitely.)

But in any case I can't say no more, as it's not in my league of knowledge.

But, if you really need the page, you can view it for offline content safely (at least, I could scroll up and down alright without errors).

Regards
Iain

---

### Post by tghe-retford on 2008-05-11
> **papoanaya said:**
> I was accessing some pages in Wikipedia and the whole X (or system) froze on me.  I personally removed firefox3 and reverted to firefox 2 (I was also having problems with the certificates on OWA as well).  You may want to try to use epiphany or revert to firefox2.

Luis
Epiphany also caused X to crash when I tried to access the page.

---

### Post by ibuclaw on 2008-05-11
> **tinivole said:**
> 
But, if you really need the page, you can view it for offline content safely (at least, I could scroll up and down alright without errors).


Which is **File>Save Page As...** in Firefox Tabs, by the way.

Alternately just hit "**CTRL+S**"

Regards
Iain

---

