---
title: "Command to switch current window."
date: 2014-06-13
forum: General Help
---

### Post by aronwalker on 2014-06-13
Hi Peoples

Is they a command to change what window is in focus? For example if I have firefox open, and I want to switch to Nautilus, I can type in a command in the terminal to switch to it. However, if the Program isn't open, the command will open the last focused instance of it. The Idea eventually is to have Super+number Style control like in windows 7+. I am using Gnome 3.

Thanks in advance

Aaron

---

### Post by dragonfly41 on 2014-06-13
I use in Ubuntu 12.04 ...

(1) Alt+Tab to switch between windows

(2) windows-list and docky installed from Ubuntu Software Centre

---

### Post by Impavidus on 2014-06-13
I keep most of my windows on separate workspaces (I have 15 of them) and switch with ctrl+alt+arrow. That's xfce by the way.

---

### Post by aronwalker on 2014-06-13
Thanks for the keyboard short cuts, but I don't need any of these. If I concentrate of Firefox, I want it so that if it is open, Firefox will come into focus, and if it is not open. I am starting to think that this will need a script for each application. This will do the following:

Check if the application is open:
         If it is open, then check if it is in focus.
               If it is focus, then hide it remove it from the window.
               If it is not in focus, Then Bring it to the top of all windows and bring it into focus
        If it is not open, Then open it

I will do this for each application, and then make some keyboard shortcuts using the gnome-shell keyboard shortcut thing, see [Here]("http://blog.sudobits.com/wp-content/uploads/2011/10/gnome-shell-keyboard-shortcuts.jpg")

I hope this makes it a bit more clear...

Aaron

---

