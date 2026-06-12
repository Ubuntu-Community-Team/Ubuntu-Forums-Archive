---
title: "Lubuntu 19.04 - Can't change Plymouth theme for text boot"
date: 2019-06-10
forum: General Help
---

### Post by &amp;wP*!) on 2019-06-10
**Problem: **I cannot set up the text boot theme for Plymouth in Lubuntu 19.04.
[COLOR="#FF0000"]**Edit: I want to see messages during boot but get GUI again**[/COLOR]
**Question: **Is there anyone who was succeeded in lubuntu-text theme?
**Question: **Is there a way to set up a Plymouth theme which enables text boot? 
None of the commands below help. Even tried them with **sudo-update grub**, no success. 
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth **/usr/share/plymouth/themes/lubuntu-text/lubuntu-text.plymouth** 100
sudo update-alternatives --config default.plymouth 
sudo update-alternatives --config text.plymouth
sudo update-initramfs -u [COLOR="#FF0000"]**(EDIT: I forgot to mention this command before, now added)**[/COLOR]

```
My understanding is, that playing with **/etc/default/grub** won't work here because Plymouth takes over control by running in initramfs, and registering itself as service to **systemd**. Thus playing with following variables won't help. I have tried all the combinations below, nothing changed.
```

# 10.06.2019 "quite" "splash" did not work
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=...
# 10.06.2019 "text" below did not work 
GRUB_CMDLINE_LINUX=""
```

---

### Post by again? on 2019-06-10
[COLOR="#FF0000"]Edit:[/COLOR]Misunderstanding... probably not what you want as you will boot into terminal.
[s]Try changing to text boot with systemd.
[https://ubuntuforums.org/showthread.php?t=2420259&p=13863348#post13863348](https://ubuntuforums.org/showthread.php?t=2420259&p=13863348#post13863348)[/s]

---

### Post by again? on 2019-06-11
FYI I tried the method outlined in the post below but do not see any plymouth splash.
The command given to test plymouth shows my changes though.
I am using an ssd...and boots pretty fast ...maybe not enough time for plymouth to load.

[https://askubuntu.com/questions/1046370/how-to-change-boot-splash-screen-in-18-04](https://askubuntu.com/questions/1046370/how-to-change-boot-splash-screen-in-18-04)

---

### Post by &amp;wP*!) on 2019-06-11
> **guber2 said:**
> FYI I tried the method outlined in the post below but do not see any plymouth splash.
The command given to test plymouth shows my changes though.
I am using an ssd...and boots pretty fast ...maybe not enough time for plymouth to load.

[https://askubuntu.com/questions/1046370/how-to-change-boot-splash-screen-in-18-04](https://askubuntu.com/questions/1046370/how-to-change-boot-splash-screen-in-18-04)

Hi guber2, thanks for your effort. What I really want is to see boot messages **and then get the GUI again**, as you have assumed correctly later on. I already tried the stuff in the URL you have mentioned above (except for initframfs update - which I forgot to mention in the original post as well) - all my commands in my original post are actually from that URL..

The Lubuntu-text theme of Plymouth does not show anything but one text, which I cannot follow. Probably boot sequence is very fast like yours because I also have an SSD, where my boot sequence lasts less than 10 seconds. Without a Plymouth theme the only possible way I can figure out to see them again is to disable video mode during boot, enable text mode. That requires a complete uninstallation of Plymouth.

I will [look other Plymouth themes]("https://www.gnome-look.org/browse/cat/108/ord/rating/")  which would save me effort to disable video mode. Maybe there is one theme which also shows the boot messages...

---

### Post by &amp;wP*!) on 2019-06-11
Other posts mentioning that boot on SSD is so fast.  
[https://ubuntuforums.org/showthread.php?t=2340103](https://ubuntuforums.org/showthread.php?t=2340103)
[https://www.reddit.com/r/pop_os/comments/ax8bvy/startup_shutdown_screen/](https://www.reddit.com/r/pop_os/comments/ax8bvy/startup_shutdown_screen/)

Probably it doesn't make sense to look at these on a machine with SSD.
I will set this to SOLVED.

Important information: [Ubuntu Wiki about this]("https://wiki.ubuntu.com/Plymouth#Debugging") is wrong. I have tried "splash" stuff. It doesn't work. Ubuntu Wiki of Plymouth is very old (4 years as of now) - to be updated. 

Possible Solutions (proposed, not tried, not searched on web)
[LIST=1]
[*]slow down the boot
[*]disable video mode during boot, enable text mode.
[*]Uninstall Plymouth (if it helps) 
[/LIST]

---

### Post by garvinrick4 on 2019-06-11
#Open a terminal
> sudo gedit /etc/default/grub

#change line 6 to "text" on the end

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""
> sudo update-grub

---

### Post by again? on 2019-06-11
You are confusing text.plymouth with grub's text option.
 text.plymouth still displays a splash but without animation. It's a fallback mode for unsupported gfx.
Just editng grub as garvinrick4 shows should work.

---

### Post by &amp;wP*!) on 2019-06-12
> **guber2 said:**
> You are confusing text.plymouth with grub's text option.
 text.plymouth still displays a splash but without animation. It's a fallback mode for unsupported gfx.
Just editng grub as garvinrick4 shows should work.
I couldn't find one in internet what exactly "text.plymouth" does. That's why.

> **garvinrick4 said:**
> 
GRUB_CMDLINE_LINUX_DEFAULT="text"

Only the entry above gives what I wanted (in /etc/default/grub). My boot takes less than 10 seconds, and the text runs very fast, but I can see finally the boot messages.

Thanks!

---

