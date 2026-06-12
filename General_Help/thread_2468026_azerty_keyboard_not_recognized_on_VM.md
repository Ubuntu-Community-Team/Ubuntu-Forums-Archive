---
title: "azerty keyboard not recognized on VM"
date: 2021-10-16
forum: General Help
---

### Post by ivanub on 2021-10-16
Hi everyone,
New user here.

I'm running Ubuntu 20.04 on a desktop and same on a Google Cloud VM.
My azerty (Belgian) keyboard works fine on my desktop, but I'm having some issues in the VM: With the exact same language, formati and kb setting as my desktop, the VM does not want to accept the azerty layout. When I have the azerty layout (be wang) selected in the VM and open the on screen keyboard, the keys don't match. So I'm pressing 'a' (first letter top left on my physical keyboard) and the on-screen keyboard indicated that 'q' (first letter second row) is pressed.

I'm now using the US layout in querty since most letters in reverse from the azerty layout, but this is driving me insane because the special characters do not match.
I've tried with another keyboard and it's the exact same result. OK on the desktop, but in the VM (via the desktop) it doesn't work.

settings:
XKBLAYOUT=be
XKBVARIANT=wang
BACKSPACE=guess

Does any of you have any idea what's going on and how to fix this?
Thanks,
Ivan

---

### Post by GhX6GZMB on 2021-10-16
You probably need to install the keyboard layout in your VM first. Otherwise it always defaults to US no matter what you try to select.

---

