---
title: "nvidia driver problems"
date: 2012-11-21
forum: General Help
---

### Post by ohad_ on 2012-11-21
Hello,
I'm having problems started several days ago where my screen turned black after logging into my user. Also, the resolution wasn't right on my logging screen. After trying a few solutions iv'e googled i ended up adding nomodeset on the grub launch option of ubuntu.

For sometime iv'e still had unity running, and i was able to access System settings through the button on the top right corner. when i did and i tried to set the resolution to the correct one, i wasn't able to do that, only one option appeared and the screen showed the word 'laptop' on it (and i'm not using a laptop...). 

After trying a few more things online, i ended up with unity crashing on start-up and still my resolution is incorrect. I'm able to surf using google-chrome which i can open using terminal.

please, help me fix this.

---

### Post by 2F4U on 2012-11-21
What nVidia driver are you using, the open source or the proprietary driver? What is your graphics card model?

---

### Post by ohad_ on 2012-11-21
i'm not sure how to check either of them.
when i use 
```
sudo jockey-kde
```
it shows me nvidia_current_updates.

before all this happened i think i had nvidia 173 or something similar...

---

### Post by Bashing-om on 2012-11-21
ohad_; Hi !

To see your graphics card and info:
terminal commands:
```
sudo lshw -C display
lspci | grep VGA
```post the output of the commands here and someone will have instructive response.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

