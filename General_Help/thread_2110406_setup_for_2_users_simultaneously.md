---
title: "setup for 2 users simultaneously"
date: 2013-01-30
forum: General Help
---

### Post by binary_dreamer on 2013-01-30
Hi. i do have a laptop that runs ubuntu 12.04.
the need is for a user to work on the laptop and a second user to work on the monitor attached to the VGA and keyboard/mouse attached to usb.
the 2 sessions will be ordinary users using office utilities, nothing extreme.
is there a way to make the forementioned configuration?

---

### Post by omeomi on 2013-01-30
You might want to check this out: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by sudodus on 2013-01-30
> **omeomi said:**
> You might want to check this out: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)
Interesting with MultiseatX but
> ... there are several different ways to achieve multi-seat; in practice there are very few approaches which are both simple and stable.

It might be a good idea to get a cheap second-hand computer and run a light-weight system, for example Lubuntu. You could use that system as a stand-alone system or use it to log in remotely with ```
ssh -X user@server
```, or use a remote desktop like rdesktop or remmina. You could also limit the networking to file sharing with samba or sftp.

---

### Post by binary_dreamer on 2013-01-30
hi. thanks for the replies. multiseat seems good, i will give it a try and come back with replies.

the second computer is out of the scope for this project.

---

