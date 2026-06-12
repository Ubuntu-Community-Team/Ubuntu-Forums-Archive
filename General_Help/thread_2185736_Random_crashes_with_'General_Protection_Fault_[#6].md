---
title: "Random crashes with 'General Protection Fault: [#6] SMP'"
date: 2013-11-04
forum: General Help
---

### Post by Bucky Ball on 2013-11-04
Hi all,

This is potentially a disaster for me as I am just trying to finish up my final dissertation for uni. Over the past few days I have had two or three random crashes on what is otherwise a very stable Toshiba Satellite Pro L510 running a minimal install with xfce4 desktop environment (kernel 3.2.0-53-generic and today 3.2.0-55-generic).

Yesterday, I was putting a footnote in a Libreoffice Writer document using Zotero when the system just crashed, screen of code and this at the end:
```

General Protection Fault: [#6] SMP
```

Only way out is to hold down the power button and kill the machine. Boot again and all fine. Until today. I backed up and updated/upgrade the machine when I got up and had been using the machine without issue all day. Take a break and close the laptop lid, as usual, take the dog for a wander, get back and open the lid and there is the screen of code to greet me, and this time I noticed this on the last line:

```
CPU 3 
```

As I say, I have everything backed up and another machine I can work on, but this is kind of a major disaster nonetheless as I just can't afford the time to screw around with crashes. I've swapped back to the -48 kernel as thought it might have something to do with that (but doubting it). 

Can anyone shed any light? I'm hating the thought, but could this be hardware related? The warranty is just about up so wouldn't suprise me, and I need the machine to be rock solid right now cos on the home straight so another reason for things to fall apart. 

Basically, what I'm saying in no uncertain terms, is 'help, I'm desperate!' ;)

I've done some digging and will continue to dig, but not finding much (about General Protection Fault [#6] specifically). Any more info required just ask and tnx in advance.

* Update: 

[https://en.wikipedia.org/wiki/General_protection_fault](https://en.wikipedia.org/wiki/General_protection_fault)

This sheds some light so not quite as worried about the failing hardware possibility. A matter of tracking down what is causing the problem. I installed and used foremost to try and retrieve a file and I think it started around then, but could be wrong. It is now removed so can't see how it would be the issue, unless there's residue.

---

### Post by Bucky Ball on 2013-11-04
Wondering if cleaning the memory cache might help. I'm thinking this is some kind of software glitch/conflict perhaps, at least from what I've read. 

I don't have a lot of time to spend on it so for now I'm just saving twice a minute and persevering in the hopes things don't start collapsing around my ears! Rather unsettling but attempting to concentrate (I lost about one hour of hard thinking work yesterday ... only an hour but that hour I pretty much created the roadmap of the whole project - that is why I installed foremost to try and retrieve the file that Libreoffice couldn't ...) ...

---

