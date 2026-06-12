---
title: "i need help loggong in"
date: 2007-07-26
forum: General Help
---

### Post by perfect_circle on 2007-07-26
i changed my root directory from /home/johnwehadababyitsaboy  to /home/helacus to save time.. but when i rebooted it said that the drive couldnt be recognized. and i can no longer log in, accept in in the safe terminal mode.  any idea how i can change it back in the terminal? thanks, and remember im a noob. thanks.

---

### Post by heimo on 2007-07-26
> **perfect_circle said:**
> i changed my root directory from /home/johnwehadababyitsaboy  to /home/helacus to save time.. but when i rebooted it said that the drive couldnt be recognized. and i can no longer log in, accept in in the safe terminal mode.  any idea how i can change it back in the terminal? thanks, and remember im a noob. thanks.

How did you do that? Did you just rename your homedirectory?

---

### Post by kuja on 2007-07-26
And assuming you did just rename the home directory, you'll need to ```
sudo usermod -d /home/helacus
```

---

### Post by dougfractal on 2007-07-26
> **perfect_circle said:**
> i changed my root directory from /home/johnwehadababyitsaboy  to /home/helacus to save time.. but when i rebooted it said that the drive couldnt be recognized. and i can no longer log in, accept in in the safe terminal mode.  any idea how i can change it back in the terminal? thanks, and remember im a noob. thanks.

[ctrl]+[alt]+[f1]
login
sudo mv /home/helacus /home/johnwehadababyitsaboy
[ctrl]+[alt]+[f7]

>system>administaration>users>
create new user "helacus"
> user prev> admin
 > advanced > user id > "1000"      #check same as johnwehadababyitsaboy
> manage groups>helacus>properties>  group id > "1000"      #check same as johnwehadababyitsaboy

```
sudo rm -r /home/helacus                                                       # clear new home folder
sudo mv /home/johnwehadababyitsaboy /home/helacus                 # rename folder
sudo ln -s  /home/helacus  /home/johnwehadababyitsaboy  # create a link
```

---

### Post by perfect_circle on 2007-07-27
> **dougfractal said:**
> [ctrl]+[alt]+[f1]
login
sudo mv /home/helacus /home/johnwehadababyitsaboy
[ctrl]+[alt]+[f7]

>system>administaration>users>
create new user "helacus"
> user prev> admin
 > advanced > user id > "1000"      #check same as johnwehadababyitsaboy
> manage groups>helacus>properties>  group id > "1000"      #check same as johnwehadababyitsaboy

```
sudo rm -r /home/helacus                                                       # clear new home folder
sudo mv /home/johnwehadababyitsaboy /home/helacus                 # rename folder
sudo ln -s  /home/helacus  /home/johnwehadababyitsaboy  # create a link
```

thanks, im logged in now. but what user does this make me? im trying to install a program, and it gave me an error and i have no idea what to do with it.  its a text to speech engine. and i tried opening it, and i got this.

cody@lappy486:/home/johnwehadababyitsaboy/Desktop$ sudo ./amy.tar./amy.tar: 1: Cepstral_Amy_i386-linux_4.2.0/0040775000174700473520000000000010576304412015646: not found
./amy.tar: 13: Cepstral_Amy_i386-linux_4.2.0/voices/Amy/settings.txt0100664000174700473520000000072210576304342022265: not found
./amy.tar: 30: Cepstral_Amy_i386-linux_4.2.0/voices/Amy/voice.idx0100664000174700473520003020244010576304345021506: not found
./amy.tar: 31: 9: not found
[: 32: missing ]
./amy.tar: 33: /home/helacus: Permission denied
./amy.tar: 34: &#65533;: not found
./amy.tar: 35: &#65533;: not found
./amy.tar: 36: &#65533;: not found
./amy.tar: 37: Syntax error: "|" unexpected

now im using johnwehadababyitaboy, but it shows the file saved in helacus, im thnking this is where the syntax error is coming from but i have no idea how to correct it.  thanks again in advance.

---

### Post by ev5unleash1 on 2007-07-27
You wouldent of done that, going into users and groups is an easy name change no doing anything toe the Root file system. That's why they only let you view the files on there.

---

### Post by perfect_circle on 2007-07-27
ok,new problem. i ran aprogram to configure my monitor because my resolution was off, and i rebooted and now its telling me.  

failed to start X server (your graphical interface). it is likely that it is not set up correctly. would you like to view the x server output to diagnose the problem?
yes

(ww) 1740: no matching devoce section for instance (busId PCI:0:21)found
(EE) no device detected

---

### Post by dougfractal on 2007-07-27
> **ev5unleash1 said:**
> You wouldent of done that, going into users and groups is an easy name change no doing anything toe the Root file system. That's why they only let you view the files on there.

I wish i thought of that.

> **perfect_circle said:**
> ok,new problem. i ran aprogram to configure my monitor because my resolution was off, and i rebooted and now its telling me.  

failed to start X server (your graphical interface). it is likely that it is not set up correctly. would you like to view the x server output to diagnose the problem?
yes

(ww) 1740: no matching devoce section for instance (busId PCI:0:21)found
(EE) no device detected


from /etc/X11/xorg.conf
>  If you have edited this file but would like it to be automatically updated again, run the following command:
sudo dpkg-reconfigure -phigh xserver-xorg

I don't know what model your graphics card is, but I find ,if its nvidia, when nvidia is enabled from >system>admin>restricted_driver_manager  the monitor is better.

---

### Post by perfect_circle on 2007-07-27
> **dougfractal said:**
> I wish i thought of that.




from /etc/X11/xorg.conf


I don't know what model your graphics card is, but I find ,if its nvidia, when nvidia is enabled from >system>admin>restricted_driver_manager  the monitor is better.

ok, im not exactly sure how to do this, i tried and i was not succesful. so i probably did it wrong.so how exactly should i perform this? or something else that will help me.

---

### Post by dougfractal on 2007-07-28
> **perfect_circle said:**
> ok, im not exactly sure how to do this, i tried and i was not succesful. so i probably did it wrong.so how exactly should i perform this? or something else that will help me.

What card do you have? 

From the menu 
>system>administration>restricted_driver_manager 

or terminal
sudo /usr/bin/restricted-manager


This is only for ati / nvidia drivers other wise you may have a monitor settings issue.

---

### Post by perfect_circle on 2007-07-28
> **dougfractal said:**
> What card do you have? 

From the menu 
>system>administration>restricted_driver_manager 

or terminal
sudo /usr/bin/restricted-manager


This is only for ati / nvidia drivers other wise you may have a monitor settings issue.

how do i identify my monitor setting issue? any tips? because that didnt work..

is there anyway i can just defere to the default setting?

---

### Post by dougfractal on 2007-07-28
> **perfect_circle said:**
> how do i identify my monitor setting issue? any tips? because that didnt work..

is there anyway i can just defere to the default setting?

I'm not sure what the problem is. > i ran a program to configure my monitor because my resolution was off,




example of  monitor settings in the xorg.conf
> Section "Monitor"
    Identifier     "TV"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Google search or otherwise find the spec for your monitor Scan Rate (Horizontal): XX kHz ~ XX kHz
Scan Rate (Vertical): XX Hz ~ XX Hz (**Must be correct values**)
and edit the HorizSync    &  VertRefresh in the xorg.conf.
```
sudo gedit /etc/X11/xorg.conf
```

Resolution Problems : [http://ubuntuforums.org/showthread.php?t=505818](http://ubuntuforums.org/showthread.php?t=505818)

---

