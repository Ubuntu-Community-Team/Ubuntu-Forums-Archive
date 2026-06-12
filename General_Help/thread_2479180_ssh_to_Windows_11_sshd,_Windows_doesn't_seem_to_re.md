---
title: "ssh to Windows 11 sshd, Windows doesn't seem to read authorized_keys"
date: 2022-09-17
forum: General Help
---

### Post by vbgf3 on 2022-09-17
Hi,

I am having a strange problem. I copied my ssh-keygen's pub file to usb stick and copied it to April's Windows folder as \Users\April\.ssh\authorized_keys. 

When I ssh -vvv [EMAIL="april@xxx.xxx.xxx.xxx"]april@xxx.xxx.xxx.xxx[/EMAIL]  I get received packet type 51. And sshd resorts to asking for password. 

I am suspecting it is a file format problem, ie, Windows can't read Linux files properly. Has anyone tried ssh to a Windows 11 machine ?

---

### Post by cbraxton on 2022-09-19
I haven't done this with Windows 11 but have used ssh with Windows servers. Possibly the Windows 11 implementation is set up the same way.

Is the "April" account an administrative account? On Windows server the sshd config file (%PROGRAMDATA%\ssh\sshd_config) contains the following:

```

Match Group administrators
    AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys

```

So for administrative accounts the pub file would need to be placed in the above referenced authorized keys file unless you comment out that section and restart the sshd service.

---

