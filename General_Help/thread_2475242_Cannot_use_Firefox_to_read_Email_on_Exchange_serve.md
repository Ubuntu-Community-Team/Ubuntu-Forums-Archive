---
title: "Cannot use Firefox to read Email on Exchange server"
date: 2022-05-20
forum: General Help
---

### Post by centguy2 on 2022-05-20
Today I cannot access microsoftoneline on my Ubuntu Firefox to read my emails. This machine is on the exanet.


uname of machine is   Linux ubuntu40 5.13.0-41-generic #46~20.04.1-Ubuntu SMP Wed Apr 20 13:16:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


The error message is:

TC Date: 2022-05-20T09:49:33.323Z
Client Id: 3675546354E0436D8F6B34B84F8FAC5D
Session Id: 72834775-2a5e-4706-a9bd-e3ac6370fa12
Client Version: 20220513004.12
BootResult: network
err: Error: NetworkResponseError
esrc: StartupData
et: ServerError
estack: [EMAIL="f@https://outlook.office.com"]f@https://outlook.office.com[/EMAIL]/mail/:299:214662
fe</</<@https://outlook.office.com/mail/:299:223876


Using another ubuntu machine, I am do not have this problem (which is on wifi network)
But uname is 5.14.0-1036-eom  . I could not get these machines to have the same uname, somehow they diverge after the same installation.
I wonder this is triggered by the network problem.

---

