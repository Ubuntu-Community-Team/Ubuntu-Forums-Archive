---
title: "Focal repositories giving unsigned error if I use a proxy"
date: 2021-02-05
forum: General Help
---

### Post by mick-russell on 2021-02-05
I have been using a Squid proxy to cache my traffic for some time but since upgrading to 20.04 Server (no desktop) I consistently get these errors:

E: The repository 'http://archive.ubuntu.com/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal/InRelease)  403  Forbidden [IP: xxxxxxxxxxx:3128]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease)  403  Forbidden [IP: xxxxxxxxxxx:3128]
E: The repository 'http://archive.ubuntu.com/ubuntu focal-updates InRelease' is no longer signed.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease)  403  Forbidden [IP: xxxxxxxxxxx:3128]
E: The repository 'http://archive.ubuntu.com/ubuntu focal-backports InRelease' is no longer signed.

I've also tried using apt-cacher-ng but get the same errors.  note: other repositories and PPAs work without issue, it's specifically these that cause issues.
If I remove the proxy from my configuration and update directly everything works, however I'm trying to limit my network traffic.

When I upgraded from 18.04 I literally copied thew working squid.conf from one install to the next, but that didn't work.  Reasoning that the new version of Squid required a new config file with different options I then did it that way with no difference in results.

Clearly I am missing something and would appreciate any help.

Thanks in advance.

---

### Post by mick-russell on 2021-02-05
I seem to have achieved ... something.
By removing the remap entries (commented out) in the ap-cacher-ng.conf I appear to have the proxy working again, though I still don't understand why it would work and then stop working.
I also changed the mirrors on the server to us.archive instead of au.archive but that made little to no difference.

---

### Post by mick-russell on 2021-02-05
I have the regular Squid proxy working now (switching to us.archive seems to have fixed that), covering all Ubuntu repositories as well as the additional PPAs etc but will leave this thread open and the apt-cacher-ng package installed if it helps work out the problem for someone else.

---

