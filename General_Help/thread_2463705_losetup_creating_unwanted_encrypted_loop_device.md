---
title: "losetup creating unwanted encrypted loop device"
date: 2021-06-16
forum: General Help
---

### Post by Steve_Silvi on 2021-06-16
I'm running a script I found at github.com/rufferson/pureos-pinephone/tree/fd5ecbc2e6b8452545dd93db5235a6e20443071c to convert a Pinephone 64 3GB .img file to a PureOS .img that the PP 64 can boot.
 When it reaches the losetup part, I'm getting a mount error:
====================================================================

 
[LIST]
[*]sudo losetup -f 
[*]LO=/dev/loop26 
[*]sudo losetup -P /dev/loop26 librem5r4.img 
[*]sudo mount /dev/loop26p2 sd mount: /home/steve/purepp/sd: unknown filesystem type 'crypto_LUKS' 
[/LIST]
====================================================================
From what I understand, the losetup default is to create an unencrypted loop device. I've tried inserting the [ -e none ] option into the losetup command, but apparently "-e" is an invalid option.
Why would losetup create an encrypted loop device when the default is unencrypted? TIA for any assistance provided.

EDIT: It seems that the script requires the newly created loop device to  be luks encrypted to run successfully. The script does not contain any  commands to encrypt the loop device. Can anyone tell me which commands to add to create a luksFormat encrypted loop device? Thanks.


ssilvi

---

### Post by TheFu on 2021-06-17
You'll need to review the **cryptsetup** manual page. I think it is too complex to just unleash commands without reading the other parts in that manpage. Sorry.

---

