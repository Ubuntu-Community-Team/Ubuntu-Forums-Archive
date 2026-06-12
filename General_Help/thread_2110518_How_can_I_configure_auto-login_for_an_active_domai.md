---
title: "How can I configure auto-login for an active domain user (after setting up likewise-o"
date: 2013-01-30
forum: General Help
---

### Post by tpope on 2013-01-30
After using likewise-open to join my Ubuntu box (12.04 LTE) to an AD, I found myself a little stumped as to how I can have Ubuntu automatically log in as a user from that domain. I've tried editing /etc/lightdm/lightdm.conf, which works perfectly for local user accounts; the following just leaves me at the login screen, with "ad-user-01" not shown in the user list:

> [SeatDefaults]
autologin-guest=false
autologin-user=DOMAIN\\ad-user-01
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter
greeter-show-manual-login=true

I have also replaced

> DOMAIN\\ad-user-01

with

> DOMAIN\ad-user-01

to no avail (I assumed that the character would need escaping, but it doesn't seem to matter either way).

Is there something I'm missing? If I log out, log in as DOMAIN\ad-user-01, then log out again, I do see DOMAIN\ad-user-01 in the user list.  I've wondered if the problem wasn't that lightdm was starting up before networking/likewise when I boot - would there be any way to work around that?

Thanks for any advice~

---

### Post by tpope on 2013-02-01
I actually found a solution for this - the problem seems to have been that lightdm was trying to log in as my domain user before the network connection was properly establish.  The details can be found [here]("http://davidmburke.com/2012/04/26/ubuntu-12-04-deployment-with-active-directory/") - I added the ping test script from that page and a 5-second sleep to my lightdm init script, and everything has been hunky dory since.

---

