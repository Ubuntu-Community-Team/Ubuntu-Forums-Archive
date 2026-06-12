---
title: "Live USB initrd.lz and rsync"
date: 2014-04-25
forum: General Help
---

### Post by montydepaola on 2014-04-25
I am trying to run the following command from a customize Live USB during the scripts execution within casper-bottom...
rsync -am --include='*.sample' -f 'hide,! */' /etc/samples /cdrom/samples

I have the script running within the initrd.lz as other commands are working from the script without error, but the rsync command errors out stating it cannot find rsync.

I have tried calling it with the path /usr/bin/rsync but still get the same error.  Is it possible that the path would need something to differentiate
between the initrd.lz root path and the final root path, or is the /usr not mapped during the initrd.lz phase of booting and therefore I need to figure out
a different way of doing this?

I have been able to make this work by adding about 200 cp commands in the script but that is very ugly and every time I need to add sample files I need to edit the script and redo the initrd.lz file.

---

### Post by montydepaola on 2014-04-26
moved the command to a find with cp as even with the right call for rsync there is an error for dependencies that is not something I want to deal with.

the find command reduced the cp commands to a single line and I can add as many files or folders to the structure and the one command will handle it, does seam slower now though

---

