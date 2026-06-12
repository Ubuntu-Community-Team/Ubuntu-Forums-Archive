---
title: "Can't log in after upgrade to 18.04"
date: 2018-08-20
forum: General Help
---

### Post by trent65 on 2018-08-20
Hi everyone,

So I recently upgraded to 18.04 and now I'm having trouble logging in. The login screen comes up as expected, but when I enter in my password it just cycles back to its unlogged in state. No error message. No anything.

So far I have tried the following, based on some suggestions found in these two links:

[https://askubuntu.com/questions/1028831/login-problem-on-18-04](https://askubuntu.com/questions/1028831/login-problem-on-18-04)
[https://www.reddit.com/r/Ubuntu/comments/8fo588/i_cant_login_after_installing_1804/](https://www.reddit.com/r/Ubuntu/comments/8fo588/i_cant_login_after_installing_1804/)

I've run:
`sudo apt install --reinstall ubuntu-desktop`
`sudo apt install --reinstall ubuntu-desktop`
This ran but no changes after reboot.
The user who suggested that also suggested some a `chown` command and rebuilding .Xauthority. But I don't know what those are so I didn't want to try it.

Also I've tried
`[COLOR=#1A1A1A][FONT=&quot]rm -r ~/.local`
Same story. Removed it then no change after the reboot.

Does anyone have any ideas I could try?

[/FONT][/COLOR]

---

