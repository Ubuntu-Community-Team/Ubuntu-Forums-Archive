---
title: "How to remove PAM, pam.d and all this CANCER?"
date: 2007-09-14
forum: General Help
---

### Post by asbesto on 2007-09-14
Hi people

I think PAM, pam.d, the keyring stuff and all this, is a CANCER.

Is totally USELESS for a normal user, for a desktop environment, for a single PC. It's a complicated way to do exactly the same things people was doing with UNIX from early 1970.

passwd, shadow, group. There's no need to complicate this!

So, having only problems with pam.d, with 2398 config files, to do a simple thing like "sudo" without password, I want to collect information to write a document about **how to disinstall the entire pam.d cancer**

I've wrote a similar thing for GENTOO some time ago ...

Any hint? :)

PLEASE i'm really serious in this - my goal is to simplify the entire system  (next goals are disinstalling other CANCERS like AVAHI, resolvconf and similar stupid programs :)

---

### Post by kidders on 2007-09-15
Hi there,

This thread doesn't seem to have anything to do with accessibility. :confused: Your posts may be answered more quickly if you put them in the right place.

I don't want to get tangled up in a religious war, so I'll pass discreetly over your issues with PAM, resolvconf, etc. (although I *am* curious about what you would put in avahi's place). I suspect though that, compared to Gentoo, a great many Ubuntu users simply won't care enough to feel particularly motivated about the PAM debate.

Incidentally, running sudo passwordlessly is a matter of adding a single line to /etc/sudoers. The man page for sudoers will help you there.

---

### Post by garba on 2007-09-15
> **asbesto said:**
> 
Is totally USELESS for a normal user, for a desktop environment, for a single PC. It's a complicated way to do exactly the same things people was doing with UNIX from early 1970.

passwd, shadow, group. There's no need to complicate this!



in fact, what u get with a vanilla ubuntu install is authentication authorization etc being dealt with through the pam_unix modules, which is the easiest of the zillion schemas pam can use as backend, what you are trying to accomplish actually escapes me

---

### Post by sebekhoteph on 2009-02-28
Hello, I agree, PAM is not required, or at least should be configurable, including option for passwordless access

I am writing my own distro, and my application uses GDM. I dont want to log in, when GDM starts. The option of AutoLogin in gdm.conf only works once at boot.

Since my application is an APPLIANCE, I dont want pam authentication - its like entering a password whenever you want to use your toaster :)

Any way, someone can start gdm without going through the authentication process?

Thanks

---

