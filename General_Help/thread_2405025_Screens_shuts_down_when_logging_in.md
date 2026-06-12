---
title: "Screens shuts down when logging in"
date: 2018-10-31
forum: General Help
---

### Post by timswait on 2018-10-31
I've recently installed Ubuntu 18.04 on a Dell Precision M4000 laptop (dual boot with Windows 7) I get the log in screen every time. However, sometimes when I enter my password the screen will just go black, no mouse cursor, nothing! Pressing and holding the power button to shut it off is all I can do. Normally when I switch it on again it's fine. However I've just tried about 10 times in a row and black screen every time. I can't get in at all now &#128549;
What can I do?

---

### Post by timswait on 2018-10-31
Hmmm, on the 11th attempt it worked! I'm now back in, but obviously want to solve it. In between it not working and then working again I had booted into Windows and then fully shut down from Windows. Before its stint of not working I had been in Windows and only restarted not fully powered off. Could that be significant? I've set the display to Never turn off in power management, although again doubt its got anything to do with that, it's always woken up fine from when the display has gone off due to time.

---

### Post by timswait on 2018-11-06
Anyone got any idea why this is happening? It's doing it again!

---

### Post by HermanAB on 2018-11-06
Hmm, this is a very annoying and perplexing problem to the uninitiated.

The problem is of course the video device driver.  Fixing it can be very difficult, since you can end up with a completely black screen (as you have seen), but it could be a permanent condition.  So, before starting to experiment further, first enable the SSH daemon, so that you can log into your machine from another machine over ethernet, to fix/revert the changes remotely, when the local machine screen turns black.

The distribution with the best configuration tools is PCLinuxOS.  So when you get tired of reading Ubuntu help files and trying things, install PCLinuxOS - it has wizards for everything, including the screen setup.

---

### Post by timswait on 2018-11-14
Thank you, it was the display drivers, I've installed the proprietary nvidia ones and haven't had the problem since :-)

---

