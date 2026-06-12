---
title: "compiz on edgy?"
date: 2006-10-30
forum: General Help
---

### Post by Bou on 2006-10-30
Hi, I'd like to know how to get compiz to work on a fresh edgy install, using aiglx and an nvidia card. I followed [this guide]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") to get a proper xorg.conf, and installed all the required packages except for, cgwd, which synaptic can't find.

The thing is, when I launch compiz, I lose the window decorations. Can you guys please give me a hand?

---

### Post by PuleX on 2006-10-30
If you lose window decorations, try starting metacity again. In a terminal do" ```
metacity &
```
You can also add metacity to the startup services under Gnome Menu > System > Preferences > Sessions > Startup Programs

Are you using the official compiz? Beryl, the fork, is supposedly a bit further and it is also well documented: 
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy) 
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX) 

(Remember, Beryl is definitely beta software!)

---

### Post by Circus-Killer on 2006-10-30
as pulex said, rather try beryl.
not only is beryl better (IMHO), but much easier to configure and manage, and is quite a bit more stable.

but as pulex said, its still early days. its not even beta yet, its still in alpha stages. dont try it if you cant risk a reformat, other than that, its worth taking a look at.:cool:

---

### Post by ekerazha on 2006-10-30
> **Bou said:**
> Hi, I'd like to know how to get compiz to work on a fresh edgy install, using aiglx and an nvidia card. I followed [this guide]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") to get a proper xorg.conf, and installed all the required packages except for, cgwd, which synaptic can't find.

The thing is, when I launch compiz, I lose the window decorations. Can you guys please give me a hand?
I also have this issue.

I can't see the windows border and the workspace switching doesn't work.

---

### Post by Bou on 2006-10-30
I tried beryl already but it's giving me rather low performance and I don't like the new effects all that much. That's why I wanted to give good old compiz a try.

---

