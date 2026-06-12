---
title: "Virus protection in Ubuntu?"
date: 2008-06-10
forum: General Help
---

### Post by AlexisMclovin on 2008-06-10
I have been having slow down errors and have even had my computer freeze up. These are common things for a computer witha virus of some kind; am i wrong? I hear that you need no virus protection on linux type OS's and i was wondering what the problem was if not that i have a virus.

---

### Post by lisati on 2008-06-10
With *nix there isn't the same need for virus protection as with Windows - see [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) for more information.

EDIT: You'll find a variety of opinion about anti-virus software in these forums, ranging from "don't need it", through to "go for it". At the end of the day, it's up to you. I pass the "talking stick" to others who might be better equipped to help you discover what might be going on to slow your system.

---

### Post by jocko on 2008-06-10
That sounds like a memory leak, which is a bug in a program that causes it to slowly fill up the memory.
Next time it happens (but before it freezes up completely), check what's using your memory.
One way is by typing the command "top" in a terminal, another is the gnome system monitor (System --> Administration --> System monitor).

It's not likely that it's caused by a virus. There are very few virii that are capable of infecting linux, because the absolute majority of virii are designed to infect windows and as you may have noticed, windows programs usually don't work on linux.
It is also probably very hard to design a virus that is capable of gaining root access, which is the only way to do any real damage to a linux system.

---

### Post by mesh2005 on 2008-06-10
very hard to suspect a virus. I do believe it is a hardware issue, most probably a RAM or a Fan.

---

### Post by todak on 2008-06-10
It could be processor or memory overheating. Make sure all fans, vents, heatsink fins, etc. are clean and dust-free :wink:

---

### Post by Pjotr123 on 2008-06-10
Viruses and security in general:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by hyper_ch on 2008-06-10
nice summary :)

---

### Post by AlexisMclovin on 2008-06-10
> **jocko said:**
> That sounds like a memory leak, which is a bug in a program that causes it to slowly fill up the memory.
Next time it happens (but before it freezes up completely), check what's using your memory.
One way is by typing the command "top" in a terminal, another is the gnome system monitor (System --> Administration --> System monitor).

It's not likely that it's caused by a virus. There are very few virii that are capable of infecting linux, because the absolute majority of virii are designed to infect windows and as you may have noticed, windows programs usually don't work on linux.
It is also probably very hard to design a virus that is capable of gaining root access, which is the only way to do any real damage to a linux system.
The memory leak thing is more than likely the problem. I had a program crash and not fully close so i checked the system monitor and it was still using up memory. Thanks for the help i just wanted reassurance that it wasnt a virus.

---

