---
title: "Changing Ubuntu to Lubuntu, getting rid of unwanted packages"
date: 2016-09-30
forum: General Help
---

### Post by hailholyghost on 2016-09-30
Hello,

I'm changing from Ubuntu to Lubuntu to minimize hardware requirements, but I want to save all of my settings on my current laptop that I've changed, i.e. Perl libraries/wifi passwords/etc.  I don't want to use the auto-backup because that will include a lot of libraries/packages I want to get rid of, and then cannot get rid of after re-install.

How can I keep only the settings I've changed in Ubuntu when switching to Lubuntu?

---

### Post by TheFu on 2016-09-30
a) which way are you going? The 1st sentence and title conflict. ;)
b) You need a backup before starting this - or any system change (like patching). Get used to that and take appropriate steps. Also, making a backup after every major change along the way would be smart.  Versioned backups mean each backup really doesn't take that long or require very much storage.  A DE change really isn't much data - less than 0.5G, I bet. A backup HDD should be 1.2x - 1.5x the size of the storage being backed up. That will support 60+ days of versioned backups, if you aren't even efficient. If you are, 120+ days is easily possible.  I have a server with 120 days of versioned backups - it needs under 200MB (yes, MB) so I can restore the system to what it was on any of those days.  It doesn't have any data, just programs and settings.
c) There is no way to "keep all the settings you've changed" - some won't apply to the new DE and some could conflict because different versions of the DE libraries might be used. Best to use a new userid when testing, until you actually decide to keep the new DE.  Not all DEs use network-manager, for example.

Ok - it isn't all bad news.  Adding another GUI is pretty trivial.  
```

# ensure everything is current
sudo apt update
sudo apt upgrade

# Install the new DE - let's assume you want lxde (which Lubuntu uses)
sudo apt install lxde

# Create a new account or test using the "guest" account. - left as an exercise for the reader
# Logout and login using new/guest account. No need to reboot. Just be certain to select the desired DE on the login page (look for the "gear" icon.
# Guest logins don't have sudo.
# Test for a few hours/days, when satisfied, remove the old DE and swap in the new login manager - will need to login as yourself/sudo-capable
sudo apt install lightdm
sudo service gdm stop # should force a logout
sudo service lightdm start

# login as yourself using the new DE. Test a little - all good?
# I'd wait a week, then 
sudo apt remove ubuntu-desktop # there will be some packages which seem important being removed. Don't worry.
```

reboot.

I could have missed/forgotten something. Sorry if I did. Get backups working first, so if any step fails, you don't lose important things. ;)
*howtogeek* wrote an article about this. Wouldn't hurt to review that too.

---

### Post by hailholyghost on 2016-10-01
thanks for error in the title, I don't see how to change the title :(

I actually switched to Gnome, I wasn't able to add icons to the taskbar in Unity.

you helped a lot!

I find that the best way of saving settings is to tarball all .files in the home directory and save that.  I used my work computer for backup.

---

### Post by vasa1 on 2016-10-01
> **hailholyghost said:**
> thanks for error in the title, I don't see how to change the title :(

...
Did that for you. If it isn't what you want, in the first post, click on edit, and then on "go advanced". Then edit the title field :)

---

