---
title: "Can't activate special effects"
date: 2008-05-04
forum: General Help
---

### Post by agentsmith23 on 2008-05-04
First I would like to tell you I am a newbie and sorry if this is really easy to fix. I was trying to update my graphics driver for my ATI X1200 and after I did what I thought was an upgrade I can't get any of the special effects to activate again. The restricted driver is active but every time I go under the Appearance Preferences and go to the visual effects tab I can't get anything but the None option to activate. The other two options always return the error "Desktop effects could not be enabled". 

Could someone please help me correct my mistake. 

According to the ATI Catalyst Control Center my driver version is: 8.47.3


Thanks for any possible help!

---

### Post by jtrag on 2008-05-04
Does it give you any specific error?  See if you could possibly find some more specific error information and post it for us.  It's a little hard to say exactly what the problem could be without a more specific error message.  One question though, have you tried to remove your graphics drivers, reboot the machine, then reinstall your graphics card drivers, restart the machine again, then try?  If not, try that and see if it helps.  

I just had the same problem literally 15 minutes ago on my old pentium 4 system with a geforce 2 card in it, and I did exactly what I just said and it fixed it.  It may work for you.  Give it a shot and let me know :)

Good Luck!  :guitar:

---

### Post by agentsmith23 on 2008-05-04
I don't have any other error messages to give you at this time. I tried your suggestion of uninstalling the drivers and rebooting and reinstalling and rebooting again. I still have the same problem.

Let me know if I am doing this correctly. To uninstall the drivers I go to the Synaptic Package manager and uninstall the fglrx driver.Then reboot. Then reinstall the fglrx driver. Reboot again and attempt to activate the special effects.

If there is a way to activate the special effects using the terminal, I could possibly get you a more exact error from there.


I  have some new info to add. I was looking at another posting about not being able to get visual effects to work and the person in the post ran this command "compiz --replace".  I ran this same command and came back with this info:

dave@dave-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:791f (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found


I don't know if this helps out at all. If any other info may help out please let me know!

Thanks again!

---

### Post by agentsmith23 on 2008-05-04
Still trying to figure this out now I have installed Xgl and when I run the command "compiz --replace" I now get this. I don't know if compiz is related to my problem or not but it is the only thing I can come up with at this point. I really appreciate any help I can get! 


dave@dave-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

---

### Post by Zorael on 2008-05-04
This is a bug with the ATI driver installer or some such. I've seen a post or two about it with a proper solution.

Earlier post, now irrelevant, see next post.
[quote=me]This workaround *COULD* work but I'm far from certain. It's very easy to reverse though.
```
$ sudo ln -s /usr/bin/compiz /usr/local/bin/compiz
```
It shouldn't output anything.


To undo it, do this.
```
$ sudo rm /usr/local/bin/compiz
```[/quote]

---

### Post by Zorael on 2008-05-04
Solution seems to be to open up a file in **/etc/xdg/compiz/**. There should be a file there named **compiz-manager**, and *not* **compiz-manager.something**, as yours likely is. So rename it to merely compiz-manager and it should hopefully work.

The non-commented contents of this file should be the following.
```
COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"
```


Earlier post:
[quote=me]Another workaround here: [http://ubuntuforums.org/showthread.php?t=585252](http://ubuntuforums.org/showthread.php?t=585252)[/quote]

---

### Post by agentsmith23 on 2008-05-04
I actually fixed the problem another way. It seems that the compiz program got messed up in some way. So the fix was really simple. Just go into synaptic package manager and uninstall compiz-core, then reinstall compiz-core and all should be well. The program marked compiz in synaptic is not actually the functioning compiz program, it was also originally installed but now it is uninstalled and compiz works great.

---

