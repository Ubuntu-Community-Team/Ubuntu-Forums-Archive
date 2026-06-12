---
title: "Help with old keyboard"
date: 2018-09-20
forum: General Help
---

### Post by xristosp59 on 2018-09-20
Hello!

So I started using a very old notebook of mine again after a long time and i noticed the keyboard was kinda broken.
And by that i mean that sometimes when i press a key it might register 2-3+ times even though i only pressed it once (depending on the force i use when pressing it). 

My question is:  is there anything i can do in lubuntu 18.04 which will make it so there is a time space between keystrokes enough so that it doesnt register more than one time? And no im not long pressing the button, i guess the fluctuation of the force applied (even though marginal) makes it think i pressed the key again.

---

### Post by Autodave on 2018-09-20
Not really: at least nothing that I can think of.  Have you tried blowing compressed air under the keys to remove and dust / dist that might be there?  Can you hook up an external keyboard?

The only other thought is to shut down the machine and just repeatedly and quickly press every key in an effort to unstick them.

---

### Post by Holger_Gehrke on 2018-09-20
Sounds like some of the keys are bouncing. There's a tool named 'xkbset' to set various options of the XKB-Extension.
```
xkbset -bouncekeys 50
```will discard all repeated keypresses within 50 ms as bounce (or chatter). If it isn't installed, 'sudo apt install xkbset'.

Holger

---

### Post by xristosp59 on 2018-09-20
[**[COLOR=#000000]@Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578") 
ok i tried this but i dont think it did anything, i even set it to 10000ms but still nothing :p

---

### Post by xristosp59 on 2018-09-20
> **Autodave said:**
> Not really: at least nothing that I can think of.  Have you tried blowing compressed air under the keys to remove and dust / dist that might be there?  Can you hook up an external keyboard?

The only other thought is to shut down the machine and just repeatedly and quickly press every key in an effort to unstick them.

No i didnt, ill try that later thanks!

---

### Post by xristosp59 on 2018-09-20
> **xristosp59 said:**
> [**[COLOR=#000000]@Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578") 
ok i tried this but i dont think it did anything, i even set it to 10000ms but still nothing :p

ok nm it seems that the command i used didnt work for some reason, now it worked after i checked with xkbset q to make sure it worked, ill try it out for a bit and see if the issue continues (even though it seems like its fixed, thanks! :D )

---

### Post by Holger_Gehrke on 2018-09-20
Well, the error was mine. '-bouncekeys' deactivates de-bouncing. The correct command(s) are
```

xkbset bouncekeys 50
xkbset exp bouncekeys

```
The second command keeps debouncing active after the XKB timeout has been reached. My only defence is that I habitually put a dash in front of options ...

Holger

---

