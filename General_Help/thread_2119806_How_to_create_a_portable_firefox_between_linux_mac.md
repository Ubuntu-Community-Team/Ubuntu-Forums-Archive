---
title: "How to create a portable firefox between linux machines?"
date: 2013-02-24
forum: General Help
---

### Post by CrucifiedEgo on 2013-02-24
I have a linux machine at home and at work, and I'd like to put a firefox build on my USB key to carry between them.  Is this possible?  Ideally, I'd like to put the whole thing in a truecrypt container.  I can write a script to automate the unlock/mount/run, but I'm not sure how to get a portable version of firefox set up in Linux.  Anyone aware of any guides, etc?  If I just drop the linux binaries on the USB drive, it loads the local ~/.mozilla/firefox/*.default profile, when I'd want it to load the local one. Thanks!

---

### Post by Impavidus on 2013-02-25
```

firefox -h
Usage: firefox [ options ... ] [URL]
       where options include:
...
  -P <profile>       Start with <profile>.
```Does that help?

---

### Post by sudodus on 2013-02-25
I suggest that you

- make a persistent live Lubuntu USB drive or 

- install Lubuntu (as a regular installation, but) to a USB drive. Install Firefox into it and boot from it wherever you find a suitable computer.

Avoid proprietary drivers (typically for graphics or wifi) to keep it portable.

I have USB drives with both these systems and it's a bit slow on USB2, but quite OK.

---

### Post by oldfred on 2013-02-25
I use Firefox on a shared NTFS partition so I had the same profile used in all my installs. I then copy the entire profile from my Desktop to my Laptop when I travel. I have profile.ini set to use the same profile on both systems.

Procedure is the same for both Firefox & Thunderbird.

       new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by pqwoerituytrueiwoq on 2013-02-25
you can use ubuntu one, but i suggest symlinking your cache out of that
symlink *.defult o ~/Ubuntu\ One/firefox
then symlink ~/Ubuntu\ One/firefox/Cache to ~.mozilla/my-cache
close firefox first

---

### Post by haqking on 2013-02-25
Download portable firefox [http://portableapps.com/apps/internet/firefox_portable](http://portableapps.com/apps/internet/firefox_portable)

---

