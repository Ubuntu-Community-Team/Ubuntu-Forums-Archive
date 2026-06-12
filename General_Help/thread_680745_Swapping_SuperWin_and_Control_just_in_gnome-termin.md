---
title: "Swapping Super/Win and Control just in gnome-terminal"
date: 2008-01-28
forum: General Help
---

### Post by Milde on 2008-01-28
```
remove mod4 = Super_L
remove Control = Control_L
keysym Control_L = Super_L
keysym Control_L = Super_R
keysym Super_L = Control_L
keysym Super_R = Control_R
add mod4 = Super_L Super_R
add Control = Control_L Control_R
```

I've got this in my ~/.xmodmaprc to swap the Super and Control keys in all X applications, but it has one unintended side effect: it swaps the keys in gnome-terminal too.

Is it possible to swap them back to normal for just one application? Or configure my shell to interpret the two modifiers in reverse? I'd really like to keep this behavior for graphical applications, while still being able to use CTRL+C for ^C in my terminal, and so on.

I was thinking it might involve ~/.inputrc, but I'm not sure how to set just modifiers in that.

---

### Post by espressopigeon on 2008-01-28
Make a bash script that sets the keymaps how you want them in gnome-terminal. Back up ~/.bashrc with this:
```
cp ~/.bashrc ~/.bashrc~
```
then edit .bashrc to run the script by putting this line it:
```
*/the/path/to/the/script*
```
This will set the keys in gnome-terminal to your preferences whenever you open it
But you'll need to make another script to set them back, and it'll have to be run manually, before you leave gnome-terminal.
If you don't want to state the full path every time you run the script, add this to ~/.bash_profile:
```
export PATH=$PATH:*/the/directory/of/the/script*
```
then you can simply type *script_name* and it will run.

---

### Post by Milde on 2008-01-28
I'm not sure what commands I'd put in there though. I can't just run xmodmap, because then my bindings would be broken outside of gnome-terminal. Looking through the readline documentation, I don't see any way to specifier the modifier keys used.

Oh, and I'm not using bash, I'm using fish.

The only other thing I can think of is modifying gnome-terminal's key bindings itself, but it doesn't seem to have an option for specifying modifier keys, and I'm not sure that adding it to the keybindings file manually would have any effect.

I was also thinking using ~/.Xresources might work, but I'm not sure where to start with that either.

---

