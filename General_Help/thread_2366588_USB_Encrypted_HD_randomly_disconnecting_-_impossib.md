---
title: "USB Encrypted HD randomly disconnecting - impossible to remount after"
date: 2017-07-19
forum: General Help
---

### Post by docpatient on 2017-07-19
HI
I am experiencing issues using an encrypted USB hard-drive in Ubuntu 16.04 on a server. I followed the instructions here [https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage) 
The hard drive is randomly unmounting and after it is impossible to remount - I receive the error '[COLOR=#333333][FONT=monospace]Command failed: Device already exists' .Please help.

thanks

[/FONT][/COLOR]

---

### Post by TheFu on 2017-07-20
Welcome to the forums.

USB ports can be terribly impacted by vibration, causing disconnections due to all the wiggles.

Please post exactly what commands you use to setup and mount the storage.  Use code tags.  Look through your history to get the exact commands.  Pointing at other instructions shows only what you _tried_ to do, not what was actually performed.  Ideally, a script would have been used (or notes) during the setup and mount so a record was created.  I do this with all non-trivial setups. Of course, my notes are tailored for my skills without  many details others would require.

I'm less interested in the cryptsetup OpenLUKS than the **mount** commands. The mount and options are critical.

---

### Post by HermanAB on 2017-07-20
Is it a Seagate drive?  Some models have a drive sleep problem that you may be able to disable.  You may find a reference to it with Google.

Otherwise use the disk as a boat anchor and get a different one from a different brand.  Toshiba disks generally work for me.

---

