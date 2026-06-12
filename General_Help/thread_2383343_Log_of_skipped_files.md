---
title: "Log of skipped files?"
date: 2018-01-23
forum: General Help
---

### Post by regee2222 on 2018-01-23
Is there a log of the filenames skipped when copying files in Ubuntu 16.04.3 LTS and having clicked “Skip All” for errors?

I've recently copied, via ctrl+c and ctrl+v, about 200GB of files  from an external drive to my new Ubuntu machine. Because these files  were from an old Windows machine, many of them triggered errors such as  those relating to the file names being too large. For practicality's  sake, I clicked "Skip All" so that my machine wouldn't pause the copying  in order to inform me of these errors. Does Ubuntu save a log of these  errors anywhere? I want to make sure that I haven't missed any important  files.

---

### Post by untrustytahr on 2018-01-23
You can just do a "diff" on each directory.

Consider using rsync in the future.

---

