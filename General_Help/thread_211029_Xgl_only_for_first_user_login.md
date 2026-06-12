---
title: "Xgl only for first user login"
date: 2006-07-07
forum: General Help
---

### Post by Crosbie on 2006-07-07
I'm not sure whether this is an issue with Xgl, Ubuntu or what - so I'm trying it here. :)

I've installed Xgl and Compiz using the gdm method as detailed elsewhere in these forums.  This allows me to login to my usual user account and enjoy the full glory of whizzy eye-candy.

However, when I log in as a second user Xgl fails to initialise. I get a server error, stating that /tmp/.X1-lock couldn't be removed.

I've tried removing this manually but no dice, for various reasons.  However, when I logged in to this second account *first*, Xgl worked fine.

For some reason Xgl seems not to be shutting down properly - I've tried adding a script to remove X1-lock on logout but unsuccessfully.  (It seemed to remove the lock file but the server still failed - reporting that another instance was running?)

Hope somebody recognises this issue and can help. :)

---

### Post by Anduu on 2006-07-07
Free bump :p 

I know this is a known issue with XGL/Compiz...just can't think for the life of me where the solution is posted...keep digging ;)

---

### Post by reacocard on 2006-07-07
are you using "Switch user" to change users? i have aiglx/compiz, and if i try to use switch user to log in another user, it won't load an aiglx xserver (standard xserver works fine). log out/in works perfectly.

---

### Post by Crosbie on 2006-07-08
> **reacocard said:**
> are you using "Switch user" to change users? i have aiglx/compiz, and if i try to use switch user to log in another user, it won't load an aiglx xserver (standard xserver works fine). log out/in works perfectly.

No, I'm using 'log out'.

Anduu, thanks for the bumpage. :)  Yes, I've found the odd mention of the *question* elsewhere but no clear *answer* (though frustratingly, some saying 'oh, it just went away' without posting a solution). :???:

---

### Post by Crosbie on 2006-07-08
Okay, update:  I've solved this problem with a workaround: ie, I changed to [Install Method B](https://help.ubuntu.com/community/CompositeManager/Xgl) and made Xgl my permanent X server.  Since I'd tested it out and it works, I thought I might as well. :)

This allows both users to use Xgl (added a startcompiz script to the session startup programs), and restores Shutdown and reboot options to the logout window by the by.

Gdm is running choppily, however, and X takes longer to start up.  I'm a little worried in case there's an Xgl update that borks it for my system, but hey, we'll see when that arises.

This still leaves the problem of how to get all this working when it's just an Xgl *session,* of course.

---

