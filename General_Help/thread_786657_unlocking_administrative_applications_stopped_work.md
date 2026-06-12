---
title: "unlocking administrative applications stopped working"
date: 2008-05-08
forum: General Help
---

### Post by bsh on 2008-05-08
since a few days, when i log on the pc using vnc, the "unlock" button on administrative applications don't work anymore.
they work if i log in physically on the pc
sudo/gksu still works in a terminal either locally or over vnc or ssh.
anyideas?

---

### Post by jlrubin on 2008-06-06
I have been experiencing a similiar problem in xubuntu.

[http://ubuntuforums.org/showthread.php?t=819916]("http://ubuntuforums.org/showthread.php?t=819916")

I am trying to run without a monitor or keyboard. I log into the box with ssh, start tightvncserver, and I can then connect from a windows box with tightvnc. When I try to use an admin program like Services, I can't use the unlock button.

In my case, gksudo won't work either. It starts the Services window, and prompts for a password, but I still can't do anything.

I am the only user, and am in the 'admin' group

---

### Post by mfdc1969 on 2008-06-20
I too am experiencing same ...

I log off my laptop and then remote login to another box, located in my crawlspace, with XDMCP.

Both computers are running Hardy i386 with all updates as of today.

I am in the admin group and yet I do not have the option of 'unlocking' anything on the remote login box. My laptop is fine ...

I have noticed that as of today's latest update, using Update Manager that the remote box is always indicating it needs to be restarted. The restart icon appears after each restart.

Mike

---

### Post by iaculallad on 2008-06-20
Try to install the PolicyKit:

```
sudo apt-get install policykit policykit-gnome
```

---

### Post by mfdc1969 on 2008-06-20
Both policykit and policykit-gnome are already installed in my case ... I even tried re-installing through Synaptic. 

It did not make a difference.

---

### Post by bsh on 2008-06-21
i have solved this issue by wiping 8.04 and reinstalling 7.04
hope this helps :)

---

