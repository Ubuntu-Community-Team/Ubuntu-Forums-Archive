---
title: "How to save changes in xorg.conf ?"
date: 2008-06-13
forum: General Help
---

### Post by AJSB on 2008-06-13
Hello, 
I tryed to edit xorg.conf at /root/etc/X11/xorg.conf to solve my problems with color depth but when tryed to save it it says that i don't have the right permissions !!!

When i installed 8.04LTS it only asked for a normal user account and not for a root password so how can i login as root and edit xorg ?!?

TIA,
AJSB

---

### Post by iaculallad on 2008-06-13
> **AJSB said:**
> Hello, 
I tryed to edit xorg.conf at /root/etx/X117xorg.conf to solve my problems with color depth but when tryed to save it it says that i don't have the right permissions !!!

When i installed 8.04LTS it only asked for a normal user account and not for a root password so how can i login as root and edit xorg ?!?

TIA,
AJSB

You don't need to login as root to edit your xorg.conf file. Just place **sudo** before your command:

i.e:

```
sudo gedit /etc/X11/xorg.conf
```

```
sudo nano /etc/X11/xorg.conf
```

```
sudo vi /etc/X11/xorg.conf
```

---

### Post by AJSB on 2008-06-13
Thanks :)

Regards,
AJSB

---

### Post by aysiu on 2008-06-13
That should be *gksudo gedit* instead of *sudo gedit*. Good habit to get into using *gksudo* with graphical applications (like Gedit) and keeping *sudo* to terminal applications (like Vi).

You can read more here about permissions and graphical ways to edit root-owned files:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by iaculallad on 2008-06-13
> **aysiu said:**
> That should be *gksudo gedit* instead of *sudo gedit*. Good habit to get into using *gksudo* with graphical applications (like Gedit) and keeping *sudo* to terminal applications (like Vi).

You can read more here about permissions and graphical ways to edit root-owned files:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Does it make any difference when doing gksudo instead of sudo since gksudo is just the GTK frontend of sudo? Thanks for pointing it out.

---

### Post by aysiu on 2008-06-13
> **iaculallad said:**
> Does it make any difference when doing gksudo instead of sudo since gksudo is just the GTK frontend of sudo? Thanks for pointing it out.
Yes, it does.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dreamdigital on 2009-02-18
> **AJSB said:**
> Hello, 
I tryed to edit xorg.conf at /root/etc/X11/xorg.conf to solve my problems with color depth but when tryed to save it it says that i don't have the right permissions !!!

When i installed 8.04LTS it only asked for a normal user account and not for a root password so how can i login as root and edit xorg ?!?

TIA,
AJSB

This is what I did to fix that problem with much frustration.  Took me a while and a lot of forum look ups!!!  And lots of god dammits!!!  My Screen Resolution was not saving everytime I rebooted so then I had to go back and put all my user settings back the way I had them.  It was very, very annoying!  Ok here is a step by step...

1. I opened up my System > Administration > nVidia X Server Settings

2. Configure it all how you want it under the X Server Display Configuration.  If you have Dual monitors like me I recommend Twin View.

3. Then on the bottom right above "Quit and Help" (ubuntu 8.10) click "Save to X configuratiion File.

4.  Now it won't let you save it so don't try instead click on "Show Preview"

5. Once that is shown highlight all the text and click "ctrl C" or just right click and copy it.

6. Now close out of there and go into your terminal, Applications > Accessories > Terminal.

7. In the command line enter this "gksudo gedit /etc/X11/Xorg.conf"  This gives you the permission to edit this file.

8. Now that that folder is open highlight and delete all the text in this folder.

10. Next press "ctrl V" or just right click or just click paste at the top.

11. This pastes your screen settings that you copied and now you can click save and then close.  You are finished.

If this doesn't work let me know, e-mail me or something, [email]dream_digital@hotmail.com[/email]

---

