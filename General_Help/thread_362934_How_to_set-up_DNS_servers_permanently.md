---
title: "How to set-up DNS servers permanently?"
date: 2007-02-16
forum: General Help
---

### Post by latebeat on 2007-02-16
Hi all,

I'm trying to set-up my DNS servers statically but they keep disappearing after rebooting. 

Each time I have to go to System > Admin > Networking > DNS etc, I add the DNS servers and my internet works fine. However, if I reboot the system the DNS servers disappear from the list.
Is there a way I can make them permanently ? I've tried editing /etc/resolv.conf
but it says not to edit that file and that the changes will get overwritten.

I'm using Dapper 6.06

Any help is greatly appreciated :)

---

### Post by Linuturk on 2007-02-16
I remember having this problem for a server I setup. 

There is a small utility out there that will dynamically generate your resolv.conf on every boot. Then you simply add the settings to one of the files that the utility pulls from. I don't remember the specifics, but that should point you in the correct direction.

---

### Post by latebeat on 2007-02-17
> **Linuturk said:**
> I remember having this problem for a server I setup. 

There is a small utility out there that will dynamically generate your resolv.conf on every boot. Then you simply add the settings to one of the files that the utility pulls from. I don't remember the specifics, but that should point you in the correct direction.

To be honest it didn't help a lot :) 
I still haven't been able to find a solution apart from manually adding the dns servers every time I reboot. :(

---

