---
title: "Screenfont for virtual (TTY) console"
date: 2007-07-26
forum: General Help
---

### Post by Thrasyllus on 2007-07-26
How do I get to see a decent screenfont in the virtual (old-fashioned) terminals? Maybe I posted my orginal question in the wrong forum (see "Establishing TTY character set" in Installation & Upgrades). **But I doubt it** because similar questions have gone unanswered in this forum for months, according to search results. 

For the time being I just want to see, on the TTY console screens, the same characters I am seeing when I bring up a terminal in GUI mode. **charset G0** and **G1** certainly don't do it.

I'll deal with the keyboard map myself later...  

It's not as if I was asking for something revolutionary -- vt screenfonts with proper accents etc. have been available for many years. Don't tell me we're starting to be ruled by the Orwellian "Downgrading is upgrading" approach: I thought only Microsoft did that. I love my new Feisty Fawn! Why does it have to be spoiled by anti-TTY prejudice?

---

### Post by Thrasyllus on 2007-08-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/130444](https://bugs.launchpad.net/ubuntu/+bug/130444) [br].[/br] ---------------------------- [br].[/br] 
To bring this up to date... I have filed this as a bug but am still hoping for help from the General Help forum - maybe from Europeans or Latin Americans, who seem to care about accents. 

The problem is definitely about echoing to screen. The characters are all "there", and if I write something on a TTY virtual terminal with an accent I can't see, then read the file on the GUI terminal, the accent shows up where I put it. 

I have also noticed that the caps lock does not work in the TTY terminals - maybe a clue?

I know most of you think I'm crazy for wanting "alien" accents to show on a virtual terminal screen, but this is not just about accents. The border-drawing characters are messed up too, so Midnight Commander looks like my unweeded front yard. Surely a lot of you use mc when you're on a virtual terminal?

---

### Post by cwaldbieser on 2007-08-29
> **Thrasyllus said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/130444](https://bugs.launchpad.net/ubuntu/+bug/130444) [br].[/br] ---------------------------- [br].[/br] 
To bring this up to date... I have filed this as a bug but am still hoping for help from the General Help forum - maybe from Europeans or Latin Americans, who seem to care about accents. 

The problem is definitely about echoing to screen. The characters are all "there", and if I write something on a TTY virtual terminal with an accent I can't see, then read the file on the GUI terminal, the accent shows up where I put it. 

I have also noticed that the caps lock does not work in the TTY terminals - maybe a clue?

I know most of you think I'm crazy for wanting "alien" accents to show on a virtual terminal screen, but this is not just about accents. The border-drawing characters are messed up too, so Midnight Commander looks like my unweeded front yard. Surely a lot of you use mc when you're on a virtual terminal?

Maybe it is just a tty setting?  Compare the output of "stty -a" in an xterm and a virtual terminal.

---

