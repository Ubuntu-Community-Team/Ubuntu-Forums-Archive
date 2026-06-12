---
title: "Frequency out of range when playing games.."
date: 2008-07-04
forum: General Help
---

### Post by DarK420 on 2008-07-04
Black screen pops up then i get that error and have to manually restart the comp.. ?
What do i do

Ehh I'm using the newest version of Ubuntu 8.04 hardy
with the newest wine..

this happens for some games in steam.. ?

Any help would be greatly appreciated thanks

or 

IM me on aim

iiviie   <--- aim

---

### Post by nikgare on 2008-07-04
> that error

Exactly which error are you getting?
Is the error coming from you monitor or your computer?

---

### Post by DarK420 on 2008-07-04
> **nikgare said:**
> Exactly which error are you getting?
Is the error coming from you monitor or your computer?

I'm not really getting an error it just says
Frequency out of range and goes black,, =/
its coming from the Monitor

---

### Post by bubba_169 on 2008-07-04
Sounds to me like your computer is trying to use a refresh rate that your monitor cant handle, perhaps you could configure your games to a different rate?

---

### Post by DarK420 on 2008-07-04
> **bubba_169 said:**
> Sounds to me like your computer is trying to use a refresh rate that your monitor cant handle, perhaps you could configure your games to a different rate?

I've tried different resolutions which come with different refresh rates
and i ve tried different refresh rates alone..


not sure what it is

---

### Post by DarK420 on 2008-07-04
> **bubba_169 said:**
> Sounds to me like your computer is trying to use a refresh rate that your monitor cant handle, perhaps you could configure your games to a different rate?

I've tried different resolutions which come with different refresh rates
and i ve tried different refresh rates alone..


not sure what it is

And i dont this its my gfx..

nvidia geforce 6 something like that

---

### Post by nikgare on 2008-07-04
Which monitor do you have?
Can you post  /etc/X11/xorg.conf

---

### Post by DarK420 on 2008-07-04
> **nikgare said:**
> Which monitor do you have?
Can you post  /etc/X11/xorg.conf

[http://www.bestbuy.com/site/olspage.jsp?skuId=8661879&type=product&id=1196470790533](http://www.bestbuy.com/site/olspage.jsp?skuId=8661879&type=product&id=1196470790533)

---

### Post by DarK420 on 2008-07-04
> **DarK420 said:**
> I've tried different resolutions which come with different refresh rates
and i ve tried different refresh rates alone..


not sure what it is
^

---

### Post by DarK420 on 2008-07-04
> **DarK420 said:**
> I've tried different resolutions which come with different refresh rates
and i ve tried different refresh rates alone..


not sure what it is

And i dont this its my gfx..

nvidia geforce 6 something like that
^ really need help =/

---

### Post by nikgare on 2008-07-07
can you post the following file: **/etc/X11/xorg.conf**

---

### Post by nikgare on 2008-07-07
You could also try specifying the correct frequency settings and checking that your actual monitor is detected using this command:

sudo displayconfig-gtk

---

### Post by blackhatbrigade on 2008-07-07
Are there any games you can play?  And which game is it you're trying to run?

I know, for example, that TF2 through steam on wine has established bugs when first running it.  You have to manually set some options on the shortcut to TF2 to get it running the first time (then you can change the res and graphics options in the menu after you're in).

If you're using regular wine you might want to look at wine's website and see if there's any known issues and whether or not you need to do anything special to get the particular game running.

---

### Post by hito1 on 2008-07-15
I'm having the same issue, my monitor blacks out and says it's out of range. But I'm experiencing just after the grub until the login screen and on the shutdown/restart screen.

Did you find any help?

---

### Post by Eddie Wilson on 2008-07-16
Good Day,
I had the same problem using a FX5200 nvidia card. It only happened when I tried to play in full screen mode. I had to downgrade my nvidia drivers from glx-new to just glx. After that I never had the problem again.

Eddie

---

