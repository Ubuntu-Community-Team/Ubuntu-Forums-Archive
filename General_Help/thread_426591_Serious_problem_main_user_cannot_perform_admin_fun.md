---
title: "Serious problem: main user cannot perform admin functions"
date: 2007-04-28
forum: General Help
---

### Post by John Azelvandre on 2007-04-28
I just bought a laptop with Ubuntu 6.10 pre-installed.

Unfortunately, they enabled the root account, and it was necessary to log into this account to set up my user account.  I created my main user, and made sure that account had all administrative privileges so I could use sudo, etc.

Once I logged into my main user account, I found that some administrative dialogs under the "system" menu in gnome don't work.

For example: 

Time and Date

Add printer, under Printers

Users and groups

The symptom of these not working is that they will freeze and the only way to close the windows is to do a force quit.

What is going on?  Is this related or unrelated to the fact that upon login I get a "GNOME Settings Daemon failed to start" error?

Thanks.

---

### Post by taurus on 2007-04-28
Did you remember to add your user account to groups adm and admin in /etc/group?  Log in as root and add your username to those two groups.

```
nano -w /etc/group
```

---

### Post by John Azelvandre on 2007-04-28
Yes, I am already in these two groups.  I added my user (zizonus) to nearly all the groups, just in case that was it:

For adm it says:

[FONT="Fixedsys"]x:4:zizonus
[/FONT]
for admin, it says:

[FONT="Fixedsys"]x:114:root,zizonus[/FONT]

---

### Post by John Azelvandre on 2007-04-28
Actually, add printer doesn't work from the root account either, so that's a separate problem ...

---

### Post by John Azelvandre on 2007-04-29
Can anyone offer any suggestions?  Or suggest some diagnostic tests I can run?

---

### Post by aysiu on 2007-04-29
This will give you the fix you need:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by John Azelvandre on 2007-04-29
I just checked the files specified in the link you posted, and neither are corrupted.  My /etc/sudoers is identical to what it should be.  LIkewise, my mainuser is in the admin group as specified.  So, that's not it.

---

### Post by taurus on 2007-04-29
Can you post the output of this command from a terminal?

```
id
```

---

### Post by John Azelvandre on 2007-04-29
Sure.  Here it is.  My main user is "zizonus".

```
zizonus@lc2000:~$ id
uid=1000(zizonus) gid=115(zizonus) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),100(users),101(dhcp),102(syslog),103(klog),104(ssl-cert),105(crontab),106(ssh),107(messagebus),108(avahi),109(lpadmin),110(haldaemon),111(scanner),112(slocate),113(gdm),114(admin),115(zizonus)
zizonus@lc2000:~$ 

```

I added zizonus to a lot of groups he probably doesn't need to be in when I was trying to figure out this problem.

---

### Post by John Azelvandre on 2007-04-30
I've been playing around with this, and want to provide more precise details to what is going on.  I think it is a Gnome desktop environment issue.  I hope someone will have the patience to read through the following and give me some advice.

Details of the peculiar symptoms:

-The error only happens when attempting to use gnome desktop environment menus - System/Administration/ functions.

-In other words, I have never had difficulties executing sudo commands (such as ```
sudo adduser
```) in a terminal.

-The error occurs when a selection on the menu is chosen, such as System/administration/Users and Groups.  Sometimes (but not always), a dialog pops up asking for my password, as it should, and then the Users and Groups dialog begins to appear, but freezes before completion.  A 'force quit' is necessary to close the dialog box.

Attempting to open Users and groups a second time, causes the box to correctly load and be fully functional, but this time without calling for a password first. (Well, this happened today.  Don't know if I can replicate it.)

Then going to another command, like System/administration/Time and Date, calls up the dialog without asking for a password, and it freezes, requiring force quit.

A third attempt at Users and groups produced the freeze.  Once again, no request for password.

In summary:

First call today to Users and groups -> password requested, dialog freezes.
Second call to Users and groups -> password NOT requested, dialog loads correctly and works.
Subsequent call to Time and date -> no password request, freezes
Repeat call to Time and date -> no password request, freezes
Third call to Users and groups -> no password request, freezes.

Some things, like synaptic package manager, always work, but don't request a password (!)

Any ideas about what could be wrong?  Thanks in advance.

---

### Post by John Azelvandre on 2007-04-30
I've been playing around with this, and want to provide more precise details to what is going on.  I think it is a Gnome desktop environment issue.  I hope someone will have the patience to read through the following and give me some advice.

Details of the peculiar symptoms:

-The error only happens when attempting to use gnome desktop environment menus - System/Administration/ functions.

-In other words, I have never had difficulties executing sudo commands (such as ```
sudo adduser
```) in a terminal.

-The error occurs when a selection on the menu is chosen, such as System/administration/Users and Groups.  Sometimes (but not always), a dialog pops up asking for my password, as it should, and then the Users and Groups dialog begins to appear, but freezes before completion.  A 'force quit' is necessary to close the dialog box.

Attempting to open Users and groups a second time, causes the box to correctly load and be fully functional, but this time without calling for a password first. (Well, this happened today.  Don't know if I can replicate it.)

Then going to another command, like System/administration/Time and Date, calls up the dialog without asking for a password, and it freezes, requiring force quit.

A third attempt at Users and groups produced the freeze.  Once again, no request for password.

In summary:

First call today to Users and groups -> password requested, dialog freezes.
Second call to Users and groups -> password NOT requested, dialog loads correctly and works.
Subsequent call to Time and date -> no password request, freezes
Repeat call to Time and date -> no password request, freezes
Third call to Users and groups -> no password request, freezes.

Some things, like synaptic package manager, always work, but don't always request a password (is there some sort of time setting on the password?)

Any ideas about what could be wrong?  Thanks in advance.

---

### Post by zvacet on 2007-05-01
```
sudo adduser zizonus admin
```

---

### Post by John Azelvandre on 2007-05-02
This does not help.  my mainuser is already a member of the group admin.  Any other ideas?

---

### Post by kjelle392 on 2007-05-07
I don't know the answer John, but want to tell you that I have exactly the same problem. No-one seems to have a solution for this... guess it's a bug.

---

### Post by John Azelvandre on 2007-05-07
I solved this problem, finally, by doing a completely fresh install of Feisty.  Something was flawed about the original Edgy install that was done by the vendor I bought the laptop (Linux Certified, Inc.).  

I don't really know, but I think it has something to do with the fact that they enabled the root account and made it the default, or the way in which they set that up.  Many of my problems seemed to stem from permissions/ownership of files, etc.

I can fully recommend the hardware I bought from Linux Certified, but use caution about having them install ubuntu.

Good luck with your issue.

---

### Post by kelvin spratt on 2007-05-07
surely if you bought the laptop with it preinstalled just take it back and they will sort it out for you or tell you what to do

---

### Post by John Azelvandre on 2007-05-07
No worries.  they didn't charge me extra for the pre-install, and now it's working great.  Lesson learned: just do it yourself.

(Although I found the config files they set up very handy in getting my graphics card to work properly...)

---

