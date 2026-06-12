---
title: "Directories repeatedly corrupted"
date: 2007-04-29
forum: General Help
---

### Post by dcroxton on 2007-04-29
I have two directories, /big and /back, that mount samba shares at boot time.  Both of them appear to be corrupted, because when I do "ls -l /", I get the following for them:

?---------   ? ?      ?          ?                ? /back
?---------   ? ?      ?          ?                ? /big

They give me an input/output error when I try to list their contents or remove them.

This is not the first time this has happened; I posted once before on this problem ([http://ubuntuforums.org/showthread.php?t=326533)](http://ubuntuforums.org/showthread.php?t=326533)).  However, at that time, it was an intermittent issue.  Whenever it occurred, I would boot into Kubuntu (which I have on a separate partition), delete these directories, run "fsck /dev/hda1" (no errors are ever reported), then boot back into Ubuntu, recreate the directories, and everything was okay for a while (maybe a month).

Now, however, these directories become corrupted every time I boot.  They only work when I create them after booting up; after one reboot, they are corrupted again.  I upgraded to Feisty this week, so I suspect the problem is related, but I don't have any idea how.  I've looked through /var/log/messages, but I haven't seen any hints.  (Not that I know what to look for.  I do see some messages about raid6, which seems odd, since I don't have raid installed.)

One possible clue is that the corruption seems to be related to the boot-up process.  If I don't set the directories to mount at boot time, they aren't corrupted, and I can mount them normally once I'm logged in.  (I can always mount the samba shares normally using other directories, if /big and /back are corrupted.)  I thought the problem might be related to running fsck at boot, so I changed the last entry in /etc/fstab to 0, but that didn't help.  Perhaps there is some problem about the order in which things are done?  I do have some symlinks in my home directory that point to subdirectories in /big and /back.

Any help would be appreciated.  Let me know if I can provide other information to help solve this problem.

Sincerely,
Derek

---

