---
title: "Syncing /home via internet"
date: 2012-12-07
forum: General Help
---

### Post by Carllacan on 2012-12-07
Hi!

I'm about to try something and I have the feel that it's going to result in a major disaster. 

My plan is to synchronize my /home folder across different Linux distros using either Ubuntu One or Dropbox. That is, I want to use symlinks to  keep a single home folder on the cloud which I will configure to be the /home of every other distro I create.

MY doubts are: is this even possible? Isn't there anything on the home folder that is specific for a single installation and will give problems if it is used on another, even if they are the same Distribution? Have the distributions to be "related", as Debian and Ubuntu are?

Furthermore, my goal is to have the configuration and state of all my aplications on the cloud, so it will be as if I had a single computer, so to say, to which I will access through different OS. Will it be enough sharing the /home?

Thank you!

---

### Post by Kirk Schnable on 2012-12-07
What you'll find is your home folder contains a lot of hidden dot folders which contain your settings and other information. Personally, I wouldn't advise doing this, because if you have two different desktop environments, say XFCE and KDE, I'm not sure if there would be any conflicts.

I'd also be somewhat concerned about some application profiles, say you have one computer updated to the latest Firefox, and one that isn't, so your Firefox profile has an issue and gets corrupted.

In my opinion, it's also a downright wasteful thing to do, since a lot of your web cache and other useless junk is stored in these dot folders, and synchronizing them will only add to their unwanted bloatedness.

I think it would be more well-advised to sync all the folders in your home folder individually, like your Desktop folder, Documents folder, Pictures folder, etc.  Less waste, and less chance for unexpected issues this way.

---

### Post by Jason80513 on 2012-12-07
DON'T DO IT! Some configuration can be synced this way, but not all. And the stuff that can't be synced this way is likely to end up corrupting user folders so you can't log in.

You would probably not want to do this with live database-type files either. 

Select the folders you want to sync with Ubuntu One and allow the rest to "float."

---

