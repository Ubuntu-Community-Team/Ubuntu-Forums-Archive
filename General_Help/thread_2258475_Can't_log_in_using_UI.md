---
title: "Can't log in using UI"
date: 2014-12-28
forum: General Help
---

### Post by yuri-guzun on 2014-12-28
Hello guys,

I have a 14.10 Kubuntu installed.
System accepts my credentials but then returns back to the log in screen after submitting the password. 

I have tried few things:
[LIST]
[*]Create a new user or log in using a guest session.
[*]Move the 'Xauthority' file ([FONT=Ubuntu Mono]sudo mv .Xauthority .XauthorityBak[/FONT]). [source]("http://askubuntu.com/questions/462272/cant-login-to-ubuntu-14-04")
[*]Change the home directory permissions ([FONT=Ubuntu Mono]sudo chmod -R ug+rwx /home/[username][/FONT]). [source]("http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade")
[/LIST]

There is kind of workaround which allows me to access desktop:

[LIST=1]
[*]Open console on the login screen (Ctrl+Alt+F1)
[*]There are few error messages after login. Sorry for the "[screenshot]("http://pikucha.ru/idWCv")". Haven't found how to save already displayed console output.
[*]Enter 'startx' command
[/LIST]
These steps allows me to open ubuntu desktop.

Is there a way to restore my system? Could you please help?

Thanks,
Yuri

---

### Post by Bucky Ball on 2014-12-28
Ok, try deleting the xauthority and the iceauthority altogether and rebooting. Boot to the recovery kernel and when you get to the options, choose to drop to a terminal as root, then:

```
sudo rm ~/.Xauthority
sudo rm ~/.ICEauthority
sudo reboot -h now
```

You may not need 'sudo' but doesn't hurt. See how that goes after a reboot.

---

### Post by yuri-guzun on 2014-12-28
Thanks Bucky Ball,

Have tried suggested commands booting in recovery mode but it says that file is not found. Should I log in as a user (sudo su) before running the commands?

Have tried to run this in a regular boot console. This didn't help.

---

### Post by oldos2er on 2014-12-28
In recovery mode you are the root user by default. I suggest you rerun the commands Bucky gave you but with absolute paths, e.g. ```
rm /home/user/.Xauthority

rm /home/user/.ICEauthority
``` Replace "user" with your actual user account name.

---

### Post by schragge on 2014-12-28
There's something wrong with your environment because error messages on your screenshot say (in Russian) directories /bin and /usr/bin are not on $PATH. I guess you either should use absolute paths for **any** command you type, i.e. the commands suggested by **oldos2er** and **Bucky Ball** should be entered like this:
```

/bin/rm /home/user/.Xauthority
/bin/rm /home/user/.ICEauthority

```
or first set the PATH environment variable to a sane value:
```

export PATH=/usr/sbin:/usr/bin:/sbin:/bin
rm ~/.Xauthority ~/.ICEauthority

```
System-wide default value for the PATH environment variable gets defined in */etc/environment*. On my system this file contains:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
See [uhelp]community/EnvironmentVariables[/uhelp]. Also check other places mentioned on the linked page like /etc/profile.d/*.sh, ~/.profile, and others as it may get redefined there. And please have a look at LP #[lpbug]1184878[/lpbug], especially comment #6.

---

### Post by yuri-guzun on 2014-12-28
Thanks Bucky Ball, oldos2er and schragge.

It didn't help.

schragge, yeah as per error messages from console output there are some missing PATH items. But my */etc/environment *content looks similar to yours:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

Thanks for the link to the EnvironmentVariables article. Will make sure everything is aligned with the requirements. Have tried to create a file in 
Xsession.d directory but this didn't help either.

Just to confirm. When I tried to run commands in recovery mode console I got a response which said that system had been mount in a read-only mode. Is that expected? Then I selected "Enable Networking" menu item in order to re-mount system in write mode and returned to the console. Is this OK?

Thanks,
Yuri

---

### Post by deadflowr on 2014-12-28
> [COLOR=#000000]Just to confirm. When I tried to run commands in recovery mode console I got a response which said that system had been mount in a read-only mode. Is that expected? Then I selected "Enable Networking" menu item in order to re-mount system in write mode and returned to the console. Is this OK?[/COLOR]

I'll simply post, as double yes.
The recovery mode loads as read-only because it's designed for you to view troubles without you possibly making things worse.
But it is perfectly fine to remount it read/write, and the enable networking way is actually ideal, since most/a lot of the time people need to fix something they'll also need a functional network too.

---

### Post by schragge on 2014-12-28
@OP
 Could you please post the contents of *~/.xsession-errors* after unsuccessful GUI login attempt?

---

### Post by yuri-guzun on 2014-12-29
Thanks deadflowr.

schragge, there are few error messages:
```
/usr/sbin/lightdm-session: 1: /usr/sbin/lightdm-session: ls: not found
/usr/bin/startkde: 22: /usr/bin/startkde: kcheckrunning: not found
/usr/bin/startkde: 54: /usr/bin/startkde: mkdir: not found
/usr/bin/startkde: 55: /usr/bin/startkde: mkdir: not found
/usr/bin/startkde: 56: /usr/bin/startkde: mkdir: not found
/usr/bin/startkde: 57: /usr/bin/startkde: cat: not found
/usr/bin/startkde: 65: /usr/bin/startkde: kstartupconfig4: not found
/usr/bin/startkde: 68: /usr/bin/startkde: xmessage: not found

```

Sorry for the delay in replying.

---

### Post by yuri-guzun on 2014-12-29
Thank you guys. Issue is fixed.

There was a custom corrupted script(.sh file) in /etc/profile.d/ directory.

Yuri

---

### Post by schragge on 2014-12-29
Glad you've got it fixed.

---

