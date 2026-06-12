---
title: "Batch File"
date: 2008-02-25
forum: General Help
---

### Post by pyrocajun2707 on 2008-02-25
I would like to make an executable file to put on my desktop that restarts all network services, preferably with just a click like you can with a windows batch. Could I get some help on how to make such a file if it's possible?

My network manager goes screwy sometimes after switching back and forth from wired to wireless connections (The internet in my dorm is notoriously unstable, so I find myself constantly hopping between connections.) Sometimes it just quits connecting to access points altogether and I have to reboot the system. Perhaps somebody knows why it does this?

I'm running Ubuntu 7.10.

---

### Post by erginemr on 2008-02-25
Hello,

I am using an ADSL USB modem to connect to Internet, and am not using Network Manager, but since no one else seems to have noticed your post, I will try to give you some direction to follow and will act as a BUMP (i.e. bring up my post) so that other people may notice your problem and give a more proper reply.

1. Configuring wired / wireless connections from the command line, AFAIK, requires the use of these commands: ifconfig / iwconfig / ifup / ifdown. You can write down "man <command_name>" on a terminal to get more info on what it does.

2.  The following is a howto on configuring wireless modems without using Network Manager:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=ifconfig+ifup](http://ubuntuforums.org/showthread.php?t=571188&highlight=ifconfig+ifup)

2. For a crash course on BASH shell scripting, you may refer to:
[http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)

Take Care.

---

### Post by pyrocajun2707 on 2008-03-06
I will bookmark this for later use; thank you very much.

---

