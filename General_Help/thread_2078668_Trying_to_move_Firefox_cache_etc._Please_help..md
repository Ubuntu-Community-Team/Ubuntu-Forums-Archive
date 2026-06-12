---
title: "Trying to move Firefox cache etc. Please help."
date: 2012-10-31
forum: General Help
---

### Post by sandiego69 on 2012-10-31
I have Ubuntu on an internal hard drive but I want to move all Firefox related folders to an external USB hard drive. In other words I want bookmarks, temp, cache etc. off the main drive.

I have tried to change the directory with 'about:config' and have set up the first value ("browser.cache.disk.parent_directory" but when it asks for the 'string' I am lost.  I think  the external drive is /dev/sdc1 but I cannot set up the whole _correct_ path.

Any help would be appreciated.

---

### Post by vasa1 on 2012-10-31
> **sandiego69 said:**
> I have Ubuntu on an internal hard drive but I want to move **all Firefox related folders** to an external USB hard drive. In other words I want bookmarks, temp, cache etc. off the main drive.
....
Have you tried setting up your **profile** on the external disc?
[http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by sandiego69 on 2012-10-31
> **vasa1 said:**
> Have you tried setting up your **profile** on the external disc?
[http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

That link is for Windows.

I do not want to 'backup' I want the whole operation and function to be from the external disk.  I am not sure how a profile can help in this instance.

---

### Post by kanikilu on 2012-10-31
> **sandiego69 said:**
> That link is for Windows. You can run the Profile Manager for Firefox in Linux from the terminal:

```
firefox -P
```

> I do not want to 'backup' I want the whole operation and function to be from the external disk. Read further on - once you backup the profile, you can restore it to a different location:

[http://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles#w_restoring-to-a-different-location](http://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles#w_restoring-to-a-different-location)

> I am not sure how a profile can help in this instance. The profile is what stores the things you mentioned (cache, bookmarks, etc.), so that's what you want to move...

Now, if you want to run the entire *executable* from the USB drive, and not just the profile, AFAIK, there isn't really a "[Portable Edition]("http://portableapps.com/apps/internet/firefox_portable")", as such for Linux.

That said, there's nothing stopping you from downloading the binary directly from Mozilla (for example, this link will take you to the latest en_US x86_64 binary: [http://download-origin.cdn.mozilla.net/pub/mozilla.org/firefox/releases/latest/linux-x86_64/en-US/](http://download-origin.cdn.mozilla.net/pub/mozilla.org/firefox/releases/latest/linux-x86_64/en-US/)). Just extract that to your USB drive, and create a new profile (again, on the USB drive).

---

### Post by sandiego69 on 2012-10-31
Thanks to all for your help.

To summarise......I want to keep the executive part of the 'program' on the main internal drive and move the variable information (cache etc ) to the external.

If I have understood you all correctly, by creating a 'profile' this is the best way to move the relevant folders to the other drive.  There's me thinking it was a simple question of putting the correct folder path in the 'string'. Reading the Firefox instructions I thought that was all I needed to do.  My problem, as I said at the beginning, was to enter the correct 'path' to /dev/sdc1.

---

