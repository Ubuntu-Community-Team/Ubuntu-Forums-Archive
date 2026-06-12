---
title: "Signal not working with X11 forwarding"
date: 2021-04-29
forum: General Help
---

### Post by cbraxton on 2021-04-29
I've been trying to run signal, which is a snap application, via X11 forwarding. However when running "*ssh -X user@remote-computer /snap/bin/signal-desktop*", signal opens up on remote-computer instead of the one that ssh is run from. Other applications do forward with no problem using the same type of invocation. Is there some mystical incantation needed to get signal to work with X11 forwarding?

This is on Ubuntu Mate 16.04. (Yes, I know it's old but I'm not ready to reinstall this PC with the latest yet and will be signing up for Ubuntu Advantage for a while to get security updates.)

---

### Post by TheFu on 2021-05-01
You need to symlink the Xauthority file.  Let me look up the specifics.
.... 
```
# ##############################################
#   ####  Not working over remote X11 due to ~/.Xauthority problems
#   ## log into the remote system and setup the .Xauthority
cd ~/snap/chromium/current
ln -s ~/.Xauthority
```

That's for chromium. Do something similar for other snaps.

---

### Post by ActionParsnip on 2021-05-01
Is 16.04.x still supported?

---

### Post by TheFu on 2021-05-01
> **ActionParsnip said:**
> Is 16.04.x still supported?

It depends.
Core libraries used in server are under ESM.
Gnome3 DE is for a few more months. Probably thru June.
Mate is not.

---

### Post by deadflowr on 2021-05-01
> Gnome3 DE is for a few more months. Probably thru June.
Not on 16.04.
That ended years ago, like mate.

Edit: I guess you might have meant unity, in which case, sure, probably supported for while longer.

---

### Post by TheFu on 2021-05-01
> **deadflowr said:**
> Not on 16.04.
That ended years ago, like mate.

Edit: I guess you might have meant unity, in which case, sure, probably supported for while longer.

The 1, main, DE, supported in the LTS release has been advertised as 5 yrs of "standard" support with either 3 or 5 more yrs of "extended" support for packages in the main and xxxx (not Universe) repos. Most DE flavors get 3 yrs.

If 16.04s main DE was Unity, then that is what I meant. Sorry.
Would be nice of the **ubuntu-support-status** tool was clearer on what "group" of packages was supported or not.  Few people keep up with which repo any specific package is from. I don't.  I just know which are snaps because of all the problems I've had.
In 20.04, the tool was renamed to **ubuntu-security-status**. It provides accurate answers, that aren't exactly useful to normal people.

For 20.04:
```
$ ubuntu-security-status 
2248 packages installed, of which:
1646 receive package updates with LTS until 4/2025
 590 could receive security updates with ESM Apps until 4/2030
   7 packages are from third parties
   5 packages are no longer available for download
```
Handy, but not exactly useful.  The command output says that -v is a supported option, but no magic incantation of that with options has produced anything except an error.

**The short answer is - move off any 16.04 ASAP.**
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes) says:

> 
**Support lifespan**
Ubuntu 16.04 LTS will be supported for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Core, and Ubuntu Kylin. All other flavours will be supported for 3 years. 

---

### Post by cbraxton on 2021-05-05
> **TheFu said:**
> You need to symlink the Xauthority file.  Let me look up the specifics.
.... 
```
# ##############################################
#   ####  Not working over remote X11 due to ~/.Xauthority problems
#   ## log into the remote system and setup the .Xauthority
cd ~/snap/chromium/current
ln -s ~/.Xauthority
```

That's for chromium. Do something similar for other snaps.

Thanks, that worked!

---

