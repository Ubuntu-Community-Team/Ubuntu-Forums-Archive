---
title: "Is my splash screen stuck looking glitchy?"
date: 2013-07-11
forum: General Help
---

### Post by caraj on 2013-07-11
On boot, it looks normal except that its edges get what looks like static, or its colors sometimes look like the negative of a photograph.
Is this because of my computer (a Dell Latitude D600), or could this issue be fixed by downloading anything?

---

### Post by Cavsfan on 2013-07-13
> **caraj said:**
> On boot, it looks normal except that its edges get what looks like static, or its colors sometimes look like the negative of a photograph.
Is this because of my computer (a Dell Latitude D600), or could this issue be fixed by downloading anything?

First of all, have you installed the appropriate video driver?

You could take a look at the green community wiki in my signature for setting up a custom grub2 screen that never needs modified unless you add or remove an OS.
There are some example pictures of what it could look like. There is a link at the bottom to post questions or problems.

If all you want is a background. Just copy a picture into **/boot/grub/** but, make sure there is only 1 picture in that folder.
**sudo cp *picture-file-name* /boot/grub/** and make sure you enter **sudo update-grub** for the change to take effect.
In the output you should see your picture listed. 

Some pictures do not work but, most do. You can use any picture format. 

If you want to change the font size, the font colors and make custom menu entries it is all there.
The font colors will depend ***if*** it finds a picture in** /boot/grub/**.

---

