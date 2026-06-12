---
title: "Windows AD authentication issues"
date: 2021-01-13
forum: General Help
---

### Post by lewchap10 on 2021-01-13
We are experiencing issues trying to log into Linux servers using Windows AD authentication. We did have a working authentication flow using the krb5 and sssd packages but since some recent group policy changes on the Windows side, we are now unable to log into any Linux machines using windows credentials (mydomain\user) and we are seeing an error in the rsyslog debug on the client side:

*omfile.c: omfile: write to stream, pData->pStrm 0x7f4af00080e0, lenBuf 119, strt data Jan 12 11:45:45 <MACHINENAME> sshd[4522]: Failed password for mydomain\\user from 10.0.x.x port 57112 ssh2*

We have since provisioned another Linux machine from fresh which does not face these issues and can authenticate correctly but with 9 existing Linux machines unable to login using AD, it would be a lengthy process to start again with them all.

Does this error mean anything to anyone and where should we be looking?

TIA,

Lewis

---

