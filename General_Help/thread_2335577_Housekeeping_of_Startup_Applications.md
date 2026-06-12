---
title: "Housekeeping of Startup Applications"
date: 2016-08-30
forum: General Help
---

### Post by nicnok on 2016-08-30
I'm sure this must have been asked many times but I can't find another post **[very happy  to be guided]**.

I want to keep my Ubuntu 14.04 trim and fast.
I am not a techie, I want to use GUI if possible.
Looking for something else I came across this command:
*sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop*

I find I have 25 or so Applications competing to start at bootup but unfortunately I can't seem to find a way of copying that list [from Applications>System Tools>Preferences>Startup Applications] and posting it here. **[help on that would be appreciated]**

I'm pretty sure some of those 25 will be vital [eg Network?] but others look irrelevant to me [eg Gwibber, Tracker Store etc]. Is there a handy list or guide to what these things do and which it would be inadvisable to remove from start-on-boot?

---

### Post by howefield on 2016-08-30
> **nicnok said:**
> ..... unfortunately I can't seem to find a way of copying that list [from Applications>System Tools>Preferences>Startup Applications] and posting it here. **[help on that would be appreciated]**

```
ls -al /etc/xdg/autostart
```

might do it.

> I'm pretty sure some of those 25 will be vital [eg Network?] but others look irrelevant to me [eg Gwibber, Tracker Store etc]. Is there a handy list or guide to what these things do and which it would be inadvisable to remove from start-on-boot?

FWIW, I disable Accessibility Profile Manager Indicator, Backup Monitor, Gnome Software, Orca Screen Reader and Update Manager. Wouldn't suggest these are "safe" to disable, eg, disabling update manager means you have to remember to do your own :)

---

### Post by nicnok on 2016-08-30
Thanks, as the youngsters say that's really cool. Here's the output of ls -al /etc/xdg/autostart:

```
total 208
drwxr-xr-x 2 root root 4096 Aug 30 12:00 .
drwxr-xr-x 7 root root 4096 Jun  7  2015 ..
-rw-r--r-- 1 root root  306 Aug 30 12:00 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  416 Aug 30 12:00 at-spi-registryd.desktop
-rw-r--r-- 1 root root  439 Apr  8  2009 at-spi-registryd-wrapper.desktop.dpkg-bak
-rw-r--r-- 1 root root  371 Aug 30 12:00 deja-dup-monitor.desktop
-rw-r--r-- 1 root root  490 Aug 30 12:00 evolution-alarm-notify.desktop
-rw-r--r-- 1 root root  524 Aug 30 12:00 gnome-at-session.desktop
-rw-r--r-- 1 root root  383 Oct 19  2009 gnome-keyring-daemon.desktop.dpkg-bak
-rw-r--r-- 1 root root  450 Aug 30 12:00 gnome-keyring-gpg.desktop
-rw-r--r-- 1 root root  486 Aug 30 12:00 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root  479 Aug 30 12:00 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root  445 Aug 30 12:00 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root  530 Aug 30 12:00 gnome-screensaver.desktop
-rw-r--r-- 1 root root  309 Aug 30 12:00 gnome-settings-daemon.desktop
-rw-r--r-- 1 root root  384 Oct 23  2009 gnome-settings-daemon-helper.desktop.dpkg-bak
-rw-r--r-- 1 root root  528 Aug 30 12:00 gnome-sound-applet.desktop
-rw-r--r-- 1 root root  310 Aug 30 12:00 gnome-user-share.desktop
-rw-r--r-- 1 root root  280 Aug 30 12:00 gsettings-data-convert.desktop
-rw-r--r-- 1 root root  354 Aug 30 12:00 gwibber.desktop
-rw-r--r-- 1 root root  285 Aug 30 12:00 indicator-applet.desktop
-rw-r--r-- 1 root root  252 Aug 30 12:00 indicator-application.desktop
-rw-r--r-- 1 root root  230 Aug 30 12:00 indicator-bluetooth.desktop
-rw-r--r-- 1 root root  300 Aug 30 12:00 indicator-datetime.desktop
-rw-r--r-- 1 root root  281 Aug 30 12:00 indicator-messages.desktop
-rw-r--r-- 1 root root  192 Aug 30 12:00 indicator-power.desktop
-rw-r--r-- 1 root root  201 Aug 30 12:00 indicator-printers.desktop
-rw-r--r-- 1 root root  302 Aug 30 12:00 indicator-session.desktop
-rw-r--r-- 1 root root  290 Aug 30 12:00 indicator-sound.desktop
-rw-r--r-- 1 root root  373 Aug 30 12:00 jockey-gtk.desktop
-rw-r--r-- 1 root root  211 Aug 30 12:00 nautilus-autostart.desktop
-rw-r--r-- 1 root root  392 Aug 30 12:00 nm-applet.desktop
-rw-r--r-- 1 root root  295 Aug 30 12:00 notification-daemon.desktop
-rw-r--r-- 1 root root  265 Aug 30 12:00 onboard-autostart.desktop
-rw-r--r-- 1 root root  288 Aug 30 12:00 orca-autostart.desktop
-rw-r--r-- 1 root root  359 Aug 30 12:00 polkit-gnome-authentication-agent-1.desktop
-rw-r--r-- 1 root root  376 Aug 30 12:00 print-applet.desktop
-rw-r--r-- 1 root root 3996 Aug 30 12:00 pulseaudio.desktop
-rw-r--r-- 1 root root  633 Aug 30 12:00 pulseaudio-kde.desktop
-rw-r--r-- 1 root root  451 Aug 30 12:00 telepathy-indicator.desktop
-rw-r--r-- 1 root root  430 Aug 30 12:00 tracker-applet.desktop
-rw-r--r-- 1 root root 3294 Aug 30 12:00 tracker-miner-fs.desktop
-rw-r--r-- 1 root root 3010 Aug 30 12:00 tracker-store.desktop
-rw-r--r-- 1 root root  223 Aug 30 12:00 ubuntuone-launch.desktop
-rw-r--r-- 1 root root  364 Aug 30 12:00 unity-fallback-mount-helper.desktop
-rw-r--r-- 1 root root  303 Aug 30 12:00 unity-settings-daemon.desktop
-rw-r--r-- 1 root root 9345 Aug 30 12:00 update-notifier.desktop
-rw-r--r-- 1 root root  313 Aug 30 12:00 user-dirs-update-gtk.desktop
-rw-r--r-- 1 root root  431 Aug 30 12:00 vino-server.desktop
-rw-r--r-- 1 root root  245 Aug 30 12:00 zeitgeist-datahub.desktop
```

I thought there'd be 25 [as above] but confusingly many items from Applications>System Tools>Preferences>Startup Applications do not seem to appear on the list [eg Network - is it masquerading as something else?].

A few other Qs arise: 
1/ Why does output start with 'total 208' when there are only 50 listed? 
2/ I may be totally off-beam here but It looks like Ubuntu uses the 'autostart' directory to boot some important elements of some of what my rabbit brain would call 'the system' including Gnome, Nautilus, & GUI tools. When I boot I just want Gnome, GUI, Nautilus, Unity fallback, Firefox, Evolution, WiFi. [Have I missed something stupid?!]. It is probably too big an ask, but  with that in mind, which of the 50 above can safely be either disabled or deleted from 'autostart'? Eg 'gwibber', 'bluetooth'. 
3/ Do I notice that Firefox and Evolution are not listed & so don't boot from 'autostart'? 
4/ Would disabling/removing lots of these noticably a] decrease boot time &/or b] increase system speed?

thank you

---

### Post by cariboo on 2016-08-30
To populate gnome-session-properties, use the following commands:

```
cd /etc/xdg/autostart/
```

then:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

the result should look something like the screenshot:

[[img]https://s17.postimg.org/gzrousvx7/image.png[/img]](https://postimg.org/image/gzrousvx7/)

---

### Post by howefield on 2016-08-31
> **nicnok said:**
> Thanks, as the youngsters say that's really cool. Here's the output of ls -al /etc/xdg/autostart:

*snip list*

I thought there'd be 25 [as above] but confusingly many items from Applications>System Tools>Preferences>Startup Applications do not seem to appear on the list [eg Network - is it masquerading as something else?].

Network Manager is there, it is the line here..

```
-rw-r--r-- 1 root root  392 Aug 30 12:00 nm-applet.desktop
```

The descriptive name sometimes doesn't match up with the .desktop file name :) If you click the edit button in Startup Applications you'll see something in the command field that matches the above list.

> Why does output start with 'total 208' when there are only 50 listed?
 
> I may be totally off-beam here but It looks like Ubuntu uses the 'autostart' directory to boot some important elements of some of what my rabbit brain would call 'the system' including Gnome, Nautilus, & GUI tools. When I boot I just want Gnome, GUI, Nautilus, Unity fallback, Firefox, Evolution, WiFi. [Have I missed something stupid?!]. It is probably too big an ask, but  with that in mind, which of the 50 above can safely be either disabled or deleted from 'autostart'? Eg 'gwibber', 'bluetooth'. 

I'd caution against being too liberal here, only disable the obvious :) If you have no need for bluetooth then you should be safe enough to disable it.

> Do I notice that Firefox and Evolution are not listed & so don't boot from 'autostart'? 

Unless you put them there, they won't autostart.

> Would disabling/removing lots of these noticably a] decrease boot time &/or b] increase system speed?

FWIW, I disable with the criteria of not using certain elements rather than from a boot time or speed benefit, I'd doubt there would be much noticeable difference unless the hardware was very weak. And even then,, shrug :) For instance I don't need deja-dup so I don't want parts of it starting up. YMMV :)

---

### Post by nicnok on 2016-09-01
sorry for the gap - tried to post this a couple of days ago [thought I had] but revisiting it it had disappeared:

thanks Cariboo [Sorry, trying to insert a quote - can't find the button]

running 
"*sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop "* 
gives no result BUT, [& sorry if this was unclear] my problem was  not failing to start the dialogue [I used Applications>System  Tools>Preferences>Startup Applications].
It was **'how do I find a way to copy/print the contents of that GUI dialogue'** because it looks very different from the output of ls -al /etc/xdg/autostart?

thanks Howefield:
I think from what you say this thread is not going anywhere in that you  have answered my basic question "Is there a handy list or guide to what  these things do and which it would be inadvisable to remove from  start-on-boot?" in the negative and that I need to know much much more  before I disable stuff. 
[eg how can I tell if I'm using deja-vu? Not to my jnowledge but is it a  vital part of some other app I do/might use? I don't use bluetooth but  are there dependencies in bluetooth-applet.desktop that will wreck  something else if I zap it? Cariboo does not start Telepathy or Gwibber  on boot, I've never come across them, but  are they vital for **my** setup etc etc].
I suppose what stands behind the question is "there are 208 items in  autostart and I only put in 4 - who put in the other 204 and why?". I  expect the answer would occupy you for weeks, so I'm not asking!

thanks for your time

In passing your mention of Evolution on autostart is interesting - it  appears not to be on the output of ls -al /etc/xdg/autostart [unless  it's name is obscure] yet **it does autostart** and is also on the GUI dilaogue.

I will follow your advice and let all that stuff autostart even though some/[much?] of it is probably irrelevant.

---

### Post by Keith_Helms on 2016-09-01
If you're shooting for "trim and fast", you might look into installing Xubuntu or Lubuntu.

---

### Post by Habitual on 2016-09-01
> **nicnok said:**
> sorry for the gap - tried to post this a couple of days ago [thought I had] but revisiting it it had disappeared:

thanks Cariboo [Sorry, trying to insert a quote - can't find the button]

running 
"*sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop "* 
gives no result BUT, [& sorry if this was unclear] my problem was  not failing to start the dialogue [I used Applications>System  Tools>Preferences>Startup Applications].
It was **'how do I find a way to copy/print the contents of that GUI dialogue'** because it looks very different from the output of ls -al /etc/xdg/autostart?

thanks Howefield:
I think from what you say this thread is not going anywhere in that you  have answered my basic question "Is there a handy list or guide to what  these things do and which it would be inadvisable to remove from  start-on-boot?" in the negative and that I need to know much much more  before I disable stuff. 
[eg how can I tell if I'm using deja-vu? Not to my jnowledge but is it a  vital part of some other app I do/might use? I don't use bluetooth but  are there dependencies in bluetooth-applet.desktop that will wreck  something else if I zap it? Cariboo does not start Telepathy or Gwibber  on boot, I've never come across them, but  are they vital for **my** setup etc etc].
I suppose what stands behind the question is "there are 208 items in  autostart and I only put in 4 - who put in the other 204 and why?". I  expect the answer would occupy you for weeks, so I'm not asking!

thanks for your time

In passing your mention of Evolution on autostart is interesting - it  appears not to be on the output of ls -al /etc/xdg/autostart [unless  it's name is obscure] yet **it does autostart** and is also on the GUI dilaogue.

I will follow your advice and let all that stuff autostart even though some/[much?] of it is probably irrelevant.

See also ~/.config/autostart/

---

