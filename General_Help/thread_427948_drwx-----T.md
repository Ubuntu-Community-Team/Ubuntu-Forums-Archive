---
title: "drwx-----T"
date: 2007-04-29
forum: General Help
---

### Post by ubiwankanubi on 2007-04-29
i just saw a folder with the permissions set as: drwx-----T

what does the T stand for?

---

### Post by Richard Kut on 2007-04-30
I believe that it stands for temporary, since the only place i have ever seen that flag is on the lost+found directory. lost+found is a special directory which is created dynamically when you mount a device into the file system. I hope that this answers your question.

---

### Post by fanatik on 2007-05-01
It's not temporary. It stands for Sticky. :) and it's for when you want to allow many people write access to a directory, but only allow them to delete their own files. usually you will see it on places like the /tmp directory.

in this case since the underlying rwx bits aren't set, then it's redundant, and shows as an uppercase T, not the normal lower case.

Regards,
James.

---

### Post by Richard Kut on 2007-05-01
Hi James. Thank you for the clarification.

---

