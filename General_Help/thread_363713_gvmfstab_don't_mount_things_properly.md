---
title: "gvm/fstab don't mount things properly"
date: 2007-02-17
forum: General Help
---

### Post by moore.bryan on 2007-02-17
[I]hopefully somebody can set me in the right direction... 
about a week ago i followed the directions at [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication), as suggested in [http://ubuntuforums.org/showthread.php?t=354489&highlight=auto+login](http://ubuntuforums.org/showthread.php?t=354489&highlight=auto+login) for a way to autologin.  

everything worked fine until i tried to access my external usb hd... couldn't find it.  i use openbox with a startup script to load gnome-volume-manager to handle all of that stuff and i just figured it hadn't mounted (for whatever reason), so i sudo mounted and it looked fine, but i couldn't write to it.  i edited /etc/fstab to fix it and everything was fine... for a while; that is, until i tried to access my usb flashdrive and that wasn't mounted.  now when i mount it, even though i have everything setup correctly in /etc/fstab, it is only "writable" when i'm sudo.  i'll attach my /etc/fstab and openbox startup script in case they can lend a hand.

anybody, please... and thanks, in advance.

=============================================================
EDIT:

nevermind... just dumped gvm for ivman... much better.  not sure why it works, though....
[/I]

---

