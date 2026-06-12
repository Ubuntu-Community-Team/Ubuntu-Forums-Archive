---
title: "Applications meu does not pop down"
date: 2008-05-17
forum: General Help
---

### Post by tarekeldeeb on 2008-05-17
Hello Ubuntu community,

I have started the Menu Editor, removed an item from the wine submenu. A program that I had previously uninstalled <no longer working> but its launcher still existed. After removing its item, the Applications did not pop down any more!!

When I click on "Applications", it only changes its color.

"Places" and "System" still work.

How can I fix this problem?

---

### Post by ibuclaw on 2008-05-17
Right-Click on the Applications bar and select "Edit Menus".

Are the folders and shortcuts still available to see there?

Regards
Iain

---

### Post by tarekeldeeb on 2008-05-17
> **tinivole said:**
> Right-Click on the Applications bar and select "Edit Menus".

Are the folders and shortcuts still available to see there?

Regards
Iain

I right click >> Edit Menus

Nothing happened!!

---

### Post by chrisccoulson on 2008-05-17
Sounds like your menu configuration is broken. Can you log in with a fresh user account to see if the problem is specific to your user account. If it is, then it's easy to fix. You can just delete your custom menu configuration so they work again.

I'll be able to help you do that

---

### Post by tarekeldeeb on 2008-05-17
> **chrisccoulson said:**
> Sounds like your menu configuration is broken. Can you log in with a fresh user account to see if the problem is specific to your user account. If it is, then it's easy to fix. You can just delete your custom menu configuration so they work again.

I'll be able to help you do that

You are thinking in the correct direction :)

The new user i made had normal menus .. So i fetched till i went into here:

/home/<myUserName>/.config/menus

and found:

applications.menu
applications.menu.undo-12
applications.menu.undo-13

I deleted the "applications.menu"
and renamed the last undo file I have there.

It worked :)

Thanks  ..

---

### Post by chrisccoulson on 2008-05-17
Good stuff! Glad it's sorted:)

---

### Post by manosone on 2008-05-17
Alo everybody.Well i got a similar problem.When i 'm clicking one of the:software sources,login windows,hardware drivers,synaptic pack. manager.,and others,nothing happens.The circle count for about 5 secs an then nothing happens.I created another user(dekstop and admin)an tried to do the same.Nothing happened again.Moreover when i'm running synaptic from terminal,it runs.I didnt checked the others cause i do not know the right commands.I am a new user by the way and i am running heron.Any ideas how to fix this?

---

### Post by tarekeldeeb on 2008-05-17
> **manosone said:**
> Alo everybody.Well i got a similar problem.When i 'm clicking one of the:software sources,login windows,hardware drivers,synaptic pack. manager.,and others,nothing happens.The circle count for about 5 secs an then nothing happens.I created another user(dekstop and admin)an tried to do the same.Nothing happened again.Moreover when i'm running synaptic from terminal,it runs.I didnt checked the others cause i do not know the right commands.I am a new user by the way and i am running heron.Any ideas how to fix this?

Actually I am a nebie like u .. but i think you have got another problem.

---

### Post by manosone on 2008-05-18
Which is?You mean that i must refer my prob to another section or i misunderstoud(misspelled i know)that?By the way problem not solved.

---

