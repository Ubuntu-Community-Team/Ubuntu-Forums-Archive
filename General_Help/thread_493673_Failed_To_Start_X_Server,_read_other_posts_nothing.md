---
title: "Failed To Start X Server, read other posts nothing helps"
date: 2007-07-06
forum: General Help
---

### Post by brendon1937 on 2007-07-06
I am attempting to run ubuntu on my computer. The computer I am trying to run it off of, unfortunately, does not have a CD drive. So I put the hard drive into a computer that has a CD drive, installed ubuntu and then switched it back. Ubuntu successfully loads using the second computer (with the cd drive), but failed to load from the original computer. I have google'd my problem countless times and searched these forums, and nothing I try seems to help. It's very likely I'm just missing something simple.

When I start it I get a, "Failed To Load The X Server" message. I have tried the "sudo dpkg-reconfigure xserver-xorg" thing but it asks me for my username and password. I type in the username correctly but when I get to the password part it won't allow me to type anything in. So it won't allow me to enter any commands or anything. I have also treid to edit /etc/x11/xorg.conf (change driver defalt to vesa). But it won't allow me to save the file, and I'm not 100% sure where I'm supposed to change the file either (to vesa or w/e).

I could seriously use any help, and would greatly appreciate it.

-Brandon

---

### Post by confused57 on 2007-07-06
> **brendon1937 said:**
> I am attempting to run ubuntu on my computer. The computer I am trying to run it off of, unfortunately, does not have a CD drive. So I put the hard drive into a computer that has a CD drive, installed ubuntu and then switched it back. Ubuntu successfully loads using the second computer (with the cd drive), but failed to load from the original computer. I have google'd my problem countless times and searched these forums, and nothing I try seems to help. It's very likely I'm just missing something simple.

When I start it I get a, "Failed To Load The X Server" message. I have tried the "sudo dpkg-reconfigure xserver-xorg" thing but it asks me for my username and password. I type in the username correctly but when I get to the password part it won't allow me to type anything in. So it won't allow me to enter any commands or anything. I have also treid to edit /etc/x11/xorg.conf (change driver defalt to vesa). But it won't allow me to save the file, and I'm not 100% sure where I'm supposed to change the file either (to vesa or w/e).

I could seriously use any help, and would greatly appreciate it.

-Brandon
You won't see your password being typed in...go ahead and type it in, then press "enter".

To edit your xorg.conf file manually:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo nano xorg.conf
```
change the video driver to "vesa"...Ctrl+X, y, enter...this will save the changes...I would try "sudo dpkg-reconfigure xserver-xorg", without quotes,  first.

---

### Post by Kevin the Olden on 2007-07-06
It probably would have been better to put the CD drive in the computer you want to run ubuntu on. Any, a CD drive is very cheap these days...

---

