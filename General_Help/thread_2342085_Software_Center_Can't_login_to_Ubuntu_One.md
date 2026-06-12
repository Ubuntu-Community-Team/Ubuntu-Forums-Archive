---
title: "Software Center: Can't login to Ubuntu One"
date: 2016-11-03
forum: General Help
---

### Post by runlevel0 on 2016-11-03
I am having an intriguing problem: 

When I open the Ubuntu Software Center and select a program with the nonfree tag I get an authentication error when I try to log in. The error is "Wrong email or password". As a rather obvious matter of fact these are the very same email and password that I have used to log in to this forum, duh.

Just to be sure I have even written the password using an editor and cut and pasted it into the form... to no avail.

I assume there must be some sort of cache in place or something the like.

Any hint would be appreciated.

Thanks

---

### Post by deadflowr on 2016-11-03
Known issue see: [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943")

---

### Post by runlevel0 on 2016-11-03
Whoa, Thanks, that was a quick reply!

I assume that the package is not yet in the production repositories. Root access using `sudo snap login [email]my@email.com[/email]` works perfectly.
I just updated and upgraded gnome-software and restarted snapd but it still doesn't work... I will give it another try tomorrow, else use the terminal.

Thanks for your answer !

---

### Post by ajgreeny on 2016-11-03
Did you try installing the snap package in terminal with ```
sudo snap install packagename
``` as that bug report suggests?

Others have found that to be successful.

---

