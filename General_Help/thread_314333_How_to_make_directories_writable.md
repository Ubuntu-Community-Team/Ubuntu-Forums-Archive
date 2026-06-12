---
title: "How to make directories writable?"
date: 2006-12-07
forum: General Help
---

### Post by Dr Small on 2006-12-07
Ok. Here's the whole gist, so you'll understand.
I downloaded and installed XAMPP into the folder:
```
/opt/lampp/
```

Now, i downloaded Joomla (a CMS portal) and put it in:
```
/opt/lampp/htdocs/joomla/
```

I logged in as root by:
```
gksudo nautilus
```
and changed the permissions on all the folders, down to joomla to Read ALL,
Write ALL and Execute ALL.

Now, I go to the joomla installation file (in my browser)
```
http://localhost/joomla/installation/
```

and it tells me I need to make the folder writable:
> Directory and File Permissions:
In order for Joomla to function correctly it needs to be able to access or write to certain files or directories. If you see "Unwriteable" you need to change the permissions on the file or directory to allow Joomla to write to it.

And all the things are "Unwriteable"

Am I doing something wrong, far as setting the permissions?
Do I need to type something in the terminal, to set the permissions?

Any help would be greatly appreciated.


Dr Small

---

### Post by taurus on 2006-12-07
Applications -> Accessories -> Terminal
```
sudo chmod -R 777 /opt/lampp/
```

---

### Post by Dr Small on 2006-12-07
Thanks. Worked perfectly! :)
* Will save command for later :)


Dr Small

---

### Post by taurus on 2006-12-07
You're welcome.  And if you forgot, just ask for it again.

---

### Post by Hendrixski on 2006-12-07
As a holdover from my UNIX days, I use command line stuff like chmod.  But when I show Ubuntu to new users, they don't want to have to memorize all that (it's their loss, but whatever it takes to spread the gospel of open source).

Is there a way to change the permissions on a folder or a file from the GUI?  like right click or run a program that would run the chmod command under the hood?

---

### Post by taurus on 2006-12-07
> **Hendrixski said:**
> As a holdover from my UNIX days, I use command line stuff like chmod.  But when I show Ubuntu to new users, they don't want to have to memorize all that (it's their loss, but whatever it takes to spread the gospel of open source).

Is there a way to change the permissions on a folder or a file from the GUI?  like right click or run a program that would run the chmod command under the hood?
Yes, you can do that by running "gksudo nautilus" from a terminal.

---

### Post by Hendrixski on 2006-12-07
Right, but that opens the entire file browser as root.  That may be dangerous for new users.  I dunno if I'd encourage that one.  It seems like it would be safer to have the option to right click on a particular file or folder and have a menu come up of permissions you would temporarily set it to, and then it would reset them after you're done doing the one operation you need the permissions to be changed for.

If nothing like that exists I may code that up this weekend and submit it.  That would be a GNOME project submission right, not an Ubuntu submission?

---

### Post by garyedwardjohnston on 2008-04-25
Thanks!!!

---

