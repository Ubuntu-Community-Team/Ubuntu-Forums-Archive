---
title: "My system font looks like that: &#8592;&#8595;€§¢€½²&#8734;&#8594;&#8592;&#8595;"
date: 2017-01-27
forum: General Help
---

### Post by jas-wanot on 2017-01-27
Hello!

I decided to update my lubuntu to the newest ubuntu version using the official updater a couple of weeks ago (unfortunately I don't remember what the version was previously, but I believe it was around 15.10), but ever since I booted 16.04 for the first time my system appears to be using some sort of an alien language for almost all text:

[ATTACH=CONFIG]273410[/ATTACH]

I searched everywhere, but googling things like "lubuntu messed up font" or "lubuntu weird characters" gives no results.

It should be noted, those characters are not just random garble, they are actually consistent - I checked it, and it seems that every letter of normal alphabet always displays as the same weird symbol.

If no one will be able to help me with this, I think I will just memorize what letter each character corresponds to and learn to read and write it like a normal alphabet. It could be pretty cool, when I think about  - no one would be able to use my computer but me. Efficiently use, at least.

---

### Post by vasa1 on 2017-01-27
Does this also happen in the terminal?

---

### Post by dragonfly41 on 2017-01-27
Also, I suggest logging out and logging in as guest user.
Do you see same unintelligible characters?

---

### Post by vasa1 on 2017-01-27
Your Openbox right-click menu seems to be just fine. So the issue is selective.

---

### Post by jas-wanot on 2017-01-27
> **vasa1 said:**
> Does this also happen in the terminal?

No, terminal looks fine, as does most text editors. Firefox is an  interesting case, because while url and search bars are "alienized", all  the webpages and forms on them are OK (I can read what you write and  see what I'm typing right now).

(I should clarify that when I say "most text editors are fine", I mean those parts of them where you type text. The interface, for instance those bars on top with stuff like "File", etc. are still mostly giberish.)

> **dragonfly41 said:**
> Also, I suggest logging out and logging in as guest user.
Do you see same unintelligible characters?

Just checked that, and on guest account everything looks normal! But when I log into my normal account, everything is weird again.

---

### Post by vasa1 on 2017-01-27
Can you try some other widget theme from "Customize Look and Feel"?

---

### Post by jas-wanot on 2017-01-27
Sure. Doesn't seem to change anything.

---

### Post by vasa1 on 2017-01-27
What theme are you using and what did you try?

The fact that you don't see anything wrong when you try with a new user points to an issue with files in your home folder. For starters, rename the hidden *.config* folder to something like *.config.bak*, log out and log back in again. And see if that changes anything.

---

### Post by jas-wanot on 2017-01-27
Uhhm... I don't really know. Because, you know, I can't really read it.

But I checked and applied almost every single one and none of them helped here.

---

### Post by dragonfly41 on 2017-01-27
Digging around ... just browsing for similar scenarios ...

[https://solidfoundationwebdev.com/blog/posts/fix-corrupted-system-fonts-in-ubuntu](https://solidfoundationwebdev.com/blog/posts/fix-corrupted-system-fonts-in-ubuntu)

Another suggestion ... reinstall desktop

sudo apt-get install ubuntu-desktop

And this thread suggests installing unity-tweak-tool then tweaking fonts ...

[http://askubuntu.com/questions/603579/ubuntu-fonts-are-corrupted-on-certain-windows](http://askubuntu.com/questions/603579/ubuntu-fonts-are-corrupted-on-certain-windows)

---

### Post by jas-wanot on 2017-01-28
I tired the first two, but it did not help. I'm installing unity-tweak-tool right now, but it will take a while (it's a pretty big tool) so I'll probably try it later today. If it's a gui program however, I might have a problem with operating it, since the txt in it will probably also be garbled.

---

### Post by RobGoss on 2017-01-28
> If no one will be able to help me with this, I think I will just memorize what letter each character corresponds to and learn to read and write it like a normal alphabet. It could be pretty cool, when I think about - no one would be able to use my computer but me. Efficiently use, at least.

Seems like a lot of work, If you are unable to correct this issue I would just do a fresh installation of **16.04**, most people trying to upgrade using the system upgrade method has always been faced with problems. Fresh installation is the best way to go

---

### Post by jas-wanot on 2017-01-29
Okay, so the guy who asked me if the problem still happens on the guest account gave me an idea, I basically created a new user account, gave it sudo access, copied all my stuff there, and then deleted the old one. And guess what? It worked! Everything is OK now! All my app configs are gone now ofc, but it's not a big problem and I would loose them anyway if I decided to do a fresh install. 

So, thanks for help anyway! I'm leaving this here in case someone in the future has a similar problem.

---

