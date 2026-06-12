---
title: "[SOLVED] Make the Caps Lock key a Shift key"
date: 2007-07-02
forum: General Help
---

### Post by apeter on 2007-07-02
I am using a Vaio laptop and the left shift key is faulty (only works if I thump it).
In Windows I solved this with a registry hack.

I am brand new to Ubuntu so please be as simplistic as you like.
I have searched various sites but all answers I've come across assume an existing knowledge of Linux/Ubuntu.

So my question is:
How can I remap keys using Ubuntu?

Also any suggestions of good sites for newbies to help learn the finer qualities of Ubuntu  and the Terminal, etc. would be appreciated?  

Thanks in advance.

---

### Post by kuja on 2007-07-02
Try running the following in a terminal and  see if it works for you. 

(Fraid it's not 100% copy & paste)
Here's what you do first
open a terminal
run xev

press the shift key, write down or remember the keycode #
do the same for the caps lock key.

run these commmands in a terminal to test the setup 
don't be afraid to make mistakes because in the worst case scenario all you have to do is logout and log back in.

```
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "remove Shift = Shift_L"
xmodmap -e "keycode thecapslockkeycodenumber = Shift_L"
xmodmap -e "keycode theshiftlkeycodenumber = Caps_Lock"
xmodmap -e "add Lock = Caps_Lock"
xmodmap -e "add Shift = Shift_L"
```

Try it, see if it works. If it's working okay, then create a file ~/.xmodmap and put this in it:
```
remove Lock = Caps_Lock
remove Shift = Shift_L
keycode thecapslockkeycodenumber = Shift_L
keycode theshiftlkeycodenumber = Caps_Lock
add Lock = Caps_Lock
add Shift = Shift_L
```

---

### Post by apeter on 2007-07-03
That works great, thanks kuja.

---

