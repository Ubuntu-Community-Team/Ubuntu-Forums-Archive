---
title: "Apparently benign but annoying ecryptfs error."
date: 2012-12-16
forum: General Help
---

### Post by pepperphd on 2012-12-16
Mint 14 64-bit (pretty similar to Ubuntu, right?)

Whenever I successfully sudo anything (that is, if I enter the correct password and bash recognizes and executes something) I get this error:

> 
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'


As the title says the error seems benign because whatever I sudo'd still gets done. I know I should never do this but the following fixes the problem until the next restart:

> 
sudo su
ecryptfs-mount-private


When I su back into the regular user the error no longer appears when sudoing things. Also note that when I sudo su the error appears twice before returning control. I vaguely recall messing around with rc.local or something and causing bash to crash on login. So I had to boot into the liveCD, mount my private directory (which was a learning experience in itself) and undoing my changes to rc.local or whatever it was (I don't think it has anything to do with this). That is the only messing around I've done with ecryptfs outside of trying to get this silly error to go away. Does anyone have any idea what I may have done, and/or how to fix it?

EDIT: I realized that when after I use my "fix", instead of printing the error above after my password is entered but before anything is executed, a different error appears after everything is executed, which is as follows:

> 
Sessions still open, not unmounting


I found something called ecryptfs-verify, when I run it with the -h option I get the following output when logged in as a regular user:

> 
INFO: [/home/anonymous/.ecryptfs] exists
INFO: [/home/anonymous/.ecryptfs/Private.sig] exists
INFO: [/home/anonymous/.ecryptfs/Private.sig] contains [2] signatures
INFO: [/home/anonymous/.ecryptfs/Private.mnt] exists
INFO: [/home/anonymous] is a directory
INFO: [/home/anonymous/.ecryptfs/auto-mount] Automount is set
INFO: Mount point [/home/anonymous] is the user's home
INFO: Ownership [anonymous] of mount point [/home/anonymous] is correct
INFO: Configuration valid


Here is the output when ecryptfs-verify -h is run as root:

> 
INFO: [/root/.ecryptfs] exists
INFO: [/root/.ecryptfs/Private.sig] exists
INFO: [/root/.ecryptfs/Private.sig] contains [2] signatures
INFO: [/root/.ecryptfs/Private.mnt] exists
INFO: [/root/Private] is a directory
INFO: [/root/.ecryptfs/auto-mount] Automount is set
ERROR: Mount point [/root/Private] is not the user's home [/root]
ERROR: Configuration invalid


EDIT:
Solved by disabling auto mount (by deleting automount in /root/.ecryptfs/) for root and restarting.

---

