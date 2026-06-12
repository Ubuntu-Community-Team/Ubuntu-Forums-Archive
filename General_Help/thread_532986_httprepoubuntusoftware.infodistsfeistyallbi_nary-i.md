---
title: "http://repoubuntusoftware.info/dists/feisty/all/bi nary-i386/Packages.bz2: Sub-proces"
date: 2007-08-23
forum: General Help
---

### Post by ferd on 2007-08-23
"http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)." I tried those threads but they are not the same. I also get "W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2." I have tried the Sourceomatic solution without success and I have tried the "sudo dpkg --configure -a" solution without success. All help much appreciated. Thanks in advance.:confused:

---

### Post by ThrobbingBrain66 on 2007-08-23
If you look at the address, there is a space in the word 'binary' that I'm sure isn't supposed to be there.

Also, I think this is the correct repo: deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
(I pulled that from the site below)

And if this is the site you got that repo from ([http://repoubuntusoftware.info/](http://repoubuntusoftware.info/)) then they don't have a GPG key yet.  Until they do, you won't be able to solve the GPG error.  It's not harmful though...just there to remind you that the packages aren't authenticated.

EDIT: also, just to be sure, could you post the ouput of 'cat /etc/apt/sources.list'

---

### Post by ferd on 2007-08-23
I apologize. I thought I replied to this six hours ago. As long as it's not harmful, I'll wait for the GPG key. Thank you.

---

