---
title: "Kubuntu Feisty Mouse - please help!"
date: 2007-04-21
forum: General Help
---

### Post by neoncode on 2007-04-21
I'm on Kubuntu Feisty and I have USB mouse, when I log on it works fine. At least for a while, after anywhere between a few minutes to an hour it just stops. My mouse no longer moves the cursor or clicks. It's an optical mouse and is still lit up. However, plugging in another USB mouse or a PS/2 mouse and the new mouse works. I have had a 2nd PS/2 mouse plugged in since boot-up these last few times and even when the USB one has stopped this one still works indefinitely. I know it's not a hardware problem because I didn't have this problem in any previous version of Kubuntu, or in Vista now(I dual-boot). Also, after it stops working. when I try to switch to another console, restart the X server or log-off/shutdown the entire system hangs on a black screen with just the cursor there that no mouse will move.

Please help me this is really getting on my nerves! :confused:

---

### Post by K.Mandla on 2007-04-21
Is this by chance a Pentium III or Pentium III mobile machine? I used to get some mouse stutter on an old Pentium III laptop, and the problem had something to do with a kernel issue and the processor -- but it was skipping a lot more frequently, like every minute or two.

Have you tried looking in any of the logs inside the /var/log/ folder? If you're suffering the same problem I had, it might be visible in there.

---

### Post by neoncode on 2007-04-21
Nope, I have a Core 2 Duo. And as I said this hasn't happened on linux before. Or in windows. However, that was on my last computer, this new one has only ever seen feisty and Vista, same mouse though. Also, I use the nvidia binary drivers. is it possible that when I ran "sudo dpkg-reconfigure xserver-xorg" that I selected the wrong mouse input?

---

### Post by K.Mandla on 2007-04-22
Yes, it's possible, but I can't imagine that causing mouse stutter like you describe. You could re-run the dpkg-reconfigure and pick a different mouse setup, just as a troubleshooting measure.

---

### Post by neoncode on 2007-04-22
Ok I'll do that and re start the X-server. (Currently my USB mouse is still working, so the server should restart fine... I hope...) Then I'll post the result here...

---

