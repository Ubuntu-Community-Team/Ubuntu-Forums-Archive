---
title: "Enabling Dual Screen On Fiesty Stops Startup"
date: 2007-07-05
forum: General Help
---

### Post by alexsabree on 2007-07-05
Ok so im quite new to linux and this is one of my first distros ever used. I tried to enable dual screen for my monitor by first editing my xorg file. I dont exactly remember what i added in the xorg file but i was falling the steps that i was given very closely. (even though they werent very good steps) :)

Now ubuntu wont startup and i dont know what im supposed to put in the backup terminal to re-edit my xorg file. If i was given access to my xorg i would be able to fix it.

How can i edit my xorg file? What about using a live cd?

I really dont want to have to reinstall ubuntu cause i have compiz-fusion installed and that took alot of effort to get to work.

Any help or suggestions is appreciated. :popcorn:

---

### Post by Soarer on 2007-07-05
In the terminal you boot to type:
```
gksudo gedit /etc/X11/xorg.conf
```

HTH

---

### Post by felix.rommel on 2007-07-05
> **alexsabree said:**
> Ok so im quite new to linux and this is one of my first distros ever used. I tried to enable dual screen for my monitor by first editing my xorg file. I dont exactly remember what i added in the xorg file but i was falling the steps that i was given very closely. (even though they werent very good steps) :)

Now ubuntu wont startup and i dont know what im supposed to put in the backup terminal to re-edit my xorg file. If i was given access to my xorg i would be able to fix it.

How can i edit my xorg file? What about using a live cd?

I really dont want to have to reinstall ubuntu cause i have compiz-fusion installed and that took alot of effort to get to work.

Any help or suggestions is appreciated. :popcorn:

Btw: Can you give information which graphic card do you use?

OK, here we go - if you have to insert your password, you must type in your regular password which you use normally for login.

1. Power on your computer
2. In the first screen of your boot menu press "e" to edit the "Ubuntu..." boot entry.
3. In the next screen goto the line which says "kernel /vmlinuz-..." and press "e" again
4. In the next screen type " single" and press <Return>
5. In the next screen press "b" - that starts Ubuntu without a graphical login screen
6. As soon as a login prompt appears in command line, login in with your user name and password
7.Make a backup of your current xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-2007-07-05

8. Call dpkg-reconfigure to setup your graphic settings. Follow the instructions on the screen. Normally you can choose defaults and go further. You can navigate with your <Tab> tabulator key and your cursor keys and <Return>.

sudo dpkg-reconfigure xserver-xorg

9. After finishing xserver setup there should be a new created xorg.conf. You can see that by typing the following command:

ls -l /etc/X11

4. Now you can start your graphical login screen by typing:

sudo gdm

5. Your graphical login screen should appear again and you should login like always.

---

### Post by felix.rommel on 2007-07-05
> **Soarer said:**
> In the terminal you boot to type:
```
gksudo gedit /etc/X11/xorg.conf
```

HTH

I don't think that it works, because as far as I understood alexsabree does NOT have a graphical environment. That's why he cannot use gedit.

---

### Post by felix.rommel on 2007-07-05
@alexsabree:

If you just want to edit your xorg.conf instead of reconfiguring it, follow steps 1-7. Then do the following:

8. Open a text editor and edit xorg.conf. You can save xorg.conf when quitting nano with <Ctrl><x>. You just have to type "y" when nano asks you if you want to save the changes.

sudo nano /etc/X11/xorg.conf

9. After editing your xorg.conf file -  start your graphical login screen:

sudo gdm

---

### Post by Soarer on 2007-07-05
> **felix.rommel said:**
> I don't think that it works, because as far as I understood alexsabree does NOT have a graphical environment. That's why he cannot use gedit.

You're right. Thanks for correcting this. Maybe I need more (or less) coffee before posting :)

---

### Post by alexsabree on 2007-07-05
I really appreciate all of the help that you guys have gave me. I will try to use the steps you have provided me with and ill let you know how it goes 	[-o<

Edit) My Graphics Card? = 6800gs 256mb agp 8x

---

### Post by alexsabree on 2007-07-05
Well i fixed my xorg file and it starts up and everything, but now my precious compiz-fusion is messing up. I cant change themes.. idk i have no idea.

---

