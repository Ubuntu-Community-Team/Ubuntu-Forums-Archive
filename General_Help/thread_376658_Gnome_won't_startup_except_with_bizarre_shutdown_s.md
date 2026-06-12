---
title: "Gnome won't startup except with bizarre shutdown sequence"
date: 2007-03-05
forum: General Help
---

### Post by citizenofnowhere on 2007-03-05
This is kind of bizzare and still tickling me, see below for update.

I get past my gdm, I can even see my cursor and am able to move it. After a few minutes of nothing happening a grey rectangle pops up on the top left hand corner, and if i move my cursor over it it shows me I can select or type. Nothing much happens after that.

Changing to a different user, or selecting GNOME failsafe gives me the same problem. However, I CAN log into my E17 session (using a different user, I didn't dare try with my main account).

When this happens my .xsession-errors shows only that a profile for my user (anna) cannot be found.

The only things I've done to my system in the last 24 hours is install a couple of KDE games, and removed a panel music player. I've upgraded wine and beryl (svn) but I started up fine a few times after that.

Here is what **DOES WORK**:

Booting into recovery mode from Grub, typing in my root password for maintenance, and typing this in:

```
shutdown -t secs now
```

It goes into a normal shutdown sequence, then it starts up ALL my services again, says it's going into single-user mode, asks me to press CTRL+D to continue which I do and I get into my session fine! ](*,)

I'd REALLY appreciate any thoughts :)

**EDIT: **I took a look at my /var/log/messages again and it says that during the times I get into my session, gconfd is started by root, but it fails with an error 15 if I bootup the normal way because it is started by a normal user. Is there a way to make root start gconfd when I log in?

**EDIT** (again): TRIED renaming my .gconf and .gconfd directories, and booting up - still the same. I even got a new kernel.  Help?

---

### Post by citizenofnowhere on 2007-03-05
*bump* Anyone?

---

### Post by citizenofnowhere on 2007-03-06
I finally fixed it by disabling samba and nfs-kernel-server in my System->Administration->Services. I'm less than happy with that, but it looks like an ancient GNOME bug that was never fixed. Still wondering why it never bothered me before, but I hope this little run around the whole day helps someone.

---

