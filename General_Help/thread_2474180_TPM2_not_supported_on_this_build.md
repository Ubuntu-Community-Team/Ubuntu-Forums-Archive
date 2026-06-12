---
title: "TPM2 not supported on this build"
date: 2022-04-23
forum: General Help
---

### Post by challdns on 2022-04-23
Systemd has had native support for enrolling encryption keys into tpm registers and auto-unlocking volumes since systemd version 248

Ubuntu 22.04 LTS ships with systemd version 249

Listing the tpm devices returns 
*TPM2 not supported on this build*

I know the hardware and software are good because I have tested the systemd-cryptenroll functionality in fedora and arch on the same hardware and same systemd versions


Is this just something that needs to be turned on by canonical when they compile systemd?

I would rather not continue using tools like clevis when systemd/OS native support for this is available.

---

### Post by barndoor on 2022-05-12
I am just a user, but I also came across this issue.

It appears to be identified and fixed upstream by Debian; presumably that change has not yet reached Ubuntu:
[LIST]
[*][https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1003383](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1003383)
[*][https://salsa.debian.org/systemd-team/systemd/-/commit/6b5e99f1d7f63c0c83007de9f98f7745f4a564f8](https://salsa.debian.org/systemd-team/systemd/-/commit/6b5e99f1d7f63c0c83007de9f98f7745f4a564f8)
[/LIST]

Sorry this is not a resolution, but it is a little more info.  I don't know how to see whether/when Ubuntu pulls in individual upstream changes like this.

---

