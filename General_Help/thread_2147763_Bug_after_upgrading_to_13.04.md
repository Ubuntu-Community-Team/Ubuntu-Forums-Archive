---
title: "Bug after upgrading to 13.04"
date: 2013-05-23
forum: General Help
---

### Post by GeovanniLemus on 2013-05-23
Not sure if this belonged in the desktop section, but basically I upgraded from 12.04 to 12.10 to 13. After I shut down and rebooted my computer, I logged in and there is no top bar and no side bar with apps. I've been looking around for solutions but nothing has been working. The closest I've gotten was to open terminal and type 
CCMS 
I believe that's what it was. The unity box was not checked. Whenever I do check it however, as soon as I click in a blank area or exit terminal, it automatically unchecked itself. I have tried the advance option of turning off the auto assign thing and allowing plugins my self but that does not work either. How do I allow the unity plugin? and how do I get my top bar and side bar back? Appologies, for not being very specific, but I am not at my computer at the time being.

---

### Post by bogan on 2013-05-23
Hi!, **GiovanniLemus**,

 Check out my Thread in 'Ubuntu +1', Posts #36 & #39 especially.
[http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435)

You will find there a long list of suggested 'solutions', as well as the only one that worked for me.

The one that seems to work for most people is:```
dconf reset -f  /org/compiz/ # if needed install dconf-tool
setsid unity
unity --reset-icons

``` Though the behaviour you report with CCSM is outside the norm, so yours may not be typical.

You may need to install or reinstall the plug-in.```
gsettings get org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins
``` Will tell you if the Unity and GLX plugins are activated. IE 'opengl' & 'unityshell'.
While the same command with the 'reset' option in place of: 'get', will reset them.

Chao!, **bogan**.

---

### Post by GeovanniLemus on 2013-05-23
When doing the setsid unity but I end up with a LOT of errors. They all start with "compiz (core)". I tried to instal unity-tweak-tool, and I got an error with
/usr/bin/dpkg error code (1)
and a list of errors that began with Python (like the program) I purged the Python programs. Then tried to fix the dpkg. I looked around it said to use 
apt-get -f install.
I get an error asking if I am root.
another person said to use the -f install after I get the dpkg error. I only get it After installing the unity-tweak-tool. However when install the tweak tool it automatically reinstalls the Python packages. I am going in circles now and I cannot fix my icons and bars.

---

