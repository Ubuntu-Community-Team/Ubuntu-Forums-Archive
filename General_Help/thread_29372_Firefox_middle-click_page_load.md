---
title: "Firefox middle-click page load"
date: 2005-04-24
forum: General Help
---

### Post by aimaz on 2005-04-24
Hi,
I used to be able to load a webpage I had selected by pressing the middle mouse button over firefox. This doesn't work in my ubuntu install. How can I enable it?

Aimaz

---

### Post by Burgundavia on 2005-04-24
This works for in FF 1.0.2 on Hoary.
Corey

---

### Post by aimaz on 2005-04-24
[QUOTE=Burgundavia]This works for in FF 1.0.2 on Hoary.
Corey[/QUOTE]

I am using FF 1.0.2 on Hoary

---

### Post by aimaz on 2005-04-24
I've just figured this one out. The steps to enable this are

[list=1]
[*]type 'about:config' in the address box
[*]in the 'filter' text box type 'middlemouse.contentLoadURL'
[*]double click on the row so that the value column is set to true
[/list]
Pretty easy really.

Aimaz

---

### Post by estel on 2005-04-24
My middle click isn't working in Firefox - but it isn't working throughout Ubuntu (as far as I can see) either.

And no, it isn't because of how about:config is set in Firefox.

---

### Post by aimaz on 2005-04-30
[QUOTE=estel]My middle click isn't working in Firefox - but it isn't working throughout Ubuntu (as far as I can see) either.

And no, it isn't because of how about:config is set in Firefox.[/QUOTE]

I imagine that is an xserver configuration issue.
Try playing with the protocol option of your mouse in /etc/X11/xorg.conf

---

### Post by dninja on 2005-05-04
[QUOTE=aimaz]I've just figured this one out. The steps to enable this are

[list=1]
[*]type 'about:config' in the address box
[*]in the 'filter' text box type 'middlemouse.contentLoadURL'
[*]double click on the row so that the value column is set to true
[/list]
Pretty easy really.

Aimaz[/QUOTE]

That worked for me. Thanks

---

