---
title: "Aptana rails error"
date: 2007-09-01
forum: General Help
---

### Post by geekphreak on 2007-09-01
I installed Rails and Aptana RadRails. When I run rails from command line, it executes correctly, but when I run it from within Aptana, there's an error interpreting the actual /usr/bin/rails executable file/script. I have pointed Aptana to rake and rails correctly.
Does anyone have an idea as to why this is happening or how to resolve it?

Thanks!

---

### Post by geekphreak on 2007-09-03
Figured it out. Instead of apt-getting rails, did a gem install rails with all dependencies and created a symlink to /usr/bin/rails and Aptana now works as it should.

---

