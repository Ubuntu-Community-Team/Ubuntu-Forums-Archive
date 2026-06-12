---
title: "Installed Compiz and beryl cant start linux"
date: 2006-11-05
forum: General Help
---

### Post by neobonzi on 2006-11-05
I'm a total newbie and made the mistake of experimenting with my x.org file to try and get compiz and beryl to work. After i rebooted after making the edits i got dumped at a prompt and a message came up saying that my X11 or something failed. Heres a mock up of what it said (i wrote down what i could).

Failed to load module fglrx
no drivers available

fatal error:
no screens found.

So i browsed the forums and figured out how to replace my x.org file with a backup i had made before. I rebooted and now it just goes to a black screen after loading. ](*,) ANY ideas?

---

### Post by highneko on 2006-11-05
Many of the tutorials you'll find are outdated. You probably want Beryl, not Compiz. Undo anything you did, and restore your backup xorg.conf file, then use the guide here; [http://wiki.beryl-project.org/](http://wiki.beryl-project.org/)

---

### Post by iamhugeinjapan on 2006-11-05
If you want to just start with a fresh xorg.conf, use this command when logged into the console:

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by neobonzi on 2006-11-05
Thanks so much for the help! This is so frustrating (i just got linux on my system ](*,) )

So i used the command to install a fresh x.org file and rebooted, and I'm still met with a black screen. This is the guide i followed - [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX")

I thought i did everything exactly - but i guess I didn't. All I really did was edit my x.org file and install a bunch of packages. yuck.

---

### Post by iamhugeinjapan on 2006-11-05
What video card do you have?

---

### Post by neobonzi on 2006-11-05
I have an ATI X1400 with 256mb memory on my e1505 dell laptop

---

### Post by iamhugeinjapan on 2006-11-05
Not all video cards are supported by AIGLX. Are you running Dapper 6.0.6 or Edgy 6.10? 

If Edgy then in theory no editing of xorg.conf would be necessary for AIGLX. If you installed Dapper packages, that may have messed things up a bit.

You might have better luck with instructions for XGL instead. It has (last time I checked) a bigger range of video card support.

---

### Post by neobonzi on 2006-11-05
I'm running Dapper 6.06 and i did everything up to before "install beryl" section in the guide because i tried to reboot. that is when i ran into all the trouble - I figured that if i restored my x.org file things would be fine but i cant figure out why the screen goes black.

Also, during load when it does all the checks and prints OK if everythings starting up fine before booting linux, right after it prints out "Configuring network interfaces [ok]" it gets really jumbled and and the graphics go kind of crazy. Idno if that means anything but it wasnt doing it before.

---

### Post by jocko on 2006-11-05
[SIZE=3]Try to run this to uninstall aiglx:
```
sudo apt-get remove xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`
sudo rm /usr/lib/xorg-air/modules/
```And undo the changes you did to /etc/gdm/gdm.conf-custom:
```
 sudo nano /etc/gdm/gdm.conf-custom
```Remove this:
[/SIZE]```
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
```

---

### Post by neobonzi on 2006-11-05
oh my gosh thank you so much! it worked perfectly - i jsut had to reinstall my video card drivers and im back to normal! 

I didnt learn my lesson though - im going to try and install it again :D I'll be a tad more careful this time.

---

### Post by jocko on 2006-11-05
I think this is the guide you should use: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

---

