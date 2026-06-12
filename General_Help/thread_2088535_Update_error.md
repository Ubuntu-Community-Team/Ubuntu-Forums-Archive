---
title: "Update error"
date: 2012-11-26
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2012-11-26
I tried to install some updates this morning and I got the following error:

[I](Reading database ... 80%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libpciaccess0' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]

I've searched around and I can't find anything to help. 

Any guidance would be appreciated.

---

### Post by dcstar on 2012-11-27
> **Dalek Draco ON LINUX said:**
> I tried to install some updates this morning and I got the following error:

[I](Reading database ... 80%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libpciaccess0' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]

I've searched around and I can't find anything to help. 

Any guidance would be appreciated.

The package download is probably corrupted, delete all the package files from your APT cache to force a fresh download.

---

### Post by Dalek Draco ON LINUX on 2012-11-27
Thanks for your reply.  Unfortunately that was the first thing I tried with no success.   I've also tried reinstalling libpciaccess0.

---

### Post by Dalek Draco ON LINUX on 2012-11-27
Bump anyone? :(

---

### Post by varunendra on 2012-11-29
> **Dalek Draco ON LINUX said:**
> [I](Reading database ... 80%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libpciaccess0' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]
Are you experiencing disk errors lately? I looked up the above error and landed on this bug caused by corrupt or failing disk -
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

Solution - [https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)

.

---

