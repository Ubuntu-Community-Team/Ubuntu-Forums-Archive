---
title: "Graphic issues!"
date: 2008-07-04
forum: General Help
---

### Post by Firedude88 on 2008-07-04
I have two monitors. is it possible to run linux on both without it being the same image? and if so can i keep the cube feature if i do so? I also have a problem with some of my graphic running software such as the chess application included in ubuntu. it wont run it in 3d mode stating that there is an issue with

"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support"

i have tryed installing python via the terminal but it says i already have it.  is there something im doing wrong.  I have been a linux user for all of a week now.  :-)  plz help!

---

### Post by Plasma_NZ on 2008-07-04
Ok need to know what kinda gfx card u have.. 

Have u enabled "restricted-drivers" etc..?

As for 2 monitors with cube, easy.. will get to that once u have sorted gfx drivers issue, but i will say if u have a ATi card i cannot help with drivers..

---

### Post by Firedude88 on 2008-07-04
I have a Nvidia 8600 GTS.  yes i have enable restricted drivers.  i even downloaded the drivers for linux off of the Nvidia site but couldnt figure out how to install them.

---

### Post by Plasma_NZ on 2008-07-05
Download your gfx card's driver from NVIDIA's website..

put it on your desktop..

once done that press

```

ctrl + alt + f1
```

This will throw you out of the GUI and in prompt mode... which needs to be done..

It will ask u for your username/password, enter them

Once logged in (still in prompt mode) u need to stop the GomeDisplayManager by issuing the following command

```
sudo /etc/init.d/gdm stop
```


that will stop gnomedisplaymanger so u can install the driver..

now u need to move to the directory u put the driver, which would be desktop.. to move there use

```

cd /home/you_user_name/Desktop
```

replace "your_user_name" with your user-account name u use to login

once there, u need to issue the command

If u have 64bit Ubuntu use this - presuming u have downloaded the latest drivers

```

sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run
```

If u have a 32bit Ubuntu use this

```
sudo sh NVIDIA-Linux-x86-173.14.09.pkg1.run
```

From there just follow its directions... it will try and download a module for your kernel but that will probley fail, so it'll probley compile one automatically for u, and also ask if u want to use 32bit something, just hit yes..

once it has finished and thrown u back to prompt - type

```

 startx
```

It should load, once it has open a terminal window and type

```

sudo nvidia-settings
```

this should launch the nvidia settings manager.. and change settings as u need..

Hope this helps your problem..

---

### Post by Firedude88 on 2008-07-06
i went through the steps you said.  and thank you for detailing them so well.  but i ran into an error during the nvidia installation.  like you said,  it looked for a kernal thing.  when it didnt find it it tryed to compile one.  after about 2 seconds it gave up another error.  it said that libc header files arnt there and that i need to install the libc development pack or something like that.

---

### Post by Plasma_NZ on 2008-07-06
ok.. so install them using 

```
sudo apt-get install build-essential
```

u also might want to make sure u have the source for your current kernel your using too

to find out which kernel u are running use 

```
uname -a
```

from there u will want to use 

```
sudo apt-get install linux-headers-2.6.24-19-generic 2.6.24-19.34
```

yours migth vary so change accordingly.. from there try re-installing drivers... good luck hope this helps..

---

### Post by Firedude88 on 2008-07-07
ok i have no idea what jsut happened but i did as you said.  i installed the headers and then the nvidia drivers.  it went past the error this time.  but when i went to do startx to finish the process it gave me major errors.  it said taht the kernal was at 163.  something and that the drivers where at 173.14.09...  basicaly what i got out of that is that the kernal and drivers are different.  it wouldnt let me load back to the desktop using startx.  i rebooted and after the loading bar before the login screen it stoped and told me it was running in low graphics mode.  it then gave me the option to continue configure or cancel.  i chose configure the first time and got really confused.  i chose continue the next time and now im in here with it not detecting my graphics card and monitor so im in a huge resolution and im not sure how to fix it.  sry for being lots of trouble.  but PLEASE HELP ME LOL

---

### Post by Plasma_NZ on 2008-07-07
Which Distro are u using..? is it up-to-date.?

Check your private MSG's please

---

### Post by Firedude88 on 2008-07-08
Im using Ubuntu  2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

Hardy Heron.

a Nvidia 8600GTS

i believe a AMD 5400 Duel core

2 GB of memory

---

