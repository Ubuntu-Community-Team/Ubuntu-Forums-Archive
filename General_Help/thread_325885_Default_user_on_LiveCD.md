---
title: "Default user on LiveCD"
date: 2006-12-26
forum: General Help
---

### Post by artinla on 2006-12-26
HELP!!

I have been working on a custom edgy liveDVD that incorporates everything a person could ever want into one DVD.  I am using reconstructor for this project, since my initial efforts using squash tools and mkisofs from the terminal were not totally successful.  I kept running into chroot issues where permissions would get hosed when I would add packages or try to import keys.   

Well..  I finally got everything that I wanted to install, but now my default "ubuntu" user's password is rejected when I try to login.  I adduser'ed a couple of other users and they work, but they don't have permission to do things such as change system settings because these things are only done by the admin user (ubuntu) on the liveCD.

I REALLY don't want to have to start over on my root environment again.  I have all the apps, codecs, etc. that I want installed and working.  Can anyone here help me remove and reinstall the ubuntu (administrative) user again, with the same exact permissions as on the liveCD?  I can easily add it within the chroot, but passwd won't accept a blank password among other problems.  I can add a user "ubuntu" but it is not the same as the *Administrative* "ubuntu" user that the liveCD uses.

ALSO, it seems that my sound only works when I boot the DVD and log in as root.. another permissions issue (probably with /dev/dsp).  Why are my permissions going haywire while using apt to install packages and dist-upgrade my chroot environment?  Many of my apps won't work once I boot the LiveDVD because I am not logged in as "root".  I even tried logging in as root, which worked but weird things happened such as the network would not talk even though all the settings were correct.

I am going to read my "Ubuntu Hacks" book and see if I can get a clue..   Thought I would post here on the outside chance that one of you might know what I am doing wrong.

Thanks,

Art

---

### Post by artinla on 2006-12-26
I see a casper.conf in /etc which sets the username and hostname when you boot up.  I also see an /etc/aliases file which contains a couple of things such as postmaster:root, gdm:root etc.  I can't find anywhere that actually sets up any user called ubuntu.  Apparently, the ubuntu user is an alias for root, but I don't really see where that is getting set up.  I checked ownership and permissions of most of the stuff in /etc and nothing was wrong.

I need to know how this "ubuntu" user is established.. there is no home folder for that user, so I have to assume that it is just a root alias.

Hmm.. anybody?

---

### Post by artinla on 2006-12-26
Sorry, one more thing:


How can I give the root user a blank or null password?

passwd won't accept a blank.

thanks,

Art

---

### Post by artinla on 2006-12-27
C'mon!... Where are all the "Master Roasters" when I need one?!!

---

### Post by artinla on 2006-12-27
I can't believe that setting a blank password is such a complicated thing.

I edited /etc/shadow and set the pw to a *, but it didn't work.

I also tried sudo passwd -l root, and then sudo passwd -u root.
neither worked.

I also tried adding a user "ubuntu" and added it to the sudoers file.  No help.

I copied the group and password files from a virgin root enviro, but that didn't work either.

I get a "user unknown to the underlying authentication module" or similar error when trying to boot the liveDVD.  I am about to just give up and buy a copy of Vista.

Art

---

### Post by olympionex on 2007-01-21
I'm having the same problem.  I want to create a livecd that requires the user to login (authenticated by active directory).  Unfortunately, something in the livecd boot process overwrites the configuration I have set for the passwords and gdm logins.  I've uncompressed the initrd file, but nothing in there seems to be the culprit.  Right now my custom cd is useless b/c my ubuntu user can no longer sudo, and I don't have any way to get root access.

---

### Post by olympionex on 2007-01-22
Well, I got a little closer though my first attempted failed and its long past bedtime.  Anyway I thought I'd share what I learned and maybe you can figure out your problem.

The script that sets up the livecd user is located at:
/usr/share/initramfs-tools/scripts/casper-bottom/10adduser

It looks like the password for the root user is also set in this file.  You can find some information on and an example of a default preseeding file that sets the root password and you can figure out the syntax.  Edit these files, remaster your cd, and you should be good to go.  Hope this helps.

---

### Post by olympionex on 2007-01-22
I tried this method and it works.  But one very important note, once you edit the casper scripts, you have to rebuild your initramfs.  Read this page for the exact details:

[https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06)

---

