---
title: "can't login after switch user"
date: 2007-04-23
forum: General Help
---

### Post by coffee-n-cream on 2007-04-23
ok guys i have this problem from edgy till feisty.after i switch user it goes to the login screen.i turnoff my monitor n came back say abt 10mins later.i switch on the LCD,all i got is the mouse pointer n the screen is black.i cant see the login screen.press keyboard,move the mouse,nothin comes alive.only the mouse pointer is there n workin as normal.so i have to do a reboot to login again.anyone else have this prob n anyone knows how to solve it?? thx

---

### Post by zvacet on 2007-04-23
Sorry,bit I don´t quite understand you.If you swich user it is normal to get login screen,because you want to login as some other user.Is the problem that you can not login(user name and password not accepted) or is it something else?

---

### Post by dannyboy79 on 2007-04-23
i have seen where right after you login, it just takes you right back to the login screen. this is due to the users home directory being full. the xserver has nowhere to write a file it needs so it crashes. check to see if you're short on space. otherwise maybe I am not really understanding your problem like the previous poster. Are you saying that you;re just using the su command in the terminal and it takes you to the login screen?

---

### Post by coffee-n-cream on 2007-04-23
alritey let me rephrase.by using swtich user i mean the default red swtich on/off looking button on the top right corner of the desktop.pressed dat n got whole other options (log off,lock screen,shut down n blah blah blah) n i choose switch user n it goes to login screen.i leave my pc alone for abt 10 mins and then come back again,i cant go to the login screen as there is a blank black screen n only the mouse pointer is visible.my screensaver is disabled coz i usually turn off my monitor whenever im away from the pc.

---

### Post by dannyboy79 on 2007-04-23
just sounds like a crash or freeze. check your error logs. look within /var/log/

and also check out 

the .Xsession-errors located within the users home directory just prior to clicking on the switch user button.
I think it's called .Xsession-errors anyway, it's called something errors and its hidden and it's inside the users home dir.

---

