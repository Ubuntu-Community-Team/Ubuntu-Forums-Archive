---
title: "XDMCP help"
date: 2007-10-28
forum: General Help
---

### Post by Green_Star on 2007-10-28
Hi,

I have installed Gusty in my desktop and laptop. I enabled XDMCP remote login in my desktop and tried remote logging from my laptop, but ended up with following error. It came on blue screen.

> There already appears to be an X server running on display :1. Should another display number tried? Answering no will cause GDM to attempt starting the server on :1 again. (You can change console by pressing Ctrl-Alt plus a function key, such as Ctrl-Atl-F7 to go to console 7. X servers usually run on consoles 7 and higher.

After pressing 'yes' there is a popup box saying ..

> The specified display number was busy, so this server was started on display :2.

How can I fix this error?

---

### Post by Jose Catre-Vandis on 2007-10-28
what command did you use to remote in, and with what program?

have you enabled mutliple logins from same user? (you have to uncheck!)

---

### Post by Green_Star on 2007-10-28
I just used the XDMCP login option which is available on the login screen. And it is not even showed me a login screen to use any user name.

When I selected XDMCP server then it went to bluescreen, in that screen it showed the  message (details are in first post ).

---

### Post by Green_Star on 2007-10-29
any help .  .?

---

### Post by Green_Star on 2007-10-29
bump

---

### Post by timcredible on 2007-10-30
imho, xdmcp is the best way to do remote access, here's a how-to i wrote on it with screenshots, hope it helps.  if any issues with the instructions, let me know:

[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

---

### Post by Green_Star on 2007-10-30
> **timcredible said:**
> imho, xdmcp is the best way to do remote access, here's a how-to i wrote on it with screenshots, hope it helps.  if any issues with the instructions, let me know:

[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

Thanks man,

I am sooo waiting to get some help in this issue. Right now I am at work, as soon as I go home I tried this in first place and let you know. As per your instruction I did every thing right except I have to double check the 'security' tab.

---

### Post by Green_Star on 2007-10-30
Nope, i end up with same error. I guess it is some thing to do with X server settings .. any clue?

---

### Post by hoa3r on 2007-10-30
Have a look here: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193/](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193/)

It's a bug with Gutsy.

---

### Post by t4thfavor on 2008-02-03
Thats generally upsetting, I wonder how long it will be until it gets fixed. Its been a while, and I am still getting that error on a fully patched machine.

---

