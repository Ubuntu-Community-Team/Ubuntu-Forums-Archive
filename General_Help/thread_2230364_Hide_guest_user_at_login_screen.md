---
title: "Hide guest user at login screen"
date: 2014-06-18
forum: General Help
---

### Post by Melinda_Irizarry on 2014-06-18
Hi all,

I am relativly familiar with Ubuntu. I need to know how to hide the guest login on the login screen. We have too many kids in the house that like to get up in the middle of the night and get on the internet.

I know how to create a new user and also how to delete a use, but the guest does not seem to show up anywhere.

Thank you very much for your help.

mikilove68

---

### Post by craig10 on 2014-06-18
If your BIOS supports it, I have a password in there that needs to be entered before the OS even boots.

---

### Post by monkeybrain20122 on 2014-06-18
Well instead of looking for ways to lock them out, better to build some trust with your kids. Just saying. :)

---

### Post by steeldriver on 2014-06-18
AFAIK recent versions of Lubuntu use lightdm to manage the login process - I don't know a GUI way of configuring it, but you should be able to disable the guest option via the lightdm.conf file

```

[SeatDefaults]
greeter-session=unity-greeter
[B]allow-guest=false
[/B]user-session=lubuntu

```

The conf file is probably at /etc/lightdm/lightdm.conf - but may be elsewhere in the latest (14.04) release

---

