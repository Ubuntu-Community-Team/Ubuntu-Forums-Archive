---
title: "Having problem w/ Update Mgr. ; any help?"
date: 2014-04-28
forum: General Help
---

### Post by drew14 on 2014-04-28
I am trying to update,via update mgr. the update mgr screen shows 22 updates avail for computer. I check and click on "install updates". I then get a screen saying, authenticate, so I enter my pswd;  the update screen goes to a shade of blue ; then another screen comes up saying "requires installation of untrusted packages", ok ,so I click close because alll the updates are ok, the screen goes right back to the initial screen of update manager ". Im going in circles trying to allow the updates to be installed. What am I missing ?

using Ubuntu 12.
Thanks, and have a good day.

---

### Post by TheFu on 2014-04-28
I don't use the GUI for this stuff.```

sudo aptitude update
sudo aptitude full-upgrade
```

If you see any errors, please post the command and problem lines only.  This will only patch the current release (including new kernels), but will NOT install a newer release.  Aptitude is a little smarter about updates than the normal apt-get tool and has been recommended by the debian team for years.

---

### Post by mcduck on 2014-04-28
> **drew14 said:**
> I am trying to update,via update mgr. the update mgr screen shows 22 updates avail for computer. I check and click on "install updates". I then get a screen saying, authenticate, so I enter my pswd;  the update screen goes to a shade of blue ; then another screen comes up saying "requires installation of untrusted packages", ok ,so I click close because alll the updates are ok, the screen goes right back to the initial screen of update manager ". Im going in circles trying to allow the updates to be installed. What am I missing ?

using Ubuntu 12.
Thanks, and have a good day.

The warning about untrusted packages is usually a result of not having the GPG signing key for some software source you have configured. Have you added any new repositories (PPAs's or others?) recently? If you have, make sure to also import the signing key for the repository.

(The warning will appear regardless of if the packages you are trying to install or update actually come from that repository or not, as long as any of the software sources is missing the signing key).

If you are absolutely sure you haven't added anything, please run "*sudo apt-get update*" in a terminal and post the output here so people can have a better look at what's going on.

---

### Post by drew14 on 2014-04-29
Got it, THANKS. im downloading the updates  now w/ no problems.

---

