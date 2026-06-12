---
title: "keyboard mapping problem due to automatic xkbmap -option"
date: 2014-01-15
forum: General Help
---

### Post by Samarions on 2014-01-15
Hi, 

I installed 13.10 a week ago and haven't had any problem with the  keyboard before. Today all of a sudden, after having done a software update and updated grub and  grub2, installed unity tweak tool (to add some more workspaces), I  added a german and a russian keyboard layout to my list (already had swedish and  english). Kept on surfing and after 5 minutes, my backspace kept  printing ]:s and my ' didn't work. 
I realized it had something to do with the mapping of the keys and checking up the keyboard mapping setup gave the following result. 

[I][B]setxkbmap -query
rules:      evdev
model:      pc105
layout:     se,us
variant:    ,
options:    japan:nicola_f_bs[/B][/I]


the option japan:nicola_f_bs is what messes everything up. I can delete it with ***setxkbmap -option*** but it's not permanent so I have to do it every time I start the computer and also if I switch language.

The same problem is described [here]("http://askubuntu.com/questions/377667/my-keyboard-is-coming-up-with-strange-options/404757").

How can I make a permanent change?

---

### Post by Samarions on 2014-01-30
> **Samarions said:**
> 
How can I make a permanent change?

Problem solved. Somehow my dconf-settings had been altered. I was able to change back to default by using the dconf-editor according to this instruction: [http://unix.stackexchange.com/questions/66624/where-is-xkb-getting-its-configuration](http://unix.stackexchange.com/questions/66624/where-is-xkb-getting-its-configuration)

---

