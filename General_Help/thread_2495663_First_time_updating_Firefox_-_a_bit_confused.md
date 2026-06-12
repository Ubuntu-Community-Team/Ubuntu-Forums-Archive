---
title: "First time updating Firefox - a bit confused"
date: 2024-02-26
forum: General Help
---

### Post by nowindows2 on 2024-02-26
Hey everyone - hope you're all doing well.

I switched to Linux a while back and everything went smoothly - it was a minimal install and I only added Gimp and Gnumeric to that install. Firefox is the only browser, and it's apparently never updated (up to v122, I'm at v99). 

I'm a bit confused which would be the best way to update FF manually.  

I found this thread from 2022-  
[https://ubuntuforums.org/showthread.php?t=2475872&highlight=firefox+update](https://ubuntuforums.org/showthread.php?t=2475872&highlight=firefox+update)

I also found this more recent thread, but that made me even more confused!
[https://ubuntuforums.org/showthread.php?t=2494912&highlight=update+firefox](https://ubuntuforums.org/showthread.php?t=2494912&highlight=update+firefox)

Any suggestions appreciated and thanks in advance for your help!


[https://ubuntuforums.org/showthread.php?t=2475872](https://ubuntuforums.org/showthread.php?t=2475872)
[https://askubuntu.com/questions/1395545/is-adding-a-ppa-safe](https://askubuntu.com/questions/1395545/is-adding-a-ppa-safe)

---

### Post by grahammechanical on 2024-02-26
What version of Ubuntu are you using? And how did you get that minimal install? How did you install Firefox?

If you used this command

```
sudo apt install firefox
```

then Firefox was installed from the Ubuntu repositories and would be updated with the usual apt update and apt upgrade commands. That version of Firefox would be packaged in the Debian package format (deb)

There is another package format that is used by Ubuntu it is called "snap" packaging. To update a snap packaged application on a Ubuntu command line installation we run

```
sudo snap refresh
```

That will refresh (update/upgrade) all snap packaged applications on the system. To only update the Firefox snap packaged application we run

```
sudo snap refresh firefox
```

To find out what Firefox package type you have open Firefox settings and scroll down to Firefox Updates it will tell if Firefox is a deb or snap package.

Regards

---

### Post by VMC on 2024-02-26
> **nowindows2 said:**
> ...
I also found this more recent thread, but that made me even more confused!
[https://ubuntuforums.org/showthread.php?t=2494912&highlight=update+firefox](https://ubuntuforums.org/showthread.php?t=2494912&highlight=update+firefox)

Any suggestions appreciated and thanks in advance for your help!...

This link is one I created. It's for installing Firefox in the "/opt" folder.
If you don't have write privileges then you have to download Firefox and dance around reinstalling into "/opt"

I think using Snap Firefox updates automatically.

---

### Post by nowindows2 on 2024-02-26
> **grahammechanical said:**
> What version of Ubuntu are you using? 



 22.04 (Jammy Jellyfish) and FF was included with the original JJ install

I definitely didn't use any sudo commands with the install  because I had just moved from Windows7 to Ubuntu and didn't feel comfortable using the cli at that point.

I checked the FF settings and it said:

[B][I]Mozilla Firefox Snap for Ubuntu
canonical-002 - 1.0[/I][/B]

so I'll try the *** sudo snap refresh firefox ***command once I'm ready to shut down the desktop.

Thanks for your time! :cool:

---

### Post by nowindows2 on 2024-02-26
I'm going to try the previous suggestion first, then go to plan B if I can't get it to work. 

Thanks for your help.

---

### Post by grahammechanical on 2024-02-26
I was not sure if your minimal install was command line only. If we have a desktop user interface and can run Software Updater then snap packaged applications are indeed automatically updated as @VMC says.

Software Updater is a utility that runs the apt update; apt upgrade; apt autoremove & snap refresh commands. Saving us the work of typing them in the command line.

Regards

---

### Post by nowindows2 on 2024-02-26
The  ***sudo snap refresh firefox command  ***worked perfectly!! Firefox now shows v123 instead of v99.

Thanks very, very much for your help!    :P

---

