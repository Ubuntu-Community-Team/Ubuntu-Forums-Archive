---
title: "When everything goes POOF"
date: 2008-05-21
forum: General Help
---

### Post by aaahoopy on 2008-05-21
I am experiencing an interesting issue with a closed source commercial product on both Gutsy and Hardy.  I am asking about the issue here because the OS is doing something that I don't think it should be doing, and I think this is an interesting enough bug that the community should have an opportunity to look at it.  

Unfortunately this is an insanely complicated software layout:
[LIST=1]
[*]Virtual Gutsy X86 installation running under KVM has source code and uses qtap and bridging to connect the network to host OS
[*]Host computer Hardy x64 (on intel core duo) mounts portion of virtual system's filesystem through SSHFS
[*]Source code uses svn+ssh to get subversion repository hosted on another machine in the LAN
[*]Finally a shell is opened on the host machine, setup with ssh-agent, and that shell is used to launch a closed source code editor called slickedit.
[/LIST]

Now with the above configuration, I can use slickedit's integrated subversion support and everything is happy.  However, occasionally, when I use slickedit to do essentially what amounts to an svn status from the root directory of the repository, it will appear to hang for a long time, and then POOF, all applications running under my user ID and some that aren't all disappear at the same time.  

I unfortunately have not had a lot of time to investigate this phenomenon, but here is what I have seen so far:
[LIST]
[*] The network filesystem in use does not appear to matter, it did it originally with kernel NFS, and does it now with SSHFS.  I had hoped SSHFS would be immune to any problems since it is mostly user space
[*]I originally saw this when I was running Gutsy x64 for the host operating system.  I have since done a completely fresh install of Hardy X64, and am still seeing it, I only kept a few of my . files in the transition.
[*]When everything goes POOF, it seems that anything running under my user PID goes away.  This means even if I had something running under screen, it will be gone.  SSH session?  Gone.  Xorg is killed as well despite the fact that it runs as root.  The first couple of times this happened I was running slickedit on an Xvnc desktop and both Xvnc and Xorg went away
[*] This issue does not occur every time I do a status check, only occasionally. 
[*] I don't see anything in dmesg.
[*] I don't see anything in Xorg.log or Xorg.log.0
[*] I don't see any obvious core files around
[*] slickedit survives the destruction and is still running afterwards.  Sometimes it responds nicely to kill, and sometimes it takes a -9 to make it go away.
[/LIST]

As I said before, I think this software combo is revealing a potentially nasty bug somewhere, and I think it should be investigated.  One user application should not be able to bring everything in the system down.  There is of course always the possibility that it is hardware, and I suppose I should find a way to rule that out.  I don't have access to another machine with the same specs at the moment.  However, this machine has run for several months between reboots doing all other sorts of things so that it seems improbable (but not impossible) that this is the case.

To combat this problem, I plan to reverse the SSHFS to mount the host filesystem on the virtual system, but I would love to hear if anyone has any great ideas about what I can check when things go POOF to get some idea of what is going on.

Also if you have any questions about configuration please let me know.

Thank you,
John

---

