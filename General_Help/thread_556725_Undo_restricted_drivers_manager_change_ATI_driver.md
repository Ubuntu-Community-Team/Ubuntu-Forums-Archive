---
title: "Undo restricted drivers manager change ATI driver"
date: 2007-09-21
forum: General Help
---

### Post by n411303 on 2007-09-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/edgy/+source/xserver-xorg-video-ati/+bug/67487](https://bugs.launchpad.net/ubuntu/edgy/+source/xserver-xorg-video-ati/+bug/67487) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My recent installation of Feisty Fawn was working but I checked the box to activate an ATI driver I found in the Restricted Drivers Manager window.  Since then I have been unable to get back into Linux with a GUI.  Symptoms are  very like Bug #67487.  

I would like to get back into GUI and uncheck the box.  I am new to Linux.  In windows I would reboot in safe mode and reverse my changes but I do not know how to do this in Ubuntu.  

I am able to boot to a command terminal by booting in recovery mode.  I know how to logon but not sure where to begin to sort the problem.

I have a home LAN and could remote onto the problem computer if I knew how to authorise remote connection from either windows or another feisty client. 

Does anyone have a quick easy to follow way to reverse this tiny change in my settings that is stopping me using GUI.

Tom

---

### Post by n411303 on 2007-09-22
Ok I am sorted back in to the GUI.  For the benefit of other newbies I found this in /etc/X11/xorg.conf 

quote
If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
unquote

Running the command from a console I got to from a recovery boot rebuilt my video config.  I had to select VESA and I am not sure I chose all the right screen resolutions but I now have basic GUI back.

For info running: lspci 

reports my graphics info as:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

Searches on this card on the web do not currently give me much comfort I can get it going with a decent driver.

If anyone is aware of some news on this please add a post.

Tom

---

