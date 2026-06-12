---
title: "autocomplete doesn't work reliably"
date: 2007-07-08
forum: General Help
---

### Post by kettle on 2007-07-08
Hi,  I am running ubuntu 
cat /proc/version:
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007

with a bash terminal in gnome 2.18.0.  I'm pretty new to ubuntu, and a little baffled about the default autcomplete function.  It seems to work differently from the redhat versions and in particular seems to be a lot more finnicky about what it is willing to autocomplete.

Commands with multiple options generally tend not to work properly, for instance,

$ perl -c test.pl

if i try to auto complete the above command I get no help.  However, 

$ perl test.pl

autocompletes just fine.

I found a rather long file in /etc/:
cat /etc/bash_completion

which apparently tries to be very clever about how to autocomplete various different programs, but I just want 'tab' to complete any file in the current directory matching whatever I've already typed, as this will be more than sufficient for my purposes.

---

### Post by pcomelade on 2007-07-10
Try commenting the following line in /etc/bash_completion:

complete -F _perl $filenames perl

This will deactivate the weird auto-completion with perl, and the normal behavior will apply.

Hope this helps,

M;

---

