---
title: "Cannot login through UI, Menubar not Showing Up"
date: 2014-06-24
forum: General Help
---

### Post by Chris_Dickerman on 2014-06-24
I attempted to update an Nvidia driver and found out that I already had the current version. Installation required that I sudo stop lightdm. (I think this is causing the problem) I quit the installation process and rebooted the computer. Upon rebooting, I was prompted to enter a password to login, which has never happened before as I had specified it to automatically login for me. When I type in my password in the GUI, it accepts it but doesn't go to my desktop, but goes straight back to the login screen.

I am able to log into my account by "ctrl-alt-f1-ing", but the only way I'm able to get a GUI in my account is to attempt to startx then hit ctrl-c. Then there aren't any menu bars. If I attempt to startx and I wait long enough, it reads out:

"xauth: timeout in locking authority file /home/[myusrname]/.Xauthority"
I open .Xauthority with nano and it is blank.

I'm clueless.

---

