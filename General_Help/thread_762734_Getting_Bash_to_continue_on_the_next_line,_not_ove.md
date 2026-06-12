---
title: "Getting Bash to continue on the next line, not overwriting"
date: 2008-04-22
forum: General Help
---

### Post by blunden on 2008-04-22
I run Ubuntu on my laptop with no problems. Something I noticed though is that it, unlike the bash shell running in Solaris, is allowing you to write multiple lines of input and showing it on separate lines instead of just starting to overwrite from the left. What part of the config file for bash do I need to copy to bash on solaris to get rid of the overwriting behaviour? 

Ex.
*Ubuntu* **(Good)**
```
$ aaaaaaaaaaaaaaaaaaa
bbbbbbb
```

*Solaris* **(Bad)**
```
$ bbbbbbaaaaaaaaaaaaa
```

---

### Post by blunden on 2008-04-24
Anyone?

---

### Post by justleen on 2008-04-24
Que??

bash is not allowing me to continue on a newline.. that is, not with out adding a ' " {  or \ at the end of the line.

If you are using bash on solaris, copy the .bashrc over...(rename your old one first). reenter bash after the copy..

---

### Post by sweeneytodd on 2008-04-24
wouldn't have the faintest idea, but does it really matter, don't mind me, justleen is the man to talk to

---

### Post by mali2297 on 2008-04-24
Don't you think that it's related to the terminal emulator rather than bash?

If you start xterm with
```

xterm +aw

```
then you get a behaviour similar to your description, with the exception that the bash prompt is overwritten as well.

---

### Post by blunden on 2008-04-24
Ok. Will try that. :)

---

### Post by mali2297 on 2008-04-25
What you see as a feature, others regard to be a bug. Perhaps you can reverse the suggestions given here:
[http://ubuntuforums.org/showthread.php?t=234232](http://ubuntuforums.org/showthread.php?t=234232)

---

### Post by blunden on 2008-04-25
> **mali2297 said:**
> What you see as a feature, others regard to be a bug. Perhaps you can reverse the suggestions given here:
[http://ubuntuforums.org/showthread.php?t=234232](http://ubuntuforums.org/showthread.php?t=234232) Seems I worded my first question badly. I want it to continue on a new line, not overwrite it. Will check out the thread above. :)

EDIT: Worked great, except for one detail. Now it continues on the next line but the first few letters of the second line gets overwritten before it continues. Only happens on line 2.

---

### Post by blunden on 2008-05-08
What could cause that? I've seen that problem before.

---

### Post by Yannick Le Saint kyncani on 2008-05-08
> **blunden said:**
> instead of just starting to overwrite from the left

I think this calls for a solaris->ubuntu upgrade :lolflag:.

But should not you be asking some solaris forum instead, as they are bound to have the same problem as you ?

---

### Post by blunden on 2008-05-09
> **Yannick Le Saint kyncani said:**
> I think this calls for a solaris->ubuntu upgrade :lolflag:.

But should not you be asking some solaris forum instead, as they are bound to have the same problem as you ? Well, it's my university that runs Solaris (also OSX and Windows). Can't really do much about that. ;) The other system I saw with the same problem was running Debian so the specific *Nix-version doesn't really matter. :)

---

