---
title: "small fonts /write permission denied despite root user"
date: 2007-09-01
forum: General Help
---

### Post by SiRiuS-233 on 2007-09-01
Hi guys

ive got this silly small font issue 
ive tried edit /.config/xfce4/Xft.xrdb

i get : Warning: unknown mime-type for "/.config/xfce4/Xft.xrdb" -- using "application/*"
Error: no write permission for file "/.config/xfce4/Xft.xrdb"

don't know what the first bit means but
ive done this a root ,so i dont get why it tells me i don't have write permission.

be very grateful for any suggestions

many thx in advance

---

### Post by taurus on 2007-09-01
How do you log in as root?

---

### Post by SiRiuS-233 on 2007-09-01
sudo -i
and password

---

### Post by taurus on 2007-09-01
Do you want to edit .config/xfce4/Xft.xrdb in your $HOME or root--/root?

$HOME:
```
nano -Bw ~/.config/xfce4/Xft.xrdb
```

Root:
```
sudo nano -Bw /root/.config/xfce4/Xft.xrdb
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by kerry_s on 2007-09-01
your going about it all wrong, no doubt using sudo in your user account has already screwed everything up. best thing to do is start from scratch.

sudo rm -rf ~/.cache 
sudo rm -rf ~/.config 

ctrl+alt+backspace
select xfce4 in the session menu and login

did you try adjusting the fonts from the settings? see pic, user is for applications & window is just for the window title.

if you fonts are still messed up->
mousepad .Xdefaults
put
Xft.dpi:100

adjust the number till it's what you want.
you need to put->

xrdb -merge $HOME/.Xdefaults

in the application startup.
log out and back in to see the changes.

---

### Post by SiRiuS-233 on 2007-09-01
well....thx a lot kerry
my font issue is solved ....but all my plug ins are gone and compiz doesen't run any longer...
guess i have to reinstall everything...

---

### Post by taurus on 2007-09-01
> **SiRiuS-233 said:**
> well....thx a lot kerry
my font issue is solved ....but all my plug ins are gone and compiz doesen't run any longer...
guess i have to reinstall everything...

That's what happens when you remove the ~/.config directory.  Everything is gone and that leaves you only with defaults.

---

### Post by SiRiuS-233 on 2007-09-01
actually compiz still works ,just needs reconfiguring
so thx again
...just wish I d understand what i have done

---

### Post by kerry_s on 2007-09-01
> **SiRiuS-233 said:**
> well....thx a lot kerry
my font issue is solved ....but all my plug ins are gone and compiz doesen't run any longer...
guess i have to reinstall everything...


you didn't mention nothing about compiz, i a summed a standard xfce4 install. my apologizes, if i had known i would have used the exact path to all xfce folders instead of doing the quick way. your programs are still there you just have to set them up again, compiz is the most likely cause of your font problems. please mention that your using that the next time you have a problem.

---

### Post by SiRiuS-233 on 2007-09-01
sorry for that, my bad
i was just setting up everything again and now have another problem
so to be precise this time
I usually have my pc hooked to my 32"Lcd TV
but when i was using the entrys you gave me , i had it connected to my 19" monitor
cause my GF was watching this xfactor crap on TV (so annoying)
so when i reconnected just now , i noticed that the fonts in the folders on my desktop are 
bit to big , so i went to change them , ive also changed the right mouse button to display the application menu
but now ,when hitting applications or pressing right mouse button , just a very tiny square comes up
and i basically cant do anything with it,so i have no access whatsoever to my system settings and apps (apart from alt F2 i guess,but being a noob , iam again clueless)
apart from that everything else seams to work just fine.
so the question is if i can change this without completely resetting everything like before?

many thanks again

---

### Post by SiRiuS-233 on 2007-09-01
btw , i managed to open a terminal by right clicking a folder
so if you could kindly help me out with the right entry's i be grateful

---

### Post by SiRiuS-233 on 2007-09-01
ok , i managed tosort it out by right clicking on the apps button - edit menue

thx anyway

---

