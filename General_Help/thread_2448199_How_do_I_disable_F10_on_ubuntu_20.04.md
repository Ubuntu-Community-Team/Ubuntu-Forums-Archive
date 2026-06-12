---
title: "How do I disable F10 on ubuntu 20.04"
date: 2020-08-04
forum: General Help
---

### Post by frostfield on 2020-08-04
Hi, 

Maybe this is a gnome question but hopefully, someone can answer here as my google-fu is failing me. I found a couple of answers on how to disable F10 but it appears to only work on older versions of ubuntu/gnome. None of them worked for me. I've tried finding a binding for F10 under "keyboard shortcuts" in settings, but nothing. Does anyone know how I go about fixing this?

---

### Post by CelticWarrior on 2020-08-04
On my Ubuntu 20.04, the F10 key does nothing.

Why do you think it needs to be disabled? What does the F10 key do in your system that you don't want?

---

### Post by frostfield on 2020-08-04
In my case, my left mouse button acts if am holding my left button down continuously. You know, like you do when select text. Except it never stops here. So basically my mouse stops working and I need to reset.

edit: Correction, pulling the usb cable out worked too.

edit2: Never mind, it worked once. But I can't replicate the fix.

---

### Post by CelticWarrior on 2020-08-04
So, what exactly a mouse has to do with F10?

---

### Post by HermanAB on 2020-08-04
To answer your question: 
Assuming that you are using Xorg.
Use *xev* to see the key bindings and *xmodmap* to change them.

---

### Post by frostfield on 2020-08-04
> **CelticWarrior said:**
> So, what exactly a mouse has to do with F10?

I mean, my left mouse button starts acting the way I described when I press F10.

---

### Post by frostfield on 2020-08-04
> **HermanAB said:**
> To answer your question: 
Assuming that you are using Xorg.
Use *xev* to see the key bindings and *xmodmap* to change them.

I'm sure it would help, but the terminal starts spamming messages when I click F10.

---

### Post by CelticWarrior on 2020-08-04
So, now the question is WHY are you pressing F10? And is it really F10? Many laptops now have additional functions added to the Fn keys that are specific for vendor/model -and-, very important the fad now is to have that additional functions defined by the manufacturer as the default (meaning: when users press any of the F keys it's the additional function rather than the typical one  that is triggered so, in order to use the actual F key function - in the desktop (system-wide) or in a program (software specific) - users actually have to press FN+F...; it used to be the other way around, of course). This feature may or may not be switched off in UEFI ("BIOS").

In a nutshell, whatever "problem" you're supposedly having is very likely related with your specific hardware and not at all related with the OS and system-wide keyboard shortcuts. But again, DON'T PRESS the key and "problem" solved! So simple. Unlike what you want to do that seems, at best, silly.

---

### Post by frostfield on 2020-08-04
I realize I could have been a bit more clear, but "don't press the F10" is not helping one bit. Completely unnecessary comment. 

Firstly I'm using a mechanical USB keyboard. So the issue might be there, thank you. It worked fine with Fedora though.  

Secondly, my IDE is set up to "Step over" a line of code with the F10  button, but ubuntu/gnome/whatever hijacks this and messes things up.  Sure, I could rebind the F10 to something else, but I tried asking here first not expecting any condescending responses.

---

### Post by frostfield on 2020-08-04
It was my keyboard, F9 and F10 have some macro features which I never use. I had to install razor drivers for the keys to work properly.

---

### Post by GhX6GZMB on 2020-08-04
> **frostfield said:**
> but I tried asking here first not expecting any condescending responses.

Sorry, but I don't see a single condescending response here. Rather, I see head-scratching over a muddled, incomplete and incoherent question. People here do not posses crystal balls. Just saying.

---

### Post by HermanAB on 2020-08-04
Also note that many people (like me too) will frequently not give a detailed answer, but simply tell you which utility to use, because we know that there is a lot written about the subject already and it is easy enough to google for a solution once you know what to look for.

---

### Post by frostfield on 2020-08-04
> **ml9104 said:**
> Sorry, but I don't see a single condescending response here. Rather, I see head-scratching over a muddled, incomplete and incoherent question. People here do not posses crystal balls. Just saying.

Sure, I agree I was a bit incoherent. This is not my mother tongue so writing takes a bit more effort. I was specifically referring to CelticWarrior's comment: "But again, DON'T PRESS the key and "problem" solved! So simple. Unlike what you want to do that seems, at best, silly. 				". To me, it sounded condescending. Maybe I overreacted but it's all good. He/she suggested it had to do with my hardware which was correct. For that I'm grateful. 


@HermanAB: I appreciate the help and I didn't expect anyone explaining step by step exactly how to solve my issue.

---

### Post by fragglebliss on 2020-08-05
> **CelticWarrior said:**
> On my Ubuntu 20.04, the F10 key does nothing.

Why do you think it needs to be disabled? What does the F10 key do in your system that you don't want?

Not sure why it does nothing on your system, but I am running Ubuntu 20.04 and GNOME, and F10 drops down the menu of the application I'm currently in.

I'd also love to know how to disable it as I use Midnight Commander lots and exiting with F10 (like mc is supposed to exit) would be nice, if possible.

Basically, yes, F10 is annoying.

---

