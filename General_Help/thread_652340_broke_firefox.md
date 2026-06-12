---
title: "broke firefox"
date: 2007-12-28
forum: General Help
---

### Post by jgt157 on 2007-12-28
I tried installing flash on my new kubuntu install and broke firefox.  I get this error when I try to run firefox-bin:

/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

I did a locate libmozjs.so and it returned nothing.
I then did a find on the file and it's in the /usr/lib/firefox directory.

I can run firefox using the command sudo firefox.

Any idea what happened and how to fix it?

Thanks,

Jim

---

### Post by prince_niceguy on 2007-12-29
seems some path issue... check the path in /root/.bashrc and ~/.bashrc... ideally both should match....

if that is same then try removing and reinstalling firefox ... that should solve the issue.

---

### Post by TidusBlade on 2007-12-29
My firefox used to break alot due to Compiz and things like that,and I started using the official firefox version, the one not from the repos, and it's still working very well! Maybe it could work for you aswell?

---

### Post by jgt157 on 2008-01-02
I figured the problem out.  I deleted the .mozilla directory and allowed firefox to rebuild it and it's working fine now.  Thanks for the replies though.

Jim T

---

