---
title: "Adding Firefox favorites to another machine"
date: 2021-10-12
forum: General Help
---

### Post by Autodave on 2021-10-12
I used to know how to copy my favorites and passwords to another computer, but I see nothing that looks familiar any longer.  How do I do this?  I want to copy all my settings from this machine to a laptop that I also use.

---

### Post by oldfred on 2021-10-12
I always copy the entire profiles for Firefox & Thunderbird after housecleaning cache2 which seems to have many useless files that make copy slow.

Exclude from backup
/cache2
/OfflineCache
/safebrowsing
/settings
/startupCache
/thumbnails

Profiles - Where Firefox stores your bookmarks, passwords and other user data
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)

Your default location for profile is in a hidden folder. Change settings in browser to show hidden files to view profile.
/home/$USER/.mozilla

---

### Post by tea for one on 2021-10-12
Firefox > History > Show All History > Import and Backup

---

### Post by Autodave on 2021-10-12
Thank you folks!

---

