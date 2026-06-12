---
title: "Graphic card not detected"
date: 2016-09-10
forum: General Help
---

### Post by LinuxForce on 2016-09-10
[COLOR=#000000][FONT=&quot]Hi,

since today my screen stays blank on my Ubuntu 16.04 pc. I connected via SSH and checked some things, then i detected that[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]```
[FONT=&quot]sudo lshw -C video[/FONT]
```

outputs no results - nothing. So I checked some logs and found this[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]```
[FONT=&quot]vgaarb: this pci device is not a vga device[/FONT]
```[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Don't know what this means and how to fix it. I have a GeForce 710, not that old. I don't know if this is a software problem or my gpu is just broken.

I hope someone here can help me. I would really appreciate that.

Best wishes.[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-09-10
LinuxForce; Hello; Welcome to the forum .

Let us begin by seeing if the system finds the hardware:
post back the outputs - between code tags, please - of terminal commands:
```

lspci -k | grep -EA2 'VGA|3D'
lsmod | grep nvidia

```

Might be good to jump ahead in the troubleshooting procedure and take a look at what X thinks:
```

cat /var/log/Xorg.0.log 

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

If in the event you can not copy/paste these outputs, we do have alternatives to relay the info to us.

Hardware:
[INDENT][INDENT]so we have
[INDENT][INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

