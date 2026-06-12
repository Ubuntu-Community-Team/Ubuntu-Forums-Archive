---
title: "How to Get A Pic to Show at Login"
date: 2014-01-13
forum: General Help
---

### Post by Rick St. George on 2014-01-13
Anyone know how to get the Background Picture to show up at the Login Prompt, instead of the default pic?
Also ... Any difference between Xubuntu or Kubuntu regarding this? Using v13.10

Thanks
Rick

---

### Post by deadflowr on 2014-01-13
Where is the picture you are using?
If it's in the users Pictures folder directly, and not in a subfolder or another folder, it should show.
Any of the default wallpapaers listed in the wallpapers section of Appearance should also show.

If your pictures in not in the users Pictures folder, then it will not show.

---

### Post by Rick St. George on 2014-01-13
My apologies, I meant the BG pic of my choice. A BG pic shows, but its the default. My desktop pic is the one I want to show during bootup and logon.

---

### Post by deadflowr on 2014-01-13
> **Rick St. George said:**
> My apologies, I meant the BG pic of my choice. A BG pic shows, but its the default. My desktop pic is the one I want to show during bootup and logon.

That's what I mean.
The picture has to been directly in the Pictures folder and not in any other folder, including a Pictures sub-folder.
But that would be only from the login screen and the desktop. Setting it for the boot screen, I don't know.

---

### Post by Rick St. George on 2014-01-14
This is what I did, Open Terminal
type command: sudo thunar
copied pic to /usr/share/xfce4/backdrops
Now it shows up in Desktop Selections.
To also make it show up on Boot-up
type command: sudo gedit /etc/default/grub
Add the following line after GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/usr/share/xfce4/backdrops/bgpicname.jpeg"
Whatever the name of your pic is.
save changes and while in the terminal type  sudo update-grub

WORKED & SOLVED

Thanks!
Rick

---

