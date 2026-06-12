---
title: "Help a new user with a couple of issues?"
date: 2008-06-26
forum: General Help
---

### Post by Deicist on 2008-06-26
Hi all, just installed Hardy on my work laptop, an HP pavilion dv2045ea, and I've got to the stage where I'm left with a couple of niggling problems.

1) the wireless card doesn't switch on with the button on the front panel.  To get it working I have to do this:

```
\sudo rmmod -f iwl3945
\sudo modprobe iwl3945 disable_hw_scan=1
\sudo ifconfig wlan0 up

```

Every time I boot.  A little annoying.  Is there a way to get this interface to come up either automatically, or with the little slider switch?

2) Also relating to the network connections.  Hardy has the wonderful habit of automatically selecting the best network connection based on what's plugged in to your machine.  For example, if you're on a wired connection and disconnect you'll automatically switch to wireless, then you'll switch back to wired when you reconnect.  Unfortunately I have a windows mobile device.  When I plug this into my USB port (for recharging) Ubuntu decides that I want to connect to the virtual ethernet port presented by the device and drops my wireless connection.  Any way to stop it doing this?

3) Ideally I'd like to be able to authenticate my machine with a windows domain.  This isn't a deal breaker, but if it's possible (and easy for a linux noob like myself to accomplish) then I'd like to give it a go.  Is it possible?  I understand Xandros is possibly the easiest distribution to authenticate to a domain with... however, I've fallen for the Heron now... 

4) This one is low down the priority list.  I have an IP softphone (an inter-tel 8602) that doesn't have a linux alternative (that I know of) and that I can't get working with Wine (I get a visual c++ runtime error, despite lots of playing with winetricks etc etc) anyone got any experience with this particular software?

I think that's about it for now :)

---

### Post by conscious on 2008-06-26
For 1) you can create the following script:

```
#!/bin/sh
rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1
ifconfig wlan0 up
```

And then follow the procedure described [here]("http://ubuntuforums.org/showthread.php?t=178682") to have it run at startup.

---

### Post by Deicist on 2008-06-27
Annoyingly, it seems I need to power the wireless on using the front panel switch before running those commands, So running them at startup doesn't work.  Annoying. 

Thanks for the help though :)

---

### Post by cpetercarter on 2008-06-27
I guess you have thought of this, but you could create a launcher which runs the script. Then a simple click on the launcher would switch your wireless card on, instead of needing to use the terminal.

---

### Post by Deicist on 2008-06-27
Yus, that's how I have it setup now :)  

I've just discovered another issue actually, I can't rename my workspaces.

If I go into the workspace switcher preferences I just see 2 spinners, one for 'columns' and one for 'rows'...there's no option to rename them.  

Anyone know what I'm doing wrong with that?

---

