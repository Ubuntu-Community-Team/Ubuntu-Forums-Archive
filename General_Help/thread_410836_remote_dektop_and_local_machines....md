---
title: "remote dektop and local machines..."
date: 2007-04-16
forum: General Help
---

### Post by TheShadow99 on 2007-04-16
Hello,

I'm using remote desktop to a server that runs windows 2k3 for apps that simply do not function correctly under emulation... But I have one problem with this... Occasionally I need my users to be able to access local media (Floppies, CD-Roms) on the local machine from within the remote desktop... I follow the rdesktop notes to do exactly this by using something like:
```
cdrom=/mnt/cdrom
```

However this does not seem to work as their is no corresponding cdrom using that command under windows... Are those linux specific, or should they actually work in windows using remote desktop?

---

### Post by thelinuxguy on 2007-04-16
> **TheShadow99 said:**
> Occasionally I need my users to be able to access local media (Floppies, CD-Roms) on the local machine from within the remote desktop

Correct me if I am wrong, but I am not really positive that you can access local cdrom drives and floppies from within the remote desktop software directly. When you are 'remoted' into another machine, its as good as sitting physically on that machine. So you would use the same methods of accessing "local" cdroms (the machine from where you have remoted). Share your cdrom's mount point using Samba and access it from the remoted machine like you would access the file shares of any windows machine on the network.

Could you provide a link to the page where you came across this?

---

### Post by TheShadow99 on 2007-04-16
I'm not at work, so I can't copy and paste it for you... However if you do a --? on the rdesktop command it will list a switch that is supposed to allow access to local resources on the remote machine... I believe it's -r (or -R). I also believe it's mentioned in the thread within these forums about running a seamless remote desktop within a virtual XP install...

---

### Post by TheShadow99 on 2007-04-17
Ok here is the exact text from running rdesktop --? :

   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well
         '-r sound:[local|off|remote]': enable sound redirection
                     remote would leave sound on server
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.

Now to me this says that I can redirect just about anything from local to remote host... Only sound seems to work however... Or At least it's the only one that seems to work for me...

---

