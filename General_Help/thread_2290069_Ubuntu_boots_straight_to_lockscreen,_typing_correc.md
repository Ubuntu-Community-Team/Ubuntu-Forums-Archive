---
title: "Ubuntu boots straight to lockscreen, typing correct password goes back to lock screen"
date: 2015-08-09
forum: General Help
---

### Post by gcolbourn on 2015-08-09
Hi, so my Ubuntu was set to automatically log in (no need to type password) and also have no password on the lock screen. Now when I boot, it goes straight to the lock screen. When I put in the correct password (I know it's correct, because it tells me "Incorrect Password" if I type it wrong), the screen goes black for a couple of seconds, and then goes right back to the lock screen! Ctrl-Alt-F1 doesn't work (screen goes blank, no terminal). Seems I'm completely locked out! Is there anything I can do short of a reinstall?

I can't do any of the things listed here - [http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04](http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04) - as I can't get to a terminal.

P.S. When booting, the screen to select Ubuntu, or recovery mode etc (grub?) doesn't appear any more either! I get half a second of the Gigabyte motherboard screen where I can select BIOS settings, but that's it.

---

### Post by grahammechanical on 2015-08-09
If there is only one OS on the machine and it is Ubuntu then we do not see a boot menu (Grub). We have to press Shift to force the Grub boot menu to appear. But you say it doesn't appear any more either. So, it used to appear?

Everything happens for a reason. Can you think of anything that you have done that could have brought about these changes?

Regards.

---

### Post by ajgreeny on 2015-08-09
If you are using a machine with the old BIOS, not UEFI, and if Ctrl+Alt+F1 does not give you a command line from the login screen, which may be the case as you have setup autologin,  you can hold down Shift at power-on to get to the grub menu, then the e key when your chosen kernel line is showing.  This allows you to edit the boot stanza for that kernel.  If this is a UEFI system it should be Esc that brings up the grub menu, but you may need to keep repeat tapping it and not hold it down.

Use the cursor keys to move to the "quiet splash" boot options and delete those two words and replace with "text" then use Ctrl+X to boot to a command line from where you can manually edit a few files to remove the autologin (temporarily if you really want it) and also try to sort out the lockscreen.

But I am baffled; what exactly is the point of locking the screen but not having a password to get out of the lockscreen mode?  Perhaps you do not mean lockscreen but screensaver, or you have light-locker set which you can disable by removing its light-locker.desktop files **/etc/xdg/autostart/light-locker.desktop** and **.config/autostart/light-locker.desktop**.

Tell us more and we may be able to help you with this difficulty.

---

### Post by gcolbourn on 2015-08-09
Thanks for the reply. So I got to the grub screen by repeatedly pressing escape (had to be careful not to press it one too many times as it would go to a grub command line then!). Pressing 'e', I get to edit the commands before boot. I changed the words "quiet splash" to text, and then pressed F10 to boot (Ctrl-X didn't work). However, I was just left with a flashing cursor, and no command prompt (typing does nothing). Trying it again, and all the commands before boot have gone (when pressing 'e' all it says now is:

setparams 'System setup'

              fwsetup

Booting into recovery mode gives me a command prompt. But trying the commands

sudo chown root:shadow /etc/gshadow
sudo chown root:shadow /etc/gshadow-
sudo chown root:shadow /etc/shadow
sudo chown root:shadow /etc/shadow-

(from [http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04](http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04)) gives:
"changing ownership of ..shadow..: Read-only file system."

So presumably I'm in a different file system here than the one I want?

I didn't want the lockscreen and didn't set it, it just appeared! (In fact upon installation of Ubuntu, it appears by default when computer sleeps, but I disabled it as it was annoying) I've got the password (my Ubuntu login), but after entering it correctly, it just goes right back to the lockscreen. As I said, it goes straight to this screen on booting, when it never did before. The only changes I made were reinstalling networking apps as I had a problem with Wifi keeping disconnecting (which it's still doing!).

---

### Post by ajgreeny on 2015-08-09
In recent versions of Ubuntu, the filesystem is mounted as read-only, so you need to enter the command below to remount it as read-write, which will allow you to make changes:
```
mount -o rw,remount /
```

However, I have no knowledge of those commands you are trying to use, though they are mentioned many times in various threads when I do a search on your problem, and the ownership shown in the chown commands is certainly correct.

---

### Post by efflandt on 2015-08-09
Did you change you video card or anything? It sounds almost like a problem I had when first installing 14.04 and my new video card was not supported yet (GTX 750 Ti with new Maxwell chip). The live/install iso worked fine (I used nomodeset), but the installed system could not even get to the gui login and I could not log into a virtual terminal (Ctrl+Alt+F1) because that would just flash something and immediately return to the login prompt.

So I did a recovery boot, enabled networking (which remounts the read-only filesystem read-write), then from a root terminal installed nvidia-current. But even though an nvidia 304 version worked in 12.04, that 304 version did not. It got to the gui login, but when trying to log in it would not start X, it would just loop back to the gui login prompt. At least I could log in on a virtual terminal. Looking at the logs from there showed that the nvidia driver was not compatible with my card. So I purged nvidia-current, installed nvidia-331-updates and that worked.

But if your system was working before and now is not, maybe either some update did not get completely installed, or maybe if your video card is older it is no longer supported by the current proprietary driver. What graphics card and driver/version are you using (a default driver or proprietary driver that you installed)? You might see if dmesg or /var/log/syslog show any errors.

---

### Post by gcolbourn on 2015-08-10
@ajgreeny Thanks, that allows me to execute the commands. However, I've tried everything on [http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04](http://askubuntu.com/questions/509834/lock-screen-does-not-unlock-with-correct-password-gnome-and-ubuntu-14-04), and none of it works! :-(

---

### Post by gcolbourn on 2015-08-10
@efflandt I'm using some R9 280Xs with fglrx drivers (mining Ethereum). Everything was working fine. I did do "sudo apt-get dist-upgrade" and a couple of things with networking (trying to stop Wifi disconnecting all the time), but that was it [Also did it on another almost identical setup - will try not to reboot it!]

 I do get to the GUI lockscreen, so probably not a video card issue?

---

### Post by CantankRus on 2015-08-10
Can you log in to the guest account?

---

### Post by gcolbourn on 2015-08-10
No, guest account does the same - straight back to lockscreen.

---

### Post by CantankRus on 2015-08-10
At the greeter press ctrl+alt+F1 and login
Once logged in try running... 
```
startx
```

ctrl+alt+F7 to get back to greeter.

---

### Post by gcolbourn on 2015-08-10
ctrl+alt+F1 just gives me a blank screen. No terminal.

---

### Post by gcolbourn on 2015-08-10
So running startx from the command line prompt in recovery mode gives me:

..
Fatal server error:
(EE) Could not create lock file in /tmp/.tX0-lock
..
xauth: error in locking authority file /root/.Xauthority

Note that neither of those 2 files existed when I looked for them straight after.

---

### Post by CantankRus on 2015-08-10
> **gcolbourn said:**
> So running startx from the command line prompt in recovery mode gives me:

..
Fatal server error:
(EE) Could not create lock file in /tmp/.tX0-lock
..
xauth: error in locking authority file /root/.Xauthority

Note that neither of those 2 files existed when I looked for them straight after.

In recovery you need to mount the file system first as in post #5.

---

### Post by gcolbourn on 2015-08-10
Ok,

```
mount -o rw,remount /
startx
```

from recovery mode command line just gives me a black screen!

---

