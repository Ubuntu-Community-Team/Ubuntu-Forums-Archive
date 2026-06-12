---
title: "Need help with Thunderbird and Ubuntu"
date: 2007-04-23
forum: General Help
---

### Post by Oki on 2007-04-23
Hi, I moved all my mail from one disk to another, with the rest of my Thunderbird profile. Then on a fresh Kubuntu install I made a new profile(started Thunbird and added all the info for an account so a profile was made), and the idea was to change the path for this profile so it went to my older profile folder(where my mail are now). 

When changing the path I most have done something wrong(and stupid med didn&#8217;t take any backup of the hidden ini profile&#8230; don&#8217;t know how to do that). When I open Thunderbird it tells me that it is already opened/running(and this is just after reboot, I have not started it, and it is not in the session). 

I have tried to run sudo aptitude remove mozilla-thunderbird, and sudo aptitude --purge remove thunderbird and reinstalled it but again I only get the same message. I have also tried to remove Thunderbird with aptitude then deleted the hidden Thunderbird profile, but with no luck&#8230; 

I guess it is a strange/stupid problem - but I would love to get help and not need to reinstall!


Thanks!

---

### Post by bananabob on 2007-04-24
Thunderbird uses a lock file to determine the presence of an existing session. Check for the  presence of the lockfile in your profile directory, make sure that thunderbird is not running when you delete the lock file.

---

