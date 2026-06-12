---
title: "Ubuntu 14.04LTS - Grub timeout: change the delay on the 'startup'"
date: 2016-05-16
forum: General Help
---

### Post by Boris786 on 2016-05-16
Hello,

I am currently on Ubuntu 14.04LTS and have a question on how to change the delay on the 'startup' screen. Using gksu gedit /etc/default/grub I have:
GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="5"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

By my interpretation my delay should be 5 seconds but it is 30. I would like it to be 5.

Please see attached pic on startup. Note - grub is version2.02BETA2-9ubuntu1.7

Grateful for advice.

---

### Post by yancek on 2016-05-16
Take a look at the link below which explains the different options.  You can comment out the line GRUB_HIDDEN_TIMEOUT and set your GRUB_TIMEOUT to 30 if that's what you want.

[http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry](http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry)

---

### Post by Boris786 on 2016-05-18
Ok we now have:

GRUB_DEFAULT="0"
# GRUB_HIDDEN_TIMEOUT="5"
# GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

My grub time out should be 2 seconds I think but remains at 30 as with my previous. In both cases I do not understand why it would be 30. Is this a bug?

---

### Post by CantankRus on 2016-05-18
Your changes work here.

After saving changes to **/etc/default/grub**, are you running
```
sudo update-grub
```

Do you have another Linux install on this computer?

---

### Post by Boris786 on 2016-05-19
Hi thanks,

Yes ran sudo update-grub & only have 14.04LTS installed. Are you using same grub version v2.02BETA2-9ubuntu1.7. I have never had a problem with this before on previous versions of Ubuntu (and presumably earlier versions of grub).

Obviously this is not a critical issue but would be nice to resolve/understand.

P

---

### Post by Cavsfan on 2016-05-19
The quotation marks are not supposed to be there.
Here is what I have on Xubuntu 16.04. I set mine to 60 seconds because sometimes I need a little extra time.

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Also if you want to have a nice grub screen with bigger fonts and you can set 3 colors for the fonts: one for the top and bottom, one for the box and regular menu entries and one for the highlighted menu entry.
Take a look at the link in my signature.

This is on Arch and it only accepts 2 colors: one for the box and regular menu entries and one for the highlighted menu entry.
The colors are cyan for the box and regular menu entries and red for the highlighted menu entry.

[[IMG]http://www.zimagez.com/miniature/20160408161917.jpg[/IMG]]("http://www.zimagez.com/zimage/20160408161917.php")

---

### Post by Boris786 on 2016-05-21
Thanks. OK I have:

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Delay still at 30 seconds though........

---

### Post by Cavsfan on 2016-05-21
> **Boris786 said:**
> Thanks. OK I have:

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Delay still at 30 seconds though........

If you also ran **sudo update-grub**, then rebooted and still got 30 seconds, then you must be editing the wrong system's grub.
Do you have more than just one Ubuntu system installed?

---

### Post by CantankRus on 2016-05-21
You may want to install boot-info-script....
```
sudo apt-get install boot-info-script
```

In terminal run ...
```
sudo bootinfoscript
```
and post the **~/RESULTS.txt** file here.

---

### Post by Boris786 on 2016-05-23
Only one system. 
Installed Ubuntu over previous dual application with Windows & Ubuntu so you never know I guess. Results.txt attached.

---

### Post by CantankRus on 2016-05-23
From your normal desktop try reinstalling grub.
```
sudo grub-install /dev/sda
```

---

### Post by Cavsfan on 2016-05-23
Yes, I'd agree to re-install grub to sda. 

You will also need to edit /etc/default/grub 

```
gksudo gedit /etc/default/grub
```
(if you do not have gedit use what ever text editor you have.)
```
sudo nano /etc/default/grub
```
will also work if you are familiar with nano.
And make sure the number beside GRUB_TIMEOUT=15 or whatever timeout you want.
Because looking at your grub.cfg file you have GRUB_TIMEOUT=0 right now.
Also make sure the # below in [COLOR=#FF0000]red[/COLOR] is there in front of GRUB_HIDDEN_TIMEOUT=0.
Then make _absolute sure_ you update grub ```
sudo update-grub
``` and then reboot. 
```
GRUB_DEFAULT=0
[COLOR=#FF0000]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

It's taking the recordfail = 1 route giving you the 30 seconds wait

```
function recordfail {
  [COLOR=#ff0000]set recordfail=1[/COLOR]
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

```
```
if [ "${recordfail}" = 1 ] ; then
  [COLOR=#ff0000]set timeout=30[/COLOR]
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=[COLOR=#ff0000]0[/COLOR]
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=[COLOR=#ff0000]0[/COLOR]
  fi
fi
```

If you do these things it cannot be taking that route.
Here is what my grub.cfg looks like with a 60 second time out:
```
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=[COLOR=#ff0000]60[/COLOR]
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=[COLOR=#ff0000]60[/COLOR]
  fi
fi
```

---

### Post by Boris786 on 2016-05-24
Thanks,
When re-installing grub I get:

Installing for i386-pc platform.
grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install: warning: Sector 33 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

All good now except:

Questions: should I be worried about 'Flexnet' ? It seems not to be affecting anything currently and re-instaling grub all seems to be working as I expect now. I am thinking leave well alone - I have trawled web and seems I can leave but maybe this explains problems I have had with dual booting previously.
Why i386? I have 64 bit Ubuntu.

Thanks both. Sorry - there are more questions than answers.................

---

### Post by Cavsfan on 2016-05-24
> **Boris786 said:**
> Thanks,
When re-installing grub I get:

Installing for i386-pc platform.
grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install: warning: Sector 33 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

All good now except:

Questions: should I be worried about 'Flexnet' ? It seems not to be affecting anything currently and re-instaling grub all seems to be working as I expect now. I am thinking leave well alone - I have trawled web and seems I can leave but maybe this explains problems I have had with dual booting previously.
Why i386? I have 64 bit Ubuntu.

Thanks both. Sorry - there are more questions than answers.................

That is just a warning, so I wouldn't worry about it. 
It also says "**Installing for i386-pc platform.**" on every system I've had for the past year or more. 
And I've always had a 64 bit system. So, I'd say your problem is resolved.

Please mark this thread as solved.

---

### Post by Cavsfan on 2016-05-24
You can also enter 
```
sudo dpkg-reconfigure grub-pc
```
In terminal and select sda.

This is from section 1.8 in the community wiki in my signature.

---

### Post by CantankRus on 2016-05-24
> **Boris786 said:**
> Questions: should I be worried about 'Flexnet' ? It seems not to be affecting anything currently and re-instaling grub all seems to be working as I expect now. I am thinking leave well alone - I have trawled web and seems I can leave but maybe this explains problems I have had with dual booting previously.
If it's working now I would leave it. You said you were no longer dual booting anyway.

Flexnet surreptitiously installs itself to the boot sector when you install adobe products and others, 
it's main purpose being to check you're not a software pirate. :roll:
Don't know if still the case as I don't use Windows anymore.
More info can be found here....
[**_[COLOR="#B22222"]Windows applications making GRUB 2 unbootable[/COLOR]_**]("http://www.chiark.greenend.org.uk/~cjwatson/blog/windows-applications-making-grub2-unbootable.html")
[**_[COLOR="#B22222"]Sector 32 FlexNet Problem -- Grub[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1661254")

---

