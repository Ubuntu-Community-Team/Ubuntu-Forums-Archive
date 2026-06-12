---
title: "Copy from File - Paste to Terminal"
date: 2007-01-13
forum: General Help
---

### Post by Tookelso on 2007-01-13
Hello,

I've recently restored my X server by using the terminal (Ctrl-Alt-F1).   While fixing my computer, I noticed that it would be cool if I could keep a TXT file which contains the lengthy commands, and then copy / paste them into my terminal using vi or some text editor. 

However, I can't get vi to paste the text into the terminal.  I've tried copying text from vi, then using Ctrl-Z to drop from vi to the terminal, but I can't paste the text into the terminal. 

Does anyone know how to copy text from vi / emacs, then paste it into the terminal (only in terminal mode?  No GNOME, etc?)

Thanks,
--Took

---

### Post by konst88 on 2007-01-13
You may use the command cat, like this:
```
cat filename
```
And it prints the file to the screen. Then you cant just select with the mouse the command, and click the middle mouse button to paste.
If it is a long file, you may use the commands: more, less, instead of cat.

Edit: don't know if it works without X running.. it works on gnome-terminal well.

---

### Post by Zimmer on 2007-01-13
Click in the terminal window, right click and select paste from the pop up menu

Just noticed you may be at the bare console, not just a 'Terminal' session...
I will investigate further :)

---

### Post by bapoumba on 2007-01-13
Interesting question.
So I have been playing around with nano (I do not know much vi).

You can open several virtual terminals and switch between them with ALT-left or right arrows.
Copying stuff from nano to its buffer cannot be pasted in another instance of nano in another virtual terminal (guess it's normal as it is another session), or in the command line to be used.

That's also where I am. Any virtual terminal wiz around ?

---

### Post by speedman on 2007-01-13
apt-cache show gpm

apt-get install gpm

SM

---

### Post by bodhi.zazen on 2007-01-13
Her is a more detailed how-to on gpm:

[http://www.cyberciti.biz/tips/howto-linux-configure-the-mouse-at-a-text-based-terminal-for-copy-and-paste-operation.html](http://www.cyberciti.biz/tips/howto-linux-configure-the-mouse-at-a-text-based-terminal-for-copy-and-paste-operation.html)

---

