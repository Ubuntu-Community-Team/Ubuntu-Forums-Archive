---
title: "Made big mistake in Adept w/ Python, can it be undone?"
date: 2008-06-30
forum: General Help
---

### Post by Nexusx6 on 2008-06-30
Hola,

After almost a year of using Ubuntu, I thought I knew what I was doing. Oh lord...

I was having a huge mess of problems with Python, to the point where it became unstable and wouldn't run even a simple program. I thought "Oh well, I'll just remove it and re-install it". So I jump into Adept, find python, and Request Removal. As soon as I hit Apply Changes I start seeing programs being removed that I didn't know were dependent on python :shock:

Because I'm that dumb, I didn't think to hit the Cancel button at the time >.> I have no idea which, or how many programs were marked dependent on Python and what happened to them :( Is there anyway to simple "undo" everything? Can I tell Adept to restore it all? I really hope so . . .

---

### Post by kuja on 2008-06-30
Well, There might be clues in your /var/log/dpkg.log or /var/log/dpkkg.log.? - if you're lucky. Asides from that, *"sudo apt-get install kubuntu-desktop"* would probably be a good start. Oh, and by the way .... the amount of programs that depends on python ..... that's one long, long, long list.

---

### Post by Nexusx6 on 2008-06-30
Dude, you aren't joking. I can see the list of the last made changes in Adept -- lord god. I'm not going to even bother trying to run that through apt-get

> Asides from that, "sudo apt-get install kubuntu-desktop" would probably be a good start.

Honestly, that could maybe fix the whole thing since kubuntu-desktop would call almost that whole list back. Buut, I know thats just asking for issues down the road. Guess that means I get to re-install for Monday :( Oh well, now I can play with KDE 4 at least.

---

### Post by VMC on 2008-06-30
Someone in the last couple of weeks did the exact same thing you did, with all the consequences. He did manage to fix a lot of his issues. Once I find the tag I will post it back here.

I've been there and done that myself :)

Edit: this is the one I'm referring to. Hope it will help. It was for ubuntu. Maybe you can gleam some useful info from it:
[http://ubuntuforums.org/showthread.php?t=835816&highlight=delete+python](http://ubuntuforums.org/showthread.php?t=835816&highlight=delete+python)

---

