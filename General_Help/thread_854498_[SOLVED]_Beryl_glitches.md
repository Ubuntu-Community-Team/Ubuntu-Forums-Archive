---
title: "[SOLVED] Beryl glitches"
date: 2008-07-09
forum: General Help
---

### Post by theshadowwithanmp5n on 2008-07-09
Hello,

Whenever I start Ubuntu, it defaults to the metacity theme.
I would like it to default to the Beryl theme.
Can anyone help me with this?

Also, sometimes the window borders disappear at random.
Is there any permanent solution to this?

Any help would be appreciated.

---

### Post by sayakb on 2008-07-09
Which version of Ubuntu? Also, beryl isn't supported anymore. If you are using Ubuntu Gutsy (7.10) or Hardy (8.04), you should have compiz installed. Install Compiz Fusion Icon by typing at a terminal:
```
sudo apt-get install fusion-icon
```Launch the icon from *Applications->System Tools->Compiz Fusion Icon*
Right click on the icon, goto **Select Window Manager** and select **Compiz**. Restart X (press *Ctrl+Alt+Backspace*) and check if you have compiz or not.

---

### Post by theshadowwithanmp5n on 2008-07-09
I have compiz,
and Beryl and Compiz started working together a little while ago, so if Compiz is working, then Beryl should be working, at least that's what I read.

---

### Post by rainwalker on 2008-07-09
Beryl is no longer in development. The whole project was originally forked between Beryl and Compiz, but they merged and became Compiz Fusion. CF comes installed on 7.10 and 8.04 and enabled by default if your hardware can support it.
So if you installed Beryl, you should remove it and use Compiz Fusion

---

### Post by acelin on 2008-07-10
Even though Beryl had better curves! lol

---

### Post by theshadowwithanmp5n on 2008-07-10
I have the emerald theme manager.
I like the themes that I download from themes.beryl-project.com.
Compiz doesn't have themes, it only has the cool effects, I'm talking about themes.
I made a temporary fix.
I made a shell script and put emerald --replace in it, then I put it in the Sessions manager and the script runs every time I boot up.

---

### Post by rainwalker on 2008-07-10
Ohh you're talking about *Emerald*!

Well if you install CCSM you should be able to set Emerald as the default decorator by setting it in the Window Decorations section

---

### Post by theshadowwithanmp5n on 2008-07-10
thanks.
now i don't have to use a shell script and worry about that
even though there's not much to worry about in terms of shell scripts, i'm much more comfortable with using your method.

one more question
arent beryl and emerald the same thing.
you use emerald to employ the beryl themes right?

---

### Post by theshadowwithanmp5n on 2008-07-10
where in CCSM is window decorations
assuming your talking about CompizConfig Settings Manager
I can't find window decoraitons.

---

### Post by rainwalker on 2008-07-10
See the attached image

---

### Post by theshadowwithanmp5n on 2008-07-11
thanks,
i must've overlooked that one when i was skimming through it.

---

