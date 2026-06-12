---
title: "Run command after boot"
date: 2017-12-22
forum: General Help
---

### Post by thanekrios on 2017-12-22
Hello. I'm trying to run this command at startup:

```
xgamma -gamma .85
```

I have tried editing the /etc/rc.local file, but I think I'm doing something wrong, because the command isn't running. The file looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


xgamma -gamma .85


exit 0

```

Any ideas?

Thanks a lot!

---

### Post by aromo2 on 2017-12-22
rc.local runs early in the boot process, perhaps before required services are started.

You could create a service that is invoked AFTER multiuser target is reached. Be aware, though that the program will run as root on a pseudo-terminal (you won't be able to see any output from the program).

---

### Post by #&amp;thj^% on 2017-12-22
You also could create Key Board short cuts.
This is just an example I use with xbacklight...**_So xbacklight won't work with color correction to be clear!_**
```
SUPER+Shift+plus   will exec  xbacklight -inc 10
SUPER+Shift+minus  will exec  xbacklight -dec 10
```
So I have a little more control with up and down.
There is also redshift which is what I use: [http://jonls.dk/redshift/](http://jonls.dk/redshift/)  
Just a Passing thought.

---

### Post by deadflowr on 2017-12-22
Can't you set the gamma in an xorg.conf file?

---

### Post by thanekrios on 2017-12-22
> **aromo2 said:**
> rc.local runs early in the boot process, perhaps before required services are started.

You could create a service that is invoked AFTER multiuser target is reached. Be aware, though that the program will run as root on a pseudo-terminal (you won't be able to see any output from the program).

Sounds good. How would one do that?

> **1fallen said:**
> You also could create Key Board short cuts.
This is just an example I use with xbacklight...**_So xbacklight won't work with color correction to be clear!_**
```
SUPER+Shift+plus   will exec  xbacklight -inc 10
SUPER+Shift+minus  will exec  xbacklight -dec 10
```
So I have a little more control with up and down.
There is also redshift which is what I use: [http://jonls.dk/redshift/](http://jonls.dk/redshift/)  
Just a Passing thought.

I'm confused. Where are you typing that code?

> **deadflowr said:**
> Can't you set the gamma in an xorg.conf file?

No idea. Maybe. That would be great. I read the man pages of xgamma, but it doesn't say specifically what it does.

---

### Post by #&amp;thj^% on 2017-12-25
> **thanekrios said:**
> 

I'm confused. Where are you typing that code?


The commands are on the right EG: 
```
 xbacklight -inc 10
```
Will increase the value by "10" And they are created keyboard short cuts.
Sorry been very busy the  past couple of weeks. ;)
This might be the easiest solution: (For Auto starting this value)
 I just looked at the command line options for redshift and it has the gamma functionality (plus lots of others). So, you need to add the following to the startup applications "after" you have installed redshift (It's in the ubuntu repository):
```
sudo apt install redshift
```
Then add this line to auto start: (You can call it gamma control or similar.Your Choice here)

```
/usr/bin/redshift -t 6500K:5000K -g .8:.8:.8
```
And Reboot to see the effects, and you may adjust the values to better fit your preference. (Default Values are 1.0)

---

