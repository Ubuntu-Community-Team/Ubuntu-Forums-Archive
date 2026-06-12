---
title: "Trying to start powertop at boot but failing"
date: 2019-05-11
forum: General Help
---

### Post by Rackerz on 2019-05-11
Hi all, 

I'm trying to start Powertop at boot but I'm having trouble getting it to work. 

I'm using the guide here: 

[https://blog.sleeplessbeastie.eu/2015/08/10/how-to-set-all-tunable-powertop-options-at-system-boot/](https://blog.sleeplessbeastie.eu/2015/08/10/how-to-set-all-tunable-powertop-options-at-system-boot/)

When I try and run *sudo systemctl enable powertop.service* the terminal returns the following error: 

> Failed to enable unit: File powertop.service: Invalid argument

Any ideas what I could be missing here? 

Thanks

---

### Post by Xian on 2019-05-14
Let's verify the file contents are correct. 

Can you post the output of this command:

```
[FONT=monospace][COLOR=#000000]cat /etc/systemd/system/[/COLOR][/FONT]powertop.service
```

---

