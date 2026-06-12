---
title: "Linux Mint machine blocks all incoming connection from a single PC on Network"
date: 2014-12-12
forum: General Help
---

### Post by Misterbadexample on 2014-12-12
I'm flabbergasted by this. I was editing /etc/network/interfaces, and then decided to change my settings over VNC instead. This halted my SSH session and also my VNC. I'm not sure if this locked me out or not, but I set cron up to restore an old copy of /etc/network/interfaces later that night and was able to SSH into the machine. Now I find that all connections from that machine--both Windows 7 and Ubuntu 14.04 can't reach the Mint Machine.

Here's output from ssh -vv.

```
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1
debug1: identity file /home/user/.ssh/id_ecdsa type -1
debug1: identity file /home/user/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/user/.ssh/id_ed25519 type -1
debug1: identity file /home/user/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
ssh_exchange_identification: read: Connection reset by peer
```

This isn't just SSH, because Putty can't get in, VNC can't get in, Remmina can't get in, nor can SMB on either OS on the machine.

All other devices on the network get SMB, VNC, and SSH without issue.

I'm just blown away. HOW can I fix this?

---

### Post by nerdtron on 2014-12-12
If it's Linux Mint it has a GUI, if you want to set static IP address, you the GUI network Manager. Now it seems that you are completely locked out, last resort would be to go the machine itself and configure what you want.

---

### Post by Misterbadexample on 2014-12-13
Truly excellent username.

After resetting the network settings with VNC on another PC and rebooting three times and walking away for a few hours (and then doing a hard reset after the PC had locked down all network traffic) it's back to normal. Computers are weird. I have no idea what fixed it but I'm calling this solved.

---

