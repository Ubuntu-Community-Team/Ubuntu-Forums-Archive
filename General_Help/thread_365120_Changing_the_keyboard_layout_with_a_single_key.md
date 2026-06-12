---
title: "Changing the keyboard layout with a single key"
date: 2007-02-19
forum: General Help
---

### Post by Spr0k3t on 2007-02-19
I'm making the switch from qwerty over to dvorak (up to 20wpm after a week and a half, doing good).  So I would like to find a way to set up the Scroll Lock key to toggle my keyboard layout.  I'd like to default to dvorak on boot.  I know it will take modding my xorg.conf, just don't know what I need to change or modify for it to work.

Thanks!

---

### Post by sdide on 2007-02-19
Hey, 

Just replace the "us" and "dk" with the two keymaps you want to swap between in the script below

```
#!/bin/bash
kbd1="us"
kbd2="dk"
if setxkbmap -print | grep xkb_symbols | grep -q +$kbd1+; then  
    setxkbmap $kbd2 
    exit 0
fi
if setxkbmap -print | grep xkb_symbols | grep -q +$kbd2+; then 
    setxkbmap $kbd1
    exit 0
fi
exit 1

```

then you need to bind the execution of this script to your preferred key.
eg. in blackbox with bbkeys running, you would do 
add the line 
[Execute] (key) {<path_to_script_above><name_of_script_above>} 
in your .bbkeysrc

---

### Post by Spr0k3t on 2007-02-19
Sweetness!  This worked like a dream.  Many thanks!

---

### Post by mr_c0w on 2007-04-30
I used to use alias for the xkbmodmap that used the home rows to switch when I was on the command line..
aoeu would switch me back to qwerty
asdf would swtch me back to dvorak

---

### Post by strabes on 2007-04-30
It's awesome that you're switching to dvorak. I've been using it for years and type effortlessly at 90-100 wpm (on a laptop).

Here's how I learned: [http://gigliwood.com/abcd/abcd.html](http://gigliwood.com/abcd/abcd.html)

Just use that and also open up a picture of the dvorak layout on your screen at the same time. It took me a couple weeks to get up to the speed I was typing with qwerty. (as opposed to years of typing classes in elementary school)

---

