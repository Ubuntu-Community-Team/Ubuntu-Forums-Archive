---
title: "Keyboard keys sometimes do the wrong thing"
date: 2014-02-08
forum: General Help
---

### Post by Smart_Patrol on 2014-02-08
(Ubuntu 12.04, using Gnome, on a Lenovo Thinkpad Edge with an intel core i5)

I am finding that when I type very quickly, some keys will simply create the wrong character or activate some keyboard shortcut that that key was not designated for. 

For example, while typing a moment ago, the "b" key suddenly became the screenshot button. I pressed "b" in rapid succession, it kept generating screenshots. I then waited a few secs before trying again, and it went back to being the "b" key again.

This just started today and is very annoying. I can't find a thread about this. Can someone help?

---

### Post by egeezer on 2014-02-08
Off-the-wall suggestion: check the keyboard shortcuts for Gnome that involve the letter b.  Perhaps the paired key is somehow permanently "on".  Might press it again to see if it frees up.

Disclaimer: I'm not familiar with Gnome, but that's what occurred to me.

---

### Post by tgalati4 on 2014-02-09
Open a terminal and run *xev*.  Test each key to make sure you get one press event and one release event for each key.  It's possible that the keyboard is dirty and needs cleaning.  They are relatively easy to take out.  Search for a video on youtube.

---

### Post by Smart_Patrol on 2014-02-16
I tried "xev." I think its telling me that I'm getting one press and release event for each key. It says "false" every time I press a key. Here's an example of what happens when I test the letter "b":

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0xaf, subw 0x0, time 751437, (314,661), root:(315,718),
    state 0x0, keycode 56 (keysym 0x62, b), same_screen YES,
    XLookupString gives 1 bytes: (62) "b"
    XFilterEvent returns: False

Should I be getting a "false?" Maybe that's computerese for "correct?"

Anyway, I also cleaned the keyboard while grounding myself with a piece of metal. I think its fixed, but the problem was always intermittent to begin with; it seems to manifest itself most often when I'm doing work related writing or trying to IM a potential date with a girl. Figures x_x

I will give it another day or two and if the problem doesn't come back I will let you all know. Thanks for the advice!

---

### Post by Smart_Patrol on 2014-02-16
Ok, it's acting up again already. Now its mostly the "e" key. When I do "xev" in the terminal, and test the "e" key, here's what happens when "e" decides to moonlight as the volume-up key:

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0xaf, subw 0x0, time 13044823, (357,424), root:(358,481),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

So I guess "xev" thinks "e" is "p" while "e" acts as the volume-up key. Meanwhile, whenever "e" acts up, the actual volume up key (which doubles as f3) becomes the "}" key. Other keys are acting up as well. Is there any precedent for this problem? It's really annoying and I can't afford to pay anyone to fix this! Someone PLEASE HELP I have no choice but to fix this for free somehow!

---

### Post by tgalati4 on 2014-02-17
Did you remove the keyboard and reseat the ribbon cable?

---

