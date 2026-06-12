---
title: "Delay startup of Rainlendar"
date: 2008-03-29
forum: General Help
---

### Post by kei-clone on 2008-03-29
I wish to delay the startup of a calendar program called Rainlendar, which starts when the computer loads. I want to get it to start only after the gnome desktop fully loads, otherwise it looks like this:

[http://i25.tinypic.com/j9rkn7.jpg](http://i25.tinypic.com/j9rkn7.jpg)

any help on this?

---

### Post by dcstar on 2008-03-29
> **kei-clone said:**
> I wish to delay the startup of a calendar program called Rainlendar, which starts when the computer loads. I want to get it to start only after the gnome desktop fully loads, otherwise it looks like this:

[http://i25.tinypic.com/j9rkn7.jpg](http://i25.tinypic.com/j9rkn7.jpg)

any help on this?

How do you start it now?

---

### Post by kei-clone on 2008-03-30
right now i put it in system>preferences>sessions>startup programs.

---

### Post by mkoyle on 2008-05-02
It's a cinch; sorry if the following makes it look complicated:

If you want this for just your user, open a terminal (Applications-->Accessories-->Terminal) and start gedit with the following command:

```
gedit ~/.config/.rainlendar2/start.sh
```

Paste the following into the file that opens (this will delay 10 seconds; I just tested 20 on my computer and I felt like I was waiting years because on my new computer my desktop pops up in about 1 second after logon... I hadn't realized it was so quick three or four seconds would probably be enough for me; anyway, change 10 to a bigger or smaller number if you want):

```
#!/bin/sh
sleep 10
rainlendar2
```

Save and exit.

Go back to the terminal window and type in the following to make the 'start' script we just created executable:

```
chmod 700 ~/.config/.rainlendar2/start.sh
```

Finally, change the 'rainlendar2' command in system>preferences>sessions>startup programs to /home/[YOUR_USERNAME]/.config/.rainlendar2/start.sh  Insert your username in there, in all lowercase.

Does that fix the problem?  If you need it, I can post how to do it for all users (you would just put the script in a global location, change its owner to root and change it to '775' with chmod).

--Matthew

---

### Post by kei-clone on 2008-05-03
I moved to kde recently and am no longer experiencing this problem. howerver, that's a nice trick to know :) thanks

---

