---
title: "Why does opening terminal ask for a sudo password?"
date: 2022-10-02
forum: General Help
---

### Post by stevermann on 2022-10-02
I have a few servers in my home, all running Ubuntu from Version 18 to 22.04.
I just installed 22.04.1 on a new laptop.
Everything works fine, but when I open a terminal window, I am prompted for a sudo password ??

```
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




```

I have never seen this before- usually the terminal window just opens.
Any ideas why I am getting this behavior?

---

### Post by QIII on 2022-10-02
So you get that immediately when you open a terminal?  That is, you have not entered any commands?

---

### Post by &amp;KyT$0P# on 2022-10-03
Does your [FONT=Courier New]~/.bashrc[/FONT] contain any commands that run [FONT=Courier New]sudo[/FONT] ?

Specifically, the code you posted looks like output from [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] or similar apt command.

---

