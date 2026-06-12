---
title: "screen resolution too small"
date: 2007-10-05
forum: General Help
---

### Post by Mr.popo on 2007-10-05
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071005210257

thats error i get after i enter the code to get into visa i chose each resultion and its still says that error
please help
cheers.

---

### Post by bodhi.zazen on 2007-10-05
That is not an error, it is a warning or advisement. Basically it is telling you that the command made a backup of xorg.conf and saved it to /etc/X11/xorg.conf.20071005210257

This is normal, and you can restore (xorg.conf) from back up if needed with :

```
sudo cp /etc/X11/xorg.conf.20071005210257 /etc/X11/xorg.conf
```

To see your new settings, restart X (log off and back in).

---

### Post by Mr.popo on 2007-10-06
> **bodhi.zazen said:**
> That is not an error, it is a warning or advisement. Basically it is telling you that the command made a backup of xorg.conf and saved it to /etc/X11/xorg.conf.20071005210257

This is normal, and you can restore (xorg.conf) from back up if needed with :

```
sudo cp /etc/X11/xorg.conf.20071005210257 /etc/X11/xorg.conf
```

To see your new settings, restart X (log off and back in).

it worked for one resolution but now it doesnt work
do i log of or restart the computer after ive used the command.

---

### Post by bodhi.zazen on 2007-10-06
What does not work ???

When you get to the screen where you choose a resolution, select the highest resolution you wish to use.

Then, log off and back in. Re-boot is not required.

To change your resolution (after you have configured and re-started X) go under 

System -> Preferences -> Screen Resolution.

---

### Post by Mr.popo on 2007-10-06
> **bodhi.zazen said:**
> What does not work ???

When you get to the screen where you choose a resolution, select the highest resolution you wish to use.

Then, log off and back in. Re-boot is not required.

To change your resolution (after you have configured and re-started X) go under 

System -> Preferences -> Screen Resolution.

ye i have done all of that but i just have the default resulutions still?



should i use this command 


sudo dpkg-reconfigure -phigh xserver-xorg
?

---

### Post by bodhi.zazen on 2007-10-06
yes, try that command ...

Then re-start X

If that fails, what video card do you have and what resolution do you want ?

---

### Post by Mr.popo on 2007-10-06
> **bodhi.zazen said:**
> yes, try that command ...

Then re-start X

If that fails, what video card do you have and what resolution do you want ?

ye i failed

my video card is a Radeon X1650 SE
i need anything high really
sorry if im asking to many questions.
thnaks

---

### Post by bodhi.zazen on 2007-10-07
You will need to install the ATI driver.

I have very limited experience with those cards :(

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by Mr.popo on 2007-10-07
> **bodhi.zazen said:**
> You will need to install the ATI driver.

I have very limited experience with those cards :(

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

thanks mate
it now works
one question though.
after installing that driver should my deskop effects work?

---

### Post by bodhi.zazen on 2007-10-07
\o/

My guess is that desktop effects *should*  now work, although if not you may need to make a few modifications ...

---

