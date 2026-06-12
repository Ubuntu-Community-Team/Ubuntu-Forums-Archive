---
title: "Openoffice buttons and menus have dissapeared"
date: 2006-07-14
forum: General Help
---

### Post by megadodo on 2006-07-14
I have installed ubuntu-desktop on a kubuntu installation to try out gnome, and Ive come across a problem with openoffice. The buttons and menus seem to have dissapeared. If I pass the mouse over the buttons they reappear, but dissapear as the mouse moves on. I have attatched a screenshot.
Any ideas?
Thanks in advance
Richard

---

### Post by amunimanghi on 2006-07-14
Why not try reinstalling it?

---

### Post by megadodo on 2006-07-15
Ive reinstalled all the openoffice bits, and uninstalled the openoffice.org-kde package, but I still have the same program. If I start openoffice in kde (before i uninstalled the kde package!) it worked fine.
Thanks
Richard

---

### Post by slimdog360 on 2006-07-15
thats really wierd, Ive never heard of anything like that before. I wouldnt know where to start but it may not be an openoffice thing but rather a graphics driver thing? Is there anything else thats running a little different than normal? Also does it only happen in Writer?

If it only happens in writer and everything else runs fine maybe you could just use a different word processor. Personally I use Abiword and Gnumeric.
Just a thought.

---

### Post by Rui Pais on 2006-07-15
Hi,
try the following. Open Oo and at the menu go:
Tools -> Options and then Openoffice.org -> View. 
Search 'Icons size and style' label. 
Under that title you got 2 comboboxs. The first allow to config the size of buttons, the second the Icons theme. 
Try to play with them and see if you got some luck. Specially the second, check if you got 'Industrial' checked try to experiment with 'Automatic' or the kde 'Crystal'.

If that wont work, close all Oo app and on terminal do
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```
Restart OpenOffice.


Edit: check too that you have openoffice.org-kde installed:
```
sudo apt-get install openoffice.org-kde
```

---

### Post by megadodo on 2006-07-15
Thanks for the replys
I tried playing with the icon settings as suggested but to no effect. Moving the config files also did not have an effect. 
However I tried uninstalling openoffice.org-gtk and the problem dissapeared, so presumably it is a problem with that package. But anyway i can use openoffice now, and looks reasonably ok, so i'll live without the gtk stuff!
Thanks
Richard

---

### Post by dsokus on 2006-08-02
> **slimdog360 said:**
> thats really wierd, Ive never heard of anything like that before. I wouldnt know where to start but it may not be an openoffice thing but rather a graphics driver thing? Is there anything else thats running a little different than normal? Also does it only happen in Writer?
Just for the record, I had the very same problem, and it was fixed by the same thing. I have no idea what causes it - it might be worth looking into for the developers!! 

Z.

---

### Post by daxdog on 2007-01-26
Apparently this problem has still not been fixed.  I was just having the same problem in OpenOffice.org Writer only in GNOME.  By uninstalling openoffice.org-gtk and openoffice.org-gnome the problem went away.

---

### Post by lvanderree on 2007-03-23
I think I fixed it (again) 

I had some serious issues in feisty, and took a rigirous step by moving my entire home-folder to a backup location, giving me a clean start. 

Now openoffice (2.2) which still had the issue before this measure works again as normal (with beryl running)

maybe other people with this issue can also check if a new user on their system also have a normal openoffice.

---

