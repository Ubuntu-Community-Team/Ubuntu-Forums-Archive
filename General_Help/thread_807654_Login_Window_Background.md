---
title: "Login Window Background"
date: 2008-05-26
forum: General Help
---

### Post by MugenDraco on 2008-05-26
I'm using Gutsy Gibbon on a Dell Inspiron 1520, and I want to display an image at the login screen, but it won't display.  The background is just black.  It did the same thing on my old Toshiba Satellite P35, so I'm guessing it's a software error and not my graphics card or something.

---

### Post by Chainz on 2008-05-26
I believe this site might help you: [http://www.gnome-look.org]("http://www.gnome-look.org")

---

### Post by MugenDraco on 2008-05-26
That site has a lot of themes and wallpapers for download, but I'm trying to make a custom one with a picture I already have; it just won't display.

---

### Post by Malvolio on 2008-05-26
I'm having a similar problem after reinstalling Ubuntu fresh on my laptop.  I can set the color but it refuses to use the image I set.  Additionally, I randomly get kicked out of my GUI when trying to edit my login appearance further.

---

### Post by Malvolio on 2008-05-26
Just giving notice that I have yet to find a fix for this.

---

### Post by Malvolio on 2008-05-27
Well, here's a possible culprit.  In /etc/gdm/gdm.conf there are these three lines.

#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true

I've activated these in my conf but it seems to have had no effect on the customizability of my login.  It's still only the color I select (or lack thereof if I unclick the color option).  Additionally, telling it not to use a theme only traps me in a login-logout cycle till I restart the laptop.  I really want my login background. T,T

---

### Post by Switch92 on 2008-05-27
I'd like to be able to customize my login screen too.

---

### Post by Malvolio on 2008-05-30
Surely someone's had this problem and found a solution.  I am loath to attempt any drastic fixes as the last time I tried something drastic I had to have a friend recover some vital files I had inadvertently deleted.

---

### Post by Malvolio on 2008-06-07
I'm still at a loss as to what is wrong.  Any assistance would be lovely.

---

### Post by Malvolio on 2009-07-17
I had a background image till I recently fixed another bug where I had my .dmrc file ignored under 644 and 700 permissions.  Now I can't get my my background image to reappear.  Any help would be nice.

---

### Post by Legace on 2009-07-17
Go to gnome-look.org, find a GDM you like, download, extract the tarball, replace the wallpaper file with the one you want (remember to resize), create tarball, install theme. Can't be more specific as I don't have time. Sorry :/

---

