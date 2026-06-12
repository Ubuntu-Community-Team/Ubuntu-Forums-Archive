---
title: "Ubuntu crashes on Shutdown"
date: 2006-12-21
forum: General Help
---

### Post by SnoWDoGJDC on 2006-12-21
Can anyone help me with my problem, i've checked forums but no one seems to have covered this.
I'm using Ubuntu edgy on an ASUS m6va. Everything worked nicely, but after i installed the proprietary ATI drivers it crashes when i shutdown. It starts playing the ubuntu logout sound, but halfway through it the screen goes crazy (horrible mess of lines and colours) and it doesn't go any further. I don't know what causes this, the only thing i can think of is that there's still the config for the radeon driver in xorg.conf as well as the one for fglrx.
Any ideas? i'm not willing to go back to the open source ati drivers cus i need 3D accellaration (and if i can't get it i might as well go back to windows)

---

### Post by André on 2006-12-26
Hi there,

i have the same problem with Kubuntu Edgy and the open source drivers on an Inspiron 8600 with Radeon 9600.

Did you already solve the problem? For me it only happens about each fourth shutdown but i am still afraid of data losses!!

Greetings
André

---

### Post by nunomiguelmota on 2006-12-31
> **SnoWDoGJDC said:**
> Can anyone help me with my problem, i've checked forums but no one seems to have covered this.
I'm using Ubuntu edgy on an ASUS m6va. Everything worked nicely, but after i installed the proprietary ATI drivers it crashes when i shutdown. It starts playing the ubuntu logout sound, but halfway through it the screen goes crazy (horrible mess of lines and colours) and it doesn't go any further. I don't know what causes this, the only thing i can think of is that there's still the config for the radeon driver in xorg.conf as well as the one for fglrx.
Any ideas? i'm not willing to go back to the open source ati drivers cus i need 3D accellaration (and if i can't get it i might as well go back to windows)
Hi! I had the same problem on an asus a6va with the latest fglrx drivers installed, i couldn't logout or shutdown without a system freeze. After spending some time searching in the forums i have found a solution in this thread :
 
[http://www.ubuntuforums.org/showthread.php?t=294839&highlight=edgy+logout](http://www.ubuntuforums.org/showthread.php?t=294839&highlight=edgy+logout) 

you have to edit the  gdm.conf-custom file like this:

 ```
sudo gedit /etc/gdm/gdm.conf-custom
```

and add this rigth after [daemon] :

```
 AlwaysRestartServer=true
```

save the file and everything should be fine!

PS: sorry for any mess in my english, it is not my native language[

---

