---
title: "How would I login and startx automatically"
date: 2022-06-11
forum: General Help
---

### Post by schwim-dandy on 2022-06-11
Hi there!

I'm setting up an Openbox install on a Ubu22 server and would like to  login & startx without utilizing a greeter application. I've managed to get x to start once I've logged in on startup via .profile but I'm having problems finding a way to automatically login on ubu startup.  This is not an actual server, I just wanted a minimal Ubu 22 install to build off of.  It's being used as a desktop install.

How would I get the machine to log in automatically to my user on startup?

---

### Post by schwim-dandy on 2022-06-11
I have tried this method to enable autologin but it's not working.  When I 
> sudo systemctl edit getty@tty1
and enter the following into the file:
> [Service]     ExecStart=
    ExecStart=/sbin/agetty --autologin Your_username --noclear %I $TERM
I get the following response upon saving.
> Editing "/etc/systemd/system/getty@tty1.service.d/override.conf" canceled: temporary file is empty.
and the file is missing the added entry when I go back to edit again.

[EDIT] Solved.  Placed the code where the file wanted it to be and everything works as it should.

---

### Post by yancek on 2022-06-11
Check the link below, it's in regard to 16.04 but probably will still work.

[https://askubuntu.com/questions/819117/how-can-i-get-autologin-at-startup-working-on-ubuntu-server-16-04-1](https://askubuntu.com/questions/819117/how-can-i-get-autologin-at-startup-working-on-ubuntu-server-16-04-1)

---

### Post by schwim-dandy on 2022-06-11
> **yancek said:**
> Check the link below, it's in regard to 16.04 but probably will still work.

[https://askubuntu.com/questions/819117/how-can-i-get-autologin-at-startup-working-on-ubuntu-server-16-04-1](https://askubuntu.com/questions/819117/how-can-i-get-autologin-at-startup-working-on-ubuntu-server-16-04-1)

Thank you very much for your help.  That's exactly what I needed.  Login and startx is working as it should now.

---

