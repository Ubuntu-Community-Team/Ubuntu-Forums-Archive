---
title: "Help with ssh error &quot;Unable to connect to X server&quot; xrdp not working"
date: 2021-04-18
forum: General Help
---

### Post by vw16v on 2021-04-18
Hi, I usually have luck installing sshd and using xrdp to connect to my desktop. However, I'm having issues with 20.04 load that has only got worse as I messed around.

I looked at a few guides like these two:

[https://c-nergy.be/blog/?p=14965](https://c-nergy.be/blog/?p=14965)

[https://www.ubuntupit.com/how-to-install-and-use-xrdp-server-remote-desktop-on-linux-system/](https://www.ubuntupit.com/how-to-install-and-use-xrdp-server-remote-desktop-on-linux-system/)

I have sshd installed and configured but after I had issues I first tried following this guide before referencing either of the two above:

[https://devanswers.co/how-to-fix-authentication-is-required-to-create-a-color-profile-managed-device-on-ubuntu-20-04-20-10/#the-culprit-polkit](https://devanswers.co/how-to-fix-authentication-is-required-to-create-a-color-profile-managed-device-on-ubuntu-20-04-20-10/#the-culprit-polkit)

This caused issues with the authentication prompt Not coming up on my laptop to install the latest updates.
So, I removed the file I created with this guide >
"[COLOR=black][FONT=Consolas]/etc/polkit-1/localauthority.conf.d/02-allow-colord.conf"

[/FONT][/COLOR]But, ever since I removed that file I'm now getting this error when I ssh to my laptop that's running 20.04

Last login: Sun Apr 18 17:14:36 2021 from 10.16.0.21
Unable to connect to X server

I'm trying to fix the "Unable to connect to X server" message that seems to be causing issues with RDP certificate.

I changed my xrpd port and when I connect to the port I get this error.

Also, I already added user to certificate>
[FONT=Calibri][https://www.ubuntupit.com/how-to-install-and-use-xrdp-server-remote-desktop-on-linux-system/](https://www.ubuntupit.com/how-to-install-and-use-xrdp-server-remote-desktop-on-linux-system/)[/FONT]
[FONT=Calibri]sudo adduser xrdpssl-cert[/FONT]

This is what it shows when I use the tunnel connection similar to the first two article I posted. 
This Windows error.

[IMG]https://i.imgur.com/9DpDE6R.png[/IMG]


I was able to get the xrdp xfce desktop to come up also but this is a less than ideal solution.

Essentially I want to figure out why I'm getting this error via ssh>?
"Unable to connect to X server"

I already tried completely removing xrdp and sshd and re-installing but I'm still getting this error.

Thanks for any help.  Let me know if I need to provide any xrdp.log files or journal entries,etc.
I seem to be off on my troubleshooting today. I believe I might need to modify my startwm.sh file or something.

---

### Post by TheFu on 2021-04-21
Just curious, is your Windows system running an X/Server?  You'd need to go out of your way to install and configure that.
For many people, x2go is a better solution to connect from Windows into a Linux desktop.  Just don't use Gnome3 as the DE. Choose something lighter, like XFCE or LXQt.

---

### Post by vw16v on 2021-04-22
> **TheFu said:**
> Just curious, is your Windows system running an X/Server?  You'd need to go out of your way to install and configure that.
For many people, x2go is a better solution to connect from Windows into a Linux desktop.  Just don't use Gnome3 as the DE. Choose something lighter, like XFCE or LXQt.

No, my Windows is not running any vnc / xserver. I don't have remote desktop enable on my Windows box. I just like connecting to my Linux boxes via xrdp over ssh. 

I created a new user account and when I connect via ssh using the new user I don't get the "Unable to connect to X server" message. I think something with my main user account got messed up in a profile setting causing this issue.
I still get that certificate error so my connection might potentially be vulnerable to man in the middle attacks if I decide to connect remotely.

However, all my current connections are done within my LAN. I'm going to check out the x2go application and maybe mess around with that. 

I believe I might be able to potentially fix my main user account from getting this error. "Unable to connect to X server"

I think the /home/'user'/.xsession-error file should allow me to figure this out. 

It's not as bad as it was a few days ago. I used to be really good at configuring secure remote connections. I never remember seeing these .pem keys.
lrwxrwxrwx   1 root root    36 Apr 19 18:15 cert.pem -> /etc/ssl/certs/ssl-cert-snakeoil.pem
lrwxrwxrwx   1 root root    38 Apr 19 18:15 key.pem -> /etc/ssl/private/ssl-cert-snakeoil.key

My other Linux load that I connect to like this without errors does not have these certificate type files.

I don't get any errors or warnings on that system with connection to the xrdp tunnel with putty.

---

### Post by HermanAB on 2021-04-22
You are connecting from Windows to Ubuntu Linux?  Do you have an an X server running on Windows?  Do you have an X server (not Wayland) on Linux?

"XFCE or LXQt." - As alluded to above, these use Xorg.  So if you install one of them, then your "cannot connect to X server" problem should be fixed on the Linux side at least.

---

