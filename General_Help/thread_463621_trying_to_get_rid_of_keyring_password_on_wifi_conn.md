---
title: "trying to get rid of keyring password on wifi connect"
date: 2007-06-03
forum: General Help
---

### Post by bishop9226 on 2007-06-03
got my broadcom working nicely on my e1505 but now im trying to get it so i dont have to keep entering in the keyring pw each time i connect

i followed this guide:

[http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html)

---
To accomplish this we have to install a package and modify a file. Lets open the Terminal to do it (Applications -> Accessories -> Terminal).
> 
# to install libpam-keyring enter
user@host:~$ sudo apt-get install libpam-keyring
# and to modify the gdm login file do
user@host:~$ sudo gedit /etc/pam.d/gdm

Now the texteditor gedit will open with a file. To the end of the file append the following three lines:

> # use session pw for gnome-keyring
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

Now save it and close gedit. That is it. You will never be asked the keyring password again.
---

i made sure my keyring pw is the same as my login pw too.  yet it still makes me enter it everytime i initially connect to my wifi.  anyone have a soln?

---

### Post by psyke83 on 2007-06-03
Hi,

Is it not easier to append the following to /etc/pam.d/gdm?

```
@include common-pamkeyring
```

The provided documentation suggests adding the above line, not what you wrote.

---

### Post by bishop9226 on 2007-06-03
uhhhhh where does it say that?

seriously i think you are looking at the wrong article 

[http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html)

---

### Post by Dougie187 on 2007-06-03
Ive never tried it. I will give it a shot and let you know if it works for me.

---

### Post by bishop9226 on 2007-06-03
i wanna know where he got that line from. it isnt in the link i have.  though ive seen other ppl suggest it.  mine didnt work so i guess ill try replacing it with that.

---

### Post by Dougie187 on 2007-06-03
Maybe its in the pamkeyring documentation.

---

### Post by bishop9226 on 2007-06-03
maybe i should read instruction manuals:P

---

### Post by bishop9226 on 2007-06-03
BAH neither works for me.

---

### Post by Dougie187 on 2007-06-03
Well i tried both, and the first one didnt work for me but ```
@include common-pamkeyring
``` worked fine. just add it to the bottom of your /etc/pam.d/gdm file. Make sure you clear our all the stuff you added from that other guide. Very cool though, i didn't think you could do this.

---

### Post by bishop9226 on 2007-06-03
is that all you did?! i tried that, i tried the other one from the other guide, and then another guide that says how to do it on edgy.  NOTHING WORKS FOR ME!!!!

---

### Post by bishop9226 on 2007-06-03
do you also have auto login enabled?

---

### Post by bishop9226 on 2007-06-03
weird ok i turned off autologin and now it works..

---

### Post by Dougie187 on 2007-06-03
All i did (starting from before you begin the guide) was
```
sudo apt-get install libpam-keyring
sudo vim /etc/pam.d/gdm
```
and add
```
@include common-pamkeyring
```
to the end. Then when i rebooted i was not asked for my keyring pw. I didnt set up any auto-login or anything.

---

### Post by Dougie187 on 2007-06-03
Glad it works now! :)

---

### Post by bishop9226 on 2007-06-03
well i was hoping i could have the best of both worlds - autologin AND no having to enter keyring manager:)

but id rather have my autologin because entering the keyring is only 1 step whereas logging in takes 2

---

### Post by Dougie187 on 2007-06-03
heh sounds good. Id rather have my keyring because i like having to authenticate myself to log into my computer (then my family cant log in as me) But it sould know that once i log in i can use the wireless...

---

### Post by bishop9226 on 2007-06-03
true true

---

### Post by ph1zzle on 2007-06-27
I am no pam pro but to the best of my knowledge auto login does not authenticate you with pam therefor there is no pam credentials in your envonment to be passed to nm / nm-applet. Again not my area of expertise but I am still pretty sure.

---

### Post by Martin Witte on 2007-06-28
thanks, this one works for me

---

### Post by markp1989 on 2007-10-24
> **bishop9226 said:**
> is that all you did?! i tried that, i tried the other one from the other guide, and then another guide that says how to do it on edgy.  NOTHING WORKS FOR ME!!!!

im in the same boat

---

### Post by rulsky on 2007-10-26
I tried this and it worked...... disable network roaming

In network settings click "wireless connections" UNCHECK roaming mode, enter your wireless settings AND ENJOY.....

The network will start automatically without asking for the password.

:popcorn:

---

### Post by calraith on 2008-06-25
Sorry to revive an old thread, but I thought someone might find this useful.  I have autologin enabled *and* my wifi autoconnects without bugging me for a password.  The way I did this was to get rid of gnome-network-manager altogether, and use [wicd]("http://wicd.sourceforge.net/download.php") instead.

```
echo "deb http://apt.wicd.net hardy extras" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wicd
```When wicd is installed, gnome-network-manager will automatically be uninstalled.  After installation is finished, go to System --> Preferences --> Session in the Ubuntu menu, and add a startup entry for /opt/wicd/tray.py .

After a reboot (I'm not sure whether a reboot is necessary, but it can't hurt), single-left-click on the new tray icon to open the Wicd Manager.  Click Preferences.

Choose the WPA supplicant driver appropriate for your system (or if you don't know, just try them one at a time until you find one that works).  Enter your wifi interface into the Wireless Interface field (I'd guess ath0 for madwifi or wifi0 for any other driver), and hit OK.

Hit Refresh and you should see your wireless network.  If not, go back to the previous step and try another WPA driver.  If none of the drivers allows you to detect wireless networks, make sure you haven't accidentally turned off your wireless radio.  On laptops, there's usually either a physical sliding switch on the side or front, or a key combination such as the blue Fn key + F2 or Fn + whatever button has a wireless tower logo.

After the initial setup of your wireless interface in wicd, the rest is pretty intuitive.  Wicd will remember whatever passwords / keys you configure.  It is also more intuitive than gnome-network-manager to join 802.1x networks, which a lot of schools use.

---

### Post by mriedel on 2008-07-11
I'll probably do that too. Since there seems no way to authenticate to gnome-keyring-manager with PAM(_usb) I'm left without a choice...

---

