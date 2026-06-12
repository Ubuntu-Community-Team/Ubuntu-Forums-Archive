---
title: "Editing Error Messages"
date: 2007-08-04
forum: General Help
---

### Post by Turboaaa2001 on 2007-08-04
Here is what I want to do. I want to change the error message you get when you don't have the appropriate permissions to edit a file to:

"You want to do what now? F*** YOU"

Basically if you could give me some sites and material on how to do it I will do the reading and research. If you have something specific thats great too but I want to be able to learn first hand as much as possible.

---

### Post by apetresc on 2007-08-04
Er, hmm... I think those error message are shell-specific things. You're probably using Bash, so probably the only way to do this is to ```
apt-get source bash
``` Find the strings you want to change (they may be in a message catalog for readline), change them to your new values, recompile bash, and set your special version as the user's default shell.
There *may* exist a way to change these things dynamically from Bash, but I doubt there is; I don't really see the utility of such a thing for 99% of people. But I guess you're that 1% :P Is there any particular reason you want to do this, if you don't mind my asking?

---

### Post by Turboaaa2001 on 2007-08-04
No real reason for changing it to that phrase.

I'm a hardware Geek and know little about programing and such. I've done little with VBS and Shell scripting, and have had little patients.

What I want to eventually do is give the system a "personality". I wouldn't mind getting to the point of making it generate different messages for the same event. i.e. "You need permision to do that" and then after another try "Your not going to get access"

If I can eventually master this and other elements of the kernel then I will create multiple personallities and share them with others.

---

### Post by apetresc on 2007-08-04
> **Turboaaa2001 said:**
> No real reason for changing it to that phrase.

I'm a hardware Geek and know little about programing and such. I've done little with VBS and Shell scripting, and have had little patients.

What I want to eventually do is give the system a "personality". I wouldn't mind getting to the point of making it generate different messages for the same event. i.e. "You need permision to do that" and then after another try "Your not going to get access"

If I can eventually master this and other elements of the kernel then I will create multiple personallities and share them with others.

Ah, okay :) That sounds like an interesting project to get your feet wet.

However, those types of things have nothing to do with the kernel and almost everything to do with bash. If you want to learn about the stuff needed to do this, you should check out that code. Also, check out "readline". It's a library that a lot of programs use to generate "message catalogs" of strings to be returned for certain meanings and situations. The main purpose is to allow easy translation, but I guess you could also use it to make wacky phrases :)

Good luck!

---

