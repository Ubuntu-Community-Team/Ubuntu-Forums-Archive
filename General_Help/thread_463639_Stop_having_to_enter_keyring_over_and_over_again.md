---
title: "Stop having to enter keyring over and over again"
date: 2007-06-03
forum: General Help
---

### Post by bishop9226 on 2007-06-03
Just making this so other people having this problem won't have to hunt around.  keywords: keyring wifi wireless e1505 password internet 

Append the following to the end of /etc/pam.d/gdm:
@include common-pamkeyring

steps - 

open terminal - 

# to install libpam-keyring enter:
> sudo apt-get install libpam-keyring

# and to modify the gdm login file do:
> sudo gedit /etc/pam.d/gdm

then it will open the file in a text editor.  add the line - 

> @include common-pamkeyring

to the end of the file w/o erasing the stuff above it.  save it and close. 

this only works if your keyring pw is the same as your login pw.  if it isnt, before doing any of this just delete your keyring - 

> rm $HOME/.gnome2/keyrings/default.keyring

then reboot and connect to your wifi, it will have you reset your keyring, make it the same as your login pw.  then do the steps above.  now you shouldnt have to enter your keyring each time you connect to a wifi and if you turned on auto-login then you shouldnt have to enter anything at all, just enjoy:)

---

### Post by necrolin on 2007-06-10
Thanks. This was exactly what I was looking for. Works like a charm.:KS

---

### Post by coffeecat on 2007-06-10
Let me add my thanks too. I've bookmarked this page for future reference.

I have one suggestion. This howto should be engraved on a piece of granite - about the size of the Rosetta stone would do. Then every Network Manager dev should be hit over the head with it. :evil: :wink:

---

### Post by bishop9226 on 2007-06-11
apparently if you want to have auto-login and not enter your keyring in you have to turn auto-login off first then do the keyring thing, then turn auto-login back on.  i thought it was one or the other but it doesnt seem so anymore.  if your computer makes you choose, just pick the one you dont mind doing every time you get on (for most ppl thats logging in).

---

### Post by pgn674 on 2007-06-11
I'm trying to get timed login and this trick working together, but they're not. I tried disabling timed login, and the keyring stopped popping up. But, when I re-enabled timed login, the keyring started asking for a password again.

I don't want to have the computer make me choose one or the other, I want to make the computer choose both :)  Oh well, guess I'll keep looking. I'll try to remember to post my ultimate answer here.

---

### Post by pgn674 on 2007-06-11
Ah-ha, got it. I got automatic login (timed login for me, 10 seconds) and the keyring manager working together. I followed post #68 here: [http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=7](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring+auto+login&page=7)

Here's what it says:
> 
Several people have asked how to get this to work with autologin. Making the same change to /etc/pam.d/gdm-autologin as to /etc/pam.d/gdm described at the start of the thread sort of works, but you do get asked for a password at login, so it isn't really automatic any more.

Instead I wrote this script:

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and added it to the session Startup Programs. Obviously it relies on being run after gnome-keyring-daemon starts but before nm-applet, but that seems to happen automagically for me.

So I don't need to enter a password at all any more! I know, I know, very lax security. But people who don't use gdm autologin might also find this method useful, because it means you can use separate passwords for logging in and for the keyring. And the script could probably be refined so as not to reveal the password in plain text.

You still need the libpam-keyring package for pam-keyring-tool. And I had to look at the source to find out how to use it. There's probably a way of doing the same thing using the dbus interface so you don't need libpam-keyring.

---

### Post by pvravi on 2007-06-25
[INDENT]this only works if your keyring pw is the same as your login pw.  if it isnt, before doing any of this just delete your keyring - 
[/INDENT]
Deleted the keyring. Keyring manager never asks me for a default or whatever password anymore. Not when I run the keyring manager, or when I configure a wireless network. How do I keyring manager to ask me for  a password and save my wireless connection info?

I upgraded to NetworkManager 0.65 (I wanted LEAP). Is that the cause? I dont think so, since at first NetworkManager 0.65 stored its leap password in Keyring Mgr!

Help, please!

---

### Post by vishalwarke on 2007-07-11
Thank you so much for this great trick.

---

### Post by woyzeckswoe on 2007-07-11
> **bishop9226 said:**
> apparently if you want to have auto-login and not enter your keyring in you have to turn auto-login off first then do the keyring thing, then turn auto-login back on.  i thought it was one or the other but it doesnt seem so anymore.  if your computer makes you choose, just pick the one you dont mind doing every time you get on (for most ppl thats logging in).

hi all,
isn't there a secure option to have both, autologin and keyring unlocked without entering a pword?

thankyou w'w

---

### Post by chadwick359 on 2007-07-12
For this, I deem you a sexy, sexy person. Thanks.

---

### Post by archiesteel on 2007-07-12
Any tips on how to do this in Kubuntu? That would be greatly appreciated. :-)

---

### Post by pgn674 on 2007-07-12
> **woyzeckswoe said:**
> isn't there a secure option to have both, autologin and keyring unlocked without entering a pword?

I don't know if the concept of security and having both auto-login really belong together. But, as the guy I quoted said, a more advanced scripter might know of a way to have the script work without having your password there in plain text.

A more advanced scripter, I am not.

---

### Post by Azakus on 2007-07-12
Hey, this made it on Digg's Frontpage!
[http://digg.com/linux_unix/Ubuntu_Stop_nm_applet_from_authenticating_with_the_keyring](http://digg.com/linux_unix/Ubuntu_Stop_nm_applet_from_authenticating_with_the_keyring)

---

### Post by caro on 2007-07-12
Great tip.  Thanks for sharing.

---

### Post by woyzeckswoe on 2007-07-17
> **woyzeckswoe said:**
> hi all,
isn't there a secure option to have both, autologin and keyring unlocked without entering a pword?

thankyou w'w

it worked for me too, i just forgot to make the script executable!

thanks

---

### Post by kolinab on 2007-07-18
Thank you for this great tip, I cannot believe I tolerated this condition in its untweaked state for so long.

---

### Post by ed67 on 2007-07-21
> **archiesteel said:**
> Any tips on how to do this in Kubuntu? That would be greatly appreciated. :-)

Set the kde wallet password to null.  Not the word "null", just leave it blank in both boxes.  Kubuntu will accept this.

---

### Post by onetb on 2007-08-24
I ran the following line:
rm $HOME/.gnome2/keyrings/default.keyring
because my keyring password was not set to the same as my login password.  Now, I cannot connect to my secured wireless network at all.  It doe not prompt me to reset the keyring password.  Does someone know what I should do?

---

### Post by dirtblack on 2007-09-05
I'm a noob that's learning and it was very easy to do. That worked out great!  Many Thanks Bishop.

---

### Post by nikef on 2007-09-05
> **ed67 said:**
> Set the kde wallet password to null.  Not the word "null", just leave it blank in both boxes.  Kubuntu will accept this.

hi thanks for this tip
i am running ubuntu with kubuntu desktop
kubuntu desktop is all i use,please can you tell me where to find the kde wallet as i seem not to have it

---

### Post by nikef on 2007-09-05
i found the kwallet :)

---

### Post by nikef on 2007-09-05
yes i have done it
pats self on back :) :)

thanks to the original op and  ed67 for helping me to do this 

now i don't have to log into ubuntu first 
straight on to kubuntu and the only password it asks for is the firewalls and i am well chuffed  :)  :guitar:

---

### Post by The Land of Smeg on 2007-09-09
This did not work for me, I am still prompted for the keyring password which is the same as my login password with automatic login disabled. I am using Ubuntu Feisty 7.04.

---

### Post by oliviacond on 2007-09-20
doesn't work for auto-login :(

---

### Post by fluteflute on 2007-10-20
> **oliviacond said:**
> doesn't work for auto-login :(

Oh thats why it isn't working for me! I would be very grateful for a solution for this.

---

### Post by JLoiac on 2007-10-29
> **bishop9226 said:**
> Just making this so other people having this problem won't have to hunt around.  keywords: keyring wifi wireless e1505 password internet 

Append the following to the end of /etc/pam.d/gdm:
@include common-pamkeyring

steps - 

open terminal - 

# to install libpam-keyring enter:


# and to modify the gdm login file do:


then it will open the file in a text editor.  add the line - 



to the end of the file w/o erasing the stuff above it.  save it and close. 

this only works if your keyring pw is the same as your login pw.  if it isnt, before doing any of this just delete your keyring - 



then reboot and connect to your wifi, it will have you reset your keyring, make it the same as your login pw.  then do the steps above.  now you shouldnt have to enter your keyring each time you connect to a wifi and if you turned on auto-login then you shouldnt have to enter anything at all, just enjoy:)

I am unable to login now.  I get an authorization error.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

### Post by TheDilettante on 2007-11-28
Did you get the 'Authentication Failed' box?

If so,

*ctrl+alt+F1* to get shell

login and then enter:

*sudo /etc/init.d/gdm stop*

then:

*startx*

then go undo whatever you just did.  I don't know how to fix the op problem, and have spent the whole day trying to make a default keyring profile while having no clue why I cannot login into the manager, but in the process I've locked myself out something like 8 times.

---

### Post by maddentim on 2007-11-28
I get Authentication Failed box at the gdm login screen.  I click "ok" and it just comes back.  I had to drop to shell and undo this.  Most bummed.  I was really hoping this would work.  :(

I really don't see a need to default to this behavior.  If I logged into the system, that is good enough for me security wise.  It is not like my laptop is connected to fort knox's network.  It is just a home network with a printer and some music on a hard drive!

---

### Post by YARDDAWG on 2007-12-14
> **TheDilettante said:**
> Did you get the 'Authentication Failed' box?

If so,

*ctrl+alt+F1* to get shell

login and then enter:

*sudo /etc/init.d/gdm stop*

then:

*startx*

then go undo whatever you just did.  I don't know how to fix the op problem, and have spent the whole day trying to make a default keyring profile while having no clue why I cannot login into the manager, but in the process I've locked myself out something like 8 times.

First let me just say I am a noob. But I am gad I found your post, I felt sure I had hosed my install.
Thank you. This was very helpful.

---

### Post by ZanexGt on 2007-12-20
> **TheDilettante said:**
> Did you get the 'Authentication Failed' box?

If so,

*ctrl+alt+F1* to get shell

login and then enter:

*sudo /etc/init.d/gdm stop*

then:

*startx*



This happened to me after trying the instructions in this thread. Thanks for posting these instructions so that I could get back into the GUI. 

Ultimately, I couldn't get the user auto-login and the keyring manager auto login to work at the same time. Perhaps they would have worked concurrently had I put in more effort. However, I ended up removing the nm-applet and installing wicd. 

Now everything is working great! (and no annoying popups asking for passwords)

---

### Post by Casual Fan on 2007-12-24
Thanks op, this worked for me.:)

---

### Post by zandy1123 on 2008-01-13
I'm running eeexubuntu on my EEE PC...and I'm trying to figure out this whole automatic keyring thing.

When I check the Synaptic Package Manager, there's no libpam-keyring package available.  When I search for "keyring" however, I see the following, all of which are already installed:

gnome-keyring (2.20-0ubuntu4)
libgnome-keyring0 (2.20-0ubuntu4)
network-manager-gnome (0.6.5-0ubuntu10)
ubuntu-keyring (2007.06.11)

I'm assuming the libpam-keyring package has been replaced by one of these...is that correct?  

Does anyone know how to work the automatic keyring trick with one of these?

btw - I'm a n00b, so go easy on me and don't assume that I know anything about anything :)

thanks.

---

### Post by zandy1123 on 2008-01-13
Update:

expanded my repositories in Synaptic Package Manager and now, when I search for packages with the keyword "keyring" I get a while bunch of new stuff, including:

debian-keyring
gnome-keyring-manager
libpam-gnome-keyring

...it's that last one that looks the most promising.  Is that what I'm looking for?  It's still not quite the same as the package referenced earlier in this thread.

Any help/ideas?

---

### Post by dzhey on 2008-01-17
I think I've found a solution for eeeXubuntu (and I'm pretty sure that same goes with usual Xubuntu), but I must warn u first - I'm actually rather new in linux. 

I have the same password for keyring and login

what I did is installed libpam-keyring(not sure if this step is nescessary):
> sudo apt-get install libpam-keyring

and then unchecked Launch Gnome services on startup:
> Applications->Settings->Sessions and Startup Settings->Advanced

Everything works fine for me; wifi connects without asking any password. Hope it'll help u as well!

---

### Post by maddentim on 2008-01-17
I rebuilt my home directory for other purposes and was hoping that it might clear this issue up too, but to no avail.  I still get "authenitcation failed" when i get to the login screen.  Would love to get this working, so if anyone has any suggestions, I am all ears!

---

### Post by dzhey on 2008-01-18
If u want to get rid of "authentication failed" problem just boot up to your login screen where u have this error; press ALT+F1 which will get u in console; enter your login and password and then type:
> sudo nano -w /etc/pam.d/gdm 
This will open gdm file that u have changed like it was advised in the first post of this thread. After u have opened it just remove the last string:
> @include common-pamkeyring
Press CTRL+X then Y to save and reboot.

---

### Post by madelman on 2008-02-26
This does not work for me. I had this configured in 7.04 and it used to work now with 7.10 does not work. Does anybody know how to get rid of this . I am really sick and tired of this keyrings.

When I tried to reinstall I got this:

sudo apt-get install libpam-keyring
[sudo] password for asaynes:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libpam-gnome-keyring instead of libpam-keyring
libpam-gnome-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a debhelper module-assistant intltool-debian po-debconf liblualib50 libpostproc0d libavformat0d
  libvte2.0-cil gettext dpkg-dev libavcodec0d html2text xtightvncviewer liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Then I have  in /etc/pam.d/gdm file :


#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so


rebooted and the same stupid window asking for the password.  I removed the keyrings file from .gnome2/keyrings directory and asked for the password to be created, typed it rebooted and nothing , same problem. This used to work with 7.04 I do not know why I upgraded to 7.10, it was a huge mistake!.

---

### Post by owenll on 2008-04-17
> **madelman said:**
> This does not work for me. I had this configured in 7.04 and it used to work now with 7.10 does not work. Does anybody know how to get rid of this . I am really sick and tired of this keyrings.

When I tried to reinstall I got this:

sudo apt-get install libpam-keyring
[sudo] password for asaynes:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libpam-gnome-keyring instead of libpam-keyring
libpam-gnome-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a debhelper module-assistant intltool-debian po-debconf liblualib50 libpostproc0d libavformat0d
  libvte2.0-cil gettext dpkg-dev libavcodec0d html2text xtightvncviewer liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Then I have  in /etc/pam.d/gdm file :


#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so


rebooted and the same stupid window asking for the password.  I removed the keyrings file from .gnome2/keyrings directory and asked for the password to be created, typed it rebooted and nothing , same problem. This used to work with 7.04 I do not know why I upgraded to 7.10, it was a huge mistake!.

Same problem for me in Hardy

---

### Post by Tews on 2008-04-17
I had this problem too!  I found that if I had autologon enabled that I was forced to enter the keyring password to logon to the net.  As soon as I disabled auto logon, the problem was resolved.

---

### Post by owenll on 2008-04-17
> **Tews said:**
> I had this problem too!  I found that if I had autologon enabled that I was forced to enter the keyring password to logon to the net.  As soon as I disabled auto logon, the problem was resolved.
So it's a choice between typing your password to logon or to connect to wifi? No automatic logon and automatic connect to wifi possible?  Step back from 7.10 IMO

---

### Post by Tews on 2008-04-17
Maybe .. It is what it is ...

---

### Post by owenll on 2008-04-17
Can now log in automatically and connect to wireless using wicd and the instructions found here: 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

There is always an answer with Ubuntu :)

---

### Post by GuiGuy on 2008-04-26
> **bishop9226 said:**
> Just making this so other people having this problem won't have to hunt around.  keywords: keyring wifi wireless e1505 password internet 


Doesn't work for me :( version Ubuntu 8.04 :( and yes, the passwords are the same.

---

### Post by AdrianStrays on 2008-05-04
Second

---

### Post by phil_elson on 2008-05-09
Solution for me: [http://ubuntuforums.org/showthread.php?t=431893&highlight=get+rid+of+keyring+requests](http://ubuntuforums.org/showthread.php?t=431893&highlight=get+rid+of+keyring+requests)

if you are using libpam-gnome-keyring instead of libpam-keyring I am still having a little difficulty

---

### Post by Zhu on 2008-05-16
Hi, Xubuntu 8.04 since 2 days and same trouble.

- I followed instructions from post 1, with same session/keyring password.
- Reboot and got a persistant pop up window with an authentification error
- needed to bypass the pop up window to be able to log in: ctrl+alt+f1
- once logged in, I deleted "@include common-pamkeyring" from /etc/pam.d/gdm
- reboot and could loggin again normally
- then I noticed that, on the keyring pop up window, I could check an option like "save password", so I input my password (same as session) and enable the option
- reboot, and everything is fine. Loggin in session and NO keyring window anymore. Wireless is fine

Here's my /etc/pam.d/gdm (looks like the "auto_start" option has been added)

> #%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

Hope this helps !

---

### Post by randysparks on 2008-05-24
> **GuiGuy said:**
> Doesn't work for me :( version Ubuntu 8.04 :( and yes, the passwords are the same.

I have a solution that's not perfect but is mostly fuss-free. Just stop using NetworkManager. Go back to using the old network configuration tool that doesn't need PAM.

To do this, click the NetworkManager icon and select Manual Configuration. In the dialog, click Unlock and then select the Wireless Connection entry. Then double-click. Remove the check from Enable Roaming Mode and enter your wifi base station name in the Network Name box, and the password in the relevant box. Change the configuration dropdown to read Automatic Configuration (DHCP). 

Note that I had to reboot before this started working. 

This will mean that you can't wirelessly roam, of course, but if you're using a desktop computer that doesn't leave the house then it's a good solution.

---

### Post by Fury5000 on 2008-05-27
> **randysparks said:**
> I have a solution that's not perfect but is mostly fuss-free. Just stop using NetworkManager. Go back to using the old network configuration tool that doesn't need PAM.

To do this, click the NetworkManager icon and select Manual Configuration. In the dialog, click Unlock and then select the Wireless Connection entry. Then double-click. Remove the check from Enable Roaming Mode and enter your wifi base station name in the Network Name box, and the password in the relevant box. Change the configuration dropdown to read Automatic Configuration (DHCP). 

Note that I had to reboot before this started working. 

This will mean that you can't wirelessly roam, of course, but if you're using a desktop computer that doesn't leave the house then it's a good solution.

ahhhhhh beautiful....thank you :)

---

### Post by Fury5000 on 2008-05-27
oh... one question... when I am in this "manual mode" and am connected to my wireless connection... Is there a way to still see what the actual signal strength is?  In the manual mode you just get the same icon on the bar as a hard wire connection now.

---

### Post by maddentim on 2008-05-28
Hey, I had trouble with getting this to work in 7.10.  I kept getting authentication errors.  

I tried it again after upgrading to 8.04. The first time I did it I got authentication errors again.  Then, I partially undid the process as I recall.  I was bummed, so I did not pay close attention.  

Basically, I NO longer have the "@include common-pamkeyring" at the end of my /etc/pam.d/gdm and I have libpam-gnome-keyring instead of the libpam-keyring installed.  (i am not even sure if libpam-keyring is still a package in 8.04.  

Anyhow, one of the next times that I was logging in with the keyring thing, when i noticed it had grown a little remember this password (or similar) button.  I clicked that puppie and it hasn't come back!  Much much better and I did not need to mess switching to wicd or any messiness.

---

### Post by alejaaandro on 2008-05-28
> **Fury5000 said:**
> oh... one question... when I am in this "manual mode" and am connected to my wireless connection... Is there a way to still see what the actual signal strength is?  In the manual mode you just get the same icon on the bar as a hard wire connection now.


hmmm... i 'd like to know that too... any ideas?

---

### Post by Fury5000 on 2008-05-28
I added the app called KWiFiManager... it puts ths signal meter back on the top bar...  in settings you can tell it to keep them up there even when the app is closed.  works great.

---

