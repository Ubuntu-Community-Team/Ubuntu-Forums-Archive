---
title: "using Vnc"
date: 2008-03-17
forum: General Help
---

### Post by chazn85 on 2008-03-17
In my quest to finally move completley away from windows i have encountered another problem.

first what i am trying to do.

I need to be able to access my PC (running ubuntu) from remote locations (work etc) using my laptop (windows).  I have previously used VNC when i was running windows on both.  

I have installed vncserver on ubuntu and can access via my windows machine when i have no password set under system>prefs>remote desktop.  As soon as a password is set it always gives me an authentication failure.  i can ssh from the laptop to the PC with port forwarding via putty but unsure of what or where im going wrong.  

Many thanks

---

### Post by Joeb454 on 2008-03-17
what VNC client are you using?

I've found Ultra VNC (on Windows) works well to connect to an Ubuntu PC :)

---

### Post by chazn85 on 2008-03-17
i have tried both ultra vnc and realvnc.

---

### Post by chazn85 on 2008-03-17
does anyone have any ideas?

---

### Post by chazn85 on 2008-03-17
can anyone help me

---

### Post by bodhi.zazen on 2008-03-17
Not sure where you are having a problem.

system>prefs>remote desktop = vino (not vncserver)

Here are some helpful links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by chazn85 on 2008-03-17
i appreciate the help.

i tried following the vnc via ssh link but the thing im getting is i can connect with no password but tryinh with a password and i get an authentication failure

---

### Post by heatpumpcontrol on 2008-04-04
Hi there, same here. I'm using [this]("http://ubuntuforums.org/showthread.php?t=383053&highlight=terminal+sever+will&page=6") howto which uses portaputty and vncviewer through SSH tunneling. It works well when I don't have a password set on the server..Gutsy remote desktop- but as soon as I set a password I get Athentication failure.

Anyone please... I can't find anything related to this....ELLLLLLLP

---

### Post by heatpumpcontrol on 2008-04-05
> **heatpumpcontrol said:**
> Hi there, same here. I'm using [this]("http://ubuntuforums.org/showthread.php?t=383053&highlight=terminal+sever+will&page=6") howto which uses portaputty and vncviewer through SSH tunneling. It works well when I don't have a password set on the server..Gutsy remote desktop- but as soon as I set a password I get Athentication failure.

Anyone please... I can't find anything related to this....ELLLLLLLP

Found a thread where someone suggested the following:

Clear the Remote Desktop password check box

Recheck the box and enter your password and hit the Return key on your keyboard then Close.... You have the hit the Return key for some reason.... it has worked for me but not others.... you may want to try it.

---

### Post by waltmawk on 2008-05-06
My discovery is that the password field for vino-preferences only allows eight characters, thus the authentication failure I experienced when attempting to use password longer than  eight characters.  Hope this helps.

Wade

---

