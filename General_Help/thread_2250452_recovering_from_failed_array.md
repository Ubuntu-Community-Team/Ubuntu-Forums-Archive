---
title: "recovering from failed array"
date: 2014-10-28
forum: General Help
---

### Post by Kevin_Pearce on 2014-10-28
Sorry if this is not the right forum for this but I am a bit of a noob here.  A server which was setup many moons ago by a predecessor of mine has encountered a hardware failure and I am trying to recover it.  There are (were) two arrays configured and the first was setup as a mirror across two drives which both appear to be fine.  It looks to house \ and I think everything (or most everything) which I need would be contained there.

The second array was setup as RAID 0 across 4 drives and that is the one which appears to be toast.  It looks to house \home which I don't think holds much of any actual data which I care about, but I can't get the OS to finish the boot cycle without it.

Presuming that \home is dead, is there a reasonably quick and dirty way to get the system to finish the boot cycle?  Ideally I would like to get the server on the network so I can copy data from it.  Booting the server now goes through the RAID controller card init processes (which calls out that there is an unusable array) and some of the boot process and then comes to this point:

 * Checking root file system...
fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 158609/4882432 files, 993124/19526999 blocks
                                                                                                                [OK]
 * Checking file systems...
fsck.ext3: Unable to resolve 'UUID=2c9189b1-af0e-4f75-91c2-45e31d4708cd'
fsck died with an exit status 8
                                                                                                                [fail]
 * File system check failed.
A log file is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the system manually.
 * A maintenance shell will now be started
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@sc-rails:~#

If I do a Control-D (or init 5 at that prompt), I get to a login page which lets me pass credentials, but it throws a prompt to say my home directory does not exist and do I want to login with the / (root) directory as home.  I say yes but after a couple more error messages it just dumps me back to login and I can't get out of the loop.

Thoughts?

---

### Post by tgalati4 on 2014-10-28
Rather than fight the system, work with it.  Add a hard drive and put /home on it.  Put the mount in /etc/fstab.  Populate it with user directories (if you have a list of users):

```
cat /etc/passwd
cat /etc/fstab
```  Don't post, just take note of the users.

The users's directories will be empty, and a lot of stuff will be broken, but at least you can get a full boot to perform some troubleshooting.  Comment out the /home RAID mount and put your substitute mount in its place.

Depending on the RAID controller, you should be able to put in a clean, working drive and the RAID BIOS (when you boot into it) should have an option to rebuild the array.  This may take several hours.  Once this is done, then you should be able to boot normally.  Undo any modifications that you made previously to bootstrap your system, including removing the extra /home drive.  Of course, if another drive fails during this rebuild (which is common), then you have effectively lost the entire RAID pool.

---

### Post by Kevin_Pearce on 2014-10-30
Thanks, that worked.  I was able to get the system back on the network with virtually no additional work and can copy off the stuff that was important.

---

### Post by tgalati4 on 2014-10-30
What steps did you actually take?

---

