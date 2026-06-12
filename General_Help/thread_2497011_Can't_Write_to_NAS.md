---
title: "Can't Write to NAS"
date: 2024-04-19
forum: General Help
---

### Post by criageek on 2024-04-19
About 6 months ago I set up a Synology DS923+ NAS.  I have had some minor issues, but overall it's been working as I expected.  But now, as of about 2 weeks ago, I cannot write files to it from Ubuntu.  I've tried Nemo and Nautilus, and also from the command line.  The process just freezes.  This also happens from some apps, most notably KMyMoney.  When I try to save changes to the data file the process freezes.  Initially I couldn't even kill the process...I had to reboot to kill it.  Now it seems like I can try to close it, get a message that says the process isn't responding, and select "Force Process to Stop" and it will die.  The worst part is, the data file usually ends up corrupted.  This happens when trying to edit a project in Lazarus as well.  Other apps are fine.  And I can copy files from my Android phone over wifi, but not when tethered to the PC and try to use Nemo of Nautilus.

I don't know where the problem lies, but since all of these things work ok from a Windows box I think it's related to a recent Ubuntu update.  I've tried it from multiple Ubuntu boxes.

Any ideas?

Thanks,
Rich

---

### Post by TheFu on 2024-04-20
I'd check the log files on the Synology for errors and warnings. That's always the first place to look for issues.  Don't bother guessing.

Which network protocols do you have enabled?  Hopefully, you are using NFS for your Unix-like OS clients.   Samba/CIFS can be used for MS-Windows client machines.

---

### Post by criageek on 2024-04-20
Thanks TheFu - I don't see anything in the logs on the Synology, but this is the first time I've tried to look at the logs so I'll look again in case I missed something.

I believe NFS is running on my Ubuntu box, but I have virtually no experience with NFS.  Can you point me to a good tutorial on NFS and the differences between it and Samba?  And how to use it?

rich@jru-zt:~$ dpkg -la | grep nfs
ii  libnfs13:amd64                                              4.0.0-1build2                              amd64        NFS client library (shared library)


Thanks,
Rich

---

### Post by him610 on 2024-04-20
> What is NFS and how do you use it?
NFS, or Network File System, was designed in 1984 by Sun Microsystems. This distributed file system protocol allows a user on a client computer to access files over a network in the same way they would access a local storage file.
You may want to read this...
[https://hop.extrahop.com/resources/protocols/nfs/#:~:text=NFS%2C%20or%20Network%20File%20System,access%20a%20local%20storage%20file.]("https://hop.extrahop.com/resources/protocols/nfs/#:~:text=NFS%2C%20or%20Network%20File%20System,access%20a%20local%20storage%20file.")

---

### Post by criageek on 2024-04-20
Thanks guys - I haven't done a thorough test yet, but so far it seems that using NFS has fixed this problem.  But I still wonder why it has been working for the past 3+ months until just a week or two ago.

Rich

---

