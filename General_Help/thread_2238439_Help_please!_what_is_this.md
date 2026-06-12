---
title: "Help please! what is this?"
date: 2014-08-07
forum: General Help
---

### Post by johnmaccuish1963 on 2014-08-07
You will notice a small window in lower right corner of my desktop, this pops up whenever I press a key, doesn't happen if I have a web browser open,  I just noticed it tonight when I was playing Enemy Territory I pressed tilde to open console in game and then couldn't do anything, every time I pressed to enter text or try and close console this would pop up and I have no idea what it is for or where it came from (maybe Grandkids changed something today).

Please tell me how to make it stop.

[ATTACH=CONFIG]255312[/ATTACH]

---

### Post by johnmaccuish1963 on 2014-08-07
Not the weather bug Icon, the box under it :(

---

### Post by coldcritter64 on 2014-08-07
That box will appear whenever you type on the keyboard but DON'T have a application selected (focused). The system sends your input here to point out you need to focus an application for the text you are entering. It is a normal function of the GUI.

All you need to do is put the desktop focus on an application, like firefox as you've noted, or a text editor for example. Regard it as the GUI telling you it has nowhere to send what you are typing and that you need to click on an application before typing any input.

---

### Post by QIII on 2014-08-07
@Johnmaccuish1963:

Please do not post large images.  Be mindful of those who have slow connections or data limitations on their internet service.

Use the attachment functionality by clicking the paperclip icon above the text entry box.

Thanks.

---

### Post by CantankRus on 2014-08-08
Your desktop is a directory and is managed by nautilus.
So when you type while the desktop is focused, your searching your Desktop directory.

Open your file browser and start typing.
You will see the same box in the bottom right of the window.

---

### Post by johnmaccuish1963 on 2014-08-08
So it is something that has always been there that I just never noticed and the game I was playing lost focus somehow.
After reading this I tried the game again and was able to play and open console to type, not sure why game was losing focus but happened three times in a row thus the panic.
Thank you.

---

### Post by johnmaccuish1963 on 2014-08-08
> **QIII said:**
> @Johnmaccuish1963:

Please do not post large images.  Be mindful of those who have slow connections or data limitations on their internet service.

Use the attachment functionality by clicking the paperclip icon above the text entry box.

Thanks.
Sorry I didn't know how to make them smaller at the time.
Thank you.

---

### Post by CantankRus on 2014-08-08
> **johnmaccuish1963 said:**
> So it is something that has always been there that I just never noticed and the game I was playing lost focus somehow.
After reading this I tried the game again and was able to play and open console to type, not sure why game was losing focus but happened three times in a row thus the panic.
Thank you.
If it becomes an annoyance you can disable nautilus handling the desktop with this terminal command.
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```You will have no desktop icons and wont be able to right click on the desktop.


To reset to default use
```
gsettings **reset** org.gnome.desktop.background show-desktop-icons
```

---

