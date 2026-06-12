---
title: "How to create a certain hotkey?"
date: 2012-10-22
forum: General Help
---

### Post by Cpt Vimes on 2012-10-22
Hello.

I've been looking for a way to achieve something like this: When I press Alt+A, the letter "å" is sent to the screen.

First I tried creating a hotkey through the settings panel, which executes "xdotool key Aring". But that has about 2 seconds delay between pressing the keys and the letter appearing.

I've been looking into xmodmap, but I find it really confusing and I can't find any specific examples of what I'm trying to do here.

Does anyone have an alternative or maybe help me with xmodmap?

---

### Post by Cpt Vimes on 2012-10-24
Bump!

---

### Post by black veils on 2012-10-24
is this what you want to do..

1. go to **system settings** >> **keyboard** >> **shortcuts** tab >> **custom shortcuts** from the left pane

2. select the plus sign from the bottom, enter name and command (example: firefox).

3. it will show in the list, then select where **disabled** shows,  and enter your keys.

---

### Post by Tralce on 2012-10-24
Or you could set up the Compose key.

---

### Post by Cpt Vimes on 2012-10-24
> **black veils said:**
> is this what you want to do..

1. go to **system settings** >> **keyboard** >> **shortcuts** tab >> **custom shortcuts** from the left pane

2. select the plus sign from the bottom, enter name and command (example: firefox).

3. it will show in the list, then select where **disabled** shows,  and enter your keys.

As I stated, this was the first thing I tried, but it didn't work very well.

> **Tralce said:**
> Or you could set up the Compose key.

Thank you, that was exactly what I needed!

---

