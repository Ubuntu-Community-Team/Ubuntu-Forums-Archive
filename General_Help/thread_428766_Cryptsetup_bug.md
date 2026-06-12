---
title: "Cryptsetup bug?"
date: 2007-04-30
forum: General Help
---

### Post by quark_77 on 2007-04-30
Hi All,

I have created an encrypted root partition and am now trying to create a secondary encrypted home partition and will extend this to a third partition (backup)

Initially, I was unable to create the encrypted home, however, doing so from a LiveCD was successful. Now, when I try to open the partition I get this:
```
root@quark_77's_pc:/# cryptsetup luksOpen /dev/sda13 home
Enter LUKS passphrase: 
Unable to make device node for 'temporary-cryptsetup-7110'
Failed to read from key storage
Command failed.
```
The passphrase is correct - I was able to open it from the LiveCD. 

The following bug: [https://bugs.launchpad.net/bugs/105266](https://bugs.launchpad.net/bugs/105266) seems to suggest this has been fixed. I am using:
[LIST]
[*]cryptsetup: 2:1.0.4+svn26-1ubuntu2
[*]Linux Image: 2.6.20-15.27
[/LIST]
I have also compiled 2.6.21.1 and have the same problem on this kernel. As far as I can tell, the bug isn't fixed! Does anyone have any advice on the matter? Any logs I should be checking -- permissions to alter, or should I submit another launchpad bug?

[COLOR="Red"]Edit: Have submitted a launchpad bug[/COLOR]: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/111746](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/111746)

Thanks for your time,

Quark_77

---

