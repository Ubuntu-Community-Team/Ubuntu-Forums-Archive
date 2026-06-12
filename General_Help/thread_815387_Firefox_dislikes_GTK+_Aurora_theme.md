---
title: "Firefox dislikes GTK+ Aurora theme"
date: 2008-06-01
forum: General Help
---

### Post by Bionic Apple on 2008-06-01
I have been theme-testing for a few days and have found one of the coolest themes out there.  It is Aurora Midnight and I would highly recommend it. However, there is one problem.  Firefox is very quirky about it.  I am also aware that this is in Thunderbird and OpenOffice.org, too.  Sometimes it will highlight things two different ways.  Other times, it may draw a box around something that isn't supposed to have a box.  Let me show you with pictures of my iGoogle page:

---

### Post by spupy on 2008-06-01
I am using this theme on Firefox 3 and have the same problem. I already asked the developer of the theme engine if he could fix it.

The problem comes from the background of the widgets. In normal GTK apps, a button has background color as the color of the thing he is placed in (his parent widget). Since Firefox is not a GTK program, it just takes the widget with some default background. In the Midnight theme it is black and is what causes these ugly boxes around things. I think it is possible to fix, because Combo Box widgets don't have an ugly box around them - because they have a transparent background. If one could change the other widgets to have a transparent background, all would be nice. I have the source code here and tried fixing it, but I can't program in GTK, so it's too hard. That is why I asked the developer, let's wait and see if he can come up with something.

---

### Post by Bionic Apple on 2008-06-01
So, basically there is no hope for this problem unless we get a bored GTK coder in here?

---

### Post by rainwalker on 2008-06-01
> **Bionic Apple said:**
> So, basically there is no hope for this problem unless we get a bored GTK coder in here?

There is hope, but you probably have to ask the developer of the Aurora theme engine to fix it.

---

### Post by Bionic Apple on 2008-06-01
I'll see if I can find his email, as it is probably on gnome-look.org.

Update: Alright, I emailed him for clarification.

---

### Post by Bionic Apple on 2008-06-03
Bump, plus I have emailed the Firefox GTK+ developer (I think).  So that is two people who will hopefully shed some light on this problem.

---

### Post by Bionic Apple on 2008-06-03
Bump, plus apparently Firefox RC2 is going to be released in about a day.  I found that out while waiting for a GTK+ developer in the IRC.

---

