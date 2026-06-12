---
title: "passwords"
date: 2013-02-09
forum: General Help
---

### Post by Mike Zahorik on 2013-02-09
I'm using Ubuntu 12.04 and I'm a new used. Attempting to be a MS convert, but am having trouble. Why must I type in a password so much, for things that are not very important. I find this very annoying. There is no one else using this computer. How can I bypass the majority of these nusance requests?

Mike

---

### Post by howefield on 2013-02-09
What "not important" things are asking for a password ?

---

### Post by Mike Zahorik on 2013-02-09
For Example, installing software from the Ubuntu software center. You press the install button for a text editor and your are asked for a password.

---

### Post by rnerwein on 2013-02-09
> **Mike Zahorik said:**
> I'm using Ubuntu 12.04 and I'm a new used. Attempting to be a MS convert, but am having trouble. Why must I type in a password so much, for things that are not very important. I find this very annoying. There is no one else using this computer. How can I bypass the majority of these nusance requests?

Mike
hi
hello here is the [COLOR=Blue]no one else using your computer[/COLOR] - you understand --> you are on the net !!!
cheers

---

### Post by Mike Zahorik on 2013-02-09
So..... I still don't want to enter a password for simple operations. I've been using MS software since the beginning and I don't have to enter so many passwords.

---

### Post by prodigy_ on 2013-02-09
> **Mike Zahorik said:**
> I've been using MS software since the beginning and I don't have to enter so many passwords.
That's because you used accounts that were members of the local Administrators group. An unprivileged Windows user is more or less as limited as a regular Linux user.

That being said, here's [the answer to your question](http://askubuntu.com/questions/98006/how-do-i-prevent-policykit-from-asking-for-a-password). Requires some tinkering with config files though.

---

### Post by Mike Zahorik on 2013-02-09
Hey, thank you. There's a lot to learn and Ubuntu is so different from MS stuff. I'm trying very hard to be open to this stuff, but get frustrated. I appreciate your help. Mike

---

### Post by nema.arpit on 2013-02-09
Sorry, but that feature is not available by default in Linux.
Requiring the Root password for any system wide change (like installing software) is considered to be a feature of Linux and a very important one at that.
You can try to log in as the root user, but this is disabled by default in Ubuntu and *highly* discouraged. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) .
Alternatively, you can start the Software Center with sudo, from the terminal.

---

### Post by Mike Zahorik on 2013-02-09
Yes, I have done this with Nautilus (started in terminal), but still, in terminal it still asks for a password? If I screw something up some how I am responsible and will learn from it and fix it up. I want to learn and if I learn the hard way so be it. Thanks

---

### Post by howefield on 2013-02-09
See post #8.

Thread closed.

---

