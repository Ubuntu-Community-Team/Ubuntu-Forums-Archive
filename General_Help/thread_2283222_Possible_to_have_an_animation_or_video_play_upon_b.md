---
title: "Possible to have an animation or video play upon boot?"
date: 2015-06-20
forum: General Help
---

### Post by James_Dean on 2015-06-20
When i was around 12 years old I saw the movie hackers as a lot of you will have done. I loved the way they had those animations of their hacker names when they turned their laptops on. I wonder can you make an animation or video play upon startup for ubuntu 15.04? 

I would really love an animation or to be able to chop a bit of video and make that my boot up screen. Hopefully this is the case. Thank you in advance, James

---

### Post by TheFu on 2015-06-20
To playback video, you need an OS. 
Lots of things in movies aren't real - especially movies with computers.

---

### Post by leunam12 on 2015-06-20
You can make a short animation and use it as your boot splash screen if you are willing to learn how to change the plymouth theme. You may also download an already made theme and apply it. Search for "change Ubuntu Plymouth theme" or "change Ubuntu splash".

---

### Post by yetimon_64 on 2015-06-20
> **TheFu said:**
> To playback video, you need an OS. 
Lots of things in movies aren't real - especially movies with computers.

 What about the tty console start up, a "black" screen that is actually the OS but no GUI. Video can be played under such a setting by activating the Linux framebuffer if the laptop video hardware supports it. 

From the console, with mplayer, I play full HD 1920 by 1080 videos using this next command with such a set up.
```
alias mplay.hd='mplayer -vo fbdev2 -zoom -x 1920 -y 1080 -geometry 95%:50% -cache 131072 -cache-min 40 -cache-seek-min 60 -nolirc >/dev/null 2>&1 %f'
```

Note I use the bash alias to make the command manageable to type quickly. I am on a laptop with hybrid graphics and have an Intel framebuffer, full HD without even having to mess with the grub default file and so on. When I choose to boot to the "full OS" or DE I use another alias for "sudo lightdm start" etc.

I suspect it would be possible but would mean messing with the tty#.conf files in /etc/init. By altering the tty#.conf file it is possible with "mingetty" to set an autologin, it may be possible to then run commands to play video and follow on to a desktop ... definitely a maybe ! 

 :-k I have done an autostart on a tty of alsamixer on Debian, but have been having major hassles trying such recently with the Ubuntu setup; I suspect it is possible, and if so, a video clip or animation could be played on the tty console boot in, then a quick switch to the GUI later on etc. Quite complex to set up and relies on good hardware, so doubt the "Hackers movie" way back then would have been along this line ;). Cheers yeti.

---

### Post by QDR06VV9 on 2015-06-20
If you are talking about boot anaimations see [http://askubuntu.com/questions/201129/how-to-change-boot-animation](http://askubuntu.com/questions/201129/how-to-change-boot-animation)
Here is what it could look like [https://www.youtube.com/watch?v=apx_HyxFqjA](https://www.youtube.com/watch?v=apx_HyxFqjA)
To install super-boot-manager on Ubuntu 15.04, run the below commands on terminal
```
sudo add-apt-repository ppa:ingalex/super-boot-manager
sudo sh -c "sed -i 's/vivid/raring/g' /etc/apt/sources.list.d/ingalex-super-boot-manager-vivid.list"
sudo apt-get update
sudo apt-get install super-boot-manager
sudo apt-get install -f
```

Kind Regards

---

### Post by leunam12 on 2015-06-20
Thank you for the links, runrickus. I wonder if I'll be able to see all the animation in the youtube video since my computer boots in five seconds or less. Right now I have a Mac bootainmation but I only see it for about two seconds.

---

### Post by QDR06VV9 on 2015-06-20
> **leunam12 said:**
> Thank you for the links, runrickus. I wonder if I'll be able to see all the animation in the youtube video since my computer boots in five seconds or less. Right now I have a Mac bootainmation but I only see it for about two seconds.
Your Welcome! I can not remember but I think It lasts a little longer maybe 10 to 15 secs longer and as brought up by "yeti" if you have Nvidia Drivers installed it just reverts back to Original Splash
There was a fix for proprietary drivers some where around the time of natty but it never worked for my Nvidia Card.
My Kids still get a kick out of the Dancing Penguin.
Kind Regards

---

### Post by Dennis N on 2015-06-20
This thread (link below) from late May 2015 got into using the **Earth Sunrise** theme (which is mentioned in the first link in post #5, above ^). I have it installed on Xubuntu 14.04, and it takes 20 seconds or so to complete on an older machine (vintage 2008) with standard hard drive. I have wondered if it were used on an SSD which boots in 10 seconds or less, what would happen - would it exit early? Can't test with the machine it's on, as it takes 30 - 40 seconds to boot anyway.

[http://ubuntuforums.org/showthread.php?t=2279649](http://ubuntuforums.org/showthread.php?t=2279649)

Anyway, there are directions in posts #3 and 5 of the thread how to get and install it without any special tools. It's easy to remove and go back to the standard boot splash if desired.

---

### Post by QDR06VV9 on 2015-06-20
> **Dennis N said:**
> This thread (link below) from late May 2015 got into using the **Earth Sunrise** theme (which is mentioned in the first link in post #5, above ^). I have it installed on Xubuntu 14.04, and it takes 20 seconds or so to complete on an older machine (vintage 2008) with standard hard drive. _**I have wondered if it were used on an SSD which boots in 10 seconds or less, what would happen - would it exit early? **_Can't test with the machine it's on, as it takes 30 - 40 seconds to boot anyway.

[http://ubuntuforums.org/showthread.php?t=2279649](http://ubuntuforums.org/showthread.php?t=2279649)

Anyway, there are directions in posts #3 and 5 of the thread how to get and install it without any special tools. It's easy to remove and go back to the standard boot splash if desired.
You will have to tell us if you choose to try.:D I have not yet bought the SSDs getting close Very soon.

---

### Post by Dennis N on 2015-06-20
> **runrickus said:**
> You will have to tell us if you choose to try. I have not yet bought the SSDs getting close Very soon.
In either case, I would think SSD users would be unlikely to want these alternate Plymouth boot splash animations installed - in the case they exit early, you miss most of the animation, and what would be the point? In the case it doesn't exit, you will grow impatient with waiting for the animation to finish each time you start up, losing part of the benefit of having the SSD.

---

