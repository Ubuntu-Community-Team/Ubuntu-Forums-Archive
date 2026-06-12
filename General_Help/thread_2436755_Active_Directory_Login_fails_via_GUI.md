---
title: "Active Directory Login fails via GUI"
date: 2020-02-12
forum: General Help
---

### Post by jyanga on 2020-02-12
Hi

I followed the document below  to setup Active Directory(AD) authentication on my Ubuntu 18.04 Desktop.

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

I can login using my AD credentials via SSH successfully.   However, when I attempt to login using the GUI, I get a blip and give me back a login screen.

Here is the error I saw on my logs.

> gdm-password][7073]: pam_systemd(gdm-password:session): Failed to create session: No such file or directory

Help.

Regards,
j

---

### Post by jyanga on 2020-02-12
I logged into TTY2 using my AD credentials and it worked.  I then attempted to run startx.  I got the error below.

> gnome-session-binary[9202]: ERROR: Failed to connect to system bus: Exhausted all available authentication mechanisms (tried: EXTERNAL) (available: EXTERNAL)
                                                                 aborting...


---

### Post by EuclideanCoffee on 2020-02-12
Hm, do you have gdm installed? Some instances of startx also require a root user.

---

### Post by jyanga on 2020-02-12
I believe I do.

> # dpkg --get-selections | grep -i gdm
gdm3                                            install
gir1.2-gdm-1.0                                  install
libgdm1                                         install




---

