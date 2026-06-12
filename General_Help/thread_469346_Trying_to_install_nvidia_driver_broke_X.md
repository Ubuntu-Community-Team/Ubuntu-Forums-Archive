---
title: "Trying to install nvidia driver broke X"
date: 2007-06-09
forum: General Help
---

### Post by Digitallysick on 2007-06-09
I have had alot of problems with beryl freezes, so i decided to install the latest nvidia driver, and totally remove beryl and then re install it.  So i removed beryl through synaptic, i went into console and installed the new nvidia driver

sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run


then, when i reboot x crashes and says no screens found, if i go through the setup again and then type startx, it loads up just fine, when i go to exit after i do that, i dont have an "exit" button like normal, i have to sudo shutdown -r now

so how do i fix it?

---

### Post by Omnios on 2007-06-09
Hello

 [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Link about how to manually install nvidia drivers

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by CocoAUS on 2007-06-09
You're saying you just have a logout button?  That's probably because you need to start gdm instead of just starting X.  Logout, then type:
```
sudo /etc/init.d/gdm start
```

This should give you the shutdown button again.

---

### Post by Digitallysick on 2007-06-09
Ok here is the exact error im getting, its about the kernel version doesnt match

[IMG]http://i11.photobucket.com/albums/a152/digitallysick/DSC00397.jpg[/IMG]

---

### Post by rvdavid on 2007-06-12
> **Digitallysick said:**
> I have had alot of problems with beryl freezes, so i decided to install the latest nvidia driver, and totally remove beryl and then re install it.  So i removed beryl through synaptic, i went into console and installed the new nvidia driver

sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run


then, when i reboot x crashes and says no screens found, if i go through the setup again and then type startx, it loads up just fine, when i go to exit after i do that, i dont have an "exit" button like normal, i have to sudo shutdown -r now

so how do i fix it?

I have the same problem (though I am using Xubuntu) X crashes with "no screens found" after restart. I have to reinstall drivers every time and restart gdm.

I use the same drivers for Kubuntu (my main desktop os), and don't have any issues whatsoever. 

btw to get logout/shutdown/restart buttons, you'd actually have to restart GDM instead of just starting X. 

```


$ sudo /etc/init.d/gdm restart


```

HTH. 

Regards, 


R. Villar David

---

### Post by rvdavid on 2007-06-13
> **rvdavid said:**
> 
I use the same drivers for Kubuntu (my main desktop os), and don't have any issues whatsoever. 


Err... lemme just retract that. After running the last dist-upgrade... it's happening to kubuntu as well... 

Must be with the latest kernel upgrade. 

hmm. Anyone else experiencing this? more importantly, anyone have a solution?


Thank you in advance. 

Regards,

R. Villar David

---

### Post by Citizin on 2007-06-13
Im having the same kind of problem over here: [http://ubuntuforums.org/showthread.php?p=2834095&posted=1#post2834095](http://ubuntuforums.org/showthread.php?p=2834095&posted=1#post2834095)

we should all try to find a solution to this, I've been spending all night just trying to get a video card to work with linux, now its been good to me up to this point, but im running out of pateince.

---

### Post by rvdavid on 2007-06-13
Hi, 

I'd like to help you out if I could, but I thnk your problem is a little different to what we are experiencing over here. 

You can't get your computer running with your video card, as in it hangs... whereas ours work fine. It's just that we have to keep reinstalling the drivers. 

Regards,

---

### Post by Digitallysick on 2007-06-13
I finally gave up and just reformatted ubuntu, and reinstalled =( *wont touch the drivers again*

---

### Post by rvdavid on 2007-06-15
Hmmm well my issue has been resolved with nvidia drivers on kubuntu. All I had to do was install nvidial-glx-new instead of nvidia-glx. 

```

$ sudo aptitude install nvidia-glx-new 

```

Although I don't know if this would be related whatsoever, but I modprobed nvidia also prior to installation 

```

$ sudo modprobe nvidia 

```

One or both of these actions seem to have solved my problem.  

HTH.

Regards,

---

### Post by steevc on 2007-06-16
I've been struggling with nvidia too. I tried using Envy. That installed loads of stuff, but didn't change my xorg.conf or give me the option to select the nvidia driver, so I was stuck with nv and no GLX.

I've installed nvidia-glx and done sudo nvidia-glx-config enable, but I can't load the module:

```
$ sudo modprobe nvidia
FATAL: Could not open '/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko': No such file or directory
```

So what should be installing the nvidia.ko file? I have one in /usr/src/modules/nvidia-kernel/nv/nvidia.ko for some reason, but I can't be sure it's the right version.

I'm using the on-board graphics on an Asus M2npv-vm, ie GeForce 6150.

There do seem to be a lot of people having problems in this area. I've run the nvidia drivers on previous versions of Ubuntu, but Feisty seems to make it harder work.

Update: Fixed as detailed at

[http://ubuntuforums.org/showpost.php?p=2868582&postcount=118](http://ubuntuforums.org/showpost.php?p=2868582&postcount=118)

---

