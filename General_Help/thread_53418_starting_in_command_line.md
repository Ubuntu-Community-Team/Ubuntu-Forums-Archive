---
title: "starting in command line"
date: 2005-07-31
forum: General Help
---

### Post by Dr. Z2A on 2005-07-31
When I use linux I like to start off from command line and call X up if i need it.  With other distros this has been the default setting and with ones that it wasnt I just switched the default runlevel to 3 and it was.  I have tried switching the runlevel in Ubuntu and it has still logged me into X to begin with.  Can anyone tell me how to start off the computer running the command line?

---

### Post by Xian on 2005-07-31
Enter this command in a terminal:
```
$ sudo update-rc.d -f gdm remove
```
Or if you prefer...

Use the first command to disable GDM and not load X.
Use the second command to enable GDM again.

This way you can basically just toggle it on and off.

```
$ sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
```
$ sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```

---

### Post by Dr. Z2A on 2005-07-31
and can I still use X after I've logged in after setting those?

---

### Post by Sam on 2005-07-31
[QUOTE=Dr. Z2A]and can I still use X after I've logged in after setting those?[/QUOTE]
Easy:
```
$ startx
```

---

