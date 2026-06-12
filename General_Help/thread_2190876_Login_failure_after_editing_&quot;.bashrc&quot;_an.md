---
title: "Login failure after editing &quot;.bashrc&quot; and &quot;.profile&quot;"
date: 2013-11-29
forum: General Help
---

### Post by pdog on 2013-11-29
After installing Android SDK Platform-tools in my HOME folder, I attempted to define the path where ADB was located.  I used the following commands per the website tutorial I was using:

gksudo gedit ~/.bashrc

(Go towards the end and add the following lines:)

# Android tools
 export PATH=${PATH}:~/android-sdk-linux/tools
 export PATH=${PATH}:~/android-sdk-linux/platform-tools
 export PATH=${PATH}:~/bin

(Lets do the same for .profile. Open Terminal and type:)

gksudo gedit ~/.profile

Scroll to the very end of the file and add the following line:

PATH="$HOME/android-sdk-linux/tools:$HOME/android-sdk-linux/platform-tools:$PATH"

(Reboot your system now to take effect.
To confirm the configuration, open Terminal and type:)

adb

After reboot, I was taken to the Lubuntu 12.04 Login screen.  The system recognizes my password (an incorrect password gives an error message) but then almost immediately returns to the Login screen.

I can login as guest or enter recovery and drop into root. I also have an Lubuntu 12.04 live cd.  What is the best way to access the corrupted files and remove the offending text?

Thanks

Paul

---

### Post by drmrgd on 2013-11-29
The instructions you were given aren't really all that good.  First, you don't need 'gksudo' to edit ~/.profile or ~/.bashrc.  You own both of these files and can edit them without admin rights!  Also, there's no need to add ~/bin to your $PATH variable manually; that should already be setup in  ~/.profile by default such that if ~/bin exists, it will automatically be added to your $PATH.

It's odd that changes to these files should prevent you from getting an X session started.  Could be something else going on.  But, to fix these, if you can drop to root as you say, just edit the .bashrc and .profile files for your username like so:

```

nano /home/<username>/.bashrc #change <username> to match the correct username, and .bashrc to .profile when you're ready

```

You can comment out the new lines if you like to see if that fixes it, and the reinsert one at a time.

Let us know if that helps.

---

### Post by pdog on 2013-11-29
Thanks for the responce.

I'm not clear on what you mean to do by "and .bashrc to .profile when you're ready".  I was able to get the GNU nano box using a terminal in this guest session I'm currently in, but with permission denied.  I am about to end this session and go into recovery to root.

---

### Post by pdog on 2013-11-29
OK, answered some of my own questions from above.  From the root in recovery, was able to see the .bashrc and .profile files and edit out my added lines.  But when I went to save my changes with ^O (Write Out) I was denied with "Error writing /home/(username)/ .bashrc(or .profile): Read-only file system. Also (Warning: No write permission).

Tried sudo before the commands with no success.  Any suggestions on how to optain write permission?

Thanks

---

### Post by steeldriver on 2013-11-29
In recovery mode, the filesystem is mounted read only (ro). You can remount it with read-write permissions using

```
mount -o remount,rw /
```

before trying to edit the file(s). Note there is no space between the remount,rw options - just a comma. You will not need sudo because you are already in a root shell.

FWIW I agree with everything @drmrgd says - although the original instructions were questionable, it's hard to see how adding that stuff to your PATH could cause a complete failure of your desktop session. Let's see...

---

### Post by pdog on 2013-11-29
Success!  Thank you drmrgd and steeldriver.

I deleted the extra code from .bashrc first, rebooted, and was returned to the same problem login loop. Then I did the same for .profile and upon rebooting, my normal session started right up (I'm set up to skip the login screen).  I guess complex systems sometimes behave in unpredictable ways.  

Now I'm going to do what I should have done in the first place.  Can you direct me to a thread on the PROPER way to install ADB tools on (L)Ubuntu, and if necc., establish a path so it can be seen by the system?  I'm trying to manually unlock the bootloader, install a custom recovery, and then root my Nexus 5 without using a one click toolkit.

Thanks again for your professional knowledge and support.  P.

---

### Post by steeldriver on 2013-11-29
Well I still don't really understand what went wrong, but there shouldn't be a need to set your PATH in both places, assuming your default shell is bash. Also the instructions for the .profile file ring alarm bells because they add stuff to the FRONT of the PATH - that means, for example, that if the SDK contains binaries with the same name as system programs, the system may find those first. Maybe if you posted a link to the instructions you were following we could see why they suggeted that?

These instructions --> [https://help.ubuntu.com/community/AndroidSDK](https://help.ubuntu.com/community/AndroidSDK) seem reasonably up to date (they are based on 10.04 but have been updated to at least 12.04) and are Ubuntu specific.

---

### Post by pdog on 2013-11-29
Here is the link: [http://www.droidviews.com/a-comprehensive-guide-to-adb-android-debug-bridge-and-commands/](http://www.droidviews.com/a-comprehensive-guide-to-adb-android-debug-bridge-and-commands/)

I originally was following threads in XDA, but they seem a bit more Windows-centric.

Thanks for the link.  I'll check it out tomorrow when my mind is fresher.  For me, the moral of this story is stay close to the knowledge base of your own system.

Thanks again.

---

### Post by pdog on 2013-11-30
@steeldriver- the [https://help.ubuntu.com/community/AndroidSDK](https://help.ubuntu.com/community/AndroidSDK) link instructions worked flawlessly and were easy to follow.  Thanks for the link.

---

