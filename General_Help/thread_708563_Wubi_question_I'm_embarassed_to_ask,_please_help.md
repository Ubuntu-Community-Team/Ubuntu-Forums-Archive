---
title: "Wubi question I'm embarassed to ask, please help"
date: 2008-02-26
forum: General Help
---

### Post by StrangeRanger on 2008-02-26
The Wubi installer worked flawlessly, very impressed, but I have a question. During the install I was prompted for a user name and pw, fine, did that. But I don't recall being prompted or told what the root password is. So that begs the question for example when I'm in a terminal and need to run something as root, how the heck do I log in? Sorry for my noobness.
j

---

### Post by evan d on 2008-02-26
Don't be afraid to ask, and there's no need to apologize.  Everyone starts somewhere.

Ubuntu doesn't create a root account in the conventional sense.  This can be seen as both a security feature (one less "known" username to try to attack) and an encouragement to only use root privileges when necessary.

That said, you can use the sudo tool to accomplish most tasks.  For instance `sudo gedit /tmp/somefile` will open gedit as root.  If you have a lot of commands to run as root or you'd like a root shell, you can type `sudo -s`.

Of course if you'd prefer to log in as root you can set up your system to do so by typing `sudo passwd` and entering what you'd like the root password to be.

---

### Post by StrangeRanger on 2008-02-28
Thanks for the info. I knew about sudo, but was just wondering about the root user and Wubi install procedure. Thank you!
j

---

