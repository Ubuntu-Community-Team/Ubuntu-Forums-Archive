---
title: "help copying a folder to /usr/share/themes"
date: 2006-11-29
forum: General Help
---

### Post by arthursc on 2006-11-29
I want to be able to copy a folder from my tmp are to the /usr/share/themes folder. In file browser it say I have no rights. So in a terminal what is the command to do this?

thanks](*,) 

newbie

---

### Post by munkyeetr on 2006-11-29
sudo cp -r /tmp/<foldername> /usr/share/themes/

then enter your password.

---

### Post by arthursc on 2006-11-29
Hi munkyeetr,

copied thanks but the theme will not install. It is a gdm theme. any ideas.

---

### Post by munkyeetr on 2006-11-29
arthursc,

Sorry it's taken so long to get back to you. I was at work on a Windows system, so needed to get back home to see what I'm trying to explain...

First of all, for gdm themes you want to put them in /usr/share/gdm/themes/

There are 2 ways to do this:

#-- METHOD 1
If you have the theme in an archived file (.tar .gz etc...) the easiest way is to open the theme manager...:
```
gksu gdmsetup
```

or, using the GUI menu
    System -> Administration ->Login Window

...and drag the archived file into the window (into the list of already available themes). Now the theme will automatically be extracted to the proper folder and added to the list. Choose the theme, and press "Close".

OR...

# -- METHOD 2
Copy the folder containing the theme (or extract the archive) to /usr/share/gdm/themes/ ,then open theme manager...:
```
gksu gdmsetup
```

or, using the GUI menu
    System -> Administration ->Login Window

...and choose the theme from the list and press "Close"

# ----------------------

The theme should be applied next time you try to login.

Hope this is clear and helpful.

---

