---
title: "Startx get black screen after install Nvidia Driver, but lightdm is working fine"
date: 2016-04-04
forum: General Help
---

### Post by sail3 on 2016-04-04
Hi , I'm a new guy for linux&Ubuntu, In my case, i need to launch ubuntu to text mode and run startx in the end of rc.local. Here is my computer's infomation : 
2 VGAs: intel ghrapic and Nvidia GT750M
Ubuntu 14.04.3 

I can run startx before I install Nvidia driver.

After I installed the Nvidia driver by doing : sudo apt-get install nvidia-352,  the startx leads me to a totally black screen. When i tap ctl+alt+t and input "sudo reboot", the system rebooted. So it seems that the system is working only with no gui. I also try to run lightdm by input : sudo service lightdm start, it can start the login window, and I comfirmed that the graphics is working  by cheking SystemSettings->Details. So I guess that I'm not missing any package but some configuration is not correct, because the lightdm is working. am I right? and can any body give me some suggestion, thank you.

Attachment is the Xorg.0.log after startx.

---

### Post by v3.xx on 2016-04-04
Hi sail3

Its possible to boot to text using grub.

[http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

For startx I create a xinitrc file to boot.

[https://wiki.archlinux.org/index.php/xinitrc#Making_a_DE.2FWM_choice](https://wiki.archlinux.org/index.php/xinitrc#Making_a_DE.2FWM_choice)

---

### Post by deadflowr on 2016-04-04
Moved to [B]General Help
[/B]

---

### Post by SeijiSensei on 2016-04-05
Did you run "sudo nvidia-xconfig" after installing the driver?  If not, give that a try.

---

### Post by sail3 on 2016-04-06
Hi SeijiSensei, I've tried to run nvidia-xconfig, and it generate the xorg.conf in /etc/X11, then i run startx in text mode ,still get the blackscreen. It seems that all applications is work but no GUI, because when I press ctl+alt+T, and input sudo reboot, the PC rebooted....

---

### Post by sail3 on 2016-04-06
Hi, Thanks a lot for the advice, but it still not work. here is my situation:
1. Install new Ubuntu 14.04.3
2. Modify the grub and launch into text mode and run : sudo startx.   
3. I can see a background image, and I can press ctl+alt+T to open the terminal.


3. Install nvidia driver : sudo apt-get install nvidia-352.
4. do step 2 , and I got a totally black screen.  But it seems that all applications is work but no GUI, because when I press ctl+alt+T, and input sudo reboot, the PC rebooted.... 

So I guess maybe there is some problem with the nvidia driver, Then i try to run : sudo service lightdm start. And it works.
Now I'm here...  The only diffirence is I installed the nvidia driver....but lightdm is work, which proved that the driver has no problem. But why startx has no GUI :(

---

### Post by Bashing-om on 2016-04-06
sail3; Ouch !

1st off with the default install of ubuntu one gets lightdm as the display manager, The call to 'startx' is not in the 'lighrdm' startup process. In the event that you did " 2. Modify the grub and launch into text mode and run :[color=red] sudo startx[/color]. " The permissions and access rights to "your" /home no longer belong to 'you' but to 'root' .
show :
```

ls -al .ICEauthority
ls -al .Xauthority
ls -al /home/
ls -al /home/<username>/

```
we see what it is going to take to get your access rights restored .
The command to start lightdm (GUI) in this instance is:
```

sudo service lightdm start

```

Once we have the rights restored, we look at what the driver situation is. Maybe all is good, just that "you" do not presently have access rights to the desktop .

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2016-04-06
Hey Bashing :D

@OP
Point startx at your desktop.

Thats all folks, your in good hands.

---

### Post by sail3 on 2016-04-10
Hi Bashing
 Thanks a lot for your advise, I've tried to set the root's password(sudo passwd root) and login with root user, but it still not solve the issue. Besides, I think it's not the problem of access rights, because startx works fine before I install the nvidia driver. I think lightdm did some thing with the driver before it start the window, But I'm not sure where to start to do the research :( 
> **Bashing-om said:**
> sail3; Ouch !

1st off with the default install of ubuntu one gets lightdm as the display manager, The call to 'startx' is not in the 'lighrdm' startup process. In the event that you did " 2. Modify the grub and launch into text mode and run :[COLOR=red] sudo startx[/COLOR]. " The permissions and access rights to "your" /home no longer belong to 'you' but to 'root' .
show :
```

ls -al .ICEauthority
ls -al .Xauthority
ls -al /home/
ls -al /home/<username>/

```
we see what it is going to take to get your access rights restored .
The command to start lightdm (GUI) in this instance is:
```

sudo service lightdm start

```

Once we have the rights restored, we look at what the driver situation is. Maybe all is good, just that "you" do not presently have access rights to the desktop .
[INDENT][INDENT]maybe Yes[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

