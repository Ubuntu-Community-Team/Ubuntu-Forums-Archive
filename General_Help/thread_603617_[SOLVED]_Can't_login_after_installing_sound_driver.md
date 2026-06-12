---
title: "[SOLVED] Can't login after installing sound driver"
date: 2007-11-05
forum: General Help
---

### Post by svivian on 2007-11-05
I was having problem recording sound in Audacity. After trying every configuration possible, I thought I might need to install drivers. I found a linux driver for my card (Realtek High Definition Audio) [here](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I downloaded that, ran the install program. But when I restarted I couldn't log in. The error message was:

```
(process:7945): Gtk+ WARNING: This process is currently running setuid or setgid

Refusing to initialise GTK+
/etc/gdm/Xsession: Beginning session setup
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

I assume there's a file missing? How can I get it back? Is there any kind of "revert" I can do?

---

### Post by svivian on 2007-11-05
anyone?

---

### Post by svivian on 2007-11-05
can someone post a copy of the missing file? maybe that'll fix it?

---

### Post by shad0w_walker on 2007-11-05
You might want to try reinstalling libasound2 using apt-get/aptitude. Should stick the needed file back in place.

---

### Post by Maestro23 on 2007-11-05
> **svivian said:**
> can someone post a copy of the missing file? maybe that'll fix it?

Can you get to a command prompt when you boot up? Or boot into Safe Mode?  If so,

> sudo apt-get install libasound2

---

### Post by svivian on 2007-11-05
Thanks for the suggestions. I logged in using the "Failsafe terminal" thing, and ran the command Maestro23 gave me. It seemed to install/update something but no luck logging in. (I ran it again just to be sure, this time it said linasound2 was up-to-date.)

I'm still getting the same error as above. The "driver" I installed must have changed something else. Any ideas?

---

### Post by svivian on 2007-11-05
Is there a way to update/revert the OS via the command line? For example, revert all packages to the ones in the repos?

---

### Post by svivian on 2007-11-05
bump

---

### Post by svivian on 2007-11-06
Well I've sent a message to Realtek tech support to see if they can tell me what this thing did to my system.

In the meantime I've done a *sudo apt-get update* and *sudo apt-get upgrade* to make sure I've got the latest things from the repos. Still no luck logging in. :(

---

### Post by svivian on 2007-11-06
I ran **sudo find / -name *libasound*** which gave me the following results:
```
/var/lib/dpkg/info/libasound2.postinst
/var/lib/dpkg/info/libasound2.prerm
/var/lib/dpkg/info/libasound2.postrm
/var/lib/dpkg/info/libasound2.list
/var/lib/dpkg/info/libasound2.md5sums
/var/lib/dpkg/info/libasound2.shlibs
/var/cache/apt/archives/libasound2_1.0.14-1ubuntu8_i386.deb
/home/scott/libasound.txt
/usr/share/doc/libasound2
/usr/lib/alsa-lib/libasound_module_ctl_bluetooth.so
/usr/lib/alsa-lib/libasound_module_pcm_bluetooth.la
/usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so
/usr/lib/alsa-lib/libasound_module_ctl_bluetooth.la
```

As you can see, no 'libasound.so.2' file. Is there a way to get it back? As I said above I've tried reinstalling libasound2.

---

### Post by svivian on 2007-11-06
**SUCCESS!**

After [finding another thread](http://ubuntuforums.org/showthread.php?t=161719) through Google, I have now fixed my system. The solution was to totally uninstall libasound2 and reinstall. However, doing that removes a ton of other libraries and apps. But you can add most of them back in by installing ubuntu-desktop.

```
sudo apt-get remove libasound2
sudo apt-get install ubuntu-desktop
```

And then any other apps that got removed (vlc, amarok, kate, konqueror, wine).

---

### Post by Maestro23 on 2007-11-06
> **svivian said:**
> **SUCCESS!**

After [finding another thread](http://ubuntuforums.org/showthread.php?t=161719) through Google, I have now fixed my system. The solution was to totally uninstall libasound2 and reinstall. However, doing that removes a ton of other libraries and apps. But you can add most of them back in by installing ubuntu-desktop.

```
sudo apt-get remove libasound2
sudo apt-get install ubuntu-desktop
```

And then any other apps that got removed (vlc, amarok, kate, konqueror, wine).

Good deal man.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

