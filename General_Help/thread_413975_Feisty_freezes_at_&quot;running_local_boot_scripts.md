---
title: "Feisty freezes at &quot;running local boot scripts&quot;"
date: 2007-04-19
forum: General Help
---

### Post by Tronfi on 2007-04-19
Hi all, I've really searched about it, but i can't get a solution.

I've upgraded to Feisty, and when I was ready to look how feisty looks, Ubuntu couldn't boot. It seems that all the process is normal, but when it's "Running local boot scripts (/etc/rc.local)" it gets freezed and nothing happens, so I can't use any shell (tty2,3,4... doesn't work either).

I've tried to do something in recovery mode, but I don't know what more can I do. I hope you can help me. Thanks!

---

### Post by coxy on 2007-04-20
Same here, I have done a command line only install with the alternate Kubuntu Feisty disc and it stops at the same place.

---

### Post by coxy on 2007-04-20
This script does nothing! If you press enter then the boot will continue. I tried changing the script but then it just failed. If anyone has any ideas then please let us know.

Thanks.

---

### Post by MrCreosote on 2007-04-22
Actually you don't even need to press enter. I installed 7.04 server on a headless box and it works even if it stalls on this line.I can connect with open ssh and everything.. it's just annoying. Hopefully it will be fixed soon.

peace.

---

### Post by Slim Odds on 2007-04-22
> **coxy said:**
> This script does nothing! If you press enter then the boot will continue. I tried changing the script but then it just failed. If anyone has any ideas then please let us know.

Thanks.

What's in the file (/etc/rc.local)? How do expect to get help without telling us?

---

### Post by rshields on 2007-04-23
I'm having the same problem, but hitting enter does not bring up a login prompt for me. The only way I can boot is in safe mode. 

> **Slim Odds said:**
> What's in the file (/etc/rc.local)? How do expect to get help without telling us?

Mine has "exit 0" in it. However, this script is not the problem since it finishes running it with an [OK], so I guess something after this script is causing the problem. I'm not really sure where to start debugging the problem.

---

### Post by pteglia on 2007-04-27
I am getting the exact same error, on my newly upgraded Feisty server, and although I can ssh in, I would like to be able to log in directly.  The file contains: 

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

Which, as you can see, is nothing.

Help!

---

### Post by James Keating on 2007-04-30
The problem probably is not the script.

rdejean found the solution ([http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2540263)](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2540263)).

The boot process would hang after the last script in /etc/rc2.d, no matter which script that was. (I have put the nosplash option in /boot/grub/boot/menu.lst, so I can see the boot messages.)
Earlier in the boot process, I would get the messages
init:/etc/event.d/tty1:13: Unknown stanza
init:/etc/event.d/tty2:13: Unknown stanza

The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines were
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should have been
exec /sbin/getty 38400 tty1
respawn

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

This seems to be a known bug. The release notes ([http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)) say:
Users who have serial consoles, or have made custom changes to the /etc/inittab file or files in the /etc/event.d directory should be aware that the format of these files have changed slightly and your changes will not be automatically migrated. Bug #89314. The following changes should be made.
"respawn COMMAND" should be changed to "exec COMMAND" with "respawn" on a seperate line.
"on EVENT" should be changed to "start on EVENT"
the "runlevel-X" events should be changed to "runlevel X"

I only changed inittab to comment out all but the first two tty processes (# 3:23:respawn:/sbin/getty 38400 tty3) to not waste the memory. I didn't make the kind of change Ubuntu warned about, but it seems to have been enough.

---

### Post by rshields on 2007-07-12
Nice work, James, that's fixed it. Thanks for your help.

The only edit I had made to inittab was to change the default run level, but that was enough to do it.

---

### Post by Lenz_Kappov on 2007-07-15
I'm a noob still having problems with this one.  I've freshly installed Ubuntu Server version 7.04 with the LAMP option (but not DNS server), and cannot edit the tty1 .. tty6 files because vi tells me "Warning: Changing a readonly file".  Also I don't have an inittab file in etc.  Is that significant?  I'm wondering if I have a wonky distro or a bad install CD or something.

Any hints appreciated.

---

### Post by inyoka on 2007-07-24
> **Lenz_Kappov said:**
> I'm a noob still having problems with this one.  I've freshly installed Ubuntu Server version 7.04 with the LAMP option (but not DNS server), and cannot edit the tty1 .. tty6 files because vi tells me "Warning: Changing a readonly file".  Also I don't have an inittab file in etc.  Is that significant?  I'm wondering if I have a wonky distro or a bad install CD or something.

Any hints appreciated.

You need to run vi or vim with the sudo command (ie. as the root user):-
*sudo vim /etc/event.d/tty1*
Feisty doesn't use the **inittab** file anymore, instead it uses the upstart system so don't worry about the file being missing.  Only people who did an upgrade from Edgy have the file, and I believe they can safely delete it.

---

### Post by mdknaebel on 2007-07-27
This happens for me too but when trying to boot into Ubuntu 6.10 on a Mac...

Any Ideas?

---

### Post by sameer.iitg on 2007-08-06
Hi, I am a newbie and have just installed Ubuntu feisty fawn. My problem is that when I boot the system, all I see is a black screen with only the circular mouse tool tip text. However all other non-gui consoles are working fine. The system is struck after the same line as mentioned in the posts above (running local scripts). Also  I had already made the above mentioned changes in /etc/event.d/tty1 to tty6. 

Initially when I had installed the system, everythig was working fine, but it failed to restart after doing system updates. Kindly suggest me about the problem and its solution. Also please mention if you need more info.

Thanks in advance
Sameer

---

### Post by cleverlyinsane on 2007-08-11
I have the same problem, ihave tried pressing esc at the beginning to try to boot with different kernel, no difference What else can i do? I am not a programmer so not sure how to use the command line I dont mind reformat if i can get my old files out first thanksDanfound my way to a terminal like command line pressctrl   ALt  f1

---

### Post by rybu on 2007-09-04
I'm having the same problem, too.  

I just installed Ubuntu 7.10 on my thinkpad 61p.  It was running fine but after a recent round of apt-gets, I had the same problem as the original poster.   I used James Keating's advice and that now boots the system into safe mode.  X doesn't start automatically anymore.  But if I type in startx, everything is alright.  Actually, more than alright... it seems my video drivers were updated and I don't remember asking for that.   I'm now in native 1920x1200 mode. 

One strange thing is happening is ubuntu seems to be tweaking the brightness of my monitor on and off now and it seems to be triggered by near random events... This is the wrong thread for this, though...

---

### Post by lorenzone92 on 2007-11-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/164980](https://bugs.launchpad.net/ubuntu/+bug/164980) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've the same problem with Ubuntu 7.10...

This is what I see:

* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
* Checking battery state... [OK]
* Running local boot scripts (/etc/rc.local) [OK]
_

...and it freezes!

I tried to login and type "startx" but the monitor started to report "Bad synchronization"; I tried to change the monitor with another and also the new one reported "frequency not supported"

What can I do?

---

### Post by lovag on 2007-11-30
I am in the same situation.
I had a working Ubuntu installation. this is a server, no X installed. ssh, ftp installed.

I was working remotely  - via ssh - and installing apache & mysql. Install was OK.
Then next morning I could not log in (via ssh). I found out that there was a power shortage. 
So, I had to go to the office to have physical access.
The server was booting properly until the point of saying:
* Running local bootscripts (/etc/rc.local) [OK]

My rc.local file is empty (just exit)

If I press enter I have login prompt. 

SSH service is not started during the boot process! It is there, having priority 20. (/etc/rc2.d/@S20ssh)
I was able to start manually the openssh server: /etc/init.d/ssh start).

Changing the priority from 20 to 19 solved the problem (ssh daemon was started on reboot).
But I wonder, could be that other services suffer in the same way? I don't like the idea to check each and every service if it started properly of not... that should the system do...

Update: I changed back the priority from 19 to 20. and wonder - ssh service did started up...
Do I have to recreate all the start-up links in /etc/rc?.d to make shure all services working properly???


Please help.

---

### Post by lovag on 2007-11-30
I have the same situation.
A working new Ubuntu server, no X, just openssh & apache & mysql & ftp.
After a power shortage the server acting strange.

The same symptoms: boot process freeze after finishing /etc/rc.local [OK]
my rc.local file is empty (only exit)

Pressing [enter] will bring up login prompt, but openssh is not started!

SSH daemon can be started manually (/etc/init.d/ssh start).
The symlink /etc/rc2.d/S20ssh was on place (and all other init level startup symlinks).
Recreating this file ,executing the following commands:
{{{
update-rc.d -f ssh remove
update-rc.d ssh defaults 20
}}}
solved my ssh related problem (on reboot now ssh started as should).

But, still boot freezes after :
Running local boot scripts (/etc/rc.local) [OK]

I wonder, maybe there are other problems too, not that obvious like not starting up ssh daemon. How can I be sure that everything is back to normal?

thanks for help

---

### Post by lovag on 2007-11-30
I have the same situation.
A working new Ubuntu server, no X, just openssh & apache & mysql & ftp.
After a power shortage the server acting strange.

The same symptoms: boot process freeze after finishing /etc/rc.local [OK]
my rc.local file is empty (only exit)

Also, I checked (following instructions from this thread) that my /etc/event.d/tty1 (and other tty? files too) has at the end these files:
respawn
exec /sbin/getty 38400 tty1

Pressing [enter] will bring up login prompt, but openssh is not started!

SSH daemon can be started manually (/etc/init.d/ssh start).
The symlink /etc/rc2.d/S20ssh was on place (and all other init level startup symlinks).
Recreating this file ,executing the following commands:
{{{
update-rc.d -f ssh remove
update-rc.d ssh defaults 20
}}}
solved my ssh related problem (on reboot now ssh started as should).

But, still boot freezes after :
Running local boot scripts (/etc/rc.local) [OK]

I wonder, maybe there are other problems too, not that obvious like not starting up ssh daemon. How can I be sure that everything is back to normal?

thanks for help

---

### Post by lorenzone92 on 2007-12-05
I've tried Ubuntu Hardy Heron alpha 1 and it works! ;)

---

### Post by soaringphx on 2007-12-12
I had this problem as well on my Dell Inspiron B130 with Gutsy installed.  I tried everything I could find on the internet, including changing all of the tty files by switching the order of the last two lines.  Nothing worked, but finally I found [_this page_]("http://www.techiemoe.com/tech/macbookub.htm") and tried ```
sudo dpkg-reconfigure xserver-xorg
``` and chose all the default options.  Then I ran ```
startx
``` and my desktop came back!  I am completely new to Ubuntu, so I don't know if this is the best way, but everything seems to be working normally again.

---

### Post by netvampire on 2007-12-31
> **soaringphx said:**
> I had this problem as well on my Dell Inspiron B130 with Gutsy installed.  I tried everything I could find on the internet, including changing all of the tty files by switching the order of the last two lines.  Nothing worked, but finally I found [_this page_]("http://www.techiemoe.com/tech/macbookub.htm") and tried ```
sudo dpkg-reconfigure xserver-xorg
``` and chose all the default options.  Then I ran ```
startx
``` and my desktop came back!  I am completely new to Ubuntu, so I don't know if this is the best way, but everything seems to be working normally again.



that worked great

---

### Post by Kaz3noRei on 2008-02-24
sudo dpkg-reconfigure xserver-xorg

works great for me too
apparently i forgot that i installed a new graphic card, and this seems to be the problem. after i reconfigure the xserver, i can enter the low grapchic mode and then install the nv driver from there.
thanks :)

---

### Post by remali on 2008-04-04
Worked great for me too..
Saved me....
Thanks a lot

---

