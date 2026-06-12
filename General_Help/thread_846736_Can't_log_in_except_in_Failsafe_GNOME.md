---
title: "Can't log in except in Failsafe GNOME"
date: 2008-07-01
forum: General Help
---

### Post by mosesu on 2008-07-01
After installing 8.04 successfully, I can't log in. Only when I switch to Failsafe am I allowed to use system. I have no experience with Linux.

---

### Post by coolaj86 on 2008-07-02
You're systems kernel refracter is broken and the piped synoquation isn't going to work if the links aren't socketed that way. You'll just have to switch back to Windows I guess.

Just kidding!

Go to Applications > Accessories > Terminal
and move all of your old settings to a new folder called OLD_SETTINGS by coping and pasting the lines below.
```
cd
mkdir OLD_SETTINGS
mv .gnome* OLD_SETTINGS/
mv .gconf* OLD_SETTINGS/
mv .metacity OLD_SETTINGS/
```

I'd be very surprised if that doesn't fix your problem.

But if it doesn't:
System > Administration > Users and Groups > Unlock > Add User
create a new user and log in as that user to test things out.

Let us know what happens and we'll give you further instruction.

P.S. If you're interested in becoming familiar with Linux, this is a good place to start:
[http://www.linuxcommand.org/lts0020.php](http://www.linuxcommand.org/lts0020.php)

---

