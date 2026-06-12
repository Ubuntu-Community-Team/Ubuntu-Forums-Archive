---
title: "COMPIZ 3D CUBE Desktop"
date: 2022-01-29
forum: General Help
---

### Post by subcook on 2022-01-29
I may be aging myself, but is it still possible to activate the 3d cube desktop in KDE Ubuntu ?



Kubuntu 20.04 LTS

Is that still a thing ?

---

### Post by deadflowr on 2022-01-29
I cannot see why not.
I use compiz cube on unity up to Ubuntu 21.10.
So if you can get compiz functional on kde I cannot see it not working.
Have you tried and it does not work, or something?

That said, why not use the builtin cube function already present in plasma-desktop/kwin?

---

### Post by mIk3_08 on 2022-01-30
> **subcook said:**
> I may be aging myself, but is it still possible to activate the 3d cube desktop in KDE Ubuntu ?
Kubuntu 20.04 LTS
Is that still a thing ? Yes. It is still possible. Just change the desktop environment from the default gnome cause i think the gnome de won't support the compiz functionalities. Just try another desktop environment that you think that support the compiz functionalities their are a lot of them here. You can choose whatever you want except the gnome one. As what I have telling you previously about the gnome desktop environment. So Good Luck and Cheers.

---

### Post by timgood on 2022-01-30
Desktop cube and associated animations have been dropped in latest versions of Plasma.

Quote from devs: "This was discussed back in May. See [https://mail.kde.org/pipermail/kwin/2021-May/005222.html](https://mail.kde.org/pipermail/kwin/2021-May/005222.html) for the reason why the effect was dropped.

I'm afraid that we can't bring the effect back because rendering abstractions have changed quite a bit. One would need to rewrite the effect from scratch. As discussed in the mailing list thread, we would like to have the effect reimplemented in qml (like the overview effect), but we don't have man power resources to do so. It will be great if the community helps with the port of the effect to qml."

---

### Post by subcook on 2022-01-31
1. DeadFlower - Thanks man
2. MLK3_08 - I have no idea what you're talking about.  Kubuntu (at least I thought) specifies KDE/Plasma - Ubuntu.    Talkinag about gnome makes no sense to me.
3. timgood -   Seems like alotta work for this.  I thought that the 3d compiz cube was already icorporated, sounds like I was wrong ???

---

### Post by deadflowr on 2022-01-31
I believe timgood's response was about cube and effects in kwin as kde and plasma really don't have anything to do with whatever compiz does or doesn't do.

I did remember this little quick post from a few weeks ago: [https://ubuntuforums.org/showthread.php?t=2470727]("https://ubuntuforums.org/showthread.php?t=2470727")
So compiz should run at least.

I forgot to mention that cube and I think 3d windows in compiz in Ubuntu requires the compiz-plugins package.
Not sure if that is known or not so just putting that out there, in case.

It's nice to see users keeping compiz in use and alive to some degree.
Other than unity users.

---

### Post by mIk3_08 on 2022-02-01
> **subcook said:**
> 
2. MLK3_08 - I have no idea what you're talking about.  Kubuntu (at least I thought) specifies KDE/Plasma - Ubuntu.    Talkinag about gnome makes no sense to me.

I've been talking the default DE of New installed Ubuntu here. But if you go KDE Plasma environment its better then. Because KDE Plasma I think supports compiz.

---

### Post by subcook on 2022-02-15
I think Timgood's response is the most accurate.   (I'm running Kubuntu 20.04), and all arrows seem to point to the idea that they dropped it in the new(er) KDE Gui's.

Although, I am coming across threads out there saying that people have done it, but I think it's very much over my skill level.  I wanted to check here to see if anyone knew of any easy ways to make it happen with a new(er) distribution, as I don't want to break my system over cosmetics.

Anything else comparable out there that anyone may know of.  I do like the cube ....

---

### Post by DuckHook on 2022-02-15
> **subcook said:**
> …Anything else comparable out there that anyone may know of.  I do like the cube ....
[https://www.omgubuntu.co.uk/2021/12/linux-3d-cube-desktop](https://www.omgubuntu.co.uk/2021/12/linux-3d-cube-desktop)

Just as Plasma is getting rid of theirs, Gnome is bringing it back.

---

### Post by subcook on 2022-02-16
Nothing for Plasma ?

---

### Post by DuckHook on 2022-02-16
> **subcook said:**
> Nothing for Plasma ?
I don't use plasma so my observations can only be academic in nature. Like you, I'm going by what timgood posted. His included link implies that the plasma devs have seen fit to nerf effects. I have no further insider knowledge as to why. The link states that effects like the cube are a dog's breakfast of indecipherable third party hacks, in which case, it makes sense to drop support for them if only for security considerations. Neither have I any idea why Gnome seems to be going in the opposite direction.

Others above have already suggested that changing your window manager to compiz will also get you what you want. Do note that compiz has been deprecated for some time now. I recall reading somewhere that even compiz's lead developer is encouraging people to move away from it. When the lead dev makes that sort of statement, I for one would think very carefully before committing myself to it—especially for something that resides at such a fundamental level in my production or daily use box.

---

### Post by subcook on 2022-02-28
Anyone ?    Plasma is great, would love one that is for KDE gui

---

### Post by Frogs Hair on 2022-03-01
I use plasma on Solus OS and as stated and linked previously the Kwin cube and other effects were abandoned because they were difficult and time consuming to maintain. The Unity and Mate desktops  support compiz effects. I'm not sure about compiz status on the latest version of Xubuntu or KDE Plasma.

---

### Post by DuckHook on 2022-03-01
> **subcook said:**
> Nothing for Plasma ?

> **subcook said:**
> Anyone ?    Plasma is great, would love one that is for KDE gui

Your question has been answered. To recap:

You are not going to get this functionality natively, so you have two choices:

[LIST=1]
[*]You can switch to a desktop that does have this functionality natively. Gnome has it natively (with an extension), and the old Unity desktop has it because it still uses Compiz. Both can be installed using the instructions in the sticky linked in my sig.
[*]Or, you can try to switch your window manager to Compiz. This comes at some risk to your install but, in the end, a window manager is a window manager. I don't see why switching to another WM would seriously break your system. However, as always when dealing with foundational system components, be prepared to reinstall with the appropriate backups, etc.
[/LIST]
There was also the caveat that Compiz's own lead dev has advised against its use—not because it is broken or dangerous, but because it is deprecated and therefore sparsely maintained.

This may not be the answer you wanted to hear, but it's the reality.

---

### Post by alias5 on 2022-03-01
Oh.  I remember that.  I loved all the COMPIZ animations.  It seems like it got increasingly harder to rely on those keyboard shortcuts.  There were a lot of great animations.

---

