---
title: "Typing latency in Gnome"
date: 2017-08-26
forum: General Help
---

### Post by tpg on 2017-08-26
I'm having a slightly strange issue that appears to be limited to the GNOME desktop environment. I'm running Ubuntu (gnome flavour) 17.04, 4.10.0-32-generic.

The problem is this: there is a significant latency when typing most non-alphanumeric characters, when previously I have been typing alphanumeric characters. To most easily see the problem, I can do the following:

1. Log in to GNOME
2. Open up any application that accepts text input (a terminal, text editor, web browser...)
3. Do a 'trill' on two letters keys, say j & k with the right hand.
4. Whilst doing that, occasionally press a symbol such as "-" or "#".
5. I notice a significant (quarter to half a second?) pause before the display catches up, 

To paraphrase: when typing the following sequence quickly

jkjkjkj-kjkjkj-kjkjkjk-jkjkjkjk-jkjkjkjk-jkjkjk-jkjkjk

There are significant pauses every time "-" is pressed. Obviously this is a contrived example, but in the course of normal typing it results in noticeable pauses every time a punctuation character is typed, which is very annoying!

If I use a different desktop environment on the same installation, say awesome or FVWM, the problem does not occur.

Does anyone know what the cause could be? Or, if not, what Gnome might be doing with keyboard input that is different compared to other desktop environments?

Also, I'd be interested if it's just me, or if other people see the same thing too. Thanks very much!

---

### Post by tpg on 2017-08-26
I'll add that this doesn't seem limited purely to GTK applications - it's still reproducible in xterm, and similar pauses can be seen in the output of xev.

---

