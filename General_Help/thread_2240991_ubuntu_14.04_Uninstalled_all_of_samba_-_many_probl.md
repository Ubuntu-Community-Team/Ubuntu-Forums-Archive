---
title: "ubuntu 14.04: Uninstalled all of samba - many problems - it left behind a mess"
date: 2014-08-23
forum: General Help
---

### Post by rewtedesco on 2014-08-23
After the usual unsuccessful struggle with samba (trying to connect two machines on a LAN both running ubuntu 14.04) I decided to start over and uninstalled all of samba and hoped for a new chance.  

First thing I noticed is that the login screen (after reboot) shows my name still as a "smbguest" or something like that, even though there should be nothing left of samba or smbclient, according to synaptic's list, and after cleanup, autoremove and what not runs with apt-get.  

The 2nd thing I noticed, which is actually a problem:  While ssh and scp still work from the console, the tool that can be found in the menu under "Connect to Server" does no longer allow anything, neither sftp://user@server, nor ssh://user@server, nor any other ways I tried - the button labeled "connect" simply isn't activated and remains grayed out. That was not the case before I first installed samba and then uninstalled it. 

At any rate, the documentation of samba is way too bloated and confusing for me to follow (240 pages!) and the numerous 1-2-3 helper guides on youtube or elsewhere seem to always not work for anything I'm trying. 

But at least I want my "good-old" sftp between machines back which allowed to move or copy files between computers by simple operations with the mouse. Am I asking for too much if I expect that samba, after being properly uninstalled by synaptics, which I also used to install it, could clean up after itself?

---

### Post by mcduck on 2014-08-23
My guess would be that while removing samba, smbclinet and everything related you also ended removing some of the SMB packages that are installed by default, breaking some of the network functionalities in the system.

The first thing to try would be checking that the ubuntu-desktop package is still installed, and reinstalling it if necessary.

---

### Post by rewtedesco on 2014-08-23
Thanks, that hint was helpful, but didn't solve the problem yet.  I found out now that if I start synaptic from the menu it will ask for the password for a user named "Samba guest account reiner" (which is my name). And then it stales after  I enter the sudo password. However, I can start it from the console as sudo synaptic, and it doesn't ask for the password (perhaps because i just made some different command with sudo from the same console). I found indeed that ubuntu-desktop was not installed. When I installed it, this triggered the installation of a few components associated with samba as well, among them samba-common. Yet, there is still no cigar: the "connect to server" feature still doesn't work.

---

### Post by rewtedesco on 2014-08-23
Also: I rebooted the machine, and on login it's still looking for the elusive "samba guest account reiner", but allows me to log on as usual. Fortunately I had used the same password for samba before as for the general login, that may be why. Yet, synaptic does now work from the menu.

And whow: You got the right hint: 

  Now I can use sftp://user@server from the connect to server menu. 
and after the reboot synaptic also works as normal.

Pretty good!  Thanks a lot. :p

I guess the rest, with the silly title "samba guest account reiner" is a different episode. There got to be some trick to reverse this, but it's more a problem of cosmetic, and I can live with this

---

### Post by mcduck on 2014-08-23
Sound good, at least you got the functionality back. :)

I have no idea about the "samba guest" stuff, I've definitely never seen it nor have I done anything complicated to set up SMB shares on my local network, (although I only use SMB for sharing a few folders so more complicated setups might of course require more tweaking), but if you can post the actual steps you did when trying to set it up, or the guides you followed, it might be easier to figure out how to get everything back to normal...

---

### Post by rewtedesco on 2014-08-23
Yes, I actually managed now to revert the "Samba guest account reiner" and replace it with my name: 

Now that the functionality of ubuntu-desktop is restored (see previous posts by mcduck) I could change the login title to whatever I want:

Chose "system settings"  ---> "user accounts" then click the unlock icon in the gui. After entering the superuser passwd, choose the user for which the features should be edited, and modify them. That did it.

(Careful though - I managed to inadvertently modify the password as well and then forget the new one for a while - the silly over acting thingy didn't allow me to reuse my good old and simple password, that's why. Fortunately, after a little swearing tantrum episode, and a calming short walk I could recall it ) 

I don't think I'll experiment with Samba any time soon again - it was a great waste of time.

Thanks to mcduck for the good hints and recommendations.

---

