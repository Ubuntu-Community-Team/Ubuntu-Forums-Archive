---
title: "System settings suddenly locked to defaults"
date: 2016-01-26
forum: General Help
---

### Post by bast2 on 2016-01-26
Hello,

I installed ubuntu 14.04 LTS on a DELL Inspiron for a friend (he's a new linux user).
Problem is that after a hard shutdown with no battery, on the next start, ubuntu found errors on /home and  offered to "press F" to fix them. 
When logging in again after this, ubuntu appeared with default settings and they don't change anymore (either from unity tweak or system preferences).

I found someone with the exact same issue here : [http://askubuntu.com/questions/566539/system-settings-suddenly-locked-to-defaults](http://askubuntu.com/questions/566539/system-settings-suddenly-locked-to-defaults)
When i tryed to create a new user account, it worked normally & the settings can be changed. But after i decided to copy/paste the /home/user1 to /home/user2 with hidden files, the second account refused to get to the desktop & kept asking for the password again & again.

How can i put the computer back to his preferences? Must he abandon his old account ? Isn't there anyway to fix this ? Could it happen again??

Thanks a lot for anyhelp (i'm trying to convert a whole group to linux & i hope there's a fix...)

---

### Post by mc4man on 2016-01-26
Try - 
boot up normally, at the login (greeter) screen don't login, instead  go,
ctrl+alt+F3
In the tty login into the affected user using their user name & password
Then run this command, replace "[COLOR="#FF0000"]username[/COLOR]" with their actual user name
```
mv /home/[COLOR="#FF0000"]username[/COLOR]/.config/dconf/user /home/[COLOR="#FF0000"]username[/COLOR]/.config/dconf/user.bak
```

The command should run without comment in tty, if you get a permission denied then either get back here with that or just re-run above command prefixed with sudo, ie.
sudo mv /home/[COLOR="#FF0000"]username[/COLOR]/.config/dconf/user /home/[COLOR="#FF0000"]username[/COLOR]/.config/dconf/user.bak

Then go in tty 
sudo reboot & see...

---

### Post by bast2 on 2016-01-28
Hello, thanks for your reply.
I tryed the command, the first time without sudo. I had no comment in tty as you said. I reboot & then no change. Still default appareance & still no way to change any setting on the main account.

---

