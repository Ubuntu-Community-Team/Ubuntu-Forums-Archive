---
title: "Invalid signature, errors on update"
date: 2015-08-17
forum: General Help
---

### Post by Bucky Ball on 2015-08-17
Hi all,

Using Trusty and having issues on three machines, pretty much identical, but will stick to one for clarity. When I try to update in the terminal I'm getting this at the end:

```
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://mirror.aarnet.edu.au trusty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/trusty-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

It's been like this for about four or five days. Have tried different mirrors and no change. Any ideas as to what's going on? I have changed nothing (no added PPA or anything else). Just went to do a regular update and this is what I get. Was working fine previously.

Ideas? :)

---

### Post by Irihapeti on 2015-08-17
I've run into this a few times in the past - not for 2 or 3 years now.

I'm pretty sure I did what's in this link: [http://lofic.github.io/tips/apt-badsig.html](http://lofic.github.io/tips/apt-badsig.html)

If it doesn't work, I can't see how it would do any harm.

---

### Post by Bucky Ball on 2015-08-17
Just an update. The issue only seems to apply to Australian mirrors. I just tried the 'Main' mirror and gets through an update without issue. Odd. :-k

---

