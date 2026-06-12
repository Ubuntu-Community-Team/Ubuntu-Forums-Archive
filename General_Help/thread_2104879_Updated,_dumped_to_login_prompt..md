---
title: "Updated, dumped to login prompt."
date: 2013-01-14
forum: General Help
---

### Post by Grim944 on 2013-01-14
I am running 64 bit 12.04 LTS, and the update manager showed there was some needed updated.  So I updated and rebooted.  Computer booted into Grub fine, I selected Ubuntu, got the splash screen for a second then was at the black screen with the login prompt and it will not accept my login information.  It says it is incorrect.

I am very new to Ubuntu, and Linux.  I have only been using it consistently about a month.  Everything was was working fine before the update.

---

### Post by hydn79 on 2013-01-14
You may have to use a rescue CD/USB and reset the root or login user password. If its refusing your password 99% of the times its because its incorrect.

---

### Post by Grim944 on 2013-01-14
> **hydn79 said:**
> You may have to use a rescue CD/USB and reset the root or login user password. If its refusing your password 99% of the times its because its incorrect.

Thanks that got the login issue fixed, but now I'm still in the terminal.  Time to start searching for this.

---

### Post by d4m1r on 2013-01-14
I had a similar issue once...Few things to try:

1) Restart the PC.

2) If that doesn't work, restart/reinstall "LightDM" which is the login manager used in Ubuntu 12.04.

3) If that doesn't work, restart/reinstall "gdm" or "unity" which is the desktop interface.

Google around on how to accomplish #2 or #3 completely/fully.

---

### Post by Grim944 on 2013-01-14
> **d4m1r said:**
> I had a similar issue once...Few things to try:

1) Restart the PC.

2) If that doesn't work, restart/reinstall "LightDM" which is the login manager used in Ubuntu 12.04.

3) If that doesn't work, restart/reinstall "gdm" or "unity" which is the desktop interface.

Google around on how to accomplish #2 or #3 completely/fully.

Tried all these and still no luck.  I have tried using the startx command and the computer just hangs.  I get the same result with ALT+F7.  Although with ALT+F7 I can use Ctrl+Alt+Del to restart instead of a hard shutdown.

---

### Post by linuxcoffeelover on 2013-01-14
Does tty7 show the login screen or is it only a login prompt?

---

### Post by Grim944 on 2013-01-14
> **linuxcoffeelover said:**
> Does tty7 show the login screen or is it only a login prompt?
It is just a login prompt.  Same thing you see if you press Ctrl+Alt+F1.

Edit:  On a properly working computer.

---

### Post by linuxcoffeelover on 2013-01-14
Oh ok so your stuck at the console. 
ok I think I found something on try running this command and see if this helps.

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Grim944 on 2013-01-14
> **linuxcoffeelover said:**
> Oh ok so your stuck at the console. 
ok I think I found something on try running this command and see if this helps.

```
 sudo dpkg-reconfigure xserver-xorg
```

No luck with that.  I found a guide that I have tried a bunch of things on.  

[http://journalxtra.com/computer-advice/getting-your-desktop-back-the-almost-definitive-guide-3723/](http://journalxtra.com/computer-advice/getting-your-desktop-back-the-almost-definitive-guide-3723/)

Although, none have worked so far.  I have seen many posts similar to my problem that are related to a video driver.  Any thoughts?

---

### Post by linuxcoffeelover on 2013-01-14
I had found this: 

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

It could be a problem with your .XAuthority  file. I had that a while ago no desktop when I logged in I was dumped back to the console I made a new user or when to guest and I could get to the desktop but I couldn't run any commands or scripts, but I could get to the form and found a post that had the same problem I ran some commands after trying updates and other things. and a couple commands later I have the desktop again.

---

### Post by linuxcoffeelover on 2013-01-14
What had happened to me was the root account had taken possession of the .Xauthority   file and I couldn't log in with the gui.

---

### Post by Grim944 on 2013-01-14
> **linuxcoffeelover said:**
> I had found this: 

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

It could be a problem with your .XAuthority  file. I had that a while ago no desktop when I logged in I was dumped back to the console I made a new user or when to guest and I could get to the desktop but I couldn't run any commands or scripts, but I could get to the form and found a post that had the same problem I ran some commands after trying updates and other things. and a couple commands later I have the desktop again.

In that link it says when you reconfigure xserver it will ask you some questions.  It doesn't do that for me.  There is a slight pause then a fresh command line.

---

### Post by linuxcoffeelover on 2013-01-14
OK sorry it must be still one. 

[http://ubuntuforums.org/archive/index.php/t-952875.html](http://ubuntuforums.org/archive/index.php/t-952875.html)


[]("http://ubuntuforums.org/archive/index.php/t-952875.html")[]("http://ubuntuforums.org/archive/index.php/t-952875.html")

---

### Post by linuxcoffeelover on 2013-01-14
sorry looks like those commands will only work when usding the terminal emulators like gnome-terminal or xterm.

what do you get when you type:  

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Grim944 on 2013-01-14
> **linuxcoffeelover said:**
> sorry looks like those commands will only work when usding the terminal emulators like gnome-terminal or xterm.

what do you get when you type:  

```
sudo apt-get install ubuntu-desktop
```

I tried that a earlier today.  It didn't make any difference.  

I'm going to just reinstall.  I have learned a lot today, but I do not have time to keep troubleshooting this week.

Thanks for the help.  I hope reinstalling fixes it.

---

### Post by linuxcoffeelover on 2013-01-14
OK your welcome yeah that's what I learned from the .Xauthority hell is if you can't get to the gui in 30 minutes it's best to just reinstall. well good luck.

---

### Post by Kinetos on 2013-01-15
Hey, if you didn't reinstall yet I have a few ideas, first of all, what kind of video card are you using? I was using nvidia and it turned out that my computer was trying to run nvidia-experimental-310 when the kernel needed nvidia-experimental-304, so I purged nvidia-experimental-310 and when I rebooted I got to a graphical login screen but I still can't log in to any user except root.  I'll let you know if I figure it out.  If you already reinstalled I hope it all works fine now.

---

### Post by Grim944 on 2013-01-15
> **Kinetos said:**
> Hey, if you didn't reinstall yet I have a few ideas, first of all, what kind of video card are you using? I was using nvidia and it turned out that my computer was trying to run nvidia-experimental-310 when the kernel needed nvidia-experimental-304, so I purged nvidia-experimental-310 and when I rebooted I got to a graphical login screen but I still can't log in to any user except root.  I'll let you know if I figure it out.  If you already reinstalled I hope it all works fine now.

I am running an AMD card. I did update to the AMD drivers, but I tried to purge them and go back to the basic driver. That didn't help either. 


I did end up reinstalling. Everything is running fine now.

---

