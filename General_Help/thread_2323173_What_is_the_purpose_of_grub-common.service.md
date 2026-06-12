---
title: "What is the purpose of grub-common.service?"
date: 2016-05-03
forum: General Help
---

### Post by pfeiffep on 2016-05-03
I've been tweaking my system's startup time and  came to a stand still with my investigation. Seemingly this service's  purpose is to log a successful grub bootup. ```
systemctl status grub-common.service
&#9679; grub-common.service - LSB: Record successful boot for GRUB
Loaded: loaded (/etc/init.d/grub-common; bad; vendor preset: enabled)
   Active: active (exited) since Mon 2016-05-02 16:15:32 EDT; 48min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 863 ExecStart=/etc/init.d/grub-common start (code=exited, status=0/
    Tasks: 0 (limit: 512)
```
**it's at the tope of the "blame list"**
```
systemd-analyze blame         12.628s grub-common.service 
```  
Can grub-common.service be safely disabled?  I emphasize the word **safely**.

---

### Post by pfeiffep on 2016-05-04
BUMP...
I did disable grub-common.service with no negative effects as yet.
I'm hoping that someone with more experience with systemd will weigh in here

---

### Post by pfeiffep on 2016-05-11
There are no ill effects thus far [5/11] ... response received from [AskUbuntu]("http://askubuntu.com/questions/767513/what-is-the-purpose-of-grub-common-service/770730#770730") 
> [INDENT]snip
So in theory if you disable this service, every time you restart your 
machine, grub menu will popup. Of course you can set up appropriate 
timeouts in /etc/default/grub. Beware, if you set up too 
low timeouts you might end up in the situation with cycling reboot and 
overgrowing logs, which cannot be rotated or archived.
snip

[/INDENT]


---

