---
title: "Nautilus doesn't work after Login"
date: 2006-11-27
forum: General Help
---

### Post by bellemerlord on 2006-11-27
I have a Prob with my edgy-installation. After  logging in to gnome, no wallpaper is shown, there are no links to the mounted devices on the desktop, the right-click on the Desktop doesnt work and i cant use nautilus, it doesnt show up if i choose try to start f. e. the home-folder. 

i had this problem several times before, but dont ask me how i solved it. The last time, i used a tip from another forum and created a new user, logged in the new account, logged out and it worked. But this time i had no succuess with this tip. 

oh, one thing more, if i start top direct after the login, there is a nautilus running, but it doesnt work. i tried to kill the nautilus-process, but it became a zombie. 

if i try to open a place, a new instance of nautilus is started, but it doesnt react. 

i also tried to start gnome with the fail-settings, than a error message appears telling me that the dbus adress couldnt be localized, i should run man dbus-launch or man dbus deamon. I did it, but i didnt find any help for my problem. 

thanks for any help.

---

### Post by mssever on 2006-11-27
I recently had a similar problem with a user account I created using the adduser command. In my case, I got tons of error dialogs about dbus and such. I'm running Dapper on that machine, by the way. I ended up deleting the account and creating a new one using System > Administration > Users and Groups. For some reason, that command didn't create a home directory for the new user, so I manually created it and chown'ed to the new user and group. Then I did ```
sudo -i
su newuser
cd
cp -a /etc/skel/* .
exit
exit
```After that, I was able to log in normally.

---

### Post by zzzaccount on 2006-12-29
I have a similar problem with ubuntu 6.06 on an imac dv.
The same installation cd works perfect on a g3 white & blue but some how in the imac I get the fallowing messages:
The panel encountered a problem while loading...
OAFIID:GNOME
(several notification windows)
& Nautilus can't be used now, due to an unexpected error.

There's no acces to right click on the desk, no icons on the task bar & I cannot find the applications if I reduce them.
No acces to the file navigator either.
Everything else works fine if I go through the terminal to visualize documents with cat or edit with vi.

Same problem encountered with edubuntu & kubuntu.
I have looked extensively over the web & cannot seem to find anyone with the same problem???

I tried making a new account but it didn't work.
Thanks to anyone kind enough to give a helping hand.
david

---

### Post by mssever on 2006-12-30
> **zzzaccount said:**
> I have a similar problem with ubuntu 6.06 on an imac dv.
The same installation cd works perfect on a g3 white & blue but some how in the imac I get the fallowing messages:
The panel encountered a problem while loading...
OAFIID:GNOME
(several notification windows)
& Nautilus can't be used now, due to an unexpected error.

There's no acces to right click on the desk, no icons on the task bar & I cannot find the applications if I reduce them.
No acces to the file navigator either.
Everything else works fine if I go through the terminal to visualize documents with cat or edit with vi.

Same problem encountered with edubuntu & kubuntu.
I have looked extensively over the web & cannot seem to find anyone with the same problem???

I tried making a new account but it didn't work.
Thanks to anyone kind enough to give a helping hand.
david
What happens when you try to start Nautilus via the terminal? please post the output of this command:```
nautilus; echo "Exit status: $?"
```

---

### Post by lryer on 2007-01-15
I'm having the same problem described above -- no nautilus, no desktop icon, no wallpaper. The wallpaper comes back when I run "desktop background" from the system menu. Before the problem I had killed nautilus using "force quit" when a large delete operation seemed to lock.

I ran the above command, but got NO response whatsoever. When I ctrl-c out I got: 
Exit status: 130

Any suggestions?

---

### Post by lryer on 2007-01-15
On the other hand:
Creating a new user, loging out, then in as the new user, then reboot and login to original account.
worked fine.

Thanks, everyone!

---

