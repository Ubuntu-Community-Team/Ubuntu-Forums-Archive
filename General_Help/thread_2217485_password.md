---
title: "password"
date: 2014-04-17
forum: General Help
---

### Post by wojoe2k6 on 2014-04-17
I attempted to install Ubuntu 13.01 on my laptop. In the boot up sequence there shows a cjoice of Windows or Ubuntu. The Ubuntu is not active. When running the installer for the new version, it asks for a password for the new account. It rejects any password I try. There must be some old one stored somewhere. What do I do?

---

### Post by Dreamer Fithp Apprentice on 2014-04-18
> **wojoe2k6 said:**
> I attempted to install Ubuntu 13.01 on my laptop. In the boot up sequence there shows a cjoice of Windows or Ubuntu. so far, clear enough. There is no 13.01 but that doesn't matter. > **wojoe2k6 said:**
> The Ubuntu is not active.But what does that mean exactly? That you highlighted an entry on the grub menu that said Ubuntu  and clicked enter and nothing happened? The screen just stayed the same? Or what? Describe what you saw EXACTLY, in plain english.

 > **wojoe2k6 said:**
> When running the installer for the new version, it asks for a password for the new account. It rejects any password I try. Installer? So are you skipping back in time now to before the problem with booting you described first? Or did you give up on that installation and try to reinstall? I get confused when things aren't chronological. Normally the installer would tell you WHY it rejects a password. It makes you enter the password twice. Both times, you can't actually see what you enter, so it can be a little tricky. The only reason I've seen the installer reject a password was when the 2 weren't the same and it gave an error message SAYING they weren't the same. I suppose there could be other reasons, like maybe too long or too short or characters that aren't allowed, but I'd expect it to give some kind of informative error message in that case.  What, EXACTLY, does the error message say?

Or are you talking about logging in? A login screen will reject a password with no more explanation that saying it's wrong, naturally. And it does come AFTER the grub screen where you select which OS to boot. But that has nothing to do with an installer. And if you are getting to the Ubuntu login screen, then clearly it HAS booted, so I can't reconcile that with you're saying it is "not active".  Anyway, if that is what's happening - you're getting to the login screen and it won't let you log in because it is rejecting your password - then try all possible permutations of caplock on/caplock off and numlock on/numlock off.  That's:
caplock on & numlock on
caplock on & numlock off
caplock off & numlock on
caplock off & numlock off
Try it each way.
If that doesn't work, you probably aren't typing the same password you did when you installed it. That's easier to happen than it sounds. When you can't see what you are typing it is easy to make the same typo twice. When I'm installing I touch type the password the first time and look at the keyboard and press one key at a time watching for the visual indicator that the keypress was recieved (an asterisk or a big dot in the password box for each character). If that is what happened you'll just have to install it again and be real careful about the password.

---

### Post by wojoe2k6 on 2014-04-18
Got it.

---

### Post by Dreamer Fithp Apprentice on 2014-04-23
So some part of that worked for you? If so, good. I suggest you mark the thread "solved" then. It saves work for people who check the unsolved post list looking for things they can help with.

---

