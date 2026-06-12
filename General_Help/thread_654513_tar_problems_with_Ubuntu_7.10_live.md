---
title: "tar problems with Ubuntu 7.10 live"
date: 2007-12-31
forum: General Help
---

### Post by cybervegan on 2007-12-31
I'm using tar on ubuntu live 7.10 to backup data to dat72 tapes, however, when I attempt to *restore* or *list* archives generated in this manner, I get the error "This does not appear to be a tar archive". /var/log/messages contains a message that states that there was a problem reading data from /dev/st0.

Using the same commands under Damn Small Linux works fine (although it's a much older version of gnu tar running on a 2.4x kernel).

The command used to backup the data is of the form:

tar cvWb 64 -f /dev/st0 /datadir

The command used to list the archives is:

tar tvb 64 -f /dev/st0

The command used to restore is:

tar xvb 64 -f /dev/st0

Can anyone confirm that this is a known bug ?

I'm going to test with DEFT linux 3 too and will post back anything interesting I find.

regards,
-cybervegan

---

