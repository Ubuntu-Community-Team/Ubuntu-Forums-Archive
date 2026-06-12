---
title: "Desktop Access via Web Browser Using VNC"
date: 2008-05-02
forum: General Help
---

### Post by trmentry on 2008-05-02
I've been Googling and searching and now have myself totally confused on how to do what I'm looking to do.

I'm wanting to setup a ubuntu server w/ a stripped gnome/x install to allow users to connect to the desktop via a web browser.  I know that I need vnc, but I've read many different ways of getting it setup and not exaclty sure which one to use.
 
This is the apt-get command I ran after installing ubuntu-server-amd64

```

apt-get install xorg gnome-core gdm firefox synaptic menu konsole wireshark tshark likewise-open gnome-nettool screen

```

basicly this server is going to be for packet captures.  so I don't need all the other stuff in ubuntu-desktop.

I'm not wanting to have the users that will have access to this box to install a vnc client on their desktops, partially due to they don't have rights to.   So, since they have browsers, I know I can access vnc servers with a browser, but I can't figure out the right way to do that with ubuntu.

SLES10 has it built in out of the box which is slick, but we're not wanting to use SLES.  


Please help.

Thanks

---

### Post by MSumulong on 2008-05-02
I think you might want to try installing this package on your VNC server:

[http://packages.ubuntu.com/hardy/vnc-java](http://packages.ubuntu.com/hardy/vnc-java)

And here's a HOW-TO to help you install it:

[http://ubuntuforums.org/showthread.php?t=107503](http://ubuntuforums.org/showthread.php?t=107503)

Hopefully this is what you're looking for.

---

### Post by Monicker on 2008-05-02
I don't think vino, which is integrated into gnome for vnc support. allows for connecting via a web browers.  You could install the vncserver and vnc-java packages, which should give you that functionality.  The clients will need to have java support in their browsers in order to run the applet.

---

### Post by trmentry on 2008-05-02
> **MSumulong said:**
> I think you might want to try installing this package on your VNC server:

[http://packages.ubuntu.com/hardy/vnc-java](http://packages.ubuntu.com/hardy/vnc-java)

And here's a HOW-TO to help you install it:

[http://ubuntuforums.org/showthread.php?t=107503](http://ubuntuforums.org/showthread.php?t=107503)

Hopefully this is what you're looking for.

On that How-To it says to go to  System -> Preferences -> Remote Desktop

however on my stripped down gnome, I don't have those options.  Plus on my old Gutsy desktop I had enabled the remote desktop thing but could only connect to it if I was logged in already on the desktop.  I couldn't logon remotely.  Will that still be the case?

I'm wanting to be able to pull the logon screen via the browser and logon as if I was on the console.

---

### Post by MSumulong on 2008-05-03
> **trmentry said:**
> On that How-To it says to go to  System -> Preferences -> Remote Desktop

however on my stripped down gnome, I don't have those options.  Plus on my old Gutsy desktop I had enabled the remote desktop thing but could only connect to it if I was logged in already on the desktop.  I couldn't logon remotely.  Will that still be the case?

I'm wanting to be able to pull the logon screen via the browser and logon as if I was on the console.

Use the following command to enable remote desktop:
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

And this link explains how to enable VNC from the login:
[https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c](https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c)

---

### Post by trmentry on 2008-05-06
Ok.. I'm just about at my wits end. 

I'm following this:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

First off, I'm just trying to get VNC to work with vncviewer from a windows client.  

I want to be able to have the gdm logon screen shown when I connect via vncviewer so that multiple people can logon at the same time if needed.  and not have to be logged on already, etc.

that being said, I followed the "VNC Server with Login Screen via GDM"

But it doesn't appear to work.  I don't get a logon.  I tried to shutdown xinetd and then do the 

Xvnc :1 -fp /usr/share/fonts/X11/misc/  

I was able to connect to 5901, but no logon screen, just a gray X type background.  

Re-enabled xinetd and the server is listening on 5901 as I can telnet localhost 5901 and connect.  

so what am I missing here?   At this point, I could care less about the web gui thing.  I just want to be able to vnc to the machine and get a logon like I'm sitting on the console without having to be logged in already.

thanks

---

### Post by timcredible on 2008-05-06
how about having the users install an XDM client?  XDM is native to unix/linux, while vnc is not.  if you have to use a browser, continue on looking at vnc, but XDM is already on your linux machine.  more info [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27").

---

### Post by yeehawjared on 2008-05-06
so question... has anyone been able to successfully create a VNC server on hardy heron which can be controlled via a browser?

---

### Post by JawsThemeSwimming428 on 2008-05-06
You may want to have a look at this thread on the Mepis forum...[http://www.mepislovers.org/forums/showthread.php?t=13076](http://www.mepislovers.org/forums/showthread.php?t=13076)

---

### Post by trmentry on 2008-05-10
> **JawsThemeSwimming428 said:**
> You may want to have a look at this thread on the Mepis forum...[http://www.mepislovers.org/forums/showthread.php?t=13076](http://www.mepislovers.org/forums/showthread.php?t=13076)


I like the NXServer solution.  The free one I know only allows for 2 remote connections.  But it appears to only allow the first 2 users to use it to log back on.  New users get that there are too many connections and get disco'ed/

I have the knob set to get rid of stale connections to 1 but that doesnt' appear to work.. ANd there really isn't any type of open source support for the NX product... ie forums.  

Any ideas?

Also it appears that XDMCP is buggy.  Sometimes users get a desktop.. other times just a tan back ground.  I've been reading that this may be something to do with gnome-settings-daemon not starting... but not sure.  Hardy appears to have some issues with remote GUI access.  At elast from the 2 weeks that I've been beating on this.

---

