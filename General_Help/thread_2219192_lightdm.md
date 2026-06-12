---
title: "lightdm"
date: 2014-04-23
forum: General Help
---

### Post by pfeiffep on 2014-04-23
The code sequence below appears in my auth.log. Apparently there's a call needing my password prior to me being prompted. There was no error when I typed my password at login. It occurs, I choose to send an automated report, and then everything works as I expect. 

Dell Laptop
Intel celeron 1.5 Ghz
2GB mem
40GB hdd
Ubuntu 14.04 gnome flashback - metacity

```
Apr 23 06:26:50 pete-dell lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 23 06:26:50 pete-dell lightdm: PAM adding faulty module: pam_kwallet.so
Apr 23 06:26:50 pete-dell lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Apr 23 06:26:52 pete-dell lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Apr 23 06:26:52 pete-dell lightdm: PAM adding faulty module: pam_kwallet.so
Apr 23 06:26:52 pete-dell lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "pfeiffep"
Apr 23 06:26:56 pete-dell dbus[480]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.40" (uid=0 pid=1401 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=631 comm="NetworkManager ")
Apr 23 06:27:05 pete-dell lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Apr 23 06:27:05 pete-dell lightdm: pam_unix(lightdm:session): session opened for user pfeiffep by (uid=0)
Apr 23 06:27:13 pete-dell polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.76 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

```

Any suggestions how or iff this should be 'fixed'?
TIA

---

### Post by ian-weisser on 2014-04-23
Also see bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535)

---

### Post by pfeiffep on 2014-04-23
@ian-weisser Thank you. I just rebooted and the problem did not occur ...  hmmmmmm

---

### Post by pfeiffep on 2014-04-27
This message appears to be extremely transient ... hasn't happened in 4 days .... marking thread solved

---

### Post by simonbaev2 on 2014-07-29
> **pfeiffep said:**
> This message appears to be extremely transient ... hasn't happened in 4 days .... marking thread solved

I experience this message when: Attempt to login with AD credentials **immidiately after reboot**
[LIST] 
[/LIST]

If I wait several minutes after reboot and login with the same AD credentials everything works OK (I can login and no such message appears in auth.log)

---

### Post by afhx on 2014-08-09
Happens in 14.04. Confirmed bug. Temporary remedy for me is to opt for automatic log-on

---

