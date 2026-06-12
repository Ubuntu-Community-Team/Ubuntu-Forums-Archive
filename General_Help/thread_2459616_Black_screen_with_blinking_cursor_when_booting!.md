---
title: "Black screen with blinking cursor when booting!"
date: 2021-03-22
forum: General Help
---

### Post by marble879 on 2021-03-22
I installed ubuntu 20.04.2 LTS. After installing, I restarted and everything was working fine. Today when I tried to boot up ubuntu again, I was met with a black screen and a blinking cursor. 

running journalctl -xe produces:
```
Jan 17 15:01:32 Desktop dbus-daemon[1477]: [session uid=1000 pid=1477] Activating service name='org.freedesktop.secrets' requested by ':1.9' (uid=1000 pid=1528 comm="/usr/libexec/goa-daemon " label="unconfined")
Jan 17 15:01:32 Desktop gnome-keyring-daemon[1566]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
Jan 17 15:01:32 Desktop gnome-keyring-d[1566]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
Jan 17 15:01:32 Desktop dbus-daemon[1477]: [session uid=1000 pid=1477] Successfully activated service 'org.freedesktop.secrets'
Jan 17 15:01:32 Desktop dbus-daemon[1477]: [session uid=1000 pid=1477] Activating service name='org.gnome.keyring.SystemPrompter' requested by ':1.15' (uid=1000 pid=1566 comm="/usr/bin/gnome-keyring-daemon --start --foreground" label="unconfined")
Jan 17 15:01:32 Desktop org.gnome.keyring.SystemPrompter[1573]: Unable to init server: Could not connect: Connection refused
Jan 17 15:01:32 Desktop gcr-prompter[1573]: cannot open display: 
Jan 17 15:01:32 Desktop dbus-daemon[1477]: [session uid=1000 pid=1477] Activated service 'org.gnome.keyring.SystemPrompter' failed: Process org.gnome.keyring.SystemPrompter exited with status 1
Jan 17 15:01:32 Desktop gnome-keyring-daemon[1566]: couldn't create system prompt: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.keyring.SystemPrompter exited with status 1
Jan 17 15:01:32 Desktop gnome-keyring-d[1566]: couldn't create system prompt: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.keyring.SystemPrompter exited with status 1
Jan 17 15:01:32 Desktop goa-daemon[1528]: secret_password_lookup_sync() returned NULL
Jan 17 15:01:32 Desktop goa-daemon[1528]: /org/gnome/OnlineAccounts/Accounts/account_1598527013_0: Setting AttentionNeeded to TRUE because EnsureCredentials() failed with: No credentials found in the keyring (goa-error-quark, 4)
Jan 17 15:01:42 Desktop systemd[1465]: tracker-extract.service: Succeeded.
-- Subject: Unit succeeded
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- The unit UNIT has successfully entered the 'dead' state.
Jan 17 15:01:56 Desktop pulseaudio[1471]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jan 17 15:01:56 Desktop dbus-daemon[607]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Jan 17 15:02:04 Desktop tracker-store[1554]: OK
Jan 17 15:02:04 Desktop systemd[1465]: tracker-store.service: Succeeded.
-- Subject: Unit succeeded
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- The unit UNIT has successfully entered the 'dead' state.
```
I found a post on askUbuntu with the exact same journalctl output here: [https://askubuntu.com/questions/1308837/20-04-black-screen-no-desktop-session-org-gnome-keyring-systempropter-issue](https://askubuntu.com/questions/1308837/20-04-black-screen-no-desktop-session-org-gnome-keyring-systempropter-issue). But, the fix was to remove nvidia drivers. I only have an AMD and INTEL gpu in my laptop, hence I was not able to try the same fix. 

I noticed that when I restart gdm3, the login screen pops up and everything works fine. The thing is that I have to restart gdm3 almost every time I boot into ubuntu! Is there a work around to this or is it even gdm3 that is causing the issue? Not sure if this is related, but could it be the kernel causing the issue? When using 20.04 in the past (with kernel 5.4) I didn't have this issue. But as soon as updating to 20.10, or 20.04.2 with kernel 5.8, this issue came up. I also wanted to note that using kernel 5.9 on Manjaro worked just fine.

What I've tried:
1) ```sudo crontab -e``` was typed into the terminal, and adding: ```@reboot service gdm3 --full-restart``` to the file.
2) Following this: [https://askubuntu.com/questions/1050672/gdm3-does-not-start-in-ubuntu-18-04](https://askubuntu.com/questions/1050672/gdm3-does-not-start-in-ubuntu-18-04) I uncommented Wayland=false in the: /etc/gdm3/custom.conf file.
3) I've followed all the commands etc in the replies to this reddit post: [https://www.reddit.com/r/Ubuntu/comments/b38d97/i_tried_sudo_systemctl_restart_gdm3_and_it_does/](https://www.reddit.com/r/Ubuntu/comments/b38d97/i_tried_sudo_systemctl_restart_gdm3_and_it_does/).
4) Reinstalling ubuntu and NOT selecting install 3rd party applications

Thanks for the help! :)

EDIT:
**RESOLVED THE ISSUE!** I was able to get help on the ubuntu discord! To fix the issue, I had to  disable gdm3, and enable lightdm. When booted up, the login screen will  be different. Near the login button, there should be an ubuntu logo.  Select the logo and choose wayland. That fixed the issue for me! Thank  you to that awesome person :D

---

