---
title: "mythgame + xmame = no lirc"
date: 2006-11-07
forum: General Help
---

### Post by amoore on 2006-11-07
It looks like xmame 1.06 in the repos has not been made without lirc suport.

This is a problem for mythtv users as we use a remote with lirc for all of our keyboard functions.

I get both of my joysticks to work in mythgame with xmame with:

   ```
xmame -vidmod 1 -fullscreen -skip_gameinfo -jt 1 -jdev /dev/input/js0 -gm
```

And I can control mythtv's menus with the joystick using the "joystickrc.example" found in the mythtv-docs.

The problem comes when I want to exit xmame when playing a game. Because xmame has been made with no lirc support I have to use the keyboard to use the "Esc" key to exit xmame.

Anyone know of a xmame package with lirc support or good instructions for compiling xmame and its extra packages?

---

### Post by amoore on 2006-11-08
> **amoore said:**
> It looks like xmame 1.06 in the repos has not been made without lirc suport.

This is a problem for mythtv users as we use a remote with lirc for all of our keyboard functions.

I get both of my joysticks to work in mythgame with xmame with:

   ```
xmame -vidmod 1 -fullscreen -skip_gameinfo -jt 1 -jdev /dev/input/js0 -gm
```

And I can control mythtv's menus with the joystick using the "joystickrc.example" found in the mythtv-docs.

The problem comes when I want to exit xmame when playing a game. Because xmame has been made with no lirc support I have to use the keyboard to use the "Esc" key to exit xmame.

Anyone know of a xmame package with lirc support or good instructions for compiling xmame and its extra packages?

I found out that xmame 1.06 is compiled with lirc suport:) 

here is how to activate it!!!!!

```
gedit /home/your_user_name/.lirc
```

**NOTE!!!! **(I'm using a Hauppauge 150 silver remote so, your buttons might not be the same!!!) You can use irw in the terminal to map what buttons you use on your remote. Just change "button = to what your button is" in the file below.

copy, and paste this into the file


   ```
 prog = xmame
    button = Back/Exit
    config = 1
```

save the file


Now the "Back/Exit" will quit Xmame when using mythtv.

---

