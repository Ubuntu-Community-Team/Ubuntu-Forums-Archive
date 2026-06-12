---
title: "Remote desktop ignoring vino settings and generating random password"
date: 2024-04-15
forum: General Help
---

### Post by rob190 on 2024-04-15
Hi,

I'm in the process of upgrading the hardware for an Ubutnu 22.04 machine and due to possible disk corruption, have had to do a fresh install of 22.04. The original install allowed remote desktop access using vino with a TightVNC client. I'm trying to replicate the setup on the new install. The remote desktop connection is now working, but only if I manually edit the password in the remote desktop settings dialog after every reboot. There appears to be a bug or something which causes it to be set to a random string.

I've tried using the dconf-editor to change the authentication to 'vnc-password' and then set the password to the one I want to use. I know that the default 'keyring' value can cause problems because the keyring won't necessarily be unlocked.

```
$ gsettings get org.gnome.Vino authentication-methods
['vnc']

$ gsettings get org.gnome.Vino vnc-password
'mypassword'

```

I don't understand why the remote desktop is ignoring these settings. I know it was working before so I assume I'm missing a step somewhere. The new installation is essentially the default but with wayland disabled.

What do I need to do?

---

### Post by rob190 on 2024-04-16
Seems this is a common problem. I found a workaround here: [https://askubuntu.com/questions/1403943/22-04-remote-desktop-sharing-authentication-password-changes-every-reboot](https://askubuntu.com/questions/1403943/22-04-remote-desktop-sharing-authentication-password-changes-every-reboot)

---

