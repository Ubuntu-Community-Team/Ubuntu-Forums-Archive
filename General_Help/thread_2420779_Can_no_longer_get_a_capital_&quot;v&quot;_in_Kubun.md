---
title: "Can no longer get a capital &quot;v&quot; in Kubuntu 18.04"
date: 2019-06-10
forum: General Help
---

### Post by cackerso on 2019-06-10
Shift+v won't give a capital v. This is true in any program, Firefox, LibreOfffice, a terminal. It will work if I use the Caps Lock key. It only seems to be for "v".  
 
The solutions I've seen seem pretty involved and look like global solutions for multiple capitalization problems.  
 
 
 I don’t see any shortcuts set to shift-v, maybe I don't know where to look. I installed "screenkey". It shows an upper case v when I do "Shift+v". I added another user and there is no problem there. I can get a lower and upper case v with a new user account.

---

### Post by Xian on 2019-06-10
Have you at any time made changes to keyboard mappings and shortcuts? 

If so ... back them out entirely. Then re-check for issues.

---

### Post by kpatz on 2019-06-11
Does rebooting fix it?  If not, there's probably a messed up configuration file in your home directory if it works ok under a different user account.

I'd back up everything in your home directory (including hidden files/directories), then rename one hidden file/directory at a time and see if the problem goes away after logging out/back in.  Or just nuke them all and start fresh, either with your current account or a new one.  If you do that you'll lose your browser bookmarks and other customizations.

---

### Post by HermanAB on 2019-06-11
This is a weird bug in X.  Set the V key combination using xev and xmodmap.  A little googling will get you going again.

---

### Post by cackerso on 2019-06-19
I think I'm out of my depth here.  After reading it's not clear to me how to set the V key combination to fix the problem of no capital v.  Running
```

xmodmap -pke

```
gives me a list with Keycode 55 = v V v V

The articles I've found give details for setting custom tables not just fixing a problem with one key.

---

### Post by HermanAB on 2019-06-19
I last had to do this about 10 years ago.

First get the key code with xev for an adjacent working key.  After some experimenting you will be able to determine what it should be for V.  

Read the xmodmap man page.  There are many examples in the man page.

Maybe something like:
xmodmap -e 'keycode 123 = V'

then either put that in rc.local or set it in the xmodmap configuration file.

I am now using a MacBook, so I cannot try it myself!

---

### Post by HermanAB on 2019-06-20
```
KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0xd6, subw 0x0, time 148129867, (88,79), root:(1145,517),
    state 0x1, keycode 55 (keysym 0x56, V), same_screen YES,
    XLookupString gives 1 bytes: (56) "V"
    XmbLookupString gives 1 bytes: (56) "V"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0xd6, subw 0x0, time 148130009, (88,79), root:(1145,517),
    state 0x1, keycode 55 (keysym 0x56, V), same_screen YES,
    XLookupString gives 1 bytes: (56) "V"
    XFilterEvent returns: False
```

Therefore try this:
xmodmap -e 'keycode 55 = V'

---

### Post by cackerso on 2019-06-23
I tried the command: xmodmap -e 'keycode 55 = V' , and it didn't solve the problem.

A couple of caveats, I can only get a capital v by using the Caps Lock key since the problem here is I can't get one with "Shift+v". I don't know
if that makes any difference.

I don't see a rc.local file in /etc and I don't see the xmodmap configuration file in my home directory (hidden or other wise) if that's where
it's supposed to be.

---

### Post by HermanAB on 2019-06-24
When you run 'xev', what happens when you press 'shift v'?

---

### Post by cackerso on 2019-06-25
xev gives all kinds of output for every move of the mouse or use of the keyboard.  But I'm pretty sure this is the output related to Shift+v:

```
KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0x1d1, subw 0x0, time 15616593, (-1305,1004), root:(149,1033),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 40, synthetic NO, window 0x5c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 40, synthetic NO, window 0x5c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 40, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   4294967172 0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x1d1, subw 0x0, time 15616859, (-1305,1004), root:(149,1033),
    state 0x11, keycode 55 (keysym 0x56, V), same_screen YES,
    XLookupString gives 1 bytes: (56) "V"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x1d1, subw 0x0, time 15616898, (-1305,1004), root:(149,1033),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by HermanAB on 2019-06-26
So, the key press is detected as keycode 55, meaning that everything works, but Xorg has forgotten something internally and doesn't know that it is supposed to display a V for it.  

Many moons ago, one of my laptops lost the capital T and I fixed it this way.  One or two other people I remember ran into the same thing over the years.  Therefore you should be able to fix it with xmodmap.  You just have to try a few times till you get the syntax right.

---

