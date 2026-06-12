---
title: "Dead Laptop"
date: 2007-05-14
forum: General Help
---

### Post by earthlingzephyr on 2007-05-14
My problem is that my laptop is dead, as in won't start, the hard disk icon blinks a couple of times when you push the power button.  The events immediately leading up to the deadness are as follows:

I was test driving the feisty fawn from a live cd, when I went away from the laptop to get something to eat.  One of my friends needed to move the laptop and so they closed the lid.  This is when the deadness started, but then the friend who had loaned me the fawn cd in the first place had to go, and wanted to take it with him, so they used the manual disc drive release to get the cd out.  And now it won't do anything except flash a light.

My thought here (probably not very accurate but it's all i've got)  is that ubuntu and laptops are not exactly the best of friends, especially when it comes to setting up the hibernation and sleep stuff for closing the lid etc.  so what happened is it sent some weird instructions to the processor that resulted in the computer being turned off, and then the problem was compounded when the cd was removed.  So now what it trys to do on the power key push is boot from the live cd which is not there and so it gets confused and does nothing.  

If anyone has any thoughts on this it would be much appreciated.  Or even if you have a suggestion about who to talk to.  (I'm going to contact the manufacturer, but who knows how much help that will be.)

---

### Post by vav on 2007-05-14
Does the initial boot screen come up at all? That should happen irrespective of anything to do with a software issue...
i.e. if it's a Dell it should show DELL and do the initial test...

---

### Post by m.musashi on 2007-05-14
First, ubuntu is quite laptop friendly. I have it on several and very few issues. However, sleep and hibernation have been a sore spot, but with feisty sleep seems to work fine for me (I never use hibernate).

Since you were using a live CD, a hard restart should bring you back to normal. Depending on your computer, this may involve holding the power button for 8-10 seconds or you may have to disconnect it from power including removing the battery and then restarting.

If it somehow actually hibernated and is trying to pull those files from the HD then there could be something else going on. However, I think (not completely sure) that closing the lid would send it to sleep and not hibernate.

---

### Post by earthlingzephyr on 2007-05-19
Thanks for the suggestions, I'll give them a try and report back.

---

### Post by earthlingzephyr on 2007-05-19
So, the battery was left out overnight, and then the hard restart didn't work.  And it still isn't doing anything when the power button is pushed except for the hard disk light blinks a couple times.  And when I say it doesn't do anything, I mean the screen doesn't light up, no sounds play, absolutely nothing happens except for the hard disk light blinking.  

Any other suggestions would, as always, be greatly appreciated.

---

### Post by m.musashi on 2007-05-19
Does this happen even when it's on AC power? This sounds more like a hardware problem. While I don't know whether or not hibernating could cause this, I think it might be worthwhile to contact the hardware vendor. It's likely the person you talk to won't know anything about Linux so I wouldn't mention it. Just tell them what is happening and see if they can tell you how to reset everything.

Sorry I can't offer any better advice but if you can't get the computer to start there isn't much I can help with. Perhaps someone else has an idea.

---

### Post by earthlingzephyr on 2007-05-19
Thanks for all your advice anyhow.  Sometimes it's just helpful to get someone else's input...

---

