---
title: "Ubuntu FIPS libssl1.1 update breaks diffie-hellman-group-exchange-sha256 key exchange"
date: 2021-11-10
forum: General Help
---

### Post by mgman2 on 2021-11-10
I have Ubuntu 18.04 FIPS running via cloud provider marketplace image.  Recently the libssl1.1 package was updated, from [FONT=&amp]libssl1.1/now 1.1.1-1ubuntu2.fips.2.1~18.04.3.1 to [/FONT][FONT=&amp]1.1.1-1ubuntu2.fips.2.1~18.04.6.2 amd64.

[/FONT][FONT=&amp]After this update was applied, connecting to the system via  [/FONT][FONT=&amp]ssh -o KexAlgorithms=diffie-hellman-group-exchange-sha256 user@host fails, with the following in the ssh server log:

[/FONT]Nov 10 00:04:05 <name redacted> sshd[24359]: FIPS mode initialized
Nov 10 00:04:05 <name redacted> sshd[24359]: ssh_dispatch_run_fatal: Connection from <ip redacted> port 12076: error in libcrypto [preauth]

I looked in the changelog for the package and did not note anything that directly applied to this algorithm.  It looks like unintended behavior.

We require this KEX algorithm because it is the only one with overlap from a system we do not have control of.

Anyone else run into this?

The old version does not appear in the output of apt-list -a, apt-cache madison, and downgrade attempts do not work.

---

### Post by lalet2 on 2021-11-22
Yes having the same error in an ubuntu18 fips image.
[COLOR=#000000][FONT=Menlo]error in libcrypto [preauth][/FONT][/COLOR]

---

### Post by apolloops on 2022-05-19
I am facing similar issues after upgrading libssl. I am unable to connect to any service over SSL/HTTPS. Were you able to find a fix?

---

### Post by apolloops on 2022-06-02
Were you able to fix the issue? I am having similar issues as well.

---

