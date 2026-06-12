---
title: "unable to update secure boot dbx"
date: 2023-02-25
forum: General Help
---

### Post by lwalper on 2023-02-25
When I try to do updates this little popup is persistent. What is this error message?--and how do I fix it? There's no such path that I can find. As far as I know everything else is up to date. It's a new install of 22.04.1.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291839&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-02-26
/boot/efi/EFI/Boot/bootx64.efi is the default bootloader when nothing else works (BootNext, BootOrder). In theory it should never be used... 

RE: [https://bugs.launchpad.net/dell/+bug/1990179](https://bugs.launchpad.net/dell/+bug/1990179)

The issue is that some Dell laptops have old bootloaders that are not used but are now marked as insecure.

```

sudo ls -al /boot/efi/EFI/Boot/

```
You will most likely see that bootx64.efi is older than the rest of the files there. 

Make sure that file reported (bootx64.efi) is not an active boot file via:
```

efibootmgr -v

```
To ensure it is not in the boot order...

If not ,then I would keep a copy of it (just in case / until you are done and can confirm it didn't need it), but delete it from the ESP
```

sudo mv /boot/efi/EFI/Boot/bootx64.efi ~/Downloads/

```
Then go ahead with retrying to update your firmware
```

sudo fwupdmgr update

```
Reboot

If for some reason, things go bad... Have an Ubuntu LiveCD Handy to copy it back there. (Not likely, but for just-in-cases)

---

### Post by lwalper on 2023-02-26
OK, Thanks.
```
leslie@leslie-OptiPlex-9020:~$ sudo ls -al /boot/efi/EFI/Boot/[sudo] password for leslie: 
total 1868
drwx------ 2 root root   1024 Dec 27  2021 .
drwx------ 5 root root   1024 Dec 27  2021 ..
-rwx------ 1 root root 960472 Feb 18 17:01 bootx64.efi
-rwx------ 1 root root  88296 Feb 18 17:01 fbx64.efi
-rwx------ 1 root root 860824 Feb 18 17:01 mmx64.efi
```
Does not look like an active boot file --
```
leslie@leslie-OptiPlex-9020:~$ efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0004
Boot0000* Windows Boot Manager    HD(2,GPT,64453a26-326c-4bd7-8159-7aeed053ecc5,0x109000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu    HD(2,GPT,64453a26-326c-4bd7-8159-7aeed053ecc5,0x109000,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Windows Boot Manager    HD(3,GPT,94fdcd39-6f89-4757-b8a5-01f8af2e42d5,0x121800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o................
Boot0004* UEFI: CT2000MX500SSD1    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(1,32768,0)/HD(2,GPT,64453a26-326c-4bd7-8159-7aeed053ecc5,0x109000,0x32000)AMBO
```

With the resulting --
```
[leslie@leslie-OptiPlex-9020:~$ sudo fwupdmgr update
WARNING: UEFI capsule updates not available or enabled in firmware setup
  See https://github.com/fwupd/fwupd/wiki/PluginFlag:capsules-unsupported for more information.
Devices with no available firmware updates: 
 • CT2000MX500SSD1
 • SSD 870 EVO 1TB
 • Unifying Receiver
&#9556;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9559;
&#9553; Upgrade UEFI dbx from 83 to 217?                                             &#9553;
&#9568;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9571;
&#9553; This updates the dbx to the latest release from Microsoft which adds         &#9553;
&#9553; insecure versions of grub and shim to the list of forbidden signatures due   &#9553;
&#9553; to multiple discovered security updates.                                     &#9553;
&#9553;                                                                              &#9553;
&#9553; Before installing the update, fwupd will check for any affected executables  &#9553;
&#9553; in the ESP and will refuse to update if it finds any boot binaries signed    &#9553;
&#9553; with any of the forbidden signatures.If the installation fails, you will     &#9553;
&#9553; need to update shim and grub packages before the update can be deployed.     &#9553;
&#9553;                                                                              &#9553;
&#9553; Once you have installed this dbx update, any DVD or USB installer images     &#9553;
&#9553; signed with the old signatures may not work correctly.You may have to        &#9553;
&#9553; temporarily turn off secure boot when using recovery or installation media,  &#9553;
&#9553; if new images have not been made available by your distribution.             &#9553;
&#9553;                                                                              &#9553;
&#9553; UEFI dbx and all connected devices may not be usable while updating.         &#9553;
&#9562;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9565;


Perform operation? [Y|n]: y
Downloading…             [***************************************]
Decompressing…           [***************************************]
Decompressing…           [***************************************]
Authenticating…          [***************************************]
Authenticating…          [***************************************]
Restarting device…       [***************************************]
Writing…                 [***************************************]
Decompressing…           [***************************************]
Blocked executable in the ESP, ensure grub and shim are up to date: /media/root/8E87-8165/EFI/Boot/bootx64.efi Authenticode checksum [007f4c95125713b112093e21663e2d23e3c1ae9ce4b5de0d58a297332336a2d8] is present in dbx
```

When I go to "Updates" everything seems to be OK without any warning popups. Thanks a bunch!! You're a superhero!

---

### Post by MAFoElffen on 2023-02-27
Glad to be of help.

Please got to the "Thread Tools: link in the upper left of the page and mark this as "Solved".

---

### Post by lwalper on 2023-03-17
Problem persists. Maybe it's inconsequential (and only an aggravation) and I should just ignore it?

---

### Post by MAFoElffen on 2023-03-17
My recommendation is to join the Bug Report at: [https://bugs.launchpad.net/dell/+bug/1990179](https://bugs.launchpad.net/dell/+bug/1990179)
as affects you also. Then add a voice with the others. The more affected will help the Bug add some momentum to fixing it.

That Bug report says it only has 6 people joined to it so far, marked as new, undecided and unassigned. Doing a google search, I see it affects more people who are probably not aware that the bug report exists yet.

---

### Post by lwalper on 2023-03-17
Done.

---

