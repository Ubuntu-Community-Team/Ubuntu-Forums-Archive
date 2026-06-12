---
title: "Popup window in apps stick to the apps (18.04)"
date: 2018-08-30
forum: General Help
---

### Post by Robbyx on 2018-08-30
I open a drop down menu. A window opens. When I move the window the underlying app also moves. I do not like this.

I want the app to be independent of the popup screen, so that I can move the popup to a different monitor without the underlying app coming with.. This happens across most if not all apps.

Is there a way to disengage the two windows? Is it a theme problem?

---

### Post by #&amp;thj^% on 2018-08-30
Open Terminal and run:
```

gsettings set org.gnome.shell.overrides attach-modal-dialogs false
```

This should detach modal dialogues from the parent window and with luck should fix your problem.

---

### Post by PaulW2U on 2018-08-30
Or if you prefer a GUI solution, in Tweaks go to Windows | Attach Modal Dialogues and move the slider to "OFF".

---

### Post by Robbyx on 2018-08-30
I am very happy with the outcome. Thank you both.

The terminal entry did not work in LibreOffice Calc using the sort option as a test.
The GUI solution via Tweaks did work. 

This has been a long standing problem and I am  pleased there is a solution.

---

### Post by #&amp;thj^% on 2018-08-30
I find it strange the terminal command did not work, the GUI (Tweak) and command in terminal both do the same thing.
But I'm glad it's now to your liking. :)

---

