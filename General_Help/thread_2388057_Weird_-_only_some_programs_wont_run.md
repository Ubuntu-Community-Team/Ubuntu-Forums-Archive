---
title: "Weird - only some programs wont run"
date: 2018-03-27
forum: General Help
---

### Post by Kevin McCready on 2018-03-27
The weirdest thing is happening. When I boot the computer all seems fine. But only some programs will run. 

I can run my text editor (Sublime Text)
I can run gimp

I can't run evince, or firefox, or whatever program is the default for looking at pictures.

I booted the computer via a usb with an old version of linux.

Then I unmounted my big harddrive (with the problems).
Then I ran 
fsck -yvfM
 which reported no errors

I have no idea what to try next. I hope I haven't been subject to some strange rootkit exploit.

My system is Linux Mint 18

---

### Post by Kevin McCready on 2018-03-28
So I purged one of the programs that didn't run, then I installed it again. When I tried to run it, a tab came up on the bottom of the screen saying it was opening the program. Then the tab disappeared and nothing happened. I don't have enough skill to trace the logs and troubleshoot this.

---

### Post by again? on 2018-03-28
Run the application in the terminal to check for errors.

---

### Post by Kevin McCready on 2018-03-28
sudo apt remove virtualbox-guest*

did the trick

---

### Post by Kevin McCready on 2018-03-28
PS. The same happened when I tried to run it from the terminal

---

