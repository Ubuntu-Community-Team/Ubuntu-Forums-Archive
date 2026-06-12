---
title: "HELP: can't log in -- no root group?"
date: 2013-05-17
forum: General Help
---

### Post by kjh_ngisd on 2013-05-17
I haven't done anything different that I recall -- no updates, upgrades, changes etc. 
I'm running Precise (12.04)  on a Dell laptop (xps17, dual boot with Win7). 
And I can't log in anymore! 

I boot to login cleanly running grub. No issues, no warnings, no errors. 
I load GDM -- no issues. 

When I try to log in, it takes me back to the GDM screen. 

I try to boot to console and get the login prompt. No issues, warnings, errors, etc. 

I enter username/password and it just bounces me back to the log in prompt. I've got a couple accounts and they both do it. 

If I re-boot, as it's shutting down I see:
something like "root group not found" (I think? I can't tell, since it goes by pretty fast).

Open to ideas on how to fix this??
--kevin

---

### Post by kjh_ngisd on 2013-05-17
> **kjh_ngisd said:**
> I haven't done anything different that I recall -- no updates, upgrades, changes etc. 
I'm running Precise (12.04)  on a Dell laptop (xps17, dual boot with Win7). 
And I can't log in anymore! 



FINALLY found an error message. Looks like there's an error in the auth.log that tells me I'm suddenly missing /lib/security/pam_limits.so. 

After some digging, i've found this in /lib/x32_64<something i don't remember>/security/

So I think something (one of the updates from before maybe?) moved the file or...something? I saw something online about someone in Fedora having to repoint pam from /lib/security to /lib64/security.

So my question now is ... huh?? how did this happen and what do i do to fix it?
--kevin

---

### Post by kjh_ngisd on 2013-05-17
Confirmed. That's it. 
I modified the /etc/pam.d/console-session to point to /lib/x86_64-linux-gnu/security/pam_limits.so and it all worked. 

*NO* idea why this suddenly was needed. It must have been an breaking update that slipped through when I wasn't looking. 

Just leaving it here for other people who may encounter the issue. 
--kevin

---

