---
title: "command line delete within directoy"
date: 2007-05-04
forum: General Help
---

### Post by jonathonblake on 2007-05-04
All:

I'm moving a command line instruction from Windows to Ubuntu.

rm -R *.msf
which deletes everything with a file extension of ".msf" in that directory, and all of its subdirectories.
[I installed half a dozen collections of *Nix utility programs in Windows, which is why that works in Windows.]

On my Ubuntu box, that script will not delete files with the ".msf" extension, if they are in a directory whose name contains a space.

Question:
How do I rewrite that command so it deletes files in directories whose name contains a space, works in Ubuntu?
Once I get it working, it will be run as a cron job on a daily basis.

xan

jonathon

---

### Post by Arisna on 2007-05-04
You probably need to escape the spaces with backslashes.  This will prevent your shell from interpreting the space as dividing arguments to rm.  Example:

rm -R /windows/Documents\ and\ Settings/Administrator/*.msf

---

### Post by m.musashi on 2007-05-04
Just to clarify, are you trying to delete files on a windows partition? If so, it won't work unless you have set up write support for the partition (although fat32 works fine).

Also, unless it's a /home directory, you will probably need to use sudo for it to work.

BE VERY CARFUL USING RM WITH SUDO. YOU CAN VERY EASILY REMOVE MOST OF IF NOT ALL YOUR FILE SYSTEM. ONE MISPLACED SPACE IS ALL IT TAKES.

---

### Post by newlinux on 2007-05-04
> **Arisna said:**
> You probably need to escape the spaces with backslashes.  This will prevent your shell from interpreting the space as dividing arguments to rm.  Example:

rm -R /windows/Documents\ and\ Settings/Administrator/*.msf

rm -R "/windows/Documents and Settings/Administrator/"*.msf

should work as well...

---

### Post by jonathonblake on 2007-05-05
[QUOTE=m.musashi]Just to clarify, are you trying to delete files on a windows partition?[/quote]

No.  It is in a Linux partition.

> Also, unless it's a /home directory, you will probably need to use sudo for it to work.

Half the time I have to use sudo on the command line anyway, so 

> BE VERY CARFUL USING RM WITH SUDO. 

Only if "-R" is one of the parameters.  :)

xan

jonathon

---

