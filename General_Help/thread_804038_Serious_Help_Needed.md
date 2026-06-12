---
title: "Serious Help Needed"
date: 2008-05-22
forum: General Help
---

### Post by thehereaway on 2008-05-22
So today i downloaded Real Player 11 after needing to access a file type i couldnt convert. Installing Real Player completley messed up my sound quality, for example Amarok sounded utter ****, distorted and fuzzy on my new speakers...anyways after hours and hours of trying to firstly remove Real Player thanks to the help of someone on here, and then fiddling around with stuff i had read on here to try fix my audio problem NOTHING worked.

At this point i was fed up, so i thought 'ill just grab my Ubuntu 7.10 live CD and re-install ubuntu.' because my pc is a mess, i have no idea what im doing with this OS so undoubtadly files are all over the place so a clean slate would be nice. So i transfered all my files onto my brothers PC via our network (some files were lost unfortunatley)

Anyways, here is my dilemma...The Live CD was asking for a username and password, and i couldnt remember what it was or if i had to have one when i first installed. After numerous attempts i just gave up and figured id just wait till tomorrow and try and sort the sound problem another way. However, now when i start up my computer (without the live disk) i get command line log in instead of the normal log in screen?! 

if anyone knows how to get the graphics back it would be a big help, then afterward if anyone has any tips on sorting my sound out it would be massively appreciated.

Thanks
-Darren

---

### Post by anindya_m on 2008-05-22
Hi. Can you post your /var/log/Xorg.0.log and /etc/X11/xorg.conf?

---

### Post by thehereaway on 2008-05-22
i've honestly no idea what that means or how i would go about finding it

---

### Post by anindya_m on 2008-05-22
These are two files on your system, and I have given the full directory path so you can easily find it. These files have the X server configuration and logs.

---

### Post by thehereaway on 2008-05-22
yeah but i dont know how i would copy that from my pc to my brothers pc (am on his now as i dont know how to access internet from terminal).

is there not some command i can just enter that will get me my graphics back lol?

---

### Post by anindya_m on 2008-05-22
Ok try ```
sudo /etc/init.d/gdm restart
``` from the command line. You will need to enter your password.

---

### Post by thehereaway on 2008-05-23
> **anindya_m said:**
> Ok try ```
sudo /etc/init.d/gdm restart
``` from the command line. You will need to enter your password.

Hey, thanks for your help but it says 'command not found.' Any ideas?

i typed ```
sudo /etc/init.d/gdm restart
```

---

### Post by mano cazalet on 2008-05-23
maybe you have uninstalled the whole ubuntu desktop? :confused:

what happens if you try

sudo apt-get install ubuntu-desktop

---

### Post by Cap'n Skyler on 2008-05-23
if you have all the files you needed,go ahead and just re install and overwrite the old one.maybe try the 8.10 version?

---

### Post by thehereaway on 2008-05-23
> **Cap'n Skyler said:**
> if you have all the files you needed,go ahead and just re install and overwrite the old one.maybe try the 8.10 version?

i tried but the live disk was asking for a password and username

i searched some threads on this site and typed ```
startx
```which seems to have logged me in, and i can use everything. however i cant shut down the pc from within my user and if i log out, it takes me back to the terminal log in, not the gui log in. 

Also, when i logged in i had an error saying... 

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet" do you want to delete the applet from your configuration?
```

And when i logged in my sound seemed to have returned to normal which is good, so i just need to fix this log-in thing

---

### Post by anindya_m on 2008-05-25
Can you boot from the hard disk without using the live cd? If you can and it gives a command prompt, you should run the install and gdm startup commands from there, not from within the live cd environment.

---

