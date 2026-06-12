---
title: "added Kubuntu desktop -can't log in now"
date: 2007-05-31
forum: General Help
---

### Post by f-emeral on 2007-05-31
Hi - Installed Ubuntu Feisty a couple of days ago and have been delighted with how intuitive a system it is and how straight forward to use. I have occasionally played with Mandrake and SUSE over the years but Ubuntu is the first Linux installation that I would feel comfortable using as my primary OS.
I have just installed Kubuntu Desktop and after rebooting have problems logging in. After entering my password the screen goes black for a few seconds and then returns to the log in screen. Now when installing the Kubuntu Desktop I clicked 'yes' without thinking when asked if I wanted it as my default desk top. I guess this is what's caused the problem?  I would really appreciate some advice as to how to get into my system again- I was only trying Kubuntu Desktop out of curiousity!
Many thanks, John

---

### Post by floke on 2007-05-31
First, from the login screen can you change your session and log in to Gnome? Failing that, the failsafe terminal. From there, try: sudo dpkg-reconfigure gdm (it might be kdm if you clicked through the options on installing K-desktop) - you can alter some of your settings - if its kdm you're using, try changing the default to gdm.

Good luck

---

### Post by f-emeral on 2007-05-31
Thanks Steve - the failsafe route worked. Well after all that I prefer GDM. 
The only thing I need to change  now is the screen during boot which still shows as Kubuntu. How do I get it to revert to Ubuntu? Is it just a matter of uninstalling the Kubuntu Desktop?
TIA,  John

---

### Post by f-emeral on 2007-06-01
The answer to my second question was already in this forum -apologies for not thinking to check first!
  
Rubengs' solution, which follows, worked perfectly:-

"Re: Change boot screens
Not my solution, copied and translated from [http://www.espaciolinux.com/foros-tema-t26526.html](http://www.espaciolinux.com/foros-tema-t26526.html) :

To chose usplash theme:
Code:

sudo update-alternatives --config usplash-artwork.so


Then update initramfs with:
Code:

sudo update-initramfs -u

To test the new usplash theme:
Code:

sudo usplash -c

To go back to your session press Ctrl+Alt+F7."
__________________

---

