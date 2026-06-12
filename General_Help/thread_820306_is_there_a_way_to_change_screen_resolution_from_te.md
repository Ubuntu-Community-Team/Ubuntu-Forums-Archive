---
title: "is there a way to change screen resolution from terminal"
date: 2008-06-06
forum: General Help
---

### Post by danaild on 2008-06-06
real-time (without restart)?

---

### Post by iaculallad on 2008-06-06
> **danaild said:**
> real-time (without restart)?

Try **sudo xrandr -s <x_res>x<y_res>** if it will work real time.

---

### Post by danaild on 2008-06-06
works perfectly, thanks :) !

(only instead of "*" I use "x" - like 1440x900)

---

### Post by iaculallad on 2008-06-06
You're welcome, i'll changed my post from * to x.

---

### Post by tech.kyle on 2008-08-04
Any tips on how to change resolution from non-gui terminal such as terminal 1?

Example, I launch GameX and it sets my resolution to something that isn't supported. I go to tty1, log in and sudo kill. Switch back and resolution is still wrong.
Switch to tty1..
```
sudo xrandr -r 1680x1050
```
...but I just get "Can't open display"

Tried ```
sudo xrandr --output tty7 -r 1680x1050
```..but no go.

Setting resolution from gnome's GUI terminal works fine.

Suggestions?

---

### Post by tony_j on 2008-08-09
I am not sure that I should be adding to this - but I have a very similar problem having newly installed 8.04 and the screen will now not get better than 800x600 although (whilst it is an old CRT) has been used at 1027x768 previously.  The screen resolution tool stops at 800x600 so cannot select better.  &.06 worked just fine with this setup.
Can anyone advise how I can add the better resolution - as I am really stuck now.
Thanks in advance for any suggestions

---

