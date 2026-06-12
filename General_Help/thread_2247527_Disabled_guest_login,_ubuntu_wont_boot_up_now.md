---
title: "Disabled guest login, ubuntu wont boot up now"
date: 2014-10-08
forum: General Help
---

### Post by thumper2 on 2014-10-08
I was looking to disable guest login and i found one link 'remove guest login ubuntu' [http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)

  I did this: Open /etc/lightdm/lightdm.conf file

  from your terminal using the following command
  gksudo gedit /etc/lightdm/lightdm.conf

  Add the following line
  allow-guest=false

  Save and exit the file
  After i restarted my laptop i see "The system is running in low-graphics mode" [http://i.stack.imgur.com/AiwJH.png](http://i.stack.imgur.com/AiwJH.png)

  My question is: How can i fix this problem? should i re-install ubuntu? Can i use LIVE Usb to edit it or something like this?

  Thank you!

---

### Post by deadflowr on 2014-10-08
What happens if you reverse the line?

Boot up and switch to a console (ctrl + alt+F1-6, any F key up to F6)
Login in like you would normally; username and password.
Then use nano to edit the file
```
sudo nano /etc/lightdm/lightdm.conf
```
change it to either true, or simple add a # to the front.
(The # will tell the system to ignore that line)
Then ctrl+x, it'll ask if you want to modify the file, click y, then enter, it'll show the filename, again click enter, and then it should close nano.

Now simply reload lightdm
```
sudo restart lightdm
```
or
```
sudo service lightdm restart
```

Now what happens?

---

### Post by thumper2 on 2014-10-08
> **deadflowr said:**
> What happens if you reverse the line?

Boot up and switch to a console (ctrl + alt+F1-6, any F key up to F6)
Login in like you would normally; username and password.
Then use nano to edit the file
```
sudo nano /etc/lightdm/lightdm.conf
```
change it to either true, or simple add a # to the front.
(The # will tell the system to ignore that line)
Then ctrl+x, it'll ask if you want to modify the file, click y, then  enter, it'll show the filename, again click enter, and then it should  close nano.

Now simply reload lightdm
```
sudo restart lightdm
```
or
```
sudo service lightdm restart
```

Now what happens?

Yeah it fixed my problem!! Thanks very much man!! [IMG]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/IMG][IMG]http://ubuntuforums.org/images/smilies/biggrin.gif[/IMG][IMG]http://ubuntuforums.org/images/smilies/eusa_boohoo.gif[/IMG]

---

