---
title: "Problem with a basic emacs command"
date: 2013-03-13
forum: General Help
---

### Post by Smajjk on 2013-03-13
I am running xubuntu 12.10 with emacs 24 and z-shell and I want to be able to increase and decrease the font size in emacs.

I should be able to use C-x C-+ and C-x C-- or equivalently M-x text-scale-increase and M-x text-scale-decrease 
([http://www.gnu.org/software/emacs/manual/html_node/emacs/Text-Scale.html](http://www.gnu.org/software/emacs/manual/html_node/emacs/Text-Scale.html)) but nothing happens when I run these commands. 

Anyone who has a clue what I am doing wrong here? :o

---

### Post by SeijiSensei on 2013-03-13
Can you not simply enlarge the font in the terminal application itself?  I use the Konsole app in Kubuntu and can change the font size either through the menus or by holding down Ctrl and using the mouse scroll button.  Ctrl+/Ctrl- usually works as well.

---

### Post by lykwydchykyn on 2013-03-13
AFAICT those commands only work on the GTK client, not in the console client.  The documentation doesn't mention it, but it makes some sense since resizing text in a console is more of a tty or terminal-emulator function, whereas X11 apps can do whatever they want with fonts.

---

### Post by Smajjk on 2013-03-13
I have tried enlarging the font in the actual terminal, in other applications I can use C-+ and C-- and scrolling aswell but not here.

OK, so it is only in the GUI version of emacs I can use those commands! I rather use the -nw version. Do you know how I zoom in and out in the console one?

---

### Post by lykwydchykyn on 2013-03-14
More than likely Emacs is trapping C-+ and C--, and the terminal isn't able to respond.  You could try reassigning the hotkeys in the terminal to something else, like maybe using the super (Windows) key.  Or try a different terminal emulator.

---

### Post by Smajjk on 2013-03-14
OK, thank you, sounds very reasonable. There's no way you know how to reassign these keys? :)

---

### Post by lykwydchykyn on 2013-03-14
Not offhand; I use Konsole generally, I assume you're using whatever's default in XFCE (xfce4-terminal?).  Check your settings dialogs, there's probably a simple way to do it.

---

