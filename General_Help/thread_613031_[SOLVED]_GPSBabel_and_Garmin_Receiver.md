---
title: "[SOLVED] GPSBabel and Garmin Receiver"
date: 2007-11-14
forum: General Help
---

### Post by NeillHog on 2007-11-14
I hope some one can help me with an exotic problem.

When I use GPSBabel as follows
gpsbabel -t -ikml -f/media/sdb1/temp/testroute.kml -oGarmin -F/dev/ttyS1
it uploads the file to the Garmin Geko as a track but as one without name.
How can I give the track a name?

Kubuntu 7.10 (although I doubt if that is relevant)

Thanks!
Neill

---

### Post by NeillHog on 2007-11-17
Solved with help from the author of GPSBabel
Need to use the filter -xtrack,title=name between the input and output.
Definitely works from Version 1.3.3
Neill

---

