---
title: "Enable root account? [Resolved]"
date: 2007-03-06
forum: General Help
---

### Post by linuxaz on 2007-03-06
Hello,
I am toying with the idea of moving both my kids computers to use Ubuntu, possible Feisty when it becomes final.
One thing about Ubuntu I don't like is sudo.

I've read how to change this for Edgy, and am curious if it will work for Feisty when complete?

My reasoning, is that I don't need them installing software, changing print settings, and such.  Also, I set them up to use a proxy filter to protect their eyes from the nasties of the internet.  I want to keep root control over their proxy settings.

So, is it possible, and is this How-To for Edgy still valid?

Thanks,

linuxaz

---

### Post by bernied on 2007-03-06
All I do to create a root account is:
```
sudo passwd
```You are then asked for three passwords, the first is your current password, the next two are the new root account and its confirmation.

But you don't need to do this to get what you're talking about, just create a new user (or two) that don't have too many privileges and are not in the sudoers file. Don't give them access to your password (or root password if you've created one).

---

### Post by alexforcefive on 2007-03-06
are you saying that you don't want your kids using sudo? why don't you just keep the password secret?

---

### Post by Malac on 2007-03-06
Yes, just  do a normal install where you are main (sudo) user.
Then setup two accounts for your kids as normal users. You can change their privileges in Users and Groups.
"sudo" would be unavailable to them unless they can guess your main password.

---

### Post by linuxaz on 2007-03-06
Malac,
That answers my questions.  

Thanks to all!

linuxaz

---

