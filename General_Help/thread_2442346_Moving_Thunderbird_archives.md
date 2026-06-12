---
title: "Moving Thunderbird archives"
date: 2020-05-02
forum: General Help
---

### Post by Autodave on 2020-05-02
Just did a clean install of 20.04 onto a new SSD.  I have the old SSD with 18.04 on it that I can access via a USB adapter.  I would like to get back my archived emails from the 18.04 SSD and move them to the 20.04 SSD.  Can someone help?

---

### Post by CelticWarrior on 2020-05-02
Depending on the software used. Typically it's stored in its configuration folder.

EDIT: Haven't noticed the "Thunderbird" part. It's inside an hidden folder then.

---

### Post by Autodave on 2020-05-02
That was easy: same 2 file types that you use for moving bookmarks and passwords in Firefox.  Thanks!

---

### Post by oldfred on 2020-05-02
Years ago I moved my profile from XP to a shared NTFS partition.
Then moved to shared ext4 partition.

In your old install the default location is a hidden . (dot) file.
Look in .thunderbird you should have a profile file xxxxxx.default

You need to start thunderbird once in new install & it will create a new default.
You then copy old default into .thunderbird & edit profile.ini with that xxxxx.default.
It used to be I could just copy profile.ini and edit it with old profile, but now installs.ini seems to also have to be edited.

Similar for Firefox if interested. Its in .mozilla and has same profile & .ini files.

thunderbird:
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)

---

### Post by Autodave on 2020-05-02
Yep: just like Firefox: super simple.

---

