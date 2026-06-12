---
title: "How can I use my firefox profile of choice?"
date: 2023-04-01
forum: General Help
---

### Post by sofasurfer on 2023-04-01
I have a Foxclone backup of my system on /sdb. I glitched my original system on /sda. I moved my clone to sda so now it is the same as my original system except that it is not up to date. I restored the /home partition with backintime. Now, however, Firefox is telling me to use a new profile because of conflicting dates that could screw up my files. ```
  Using an older version of Firefox can corrupt bookmarks and browsing history already saved to an existing Firefox profile. To protect your information, create a new profile for this installation of Firefox. 
``` I do not want a new profile but when I run <$ firefox -P> and change to my preferred profile I get the message about conflicts again and I am only able to use the new profile that has none of my bookmarks, history, etc. All of my other /home folder documents are as they should be (pictures, docs, /desktop, etc). I have, for now, just restored bookmarks to the new profile but I would prefer to use my old profile.



What to do?

---

### Post by Quarkrad on 2023-04-01
I have had this before.  I copy the following folders and files from my old profile to the new profile that firefox creates.  That is, these folders/files are from the old profile *xxxxxxx.default-release* folder  to the new *xxxxxxxx.default-release* folder.

bookmarkbackups  (folder)
extensions      (folder)
features  (folder)
places.sqlite
favicons.sqlite
key4.db
permissions.sqlite
content-prefs.sqlite
xulstore.json
search.json.mozlz4
prefs.js
logins.json

Just over-write the folders/files in the new profile.  The new firefox should look the same as the old (bookmarks, passwords etc)

---

### Post by sofasurfer on 2023-04-01
Looking good so far. Do you know where history is kept? Restoring the dirs and files you mentioned did not restore history. I know its somewhere within the profile folder but where?

---

