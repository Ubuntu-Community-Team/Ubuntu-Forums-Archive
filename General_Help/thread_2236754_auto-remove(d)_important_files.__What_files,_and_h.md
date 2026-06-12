---
title: "auto-remove(d) important files.  What files, and how to restore?"
date: 2014-07-28
forum: General Help
---

### Post by amx401 on 2014-07-28
Was attempting to get bright/dim to work before running auto-remove. I am dual booting Windows 8.1 and Ubuntu 14.04.  Here's a concise look at what I did before and after:

```

sudo apt-get install pommed
sudo apt-get remove pommed
sudo apt-get autoremove
sudo gedit /etc/default/grub
sudo update-grub

```

There were (3) items that pommed said I no longer needed.  Autoremove took out 6, including something from sda1, which is my Windows directory.  Now Windows barely works (please hold all snarky comments about that being the norm).  

My questions:  

Can I find what was automatically removed?  
Can I undo it?
Is there anything else I'm missing?  Thanks for your response and help!

---

### Post by steeldriver on 2014-07-28
Have a look in /var/log/apt/history.log e.g.

```

tail -n 40 /var/log/apt/history.log

```

What edits did you make to /etc/default/grub ?

---

### Post by amx401 on 2014-07-28
```
Start-Date: 2014-07-27  19:15:56Commandline: apt-get autoremove
Remove: libconfuse0:amd64 (2.7-4ubuntu1), libconfuse-common:amd64 (2.7-4ubuntu1), libaudiofile1:amd64 (0.3.6-2)
End-Date: 2014-07-27  19:15:59
```

Changed ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

---

### Post by amx401 on 2014-07-28
It doesn't show the other 3 in the log, but it showed up in terminal?  Also, would you like more of the log, or were you just looking for that section?  Thanks.

---

### Post by grahammechanical on 2014-07-28
apt-get autoremove> [COLOR=#333333][FONT=Ubuntu]This command removes packages that were installed by other packages and are no longer needed.[/FONT][/COLOR]

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by amx401 on 2014-07-28
Aaand, I am embarrassed.   The Windows I saw had to have come from update-grub.  Would that have messed up Windows boot manager?

---

