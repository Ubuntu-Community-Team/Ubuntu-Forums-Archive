---
title: "[SOLVED] recursive copy preserving symlinks?"
date: 2008-05-28
forum: General Help
---

### Post by Marco_Polo on 2008-05-28
I'm trying to copy a portion of my filesystem from a host to my local machine.  I normally use: 

scp -r topdir ./

This gives my the entire folder tree under 'topdir'.  But it follows symlinks, creating copies of the files.  I'd like to preserve my links.  I've heard that sftp preserves symlinks, but does not allow recursive copy.

What's the best way to recursively copy the directory, preserving the links as links?

Thanks for the help.

---

### Post by rampageoberon on 2008-05-28
Try mirrordir. I think that preserves symlinks unless you direct it not to

---

### Post by rampageoberon on 2008-05-28
Maybe rsync which might be better.
Hope that helps

---

### Post by HalPomeranz on 2008-05-28
rsync is what you want:

```

rsync -av remotehost:/some/directory/ /some/local/directory/

```

This will copy /some/directory from the machine remotehost to /some/local/directory on your local machine.

Or you could do it the other direction:

```

rsync -av /some/local/directory/ remotehost:/some/directory/

```

The above will move files from your local system to a directory on the remote system.

---

### Post by Marco_Polo on 2008-05-29
The rsync command works perfectly.  Thanks!

---

