---
title: "Ubuntu, can't login?!?!"
date: 2008-06-08
forum: General Help
---

### Post by tozymba on 2008-06-08
hi, im using vista now and im trying to dual boot with ubuntu. i installed ubuntu but i can't login!...
i created an account on the installing but it doesn't work. when i put username and pass in, it looks like its working and it plays music too but it goes back to login screen. i've also tried live cd. but after it plays login music it takes me to login screen.

anyone please help me! :( :confused::confused:

---

### Post by pro003 on 2008-06-08
this is weirdest thing I ever heard about ubuntu login 

try to login in some failsafe mode, perhaps gnome failsafe...

if not then failsafe terminal and add a new user and new password...then try to ligin with this new user and password

---

### Post by pro003 on 2008-06-08
maybe I should explain it little bit better since u are new in this I suppose...

when the log on screen appears, go to the bottom left side change session and then select FAILSAFE GNOME > enter the password 

if you're lucky and you see your ubuntu desktop, go to System > Administration > Users and groups

then you must authenticate yourself with some of the drop down menu, if that happens to be you unlucky user name then select it and enter the password > the you should ADD USER with some privilegies and chose main group root and then save it all and then REBOOT... 

>>>TRY TO LOG IN WITH YOUR NEW USER NAME ....

Good luck!

---

### Post by tozymba on 2008-06-08
> **pro003 said:**
> maybe I should explain it little bit better since u are new in this I suppose...

when the log on screen appears, go to the bottom left side change session and then select FAILSAFE GNOME > enter the password 

if you're lucky and you see your ubuntu desktop, go to System > Administration > Users and groups

then you must authenticate yourself with some of the drop down menu, if that happens to be you unlucky user name then select it and enter the password > the you should ADD USER with some privilegies and chose main group root and then save it all and then REBOOT... 

>>>TRY TO LOG IN WITH YOUR NEW USER NAME ....

Good luck!


Thx for reply, i got to the part loggin in the failsafe gnome session and i got in. but i don't get the next part, what do you mean by "must authenticate yourself with some of the drop down menu, if that happens to be you unlucky user name then select it and enter the password"?? :)

---

### Post by pro003 on 2008-06-08
just forget that part, ok... i was kinda very into details and for the unlucky username i meant your first username which you could not login...

just create the new user and give it some privileges and group and pass and then you login with this new user which will have its own home and everything you need you can manage.. what is important it's that you can get in i.e log in and do your stuff... and if you forgot some of your files in your very first 'home" folder, then run "gksu nautilus" from terminal and get in that folder and take out whatever you pleased...

let me know if something else is unclear :popcorn:

---

