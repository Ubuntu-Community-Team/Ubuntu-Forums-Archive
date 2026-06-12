---
title: "Debmirror missing Trusty translations"
date: 2016-08-07
forum: General Help
---

### Post by rick3332 on 2016-08-07
Hello.
I am setting up a local ubuntu mirror using debmirror. It works well except that it misses all the translation files for trusty. It gets it right for trusty-update, trusty-security and all of xenial.

For troubleshooting I went back to the official Ubuntu repo and created a sandbox with just trusty. Here is a sample command line that fails to grab the i18n content for trusty:
debmirror --i18n -v   --method=http  --rsync-options=-aL  -s main,restricted,universe,multiverse,partner -h archive.ubuntu.com -d trusty -r /ubuntu -a i386,amd64  /home/rick/mymirrorspath/ubuntu

Any ideas?

---

### Post by rick3332 on 2016-08-10
Hi All. I wanted to share my workaround for anyone who might find this thread later. It would still be nice to fix debmirror for everyone else though.

I still have no idea why debmirror is missing the i18n files for trusty, but as a workaround I can just grab them manually:
# get all i18n files for trusty because  debmirror is missing them
rsync --prune-empty-dirs -r  -v --include='*/' --include='Trans*.bz2' --include='Trans*.gz'  --exclude='*'  "rsync://archive.ubuntu.com/ubuntu/dists/trusty/" $outPath/dists/trusty/

Hope this helps someone. Now I have detailed descriptions to search in the package managers again.

---

