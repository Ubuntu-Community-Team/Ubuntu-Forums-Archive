---
title: "[SOLVED] Batch install for TTF fonts. Is it possible?"
date: 2007-11-21
forum: General Help
---

### Post by Luis Santos on 2007-11-21
Hi guys. I´m a Gutsy Kubuntu user.  Sometimes I download one or two free truetype (.ttf) fonts avaiable on Internet. Installing them is easy. I just right click them on Delphin and choose Action -> Install font.  But now I have 35 fonts that I need to install.  Is there a command line (or GUI batch) tool where I can install all of them in one (or very few) step (steps)?  Best regards, Luis Santos

---

### Post by hikaricore on 2007-11-21
You know you can just drop them in your *~/.fonts* directory right?  ^_^

This will install them for your current user, if you don't have multiple users it shouldn't be an issue.

---

### Post by Luis Santos on 2007-11-21
> **hikaricore said:**
>  
This will install them for your current user, if you don't have multiple users it shouldn't be an issue.

 Good input! But I have my account and my wife has her one. Which is the public fonts directory? When I install a font (right clicking on it) I always choose install it for all users.  Best regards, Luis Santos

---

### Post by nick_h on 2007-11-21
> Which is the public fonts directory?
/usr/share/fonts/truetype for truetype fonts

---

### Post by walkerk on 2007-11-21
Here is an example... this script i wrote installs ms like fonts from sharpfonts.com

This may or may not help...

---

### Post by Luis Santos on 2007-11-21
Thanks a lot for all replies. I will test tonight, at home, on my personal Kubuntu. Here in my job I have to use Windows... :cry:

---

### Post by Luis Santos on 2007-11-23
Thanks a lot guys. A simple copy of all fonts to /usr/share/fonts/truetype worked nicely. 

Thanks again,
Luis Santos

---

