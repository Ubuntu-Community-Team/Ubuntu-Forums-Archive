---
title: "Automount at boot taking very long time after 15.04 upgrade"
date: 2015-05-06
forum: General Help
---

### Post by m_m3 on 2015-05-06
After my recent upgrade to 15.04, I noticed that the boot is taking a very long time -- I have an SSD, and previously boot to the login screen was taking about 7-8 seconds.  Now it's more like 35-45. 

I switched to the terminal output during the wait, and noticed that is sitting on a line mentioning my automount for a long time before moving on -- this did not appear in 14.10.  

I removed the lines from my /etc/fstab, and the boot time to login screen returned to about 7-8 seconds.  I would like to have these mounted at boot time, though --  any ideas?  The relevant lines from my fstab are:

```
//192.168.1.110/Public /mnt/titanpublic cifs iocharset=utf8,uid=1000,gid=1000 0 0
//192.168.1.110/backups /mnt/titanbackups cifs iocharset=utf8,uid=1000,gid=1000 0 0
```

---

### Post by dino99 on 2015-05-06
maybe these lines might be set a bit differently; better to ask devs on askubuntu, as it seems related to systemd.
do you have tested to boot with upstart instead ?

---

### Post by m_m3 on 2015-05-06
No problem -- asking on askubuntu now.  I can't say in regards to upstart -- I'm still learning.  Do you mean creating a service for these mounts?

---

### Post by ajgreeny on 2015-05-06
From the grub menu go to Advanced and from that choose the kernel line with **upstart** showing in the line.

Does that remove the delay?

---

### Post by m_m3 on 2015-05-06
Yes -- yes it does.  Interesting.  

For anyone finding this:

1) Hold down shift during startup, to load the GRUB loader screen
2) Go to "Advanced" and from that choose the kernel line with "upstart" showing in the line

Guess I'll file a bug report and debate whether to do upstart permanently. :P

---

### Post by Morbius1 on 2015-05-06
[COLOR=#0000cd]**EDIT**: Didn't see your post when I posted. Seems you moved back to upstart and that resolved it?[/COLOR]

Do you mind doing an experiment? 

With the lines in fstab either commented and the shares unmounted run this command:
```
sudo mount -t cifs //192.168.1.110/Public /mnt/titanpublic -o uid=1000,gid=1000
```
You should get prompted for sudo's password then this will happen:
> Password for root@//192.168.1.110/Public
It will stat that way until the earth stops revolving around it sun.

Now run it this way:
```
sudo mount -t cifs //192.168.1.110/Public /mnt/titanpublic -o guest,uid=1000,gid=1000
```
Do you get access now?

If you do then add the "guest" parameter in your line in fstab and see if that resolves the problem.

Of course there may be another issue and that's one where fstab is executing before the network is up.

---

### Post by m_m3 on 2015-05-06
Temporarily moving back to upstart fixed it, yeah, but I'll try this too, while starting up normally.

---

### Post by m_m3 on 2015-05-06
It works!  Adding "guest" to the options line in /etc/fstab makes the boot normal, even with systemd.

Thanks!

---

