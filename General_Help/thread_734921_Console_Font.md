---
title: "Console Font"
date: 2008-03-25
forum: General Help
---

### Post by snowsmash on 2008-03-25
I liked the font on the console when I was using Feisty (Linux image 2.6.20-16). After upgrading to Gutsy (Linux image 2.6.22-14), the font on the console was different. I compared /etc/default/console-setup on the two releases and saw that both were configured to use font face VGA at size 16. Yet, I tried out the other font faces (Terminus*, Fixed, and Goha*) to see if I could get back the console look I used to have on Feisty but could not. I also tried activating the frame buffer console  in the kernel and setting different modes and compiled-in fonts but got nowhere. However, I noticed that the GRUB menu--on Feisty as well as on Gutsy--displays text in the font I am looking for. Is that possibly a font built into one of the text modes of my video card? Is it perhaps that Feisty was using a video card text mode to set up the console? If yes, how can I get to the same setup in Gutsy?

---

### Post by x1a4 on 2008-03-25
HOWTO: [Fix console fonts in Gutsy]("http://hex1a4.net/xubuntu/howto.php?htid=02")

---

### Post by notwen on 2008-03-25
[fixed link]("http://hex1a4.net/xubuntu/howto.php?htid=02")

---

### Post by x1a4 on 2008-03-25
> **notwen said:**
> [fixed link]("http://hex1a4.net/xubuntu/howto.php?htid=02")

Missed the closing quote in the url tag.  Thanks.

---

### Post by snowsmash on 2008-03-26
Thank you for the link. I followed the instructions and activated the frame buffer console. However, I still did not get the font on the console to look like the font in the GRUB menu. I am guessing that the font used in the GRUB menu, which I like, is that of a video card text mode. I am wondering how I could set up the console such that it uses that same text mode, which seems to me to have been the setup in my Feisty installation.

---

### Post by snowsmash on 2008-03-26
I was able to get to where I wanted by blanking out the FONTFACE and FONTSIZE variables in /etc/default/console-setup and running update-initramfs, which caused the console setup process not to set a font during booting, thus leaving the font of the video card text mode as it is, I suppose. What I have not yet been able to answer is why things were different in my Feisty installation, where the system initialization process apparently did not set a font on the console even though FONTFACE and FONTSIZE were set to VGA and 16, respectively, in /etc/default/console-setup.

---

