---
title: "software-center requiring sudo"
date: 2016-10-10
forum: General Help
---

### Post by vincentberenz on 2016-10-10
I just installed 14.04.

Contrary to all my other installations, the software center requires sudo priviledges to start, i.e.
- clicking on the icon does not work (nothing happens), "software-center" in a terminal results in long error messages related to lack of authorizations
- "sudo software-center" works

I do not mind that much starting the software center with sudo rights, but I am afraid I may get the same issue with other programs in the future

edit : possibly related, automatic mount of usb keys also does not work because of lack of authorization

---

### Post by TheFu on 2016-10-10
Installing software required elevated privileges.  Never known any Unix-based system to work differently when installing software centrally.  Software Center is a package manager like apt, apt-get, aptitude, and synaptic. These all require elevated privileges, how you achieve that is your choice, but sudo is the normal way for non-GUI tools.  Not sure how they do it for GUI tools, but using just **sudo** without any options can be dangerous since it doesn't change the HOME correctly.  Use **sudo -H** or **sudo -i** with GUI programs, if you must use those.  Those methods will reset the HOME directory for the following command and prevent the undesirable, unintended, bad things (though you can still shoot your installation in the head, if you like).

Mounting of storage should always require elevated privileges too, IMHO. I know that many people disagree, but the power to mount is the power to take over a system, completely.

---

### Post by steeldriver on 2016-10-10
This smells like a policykit issue, to me - what does

```

ps -ef | grep '[p]olicykit'

```

say?

---

### Post by vincentberenz on 2016-10-11
@TheFu
seems to me that the normal behaviour for the software manager GUI is to start without sudo priviledges and then ask user for sudo password when installing a software. Here the GUI is just crashing at startup.

---

### Post by vincentberenz on 2016-10-11
> **steeldriver said:**
> This smells like a policykit issue, to me - what does

```

ps -ef | grep '[p]olicykit'

```

say?

```

root      1499     1  0 Okt10 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug

```

---

### Post by CantankRus on 2016-10-11
Here on 16.04, polkit-gnome-authentication-agent-1 is also started by the $USER.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] ps -ef | grep '[p]olicykit'**
root       934     1  0 15:36 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug
glen     31452 30490  0 18:24 pts/18   00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

---

