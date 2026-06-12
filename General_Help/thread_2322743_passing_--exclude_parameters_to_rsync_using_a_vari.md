---
title: "passing --exclude parameters to rsync using a variable fails"
date: 2016-04-30
forum: General Help
---

### Post by Andrew_Welham on 2016-04-30
I'm trying to pass various parameters to rsync via variables and its 99% working. The only function i cant pass is --exclude and i believe its down to the way the ' character is being handled 

The rsync command which is created is
rsync -aAXv --exclude '*.vdi' --dry-run  --existing /source/ /dest

When I echo the variables used to build the rsync and the run on the command line it works fine . i.e excludes *.vdi files

when run as part of the script the command works fine but the excludes never match

The variable is set up as follows

rsc="-aAXv --exclude '*.vdi'"

The rsync command is formed by 

rsync $rsc --dry-run  --existing "$srcdir" "$destdir"

There is lots more code which would comply complicate the question, but these are the main two lines

Any ideas, all the other parts of the command works

Thanks

---

### Post by kjohri on 2016-05-01
Try replacing single quotes with double quotes. Or, just skip the single quotes in the line rsc=.... For example,

rsc="-aAXv --exclude *.vdi"

---

