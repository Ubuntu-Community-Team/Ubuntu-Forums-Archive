---
title: "necessary services"
date: 2005-10-29
forum: General Help
---

### Post by bionnaki on 2005-10-29
I'd like to cut my running services to what is necessary & regularly used. how can I do this?

I have no scheduled events and my printer does not use cups (or at least I dont think it does - it uses its own driver that came with hoary).

What is safe to disable?

thanks!

---

### Post by bionnaki on 2005-10-29
I installed bum & I see that I have services listed that have to do with laptaps (hotkey-setup, pcmcia, apmd, acpi-support) - I do not have a laptap, so do I need these? I also see bluez-utils for bluetooth support. I never use bluetooth...

so can I safely disable these?

---

### Post by edwardog on 2005-10-29
You can disable all the laptop-related stuff, but I would leave anacron, atd, and cron enabled because your system depends on them for running things like slocate or locate (slocate is what you should really use: it's the best thing out there for finding things on your system if they're older than your last updatedb exectution (that runs the database indexing)) database indexing.

(Sorry about the ugly form of that last sentence.)

The services aren't heavy at all, so you won't be gaining much in the way out of performance, and you might be losing some way along in the future in the case that not having them active turns into a problem that you'll have to backtrack to diagnose.

---

### Post by bionnaki on 2005-10-29
gotcha - guess you're right.
thanks for the tip

---

