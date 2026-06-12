---
title: "Issues with system administration"
date: 2008-05-04
forum: General Help
---

### Post by johnsto on 2008-05-04
I upgraded from Gutsy to Hardy last weekend, but in the past week I've uncovered 3 (perhaps related) issues when it comes to administrating my system.

1. The update manager doesn't want to update anything - although it will pop up and show me updates to install, and have the correct ones ticked, and prompt for a password when I click 'apply updates' - it doesn't actually perform the updates. It just refreshes the list, and if I click update again, it prompts for a password again, refreshes again, ad nauseum. I have to use apt-get to update instead.

2. The 'Crash Report Detected' thing doesn't appear to work either. I can click on the tray icon, choose to see the report, enter my password, and then nothing. It vanishes and I don't get to see the report or find out what crashed.

3. Using sudo do run some programs, it frequently prompts for my password twice. First a "Password or swipe finger" prompt, then a "[sudo] password for dave" prompt. I have to enter the correct password twice!

All these things sound like failed authentication, but not sure exactly why or what's going on!

Here's an excerpt from my auth.log after trying to get to the crash reports, if it helps:

```
May  4 09:45:31 leela sshd[6612]: Server listening on :: port 22.
May  4 09:45:31 leela sshd[6612]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
May  4 09:46:38 leela gdm[6982]: pam_unix(gdm:session): session opened for user dave by (uid=0)
May  4 09:48:04 leela sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=dave
May  4 09:50:47 leela sudo:     root : TTY=unknown ; PWD=/ ; USER=dave ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May  4 09:50:47 leela sudo: pam_unix(sudo:session): session opened for user dave by (uid=0)
May  4 09:50:47 leela sudo: pam_unix(sudo:session): session closed for user dave
May  4 09:50:48 leela sudo:     root : TTY=unknown ; PWD=/ ; USER=dave ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May  4 09:50:48 leela sudo: pam_unix(sudo:session): session opened for user dave by (uid=0)
May  4 09:50:48 leela sudo: pam_unix(sudo:session): session closed for user dave
May  4 09:50:48 leela sudo:     root : TTY=unknown ; PWD=/ ; USER=dave ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May  4 09:50:48 leela sudo: pam_unix(sudo:session): session opened for user dave by (uid=0)
May  4 09:50:48 leela sudo: pam_unix(sudo:session): session closed for user dave
May  4 09:50:54 leela sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=dave

```

Any suggestions and/or cake would be nice :)

---

### Post by johnsto on 2008-05-04
I've just modified /etc/pam.d/common-auth and commented out the following line:

```
auth   sufficient      pam_thinkfinger.so
```

That appears to have stopped the authentication failures, as well as the double sudo prompts and crash detector program. Not been able to test the update manager, but wouldn't be surprised if that's fixed too.

---

### Post by antiOST on 2008-07-28
Hi

I've been playing around with thinkfinger a couple of months ago but couldn't get it to work.
It seems that somehow its enabled correctly and I ended up with the same problem as you (didn't know though)

thanks this worked for me
Kim

---

### Post by daking874 on 2009-03-30
I had the same issure with thinkfinger and the double sudo request. I solved it by editing the /etc/pam.d/common-auth file.

After all the comments at the top it now looks something like:

# here are the per-package modules (the "Primary" block)
auth sufficient pam_thinkfinger.so
auth [success=1 default=ignore] pam_unix.so try_first_pass nullok_secure
# here's the fallback if no module succeeds
auth requisite pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth required pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config


It seems when thinkfinger is installed it alters the file so that the important lines:

auth sufficient pam_thinkfinger.so
auth [success=1 default=ignore] pam_unix.so try_first_pass nullok_secure

are added at the end. This is incorrect as the first line:

auth [success=1 default=ignore] pam_unix.so nullok_secure

is still there which is why thinkfinger asks for passwords twice and gets confused. Since I changed it the problem has been solved.

---

