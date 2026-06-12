---
title: "Reboot and shutdown options greyed out"
date: 2021-10-14
forum: General Help
---

### Post by cjhabs on 2021-10-14
Hi
I am running Ubuntu 20.04 server version with xubuntu-desktop installed using the --no-install-recommends option.
I have installed xrdp from the standard repositories.
By default, the "Reboot" and "Shutdown" menu options on the logout menu are greyed out - that makes sense.

I wish to allow certain users - part of the sudo group - who are logged in via RDP to "Reboot" and "Shutdown" from the menu.
I was able to achieve that with the following settings in a .pkla file in /etc/polkit-1/localauthority/50-local.d/

```
[Enable Reboot]
Identity=unix-group:sudo
Action=org.freedesktop.login1.reboot;org.freedesktop.login1.reboot-multiple-sessions
ResultAny=yes
ResultActive=no
ResultInactive=no


[Enable Shutdown]
Identity=unix-group:sudo
Action=org.freedesktop.login1.power-off;org.freedesktop.login1.power-off-multiple-sessions
ResultAny=yes
ResultActive=no
ResultInactive=no

```
This all works as expected.

I have 2 questions:
I want the users to have to authenticate before being able to shutdown/reboot.
When I set "ResultAny" to be "auth_self" or "auth_admin", the menu options become greyed out - why is that? What am I missing here?

"ResultAny=yes" is the only option that results in the menu options being available.
I expected to have to use "ResultActive=yes". Checking the user sessions with "loginctl show-session" does in fact confirm that the user is both active and local.
Why does "ResultActive=yes" not work?
Bonus question - what is the difference between "ResultAny" and "ResultActive/ResultInactive"? My Googling showed that ResultAny = ResultActive or ResultInactive. My testing shows otherwise.

Thanks

Chris

---

