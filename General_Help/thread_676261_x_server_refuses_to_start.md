---
title: "x server refuses to start"
date: 2008-01-23
forum: General Help
---

### Post by wavemasta on 2008-01-23
I am using ubuntu feisty. I installed some new updates, and then when I finished, I did a restart, and now all am getting is the command line interface.
I tried typing startx, but it didnt work. I tried it from recovery mode, still got the same thing.
Any ideas? Im doing some work, and this thing is slowing me down.
I need my Graphical environment!!
thanx

---

### Post by nemilar on 2008-01-23
Need more information!  A recent update caused a lot of problems with X, but they should all be fixed by now.  Try running:

```
sudo apt-get dist-upgrade
```

If that doesn't fix it (or doesn't update any packages), then post the contents of your /var/log/Xorg.0.log file so we can better help you.

---

### Post by peitschie on 2008-01-23
What type of grapics card do you have?  (Including manufacturer and model)...
Where you using the default Ubuntu drivers before or the Restricted drivers or some other source (such as Envy)?

---

### Post by wavemasta on 2008-01-24
Guys...this is serious.......the commands dont work......sudo doesnt work, apt and apt get dont work, and when I used vim to view the contents of the /var/log/xorg.0.log file, I got this message sayin vim wasnt installed, and I should run apt...which in turn doesnt work :)
On the screen however, I get this funny message  " bcm43xx_microcode5.fw not available".
I am using a nividia graphics card and a compaq presario v6000...dont think thats the prob cus it worked before...
Please can any1 help?

---

### Post by tzulberti on 2008-01-24
Try to use: "sudo dpkg-reconfigure xserver-xorg". Try different resolutions or try vesa driver. The to start X11 use: "sudo /etc/init.d/gdm".
I forgot, instead of using vim use nano.

---

### Post by wavemasta on 2008-01-24
Now I decided to install gutsy from the cd, but now I am getting the damn white screen..I had this problem before, I fixed it somewhere, I just had to add some extra flags, but Ive forgotten unfortunately. Can anyone help out?
Because now, If I try booting from the hard drive, I end up with grub error 17.meaning I cannot even access my windows partition.
Help?

---

### Post by wavemasta on 2008-01-24
I fixed it......changed the irq flags and it worked ok.
Thanks!!

---

