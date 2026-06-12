---
title: "Unable to type key in LUKS greeter"
date: 2016-05-29
forum: General Help
---

### Post by atl45 on 2016-05-29
Ubuntu 16.04 

I'll try to provide as clear a walkthrough as possible.

From coldboot, the LUKS (crypt_setup) greeter is loaded. However, I'm unable to type my key into the unlock disk field. Note that my keyboard IS working, so this isn't related to USB issues. If I attempt to open a shell, I get a black screen with a flashing cursor but no prompt, i.e. I'm unable to type anything in. I therefore ctrl-alt-del to restart and load recovery mode from GRUB.

During recovery mode boot, I note the following:

Begin: Mounting root file system ... Begin: Running /scripts/local-top ...     lvmetad is not active yet, using direct activation during sysinit

...

Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
Please unlock disk sdb3_crypt: _

I enter my encryption key and the Recovery Menu (filesystem state: read-only) is loaded.

Now I select "resume normal start-up" (if I hang too long here though then the system will crash). Initially I am returned to the Recovery Menu, where I again select "resume normal start-up". On the second time of asking, the login screen is loaded. I enter my password and my desktop is loaded but without Unity.

I open a terminal in order to view the bootlog (keyboard short-cuts do not work but I can r-click and open a terminal from there).

lvmetad is not active yet, using direct activation during sysinit
  Volume group "ubuntu-vg" not found
  Cannot process volume group ubuntu-vg
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  2 logical volume(s) in volume group "ubuntu-vg" now active
/dev/mapper/ubuntu--vg-root: clean, 255640/14155776 files, 19809120/56610816 blocks

I've also taken logs for lightdm and x - see [https://paste.ubuntu.com/16820029/](https://paste.ubuntu.com/16820029/) and [https://paste.ubuntu.com/16819926/](https://paste.ubuntu.com/16819926/) respectively.

Because I can only boot via recovery mode, I can only boot with the 'nomodeset' boot parameter, which defeats Kernel Mode Setting such that the proprietary driver can't be loaded. I've searched extensively for a fix to this issue without success. 

In short, my issue appears to be the same as that outlined in this thread [http://ubuntuforums.org/showthread.php?t=2298740](http://ubuntuforums.org/showthread.php?t=2298740) but the poster hasn't given a very clear description of their issue and there have been no solutions offered.

It may also be connected to [https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but](https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but) but I'm not sure how to make sense of the solutions offered when taking into account that I'm running Ubuntu. To my own mind, my issue appears to be related to the LUKS greeter more than anything else, since I'm able to decrypt the disk if booting in recovery mode.

---

### Post by rae_bot on 2016-05-31
I'm the person from the thread you linked with a similar issue. I'm not a Linux genius; I just use Ubuntu as my main OS and if something breaks I try to handle it. So I don't know if the "full-disk encryption" option Ubuntu gives on install is LUKS or something else, but that's what I'm using now. So yes, once I get past the "greeter" screen -- by manually rebooting and getting GRUB, going to recovery mode, typing in my encryption password there, and then hitting "resume normal boot" -- everything works fine. It is a rather aggravating way to handle it, of course, so I find myself avoiding restarts and shutdowns.

The closest thing I have to insight on the problem is a friend of mine mentioned the need for a certain chip on the motherboard to use encryption. I believe it's the TPM chip. He said he'd take a look at my computer and see if he can get it to work regardless. I've not yet taken him up on the offer, so I don't know if that's the problem or if there's a solution yet.

EDIT: So, I just actually Googled it and LUKS doesn't use TPM. So that's not the problem. If your issue isn't solved by the time my friend looks at it, and if he fixes it (or at least makes useful progress), I'll reply to this thread again.

Good luck? I'm looking forward to an answer. It just hasn't been a priority lately, since I can still use the OS and I'm using encryption for the sake of learning, not for protection.

EDIT: I see using "nomodeset" actually does something for you. I think it changed things but didn't actually fix anything when I tried that, so our issues may differ.

---

### Post by cbraxton on 2016-05-31
Maybe your BIOS needs to be set up for legacy keyboard emulation?

---

### Post by rae_bot on 2016-07-10
I have an answer, at least for my version of the problem, which my friend found here: [URL="https://askubuntu.com/questions/574296/cannot-enter-password-to-start-ubuntu"]https://askubuntu.com/questions/574296/cannot-enter-password-to-start-ubuntu
[/URL]
Basically, Plymouth doesn't work correctly. I guess the keyboard driver isn't loaded by the time you need to enter the password. So, for a less-pretty-but-more-functional greeter, you edit the default grub file to have "nosplash" where it currently has "splash", then do "update-grub" (really, see the link; I'm not the expert here), and then reboot and all should be well.

I have also been advised to upgrade to 16.10 when it comes out, as Plymouth may be more functional then.

---

