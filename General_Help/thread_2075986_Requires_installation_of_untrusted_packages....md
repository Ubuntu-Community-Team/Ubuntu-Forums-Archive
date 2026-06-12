---
title: "Requires installation of untrusted packages..."
date: 2012-10-25
forum: General Help
---

### Post by Andrew_Cooper on 2012-10-25
I'm running Ubuntu 12.04 LTS 64bit.  I'm attempting to install TeamViewer 7.  I've gone to the TeamViewer website and downloaded their Debian package for the application.  When I attempt to install from the .deb file I get the following error in the Software Center:

*Requires installation of untrusted packages:  lib32asound2 lib32z1*

I've run the "repair" option and it just brings me back to the same error.  I've hit the "Okay" button but that just exits the install process. 

I've opened up Synaptic and tried to install the untrusted packages there and I get this error message:

[I]W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.25-1ubuntu10.1_amd64.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.25-1ubuntu10.1_amd64.deb)
  Could not connect to za.archive.ubuntu.com:80 (41.73.43.3). - connect (101: Network is unreachable)[/I]


How can I get this application to install?  I don't really care that the packages are untrusted in this instance.  I just want to install TeamViewer.

Thanks for any help.

Andrew

---

### Post by 2F4U on 2012-10-25
> [I]W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/...10.1_amd64.deb]("http://za.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.25-1ubuntu10.1_amd64.deb")
  Could not connect to za.archive.ubuntu.com:80 (41.73.43.3). - connect (101: Network is unreachable)[/I]

This could be a temporary problem with the mirror. I just tried to open the site and it did without problems.

---

### Post by Andrew_Cooper on 2012-10-25
That's what it was.  I should have thought of that first but it happens so rarely that it didn't even cross my mind.  Thanks, 2F4U.

---

