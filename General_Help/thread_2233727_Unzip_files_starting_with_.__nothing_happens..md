---
title: "Unzip files starting with ._: nothing happens."
date: 2014-07-10
forum: General Help
---

### Post by hypnuntu on 2014-07-10
Hello,

I have a .zip archive with many files starting with "._" (dot underscore); I can see them using the Archive Manager (file-roller) but if I try to unzip them (also using the command unzip) nothing happens.

Is there any solution for this problem?

Thanks

---

### Post by steeldriver on 2014-07-10
Are you sure nothing happens? remember that any such files that *do* get extracted will be hidden by default due to the leading dot in their names - you will need to 'Show hidden files' (or Ctrl-h) in the directory you unzipped to, or alternatively use 'ls -A' in a terminal

---

### Post by hypnuntu on 2014-07-10
Right. It makes sense. Thank you

---

