---
title: "open konsole and run a command"
date: 2022-06-02
forum: General Help
---

### Post by demonenero84 on 2022-06-02
Hi there :)
I made a very simple script to search (using grep) the content inside a text file, normally I open konsole, run the script (then the script runs the read command to get the term to search) and get the result.
 So how can I run konsole telling it to run the script automatically ?
thanks a lot in advance

---

### Post by Holger_Gehrke on 2022-06-02
Make a [desktop file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") for your script and put a line "Terminal=true" in it and put the file in '~/.local/share/applications'. This will add an item for your script to the menu.

And while you're at it, you could also change the script to use zenity - or more likely [kdialog]("https://man.cx/kdialog") since you're using KDE - to give your script a GUI (a graphical text-entry for the search term, a graphical text viewer for the result(s)).

Holger

---

### Post by demonenero84 on 2022-06-02
I will take a look at zenity.
So I would need a pop up box to "read" my search term and another to give the output of "grep"
I will take a look here [https://help.gnome.org/users/zenity/stable/](https://help.gnome.org/users/zenity/stable/)
thanks a lot

---

### Post by Holger_Gehrke on 2022-06-02
I specifically mentioned kdialog because zenity is a Gnome program and will look a bit strange on a KUbuntu desktop. The two programs are similar in capabilities but the options are slightly different ...

Holger

---

### Post by SeijiSensei on 2022-06-02
KDE includes a full-text search engine.  See System Settings > Search.

---

### Post by demonenero84 on 2022-06-02
Thanks a lot guys :)
with zenity I got what I wanted ( actually something better than what I wanted )

---

