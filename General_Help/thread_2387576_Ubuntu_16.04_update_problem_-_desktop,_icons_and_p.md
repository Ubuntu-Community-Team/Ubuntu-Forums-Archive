---
title: "Ubuntu 16.04 update problem - desktop, icons and programs gone"
date: 2018-03-20
forum: General Help
---

### Post by ewog on 2018-03-20
Good afternoon -

I've just built a dual-boot with Ubuntu 16.04 LTS and Windows 10 on a brand new Lenovo (2015 - just removed from the box) Flex 3.  All went well and I had the dual boot working the way I wanted.  Then I ran Ubuntu Update today, and it downloaded about 300 mb of update files and installed them.  After the screen prompt to restart the computer to complete the installation of the updates, I used the restart option.  All appeared normal through the boot process until after I entered my admin password.  When Ubuntu loaded, it only loaded the desktop background  image, but no icons or GUI, and I cannot figure out how to restore them.  I can access a command line prompt, but that is it.  I haven't found a method to shut down the computer without holding the power button for about 5 seconds.

Any suggestions on how to recover my desktop and programs?

Thanks!

Paul

---

### Post by tinylagarto on 2018-03-20
How old is this installation?

It could be a kernel issue. You could try to boot into an older kernel and see if there everything works.

In some cases it helped to go back to the originally shipped 4.4 kernel on Ubuntu 16.04.

After boot press shift and try to boot into an older kernel. Report back.

---

### Post by #&amp;thj^% on 2018-03-20
> **ewog said:**
> Good afternoon -

I've just built a dual-boot with Ubuntu 16.04 LTS and Windows 10 on a brand new Lenovo (2015 - just removed from the box) Flex 3.  All went well and I had the dual boot working the way I wanted.  Then I ran Ubuntu Update today, and it downloaded about 300 mb of update files and installed them.  After the screen prompt to restart the computer to complete the installation of the updates, I used the restart option.  All appeared normal through the boot process until after I entered my admin password.  When Ubuntu loaded, it only loaded the desktop background  image, but no icons or GUI, and I cannot figure out how to restore them.  I can access a command line prompt, but that is it.  I haven't found a method to shut down the computer without holding the power button for about 5 seconds.

Any suggestions on how to recover my desktop and programs?

Thanks!

Paul

compiz problem :
```

sudo rm -fr ~/.cache/compizconfig-1
sudo rm -fr ~/.compiz
```

Then try this **only** if your session not loading :
```

sudo rm -fr ~/.Xauthority
sudo rm -fr ~/.config/autostart
```

Reinstall compiz 
```

sudo apt-get install --reinstall ubuntu-desktop unity compizconfig-settings-manager upstart
```

Now Reset Unity Desktop :
```

sudo dconf reset -f /org/compiz/
```

And if still no love:
```

setsid unity
```

---

### Post by ewog on 2018-03-20
Created about Feb. 10th, so just over a month old.  No issues running it on either side during the month.  Only after the Ubuntu update.

---

### Post by ewog on 2018-03-20
Thanks for the possible solution.

I'll try it and see if it works.  If not, I'll just have to reload Ubuntu.  Maybe I'll get the newer version then.  Didn't have too much on it as I've been busy on the work computer the past month, so there's no loss of data, just time.....

---

### Post by dragonfly41 on 2018-03-21
A very long shot .. since you refer to only seeing the background colour after booting. In fact I also see that "no icons" quirk and I don't yet know why.
My work around after booting is to tap the dual key sequence [Super key]+[P key] a few times to cycle to the point where I see Desktop icons.
[Super key] is the one with Windows icon, bottom left on keyboard. Mine is located between Fn and Alt.

A clue is if you see the cursor disappearing off screen.
If you launch xrandr you can inspect monitor settings.

---

### Post by ewog on 2018-05-21
Howdy everyone -

Sorry for the delayed response - it's the busy time of my job with annual meetings and budgeting and blah blah blah...   So, I tried 1fallen's suggestion and it worked.  I'm back to logging in and finding my desktop and icons.  I never got to try dragonfly41's suggestion, but will keep in it mind for the future.

Thanks for the help!

Paul

---

### Post by thinkinghorse on 2018-11-18
I have a HP Omen laptop running Ubuntu Mate 16.04 After running the updates the system would not log in except in recovery mode from which neither the keyboard brightness control nor suspend would function. In normal mode after logging in you were left with the Ubuntu Mate background but the top and bottom bars of the desktop never appeared. In recovery mode using the menu to look at System>Preferences>Hardware>Additional Drivers and selecting the Nvidia binary driver rather than the X.Org X server solved this problem. At one point I attempted an Upgrade to 18.04 which ended in desaster and I re-installed 16.04 which worked when not updated but unfortunately other software demanded updates.

---

