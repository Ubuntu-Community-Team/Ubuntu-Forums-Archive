---
title: "Parental Controls for Gutsy that can use unique password?"
date: 2007-10-26
forum: General Help
---

### Post by Glunn11 on 2007-10-26
Hello Ubuntuforums!
I am in need of a parental controls program that, unlike dansguardian, uses a UNIQUE (not root) password to make changes. Is there one? Thanks!
-Glen

---

### Post by p_quarles on 2007-10-27
> **Glunn11 said:**
> Hello Ubuntuforums!
I am in need of a parental controls program that, unlike dansguardian, uses a UNIQUE (not root) password to make changes. Is there one? Thanks!
-Glen
I'm curious about *why* you would want something like that. If it's because the kids have root access, then I would just point out that they can turn off any and all programs without needing anything other than the root password. 

There *are* ways of giving users some root privileges without giving them the ability to change everything on the system. Is this what you're looking for?

---

### Post by Glunn11 on 2007-10-27
Yes, if that is possible, that will work, as well.

---

### Post by p_quarles on 2007-10-27
Yeah, it's definitely doable. I'll try to find a tutorial on this tomorrow, and if I don't, I'll attempt to write one (because it would be useful for many people, after all). 

Anyway, you could help me out by telling me what kind of root privileges the kids need to have. This kind of thing is easier to do by denying privileges by default, and enabling them one by one. In other words, if they just need to be able to install programs from the repositories, it's much easier to allow that than it is to disallow everything except changing dansguardian.

---

### Post by Glunn11 on 2007-10-28
They need to be able to install programs from the repositories, as well as install updates. That should be about all.

---

### Post by p_quarles on 2007-10-28
All right, that's easy enough. 

For these directions, I'm going to make several assumptions. First, that you're using Gnome, and second, that there is one child in question, and that he/she has his/her own computer. If any of these are incorrect, a few steps will be different, and I can provide them if needed. 

First, you'll want to edit the sudoers configuration file. There is a very specific way in which this needs to be done. First, open a terminal (alt-F1), and type (or paste) the following:
```
export EDITOR=gedit && sudo visudo
```
This brings up the configuration file. Add a line to it that says the following:
```
*user_name *ALL=(root) /usr/bin/synaptic, /usr/bin/apt-get
```
*user_name* should be replaced with the actual name of the user's account. Once you've done that, save the file and exit.

If you haven't already, be sure to create your own administrative account on this computer. This needs to be a user that is separate from the user you wish to restrict, since you'll need to be able to configure dansguardian and do other administrative work.

Now you need to remove the user in question from the admin group. You may have noticed a line in the sudoers file that said:
```
%admin ALL=(ALL) ALL
```
This means that any member of the group admin can run any command as any user. To remove the child's account from this group, type in the terminal:
```
gksudo gedit /etc/group
```
Find the line beginning with "admin", and delete the user's name. Make sure that your account *is *in that line, and if it's not, type it in. 

Now, all you have to do is log out, log back in, and the new settings will take effect. It's a good idea to login as the restricted user, too, to make sure that he/she is able to use the package manager, and unable to use other root functions. 

If you need to set up more than one computer like this, just follow the same steps on each one. If more than one restricted user is using the same computer, just let me know. There's an easy way to add them all to a single group, and then restrict that group's privileges.

---

### Post by Glunn11 on 2007-10-28
Alright, thanks! Now I just need to know of a download site I can get DansGuardian from that WILL work with Gutsy. I found one when I was using Feisty after a long search, but I can't seem to find it again.

---

### Post by p_quarles on 2007-10-28
Hmm. Dansguardian is in available via Synaptic if you have all the repositories enabled. If a search in Synaptic doesn't make it show up, do this:
```
gksudo gedit /etc/apt/sources.list
```
In this file, delete the # symbols in front of the four lines ending with "universe." Then, run the following two commands:
```
sudo apt-get update
sudo apt-get install dansguardian
```

---

