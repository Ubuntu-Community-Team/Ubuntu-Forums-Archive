---
title: "Having trouble with update. Additionally my screen is large and slow after boot."
date: 2013-07-18
forum: General Help
---

### Post by xrevenentx on 2013-07-18
Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install 



I'm not good at this whole ubuntu thing...

---

### Post by Bashing-om on 2013-07-18
xrevenentx; Hi ! Welcome to the forum.

Let's see what can be done to enlighten you and relieve your anxiety.
Command line, because it is the easiest way to relate;
We want to know the state of the package system at large.
Terminal code:
```
sudo apt-get update
```
refreshes the package system's data base with that of the repositories data base.
```
sudo apt-get upgrade
```
Updates all packages on the system and advises if there are any problems.

So, post back - between code tags (# - at the top of the post) the out put of the "apt-get upgrade" command.

terminal code:
```
man apt-get
``` for full disclosure on apt-get performance.

[INDENT][INDENT]it is all a process of learning[/INDENT][/INDENT]

---

### Post by RHogskin on 2013-10-20
#Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libdrm2 : Breaks: libdrm2:i386 (!= 2.4.43-0ubuntu0.0.3) but 2.4.43-0ubuntu0.0.2 is installed
 libdrm2:i386 : Breaks: libdrm2 (!= 2.4.43-0ubuntu0.0.2) but 2.4.43-0ubuntu0.0.3 is installed
E: Unmet dependencies. Try using -f.

I was not the poster of the original problem, but I am having the same issue, so since the post seems to have ended with the request for this output, I provided it. Hopefully that is not some kind of major faux pas.

---

### Post by Bashing-om on 2013-10-20
RHogskin; Hi !

Looks like a graphics driver issue, I am not the most knowledgeable person in this realm, You might want to start another thread with your specific issue to gain a wider viewing.
If my surmise is correct, - that you have a failed proprietary graphics driver install attempt, provide in that new thread the outputs of:
With a descriptive new title such as "  dependency issue; libdrm2/libdrm2:i386  "
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```

I am more than willing to offer help, but
[INDENT][INDENT][INDENT]this could get deep
[INDENT][INDENT][INDENT][INDENT][INDENT]and other help would be nice
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RHogskin on 2013-10-20
Thanks!! I will do that.

---

