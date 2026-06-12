---
title: "EasyCam2 gnome.ui error"
date: 2006-11-19
forum: General Help
---

### Post by oliwally on 2006-11-19
I've installed EasyCam2 in Kubuntu 6.10 but I'm getting an error when running it:
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  File "/usr/share/EasyCam2/easycam.py", line 25, in ?
    import gnome.ui
ImportError: No module named gnome.ui


```

I'm assuming that I'm missing something. What do I need to install?

---

### Post by oliwally on 2006-11-20
Can anyone help with this gnome.ui error?

---

### Post by oliwally on 2006-11-22
bumb :-k

---

### Post by oliwally on 2006-11-23
Is there nobody who may know how to fix this? Please help me.

---

### Post by oliwally on 2006-11-26
> **oliwally said:**
> I've installed EasyCam2 in Kubuntu 6.10 but I'm getting an error when running it:
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  File "/usr/share/EasyCam2/easycam.py", line 25, in ?
    import gnome.ui
ImportError: No module named gnome.ui


```

I'm assuming that I'm missing something. What do I need to install?

I'm still hoping for some help with this problem please.

---

### Post by junglepeanut on 2006-11-26
Is it working otherwise? I think those errors refer to not having your xorg.conf set up exactly right. Maybe you wacom enabled but dont have it or something of that nature. So it might just be saying hay you dont have this but otherwise it is functioning fine. 

If it is not working, then it actually might be for a seperate reason. Here is the bug, there is a fix in the reading but it only works for some. Not me, it also has to do with what tpye of webcam you have, and is edgy + specific, so your dapper worked maybe but edgy and newer wont.


[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090)

---

### Post by oliwally on 2006-11-27
> **junglepeanut said:**
> Is it working otherwise? I think those errors refer to not having your xorg.conf set up exactly right. Maybe you wacom enabled but dont have it or something of that nature. So it might just be saying hay you dont have this but otherwise it is functioning fine. 

If it is not working, then it actually might be for a seperate reason. Here is the bug, there is a fix in the reading but it only works for some. Not me, it also has to do with what tpye of webcam you have, and is edgy + specific, so your dapper worked maybe but edgy and newer wont.


[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090)

Thanks for your reply.

The webcam kind-of works but the EasyCam2 application doesn't. I certainly get a picture but it's low fps and colour and resolution are of poorer quality than in windows.

The real problem I wanted to solve in this thread is to make the EasyCam2 application run. I was hoping to configure the camera using this utility - but it won't run - I get a sudo type login (gui) and then nix.

---

### Post by oliwally on 2006-11-28
Help please

---

### Post by junglepeanut on 2006-11-29
How are you launching it?

launchcam2?

easycam2?

camorama?

Also look through these pages, one has a lot of french but there is english spread through out. 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[http://forum.ubuntu-fr.org/viewtopic.php?id=16670&p=57](http://forum.ubuntu-fr.org/viewtopic.php?id=16670&p=57)

I always thought easycam2 just installed the drivers. And the gui let you click from a list of cameras.if you wanted a specific driver i.e. for my camera I just installed easycam2 and then said camorama and it worked. I adjust my settings in camorama.

Havent done it in a while so I dont remember if camorama has fps options. But I know many messaging programs can control the fps. If your not sending it should near perfect.

Let me know if you have already looked through all those pages. Lastly you never stated what camera you have? Is it covered by the drivers even?

Have you tried reinstalling easycam2? Where are you downloading it from?

A little more info and maybe we can get this running.

---

### Post by akshaysrinivasan on 2006-11-29
I got my webcam working in Dapper right away without installing Easy cam,which i had to do for breezy

---

### Post by oliwally on 2006-11-30
> **junglepeanut said:**
> How are you launching it?

launchcam2?

easycam2?

camorama?

Also look through these pages, one has a lot of french but there is english spread through out. 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[http://forum.ubuntu-fr.org/viewtopic.php?id=16670&p=57](http://forum.ubuntu-fr.org/viewtopic.php?id=16670&p=57)

I always thought easycam2 just installed the drivers. And the gui let you click from a list of cameras.if you wanted a specific driver i.e. for my camera I just installed easycam2 and then said camorama and it worked. I adjust my settings in camorama.

Havent done it in a while so I dont remember if camorama has fps options. But I know many messaging programs can control the fps. If your not sending it should near perfect.

Let me know if you have already looked through all those pages. Lastly you never stated what camera you have? Is it covered by the drivers even?

Have you tried reinstalling easycam2? Where are you downloading it from?

A little more info and maybe we can get this running.

Thank you so much for replying. I'll answer the questions one by one.

To launch EasyCam2 I use the button that has been set up through the installation in the Kmenu. Essentially this executes a 'launchcam2' command. A SU login screen window comes up, and after entering the password nothing happens. When launching from a terminal (sudo launchcam2), the error listed in my first post comes up.

Camorama is installed and works (launch through Kmenu) and I get a picture with my webcam, but it's low fps and resolution without trying to send images (ie all local), with no option to adjust. VLC player also lets me see the image with the same quality. 

I can't get Skype to recognize the camera - no option? Plugin needed?

I have seen one of the links you suggested. That's where I found easycam installation instructions ([https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam))

I was hoping that easycam2 would give me the option to configure the camera settings. 

The camera I have is a Logitech QickCam for notebooks deluxe.

I haven't tried reinstalling yet - will do in a few minutes.

I'm a little worried that my camera may not (yet) be supported. Found info at [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) to suggest that this may be so, although my exact camera is not listed.

Thanks again for your willingness to help. Please be patient with me.

---

### Post by junglepeanut on 2006-12-01
I have two logitech quickcams and have been able to get both of them up, one was a notebook (almost a year old..maybe two) the other is a pro 4000. The notebook one is at home in Denmark, so I can not check that one right now. But I will reinstall my stuff and see if I get any errors similar to yours.

---

### Post by oliwally on 2006-12-05
> **junglepeanut said:**
> I have two logitech quickcams and have been able to get both of them up, one was a notebook (almost a year old..maybe two) the other is a pro 4000. The notebook one is at home in Denmark, so I can not check that one right now. But I will reinstall my stuff and see if I get any errors similar to yours.

Thanks, that would be great.

I've got the camera working - the image is just not very good quality.

---

### Post by lucia_engel on 2006-12-23
I got the same error. It was fixed after I installed python-gnome2. I have a base installation of edgy with fluxbox.

---

