---
title: "laptop crashed!!"
date: 2008-02-13
forum: General Help
---

### Post by reefsrt4 on 2008-02-13
Was doing some research for a term paper when the laptop froze.  I shut it off and restarted.  It booted, I logged in and it hung while the GUI was loading.  Reboot again, same thing.  Reboot again, but this time it during root system file check it says an error was found.  fsck was forced and failed.

From here I have no idea how to repair whatever it is that happened.




Anybody have ideas about how I can fix this or use the live CD to make some sort of repair to why the GUI wouldn't load?  Any help is greatly appreciated, if I lose the laptop, I lose ALL of my term paper prep and research!  Desperately hoping this isn't a permanent death...

---

### Post by santiagoward2000 on 2008-02-13
> **reefsrt4 said:**
> Was doing some research for a term paper when the laptop froze.  I shut it off and restarted.  It booted, I logged in and it hung while the GUI was loading.  Reboot again, same thing.  Reboot again, but this time it during root system file check it says an error was found.  fsck was forced and failed.

From here I have no idea how to repair whatever it is that happened.




Anybody have ideas about how I can fix this or use the live CD to make some sort of repair to why the GUI wouldn't load?  Any help is greatly appreciated, if I lose the laptop, I lose ALL of my term paper prep and research!  Desperately hoping this isn't a permanent death...

Hi!
I have a question: does it work correctly if you use a LiveCD? If so, you can log in with one, and make a backup of your research into a usb drive for example.
I'm sorry I can't help you fix it.
Good luck! :KS

---

### Post by reefsrt4 on 2008-02-13
> **santiagoward2000 said:**
> Hi!
I have a question: does it work correctly if you use a LiveCD? If so, you can log in with one, and make a backup of your research into a usb drive for example.
I'm sorry I can't help you fix it.
Good luck! :KS

I used the live CD to boot into safe graphics mode.  After opening a file browser, I was able to look in the hard drive, home, "user" folder.  However, it wouldn't let me go any further.  It said it wasn't able to display those contents.  I can see the stuff in my user directory, but there are no icons to distinguish folders or files and double clicking what I know to be the home folder of my research comes up like I said before "Couldn't display - The attempt to log in failed"

---

### Post by reefsrt4 on 2008-02-13
Anybody have any other advice on how I can restore the GUI functionality of my laptop and get back to normal use?

Thanks in advance.

---

### Post by seventhc on 2008-02-13
did you use
```
gksudo nautilus
```
when in the live cd?
Even though it doesn't actually ask you for a password it still gives you extra permissions.

---

### Post by reefsrt4 on 2008-02-13
> **seventhc said:**
> did you use
```
gksudo nautilus
```
when in the live cd?
Even though it doesn't actually ask you for a password it still gives you extra permissions.


Thank you.  That worked for being able to recapture the research I had saved and put it on a mem stick.






Anybody else have the fix to restore my GUI, so I can get off of the live CD and back to the laptop?  Do I need to reinstall GRUB?  If so, how do I go about doing that?

---

### Post by seventhc on 2008-02-13
Great, glad you got it back. :)

---

### Post by reefsrt4 on 2008-02-13
re-installed GRUB and found that is not the issue causing me problems.  


When GRUB starts and the last check takes place (root file system), it goes into an auto fsck.  That file check fails with an error in the root file system.  I am prevented from being able to continue in the boot process.

Has anyone experienced this or know what I have to do to get my machine back in order?

---

