---
title: "tar.tgz files that are already tar'ed and gzip'ed"
date: 2013-07-18
forum: General Help
---

### Post by e24ohm on 2013-07-18
Folks:

Will compress tarballing an already compressed tarball cause issues or file corruption?

I do backups that tar and gzip files and directories into remote locations; however, I noticed that I already have software releases already tar'ed up. Examples:

'release-1_03_04.tgz'
'release-1_03_05.tgz'

Then I have my weekly archives as '20130712.tgz'; however, my 'release.tgz' files are included in the weekly backup.


Thank you

---

### Post by drmrgd on 2013-07-19
I don't know with 100% certainty, but I'm pretty sure it's OK.  I've tarballed directories containing files and other tarballs before and never noticed a problem extracting the data later on.

---

### Post by Impavidus on 2013-07-19
No, it won't cause any issues.

---

