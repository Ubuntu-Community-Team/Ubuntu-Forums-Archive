---
title: "My Menu launcher disappeared  ubuntu 14.04"
date: 2014-08-09
forum: General Help
---

### Post by jaimegm on 2014-08-09
Hi There

I turned off my computer and then when I turned it on, Menu launcher disappeared, (I hadn't done any extra modifications during this time) following some of the information from [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears/76951#76951](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears/76951#76951) I was able to install compiz, and I enabled the unity, but nothing happen, in the same way I am not able to lunch the terminal from the graphic tty and when I am in a window I am not able to see the top I mean where the [x] close button is, any ideas are welcome

This is in a Laptop Lenovo 640

---

### Post by Jesse_Campton on 2014-08-09
Try this: [http://ubuntuforums.org/showthread.php?t=2236849](http://ubuntuforums.org/showthread.php?t=2236849)

---

### Post by grahammechanical on 2014-08-09
Which commands in that AskUbuntu thread did you follow? What was good for Ubuntu 12.04 does not work for Ubuntu 14.04. Installing Compiz Configuation Settings Manager (CCSM) is not necessarily the answer. In fact CCSM gives the inexperienced user the power to really mess things up. The important commands in 14.04 are

```

sudo dconf reset -f /org/compiz/

setsid unity
[COLOR=#222222]unity --reset-icons[/COLOR]
```Regards.

---

### Post by jaimegm on 2014-08-09
Thank you Jesse_Campton and grahammechanical

My problem at this moment is that I am not able to run the terminal from my graphical tty, When I move to a different tty and then I type: **sudo dconf reset -f /org/compiz** I receive the following message: 

```

error: Cannot autolaunch D-Bus without x11 $DISPLAY
Usage:
  dconf reset [-f] ...

```

In my graphical tty when try CTRL-ALT-t does not work

---

### Post by jaimegm on 2014-08-09
Thank you Jesse_Campton and grahammechanical

Ok I found the way to oopen the terminal in the graphical area from a different tty [http://ubuntuforums.org/showthread.php?t=2238706](http://ubuntuforums.org/showthread.php?t=2238706)

Then I was able to follow your instructions and it worked just fine.

Thanks again

---

### Post by garpt01 on 2014-09-01
[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"),

  THANK YOU! i was having exactly the same issue, could only find "fix" for 12.04 which simply brought a black screen and locked me out. This worked perfectly, restoring not only the menu launcher but fixed my whole theme. Great advice.

---

### Post by Lukas_Carls on 2014-11-03
> **grahammechanical said:**
> Which commands in that AskUbuntu thread did you follow? What was good for Ubuntu 12.04 does not work for Ubuntu 14.04. Installing Compiz Configuation Settings Manager (CCSM) is not necessarily the answer. In fact CCSM gives the inexperienced user the power to really mess things up. The important commands in 14.04 are

```

sudo dconf reset -f /org/compiz/

setsid unity
[COLOR=#222222]unity --reset-icons[/COLOR]
```Regards.

Thank you so much! This solved my identical issue as well.

---

### Post by nirama on 2014-11-21
Hi everybody,

have a similar problem: installed and started ccsm to get rid from some 3D effects and then the launcher disappeared. I have tried your advice. But the execution of the

setsid unity

stops or, better to say, hangs at

compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom

Could you comment on this, please?

Thanks in advance :)

---

### Post by maria222 on 2015-03-05
I am new to Ubuntu and linux in general too.  But using puppy-linux for about an year without any issues.  Now got a Dell XPS-18 inch touch tablet(windows OS was erased from it, owner could not use the machine) at a very cheap price.  Since it is a touch based tablet, I could not put Puppy linux on it.  Based on the reviews, I found Ubuntu as the leading distro for touch based machines.  Then I installed ubuntu latest ver; it worked fine.  After that I added compiz and made a few settings.  That is it!  the machine is almost dead!  Then I had use my old puppy machine to go online and find the solution; ended up on this thread, after a struggle I could get the tablet/Ubuntu back to life again.

With all respects why this issue is not solved?  I am asking this question, due to the fact that this issue was there for long and is well known.  Many users reported this issue on various websites.  I know it is easy to comment, but I sense that Ubuntu and Compiz/ unity do not mix well.  Also, Ubuntu has no bells and whistles such as built-in screen-savers, window decorations etc that can be used right away.  I added x-screensaver, but it is really not included in the distro.

For touch tablets, Ubuntu should recommend a touch-based browser.  Firefox (which is bundled with the distro) is not touch friendly currently.

I was about to get rid of Ubuntu and try Mint-Linux; luckily the fix was simple for me, so staying on for a while.

Lastly, I am not a technical person and least interested in complaining, that too on a license-free product like this.  It is a well made product, but small things can make the machines un-usable.  
My 2cents.

---

