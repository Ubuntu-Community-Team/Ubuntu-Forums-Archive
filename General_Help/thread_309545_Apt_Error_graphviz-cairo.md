---
title: "Apt Error: graphviz-cairo"
date: 2006-11-29
forum: General Help
---

### Post by Mr Fat Bat on 2006-11-29
Hi guys,

Every time I install or remove packages with apt (including using Synaptic) I get the following error:

> 
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
I've tried removing graphviz-cairo but:

> $ sudo apt-get remove graphviz-cairogives

> Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
It's been bugging me for a week now ;)

---

### Post by calvmari on 2006-12-03
I have the same problem, but with a different library. Here's a link to my post: [http://www.ubuntuforums.org/showthread.php?t=311333&highlight=apt-get+127](http://www.ubuntuforums.org/showthread.php?t=311333&highlight=apt-get+127)

I have no idea how to fix this, just offering some empathy since I'm going through the same thing ](*,) 

I'd imagine if we could someone manually delete it from apt-get we could get around this error. No one seems to know or care enough to address this issue, so far as I can find. I'll post again if I find something.

---

### Post by calvmari on 2006-12-03
Okay, I think I have it. I took it from here: [http://www.ubuntuforums.org/showthread.php?t=290450&highlight=apt-get+127#2](http://www.ubuntuforums.org/showthread.php?t=290450&highlight=apt-get+127#2)

So first run: dpkg -L packagename
Delete everything mentioned from there.

Now manually change the status: [FONT="Courier New"]sudo gedit /var/lib/dpkg/status[/FONT]

Find your package. In my case, it's mfc8500lpr. Change that status to **purge ok not-installed**

here's a snippet of my revised piece:

```
Package: mfc8500lpr
Status: **purge ok not-installed**
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.1.2-1
Description: Brother lpr Printer Definitions
 Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
 Brother printer Driver
```

Save and exit. Now type: [FONT="Courier New"]sudo apt-get update[/FONT]

Now you should be in business. Good luck!

---

### Post by Mr Fat Bat on 2006-12-03
Was a little scared when I got this =)
> jim@Jimbuntu:~$ dpkg -L graphviz-cairo
Package `graphviz-cairo' does not contain any files (!)

But I appears that manually editing /var/lib/dpkg/status did the trick!

Thanks Calvmari!

---

### Post by lamego on 2006-12-03
Deleting /var/lib/dpkg/info/graphviz-cairo.postrm would also do the trick...

---

