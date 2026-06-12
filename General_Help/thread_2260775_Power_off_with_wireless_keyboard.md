---
title: "Power off with wireless keyboard"
date: 2015-01-14
forum: General Help
---

### Post by casmiddy on 2015-01-14
I have a home-built PC running Ubuntu 14.10 and I'd like to be able to shut it down (or open the shut down dialog box) via my wireless logitech keyboard. I used to be able to put the computer into suspend by using this button, but since the computer was never able to recover from suspend properly (and twice, when i accidentally hit it, it actually broke the installation making grub rescue appear) I decided to disable the suspend option completely. I just wondered if it would be possible instead to set this button to shut the PC down, as it would be very convenient to do so from my keyboard. I've already tried editing the CTRL+ALT+DEL short cut to use this one button instead but it still didn't work. I also tried creating a new shotcut using a number of commands that I found online which said they were to shut the PC down, but none of those worked either. I'm by no means a pro at PCs so I'm not 100% sure how to use commands in shortcut keys, but since I was just copying and pasting from the internet I would have assumed it would have worked.

Any help would be much appreciated

---

### Post by phidia on 2015-01-14
There's a way to do what you want with a script but that might be kind of elaborate. See if the answer posted [here]("http://askubuntu.com/questions/423114/keyboard-shortcut-to-shutdown?rq=1") could work for you.

---

### Post by casmiddy on 2015-01-15
Thanks for the reply phidia!

I have already tried that one (and just tried it again to make sure), but it just does nothing if I press the button. I can set it up as a short cut (give it a name, add the command and then select the short cut button) but pressing it after that just does nothing. Maybe I should just give up on this dream...it:s not that important after all.

Thanks for your help anyway.

---

### Post by Photobug on 2015-01-15
I was wondering what the problem is as I have not problem shutting down using my keyboard then realized my keyboard has a mouse built into it.

Logitech makes a keyboard with a trackpad built into it.  I use it to operate my Ubuntu computer on my big screen TV.  If you have a mouse you can click in the upper right corner and drag down to shutdown the computer.

---

### Post by phidia on 2015-01-15
Well if you find a solution it will make your use of ubuntu more satisfying. You can try the most recent tips at [this blog]("http://blog.3soh.flat1003.com/2013/06/creating-shutdown-shortcut-on-ubuntu/").

---

### Post by Penguin360 on 2015-01-15
I would suggest you to check Logitech web site to see if they have a Linux driver for the wireless keyboard. My guess is the kernel cannot disable the device properly with the built-in generic driver, which causes the PC not be able to enter into the suspend mode.

---

