---
title: "x11vnc on HEADLESS machine running XDM"
date: 2007-09-02
forum: General Help
---

### Post by hebetude on 2007-09-02
OS: Feisty Fawn 7.04
Kernel: 2.6.20-16-server
x11vnc: x11vnc: 0.8.2 lastmod: 2006-07-12
Client: Vista running TightVNC
DM: XDM/xfce4

I currently have a headless machine that I want to control with VNC.  It does correctly export the X display through x11vnc once I login locally, but being headless I must  carry a monitor/mouse to it everytime I need to reboot.

How can I get a persistent X session under x11vnc to start before/at the login screen, so that I can VNC in start X and have it stay running forever.  I am currently running xfce4, so my display manager is XDM or XDMCP (I don't know guides seem to mix these two up).  What do I need to setup so I can access the machine while it is not logged in.

From what I understand I can run it with xinetd.d (not working) or setup XDMCP (not working?).  

Here are the numerous guides I have read (linked for your convenience) all written for gdm/kdm of course with little clues to how this is done with xdm/xfce4:

[HOWTO: Share desktops with x11vnc instead of built-in Remote Deskto]("http://ubuntuforums.org/showthread.php?t=45565")
[x11vnc over SSH on Ubuntu]("http://z.cs.utexas.edu/users/habals/blog/index.php/linux/22")
[HOWTO x11vnc]("http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions")
[x11vnc: a VNC for real X display]("http://www.karlrunge.com/x11vnc/")

Some code I have installed (and am removing and retrying again):

Xsetup:
```
xhost +localhost
killall x11vnc &>/dev/null
x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -scale 4/5 -scale_cursor 1 -desktop dumassx2 -bg
```

Xsession:
```
killall x11vnc &>/dev/null
x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -scale 4/5 -scale_cursor 1 -desktop dumassx2 -bg
```

/etc/X11/xdm/xdm-config (changes) commented displaymanger.requestport for some reason
```
! SECURITY: do not listen for XDMCP or Chooser requests
! Comment out this line if you want to manage X terminals with xdm
! DisplayManager.requestPort:    0
```

/etc/X11/xdm/Xaccess uncommented this line so X was insecure? let anybody login
```
*                                       #any host can get a login window
```

/etc/xinetd.d/x11vncservice
```
# default: off
# description:
service x11vncservice
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -q -display :0 -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
        disable         = no
}
```

The above directory /var/lib/xdm/authdir/authfiles exists, but that file doesnt.  I pulled this from a gentoo description for the location of the xdm MIT-MAGIC-COOKIE


$ startx &
$ xauth:  creating new authority file /home/drew/.serverauth.5208

X: user not authorized to run the X server, aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

$ X -query :0
X: user not authorized to run the X server, aborting.

---

### Post by krunge on 2007-09-02
I'm not sure if you are doing all of those things simultaneously or not.  Doing separate solutions together may cause problems.
 
Here are some steps I think will get you what you want.

- Get rid of /etc/xinetd.d/x11vncservice completely.  we will not need inetd.

- Undo all of your changes to /etc/X11/xdm/Xsession

- Undo all of your changes to /etc/X11/xdm/xdm-config and Xaccess too.

- Make sure your firewall allows TCP connections to port 5900 (or use an SSH tunnel)

Put this in your /etc/X11/xdm/Xsetup file (this is the only file that needs to be changed)

```
x11vnc -rfbauth /path/to/.vnc/passwd -rfbport 5900 -shared -forever -desktop dumassx2 -bg -o /var/tmp/x11vnc.log
```

I got rid of -nowf because it will slow you down (I assume you are using a real h/w video card).

I also got rid of -notruecolor because that only applies to a very rare problem in 8 bit color.

I added "-o /var/tmp/x11vnc.log" so you will get debugging output into that file.

If you really want to scale the desktop size by 4/5 put the -scale options back in.  I also got rid of -norc since I doubt you want that.

If you haven't created the password file yet, do:

```
x11vnc -storepasswd  /path/to/.vnc/passwd
```

it should prompt you for the password.

Probably best to reboot to restart all of the services.

This is all from the 'Continuously:" section of: [http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

If that doesn't work post back here.   Also check the /var/tmp/x11vnc.log file for useful information.

---

### Post by hebetude on 2007-09-03
Thanks for the response

I got the impression that xdm is aging, so I switched to gdm and had it up pretty quick.  Of course, there still is no one guide that got me through that process :).  Based on what I've learned so far, the above solution will probably work for booting up.  However, once you attempt to login through VNC inside X, x11vnc will die because it does not have access to the Xsession the user has just started.

Basically, I have two x11vnc start to get in from a cold boot.  One pops up showing the login for gdm/xdm, this one exits (and kicks you out) after you login to gdm/xdm.  You relogin to VNC to a new x11vnc process that is part of the start scripts for whatever desktop manager you are using xfce4/gnome/kde.  This second process must have access to your Xauthority.  This second one will not work if KillInitClients=true in gdm.conf or gdm-cdd.conf.  The xdm equivalent to this is the last line in xdm.conf.

---

### Post by krunge on 2007-09-03
Are you saying KillInitClients=false in gdm.conf (or gdm*.conf) no longer allows x11vnc to remain attached after the user logs in?

And are you saying xdm now has a "Kill Initial clients" setting?  If so, could you post the config line?  And also post the full path and name of the file, I can't find an "xdm.conf" file, only "xdm-config".

---

### Post by hebetude on 2007-09-05
xdm does not have a KillInitClient that I know of, I switched to gdm b/c I couldn't get past this step in xdm.  Nobody uses xdm anymore?

---

### Post by lns on 2007-09-11
*rant*

I honestly don't see why VNC/Vino can't be natively integrated at the GDM level. How can anyone figure that having to log in locally first to get a remote session working (via Vino) is productive at all?

IANAP, but with the many HOWTOs out there on getting VNC going at the GDM level, tunneling through SSH, etc... that normal users still have to manually install this stuff, configure /etc/gdm/gdm.conf, etc. to just be able to reboot remotely and log in via VNC. It's stuff like this that makes Linux look like it's still in the stone age.

*/rant*

P.S. I'm really sorry if I am offending anyone out there, especially if you work on Gnome... It's not my intention to flame or point the finger. If this is a technically complex task, then I'd love to hear why, though, since like I said - there are many HOWTOs out there that require configuration, alternate VNC server installation, etc...I can imagine a single checkbox in "System --> Administration --> Login Window --> Remote", though, that says "Allow remote connections via VNC", which would essentially set everything up for you.

---

### Post by MetalMusicAddict on 2007-09-11
I myself just put **x11vnc -forever** in the startup session and have a user log in automatically.

Or you could SSH in, start VNC then connect.

---

### Post by lns on 2007-09-11
This would be nice in single-user situations, but for ones like mine (where there are ~200 users on the system), this would be a security/management nightmare... :(

> **MetalMusicAddict said:**
> I myself just put **x11vnc -forever** in the startup session and have a user log in automatically.

Or you could SSH in, start VNC then connect.

---

### Post by krunge on 2007-09-12
> I honestly don't see why VNC/Vino can't be natively integrated at the GDM level....I can imagine a single checkbox in "System --> Administration --> Login Window --> Remote", though, that says "Allow remote connections via VNC", which would essentially set everything up for you.

Yes. For some reason neither the Desktops nor the Distros have this as a high priority... even though it would be simple to implement.

Perhaps not the biggest reason, but I think the fact that after all of these years VNC still doesn't have integrated encryption/security is a deterrent to enabling things like this.  E.g.  even with the easy config you describe, the user would still have to rig up his own SSH tunnel from the viewer side if he wanted a secure connection.

I have some kludges in my ssvnc package [http://www.karlrunge.com/x11vnc/ssvnc.html]("http://www.karlrunge.com/x11vnc/ssvnc.html") to try to make this easier from a user level that you may want to look at.  But not being integrated in at the Distro or Desktop level it is still far from the easy configuration that you describe.

---

### Post by lns on 2007-09-12
Thank you for your reply krunge.. I will take a look at your package, as VNC encryption is still sorely lacking (as I am sure a lot of people already know). Integrating this into the GUI level, I see another "vision" under "Remote Session via VNC", a checkbox that says "Use SSH Encryption". ;) I am absolutely positive that this is a bigger feat than I can imagine, implementing it, but it seems that this should be a high priority (and somewhat of a niche market for Ubuntu if they were able to do it before the other distros). Encrypted graphical remote sessions is a *must* for so many businesses/IT Professionals that....well, I already expressed how I felt. =) I wouldn't mind chipping into a collective 'pot' for them to implement this stuff, either. I'm sure a lot of people wouldn't mind! I wish Canonical still had their bounty page. :(

> **krunge said:**
> Yes. For some reason neither the Desktops nor the Distros have this as a high priority... even though it would be simple to implement.

Perhaps not the biggest reason, but I think the fact that after all of these years VNC still doesn't have integrated encryption/security is a deterrent to enabling things like this.  E.g.  even with the easy config you describe, the user would still have to rig up his own SSH tunnel from the viewer side if he wanted a secure connection.

I have some kludges in my ssvnc package [http://www.karlrunge.com/x11vnc/ssvnc.html]("http://www.karlrunge.com/x11vnc/ssvnc.html") to try to make this easier from a user level that you may want to look at.  But not being integrated in at the Distro or Desktop level it is still far from the easy configuration that you describe.

---

### Post by krunge on 2007-09-13
> Integrating this into the GUI level, I see another "vision" under "Remote Session via VNC", a checkbox that says "Use SSH Encryption".

Yes, although my ssvnc GUI is quite an ugly duckling (you'll see...), I would claim it has that, and a "Use SSL" encryption option too. Actually you basically can't run it w/o SSH or SSL encryption.

The 'Terminal Services' mode for it is rather new, but it does some nice things.  It assumes x11vnc 0.9.3 is available on the remote side and runs it for you via SSH, thereby automating much.

---

### Post by lns on 2007-10-15
Check out this HOWTO I wrote up about: VNC/GDM/SSH/inetd:

[http://ubuntuforums.org/showthread.php?p=3489584#post3489584](http://ubuntuforums.org/showthread.php?p=3489584#post3489584)

---

### Post by aavaliani on 2008-05-30
I had the same case. And opening tunnel for only 5900 was not enough. but it of course depends on your configuration. I think you can open 5800 for http, and 5901 (configured for your resolution)

---

