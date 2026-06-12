---
title: "Starting ADSL link on startup"
date: 2005-07-01
forum: General Help
---

### Post by justjuice on 2005-07-01
1) I wanted to get my ADSL connection working for non-root users, but got stumped so:
2) I tried to get the ADSL connection up and running automatically on startup.

I've failed on both. Any suggestions appreciated.

For (2), I have done the following:
Created a shell script in /etc/init.d.  Contents are:
#! /bin/sh
sudo usr/sbin/adsl-start

Made it executable with sudo chmod +x /etc/init.d/myscript

Create a symbolic link with sudo update-rc.d myscript defaults

But it doesn't activate my connection on startup.

Also tried to create a symbolic link in rcS.d using the ln command.  But to no avail.

Also tried adding it to the startup programs in System -> Preferences ->Sessions.  No luck.

So can anyone find what I'm doing wrong?

Or if you can't help me in that, any help in getting my adsl connection to work with non-root users would be appreciated. (Am using roaring penguin, and tried screwing with my sudoers file, but suceeded only in doing just that, screwing it).

Thanks.

PS: If I install an application from source as one user (or root), are other users supposed to be able to access it? Or do I have to install for each user separately?

---

### Post by dresnu on 2005-07-01
Have you tried pppconf? I have a dsl connection too and all I did was to run that configuration program. It sets your connection to start automatically at startup for all users.
If you install an application as root, all other users should be able to use it as long as it's not a program that can only be run with root privileges.

---

### Post by justjuice on 2005-07-01
pppconf seems to be just for modem dialup. When I go through the configuration it keeps talking about dialup, and you have to put in a dialup number. There is no number to dial for my ADSL connection.

---

### Post by jonrkc on 2005-07-01
[QUOTE=justjuice]pppconf seems to be just for modem dialup. When I go through the configuration it keeps talking about dialup, and you have to put in a dialup number. There is no number to dial for my ADSL connection.[/QUOTE]
Try pppoeconf.  It is made to configure DSL connections rather than dial-ups.

---

### Post by dresnu on 2005-07-02
yeah! pppoeconf, that's what i meant too, sorry for misleading you   :roll:

---

### Post by justjuice on 2005-07-03
Thanks, guys!  pppoeconf did it!  Still don't know why the other start up script didn't work, but never mind.  Thanks!

---

### Post by jnoreiko on 2005-08-05
[QUOTE=jonrkc]Try pppoeconf.  It is made to configure DSL connections rather than dial-ups.[/QUOTE]

Can that work with a USB ADSL modem?
When I ran it, I got a screen about my ethernet device.

---

### Post by emoui on 2005-08-05
[QUOTE=jnoreiko]Can that work with a USB ADSL modem?
When I ran it, I got a screen about my ethernet device.[/QUOTE]

On the www page:

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/)

I have found excellent description on configuring Ubuntu Hoary to work with Thomson Speedtouch ADSL modem. Among the Speedtouch-specific details you can find notes  on writing scirpts automatically starting modem and connecting to ISP.

emoui

---

### Post by emoui on 2005-08-05
[QUOTE=justjuice]Thanks, guys!  pppoeconf did it!  Still don't know why the other start up script didn't work, but never mind.  Thanks![/QUOTE]

On the www page:

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/)

I have found excellent description on configuring Ubuntu Hoary to work with Thomson Speedtouch ADSL modem. Among the Speedtouch-specific details you can find notes  on writing scirpts automatically starting modem and connecting to ISP.

emoui

---

### Post by ubunta on 2005-08-08
Hi!

Now i am ubuntu user. But my problem is that i want to install my adsl. I have a rooter. I tried with pppoeconf, but it didn´t work, 'the acces concentrator didn`t answer'. 
I would be very glad if anybody could help me.

Thanks in advance.

---

### Post by GTvulse on 2005-08-08
[QUOTE=jnoreiko]Can that work with a USB ADSL modem?
When I ran it, I got a screen about my ethernet device.[/QUOTE]
What kind of USB device? I have an USB ADSL bridge with a Globespan Virata chipset. It uses the driver available from [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) and among the things provided in the source package there is a small init script. I copied it as /etc/init.d/adsl, added a couple of lines to set the clock with an NTP server as well as register the assigned IP address with the dynamic DNS service and installed it with the command:
```

sudo update-rc.d adsl defaults 14 86

```
(see man update-rc.d for the meaning of that command line). The start and stop priority numbers are rather arbitrary, I just chose to use the same priorities as the ppp start-up script.

---

### Post by Kapre on 2005-08-08
[QUOTE=ubunta]Hi!

Now i am ubuntu user. But my problem is that i want to install my adsl. I have a rooter. I tried with pppoeconf, but it didn´t work, 'the acces concentrator didn`t answer'. 
I would be very glad if anybody could help me.

Thanks in advance.[/QUOTE]

I think pppoeconf only works for direct connection to your pc (coz that is what I have). If you have a router, I think you should set it up first. Sorry I cannot help you outright, I'll try it at home tonight and will post it later. 

Maybe you can also searchin this forum using router.

K

---

### Post by jnoreiko on 2005-08-08
[QUOTE=dradul]What kind of USB device? I have an USB ADSL bridge with a Globespan Virata chipset. It uses the driver available from [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/).[/QUOTE]

That's the driver I use. My modem is a BT Voyager 105 and it's supported by the beta version of eciadsl.
Every time I start up, I have to do eciadsl-start in a root terminal.

---

### Post by GTvulse on 2005-08-09
[QUOTE=jnoreiko]That's the driver I use. My modem is a BT Voyager 105 and it's supported by the beta version of eciadsl.
Every time I start up, I have to do eciadsl-start in a root terminal.[/QUOTE]
 When I compiled and installed the 0.11 beta driver (my ADSL bridge is a Xavi 7005Q2 Marconi) with the help of checkinstall, I also copied the file rc.adsl from the sources directory to /etc/init.d with the name adsl. I edited the start section a bit like so:
```

case "$1" in
	start)
		echo -n "Starting adsl: "
		PATH=$EXEC_PREFIX:/usr/bin:/usr/sbin:/bin:/sbin eciadsl-start
		/usr/local/bin/ipcheck.py -l -i ppp0 -d /var/cache/ipcheck myname mypass  mydyndnsname
		/usr/sbin/ntpdate ntp.ubuntulinux.org
		exit $?
        ;;

```

Then I typed:
```

sudo update-rc.d adsl defaults 14 86

```

And that was it. You need to be a bit patient to let the connection process finish succesfully before you log into your account, or Gnome may fail to start hald; that's the only caveat.

Note I use ipcheck.py (which I found in the client listings at [http://www.dyndns.org/](http://www.dyndns.org/)) because it doesn't run as a daemon but rather it is a one-shot affair, contrary to most other dyndns clients (including the ddclient or ez-ipupdate both available in the Universe repository). If you were obtaining your IP address with DHCP  rather than with automatic PPP server configuration, you would need a different client such as the others I mentioned above.

---

### Post by ubunta on 2005-08-09
Thanks 'Kapre'. You help me to look for another alternatives. I was blinded yesterday with the pppoeconf option. ](*,) 

Now i am using my ubuntu os to write this post. The solution is easy when yo find it. I realised that i have a static ip, and the second step was 'system - adminstration - network'. I put there my static ip and dns, then i did a ping and now i am in the cyberspace.

 \\:D/

---

### Post by ad1138 on 2005-08-10
I've configured my ethernet DSL connection with pppoeconf too and it works fine, I usually start it with **pon dsl-provider** and stop it with **poff**. But is there some sort of an applet to connect and disconnect form the internet by clicking an icon? Maybe something to add to the gnome panel. 

Thanks.  :)

---

