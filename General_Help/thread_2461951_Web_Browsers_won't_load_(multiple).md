---
title: "Web Browsers won't load (multiple)"
date: 2021-05-10
forum: General Help
---

### Post by heroquestelf on 2021-05-10
Okay, so I'm starting with a brand new Kubuntu 20.04 LTS install on a Lenovo Thinkpad. This computer has been running with the 18.04 LTS on it for over two years with little to no problems. But the other day the icons started showing up without the text beneath them, so I assumed there was some kind of corruption going on and I did a fresh 20.04 install.

So I installed 20.04 today and tried to load up Firefox. It absolutely refused to launch, so eventually I had to "purge" Firefox from the system and completely reinstall. (I tried multiple solutions, including deleting the /.mozilla folder).

I rebooted and tried to launch the software and it pulled up the profile manager. It gave me a "Choose User Profile" field which was blank and prompted me to Create a new profile. I tried to do this, first trying to create a profile using the "Default User" profile name, then the logon account name. Neither worked. Both provoked an error that read:
```
Profile couldn't be created. Probably the chosen folder isn't writable. 
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [ns]ToolkitProfileService.createProfile]" 
nsresult:"0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)" location: "jS frame ::chrome://mozapps/content/profile/createProfileWizard.js
 :: onFinish :: line 239" data: no]

```

So in frustration I installed Chromium. I installed it, then clicked on the icon and it says 
```

cmd_run.go:994: WARNING: cannot create user data directory: cannot create "/home/---/snap/chromium/1568": mkdir /home/---/snapchromium: permission denied
cannot create user directory: /home/---/snap/chromium/1568: Permission denied

```

so I tried a ```
 sudo chromium 
```

and it came back with "Running as root without --no-sandbox is not supported."

So then I installed Brave. I then clicked on it and it gave me almost the **exact** same error.

Can someone please advise?

---

### Post by heroquestelf on 2021-05-10
Okay, so update:

I manually created the "/home/---/snap/chromium/1568" directory and tried again, and it gave me this long error message:

```

2021/05/10 18:03:09.279054 cmd_run.go:994: WARNING: cannot create user data directory: cannot create "/home/---/snap/chromium/common": mkdir /home/---/snap/chromium/common: permission denied
mkdir: cannot create directory '/home/---/snap/chromium/1568/.config': Permission denied
chmod: cannot access '/home/---/snap/chromium/1568/.config': No such file or directory
mkdir: cannot create directory '/home/---/snap/chromium/1568/.local': Permission denied
mkdir: cannot create directory '/home/---/snap/chromium/common': Permission denied
/snap/chromium/1568/snap/command-chain/desktop-launch: line 255: /home/---/snap/chromium/1568/.config/user-dirs.dirs: No such file or directory
/snap/chromium/1568/snap/command-chain/desktop-launch: line 256: /home/---/snap/chromium/1568/.config/user-dirs.dirs.md5sum: No such file or directory
cp: cannot create regular file '/home/---/snap/chromium/1568/.config': Permission denied
/snap/chromium/1568/snap/command-chain/desktop-launch: line 261: /home/---/snap/chromium/1568/.config/user-dirs.locale.md5sum: No such file or directory
Can't create dir /home/---/snap/chromium/1568/Desktop
Can't create dir /home/---/snap/chromium/1568/Downloads
Can't create dir /home/---/snap/chromium/1568/Templates
Can't create dir /home/---/snap/chromium/1568/Public
Can't create dir /home/---/snap/chromium/1568/Documents
Can't create dir /home/---/snap/chromium/1568/Music
Can't create dir /home/---/snap/chromium/1568/Pictures
Can't create dir /home/---/snap/chromium/1568/Videos
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
/snap/chromium/1568/snap/command-chain/desktop-launch: line 392: /home/---/snap/chromium/1568/.config/fontconfig/fonts.conf: No such file or directory
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.local/share': No such file or directory
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.themes': Permission denied
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
mkdir: cannot create directory &#8216;/home/---/snap/chromium/common&#8217;: Permission denied
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.config/dconf'mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.local&#8217;: No such file or directory: Permission denied

ln: target '/home/---/snap/chromium/common/.cache/gio-modules' is not a directory
/snap/chromium/1568/snap/command-chain/desktop-launch: line 486: /home/---/snap/chromium/common/.cache/gdk-pixbuf-loaders.cache: No such file or directory
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.local&#8217;: Permission denied
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.config/gtk-3.0/settings.ini': No such file or directory
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.config/gtk-3.0/bookmarks': No such file or directory
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.config/gtk-2.0/gtkfilechooser.ini': No such file or directory
mkdir: cannot create directory &#8216;/home/---/snap/chromium/1568/.config&#8217;: Permission denied
ln: failed to create symbolic link '/home/---/snap/chromium/1568/.config/ibus': No such file or directory
mkdir: cannot create directory &#8216;/home/---/snap/chromium/common&#8217;: Permission denied
ln: target '/home/---/snap/chromium/common/.cache/immodules' is not a directory
/snap/chromium/1568/snap/command-chain/desktop-launch: line 563: /home/---/snap/chromium/common/.cache/immodules/immodules.cache: No such file or directory
/snap/chromium/1568/snap/command-chain/desktop-launch: line 571: /home/---/snap/chromium/1568/.last_revision: Permission denied
Unable to open directory /home/---/snap/chromium/common/.cache/gio-modules: Error opening directory &#8220;/home/---/snap/chromium/common/.cache/gio-modules&#8221;: No such file or directory
sed: can't read /home/---/.config/chromium/Default/Preferences: Permission denied
Trace/breakpoint trap (core dumped)

```

Is my hard drive dying? Is that's what's going on?

**(oh, and by the way, the "---" is me redacting the user name. it isn't actually "---".)**

---

### Post by ActionParsnip on 2021-05-10
Sounds like the snap needs to be given access to the storage to make the profile

---

### Post by heroquestelf on 2021-05-11
A. how do I give snap the access rights.
B. What about Firefox. It isn't a Snap app as far as I know.

---

### Post by ajgreeny on 2021-05-11
It sounds to me as if your home has permissions problems of some sort.
Run command ```
ls -la
``` and show us  the output from that.

Everything except one of the two top lines should be owned by you as your username; if anything else is owned by root or someone else other than you you will need to use a ```
sudo chown -R $USER:$USER /home/$USER
``` command to ensure you are the owner of all your home files and folders.

---

### Post by heroquestelf on 2021-05-11
That **WAS **the solution. The user did not own their own /home folder! 

Problem solved! 

You guys are the **BEST!!**

---

### Post by ajgreeny on 2021-05-11
Brilliant!

The question that now needs answering is **why was your home owned by other than you?**
Have you been running GUI applications as root using sudo?

Doing that has in the past moved ownership of some files and folders in a users home to root, though that should no longer happen in Ubuntu-20.04 so I presume it also should not happen in Kubuntu-20.04 either.
Did you perhaps restore a backup of your previous home files and folders to your new home, and if so, how did you do that?

---

