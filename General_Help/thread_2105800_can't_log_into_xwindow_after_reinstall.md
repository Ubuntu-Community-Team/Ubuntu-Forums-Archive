---
title: "can't log into xwindow after reinstall"
date: 2013-01-17
forum: General Help
---

### Post by marchelloUA on 2013-01-17
Hi all, 

I was wondering why should I have libreoffice on my machine if I never use it, so I've uninstalled it with forse option. Well, it was not good idea, 'cause xwindow couldn't start after that. So I reinstalled it. 

Now I can not log into xwindow, it doesn't report any error, but thinks awhile after typing password and shows me the same window with password prompt. 

How do I live with that: I go to console by pressing ctrl-alt-f1, log in and start manually 

# startx 

But can I fix it somehow? I hope I do not have to reinstall whole ubuntu...

---

### Post by marchelloUA on 2013-01-18
here is my /var/log/auth.log 
but I can't understand what is wrong... 
Somebody? 

Jan 18 00:15:04 ubuntu sudo: pam_unix(sudo:auth): conversation failed
Jan 18 00:15:04 ubuntu sudo: pam_unix(sudo:auth): auth could not identify password for [ymarkiv]
Jan 18 20:20:47 ubuntu lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jan 18 20:20:47 ubuntu lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Jan 18 20:21:15 ubuntu lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ymarkiv"
Jan 18 20:21:16 ubuntu lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jan 18 20:21:16 ubuntu lightdm: pam_unix(lightdm:session): session opened for user ymarkiv by (uid=0)
Jan 18 20:21:16 ubuntu lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 18 20:21:17 ubuntu lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jan 18 20:21:17 ubuntu lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Jan 18 20:21:34 ubuntu login[1471]: pam_unix(login:session): session opened for user ymarkiv by LOGIN(uid=0)
Jan  18 20:22:10 ubuntu dbus[615]: [system] Rejected send message, 2 matched  rules; type="method_return", sender=":1.5" (uid=107 pid=727  comm="/usr/lib/x86_64-linux-gnu/colord/colord ") interface="(unset)"  member="(unset)" error name="(unset)" requested_reply="0"  destination=":1.46" (uid=1000 pid=2277 comm="kdeinit4: kded4 [kdeinit]                        ")
Jan 18 20:22:26 ubuntu  polkitd(authority=local): Registered Authentication Agent for  unix-session:/org/freedesktop/ConsoleKit/Session5 (system bus name :1.66  [/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1], object path  /org/kde/PolicyKit1/AuthenticationAgent, locale uk_UA.UTF-8)

---

### Post by dabl on 2013-01-18
The presence or absence of LibreOffice had no direct effect on your ability to run gdm, but perhaps the way you used "sudo" to remove it changed your user's home directory.

If you can boot recovery mode and log in, and navigate to your user's home directory, then run ```
ls -la
```

Are there any files that are owned by root -- especially the "dot" files?  If so "sudo rm" those files.

Now navigate to the .config directory in your home directory, and "ls -la" again.  Do you see anything owned by root? If so, you will need to "sudo mv" it to something like "gtk-3.0.bak".

When you think you have corrected any such root permissions issues, then you can do a shutdown/reboot from the command line with "sudo shutdown now -r", and hopefully you will be able to log in normally.

---

### Post by marchelloUA on 2013-01-18
[dabl]("http://ubuntuforums.org/member.php?u=217451"), 

works great, thanks.

---

