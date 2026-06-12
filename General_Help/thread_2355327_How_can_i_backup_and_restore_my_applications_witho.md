---
title: "How can i backup and restore my applications without installing software on Ubuntu?"
date: 2017-03-11
forum: General Help
---

### Post by ahawkua on 2017-03-11
How can i backup and restore my applications without installing software on Ubuntu? I would like to have the applications on my computer backed up so I can install them on another computer in the future without internet.

---

### Post by TheFu on 2017-03-11
There are many ways, but they all suck if you won't/can't install any nicer backup software. It just depends on how hard that limitation is for your network.

For example, I keep an ISO of Ubuntu Server and a few other Linux distros around, so I can boot off the one that makes the most since after an issue happens where restoring from a backup is the best answer. The ISO has all the backup/restore tools I need, so restoring without any WAN networking is possible.  Effectively it means I can use the convenience of a full backup tool but not have any WAN connectivity.

The other options are to use only built-in tools - that would mean **tar** or **dd**. Both of those suck for whole system backups. Tar really shouldn't be used for anything over 500MB in size. dd is only effective when the entire OS being backed up isn't in use. So, it is next to impossible to perform daily, incremental, versioned, backups with either of those tools.

You don't need commercial tools, or odd tools from outside the normal repos to do backups on Linux. Can't tell from your beans how much knowledge you have about this stuff. rsync is about the minimal tool I'd use for system level backups. It can be very smart, but it must be installed to be used.  I prefer to use rdiff-backup myself. There are lots of good tools for backups in the normal repos which would be on an ISO.

My backup techniques DO NOT backup any applications that were installed by the package manager. I can reinstall those from the ISO in a few minutes by just backing up a list of those applications using a dpkg command. That effective saves about 4G of backup storage per system and doesn't impact the restore time should anything bad happen in any significant way - restores take less than 45 minutes, but there are multiple steps.  For a single-step restore, without installing any other software, you'd need to use dd. Ouch. That is ugly.  If you could, I'd strongly suggest that ddrescue be used. It works in the same way as dd, but it is more forgiving.

A typical method of doing old-school backups is to use dump and restore, but these aren't installed by default. They are probably on the ISO.

Anyway, there are some things to consider.  Perhaps someone else has better ideas/solutions?

---

