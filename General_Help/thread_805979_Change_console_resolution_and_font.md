---
title: "Change console resolution and font"
date: 2008-05-24
forum: General Help
---

### Post by Jonathan Lahav on 2008-05-24
Hello.
When I had the 8.04 beta installed, the console at boot time, and the alternate consoles had a very nice sharp font with high resolution.
Now, in the final release I have a thin big weird font that starts to appear in the _middle_ of the boot and serves also the alternate consoles.
How can I change the resolution and font back to the beautiful and useful one?

Thanks!

---

### Post by latna on 2008-05-25
There could be something useful here: [http://ubuntuforums.org/showthread.php?t=347856]("http://ubuntuforums.org/showthread.php?t=347856")

---

### Post by Jonathan Lahav on 2008-06-10
Thank you very much! I found the answer.

This is the way to go:
* open the terminal
* paste this command
sudo dpkg-reconfigure console-setup
* press enter until you get to a dialog where you have to choose between vga and fixed.
* choose vga and then 16
* you're all done!

---

