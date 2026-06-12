---
title: "New install of 12.04 - can't change many settings."
date: 2014-01-11
forum: General Help
---

### Post by wirelessmonk on 2014-01-11
Hi all, I've got a weird one for you guys.

I just did a fresh install of 12.04 (64 bit) on my laptop (with a not-so-fresh home directory), and pretty quickly decided that I wanted to install gnome-shell.  I did so, and logged out/in just fine.  I went to change the wallpaper, and found that I couldn't.  I can open the Settings utility, and Appearance, and even click on a wallpaper that I want to use, but it never actually changes the wallpaper on my system.  I've tried with my own pictures, and with the ones that come stock.  I double checked permissions on my files, but they looked ok.  I changed one to 777 just for troubleshooting sake, but there was no change to the behavior of the Appearance utility.

Also in the Appearance utility, when I select a different theme from the theme dropdown, nothing changes.

I also tried making some changes with the gnome-tweak-tool, but the changes that I make aren't actually changing on my system.

I've been a Ubuntu user for a while now, but this is the first time I've seen this.  Anyone out there have any ideas?

Thanks.

Also, because I'm sure I'll get this question:  Yes, I need to use 12.04.  12.10+ doesn't seem to cooperate with my company's SSL vpn.

---

### Post by wirelessmonk on 2014-01-12
In doing a little more troubleshooting, I created a second user.  I logged out and logged back in as that user.  With that user, I can change wallpapers as expected.  

As I mentioned in my first post, I am bringing over my home directory from my last install.  Actually, this home directory has been around for a while, and no doubt has plenty of older configs that could, I suppose, muck things up a bit.  I'm going to try to move all of my config files over to a backup directory somewhere and see if that fixes my problem.

---

### Post by wirelessmonk on 2014-01-13
Moving config files didn't help, and in fact, broke things further, but I think I was on the right track.  I copied all of my home directory's contents to a fileserver, then did a fresh install, choosing to format the /home partition this time.  Upon completion, everything seems to work fine.  I'm slowly copying over non-config data from my backup and so far everything's working fine.

---

