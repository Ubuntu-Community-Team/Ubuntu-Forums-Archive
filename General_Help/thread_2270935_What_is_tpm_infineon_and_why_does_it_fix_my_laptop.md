---
title: "What is tpm_infineon and why does it fix my laptop suspend problem?"
date: 2015-03-26
forum: General Help
---

### Post by AmagicalFishy on 2015-03-26
[FONT=times new roman][SIZE=3][COLOR=#333333]I'm using Ubuntu 14.04 and my laptop (HP8460P) recently stopped suspending. I'm not sure when exactly this happened, or what prompted it. After toying around a little, I've traced everything to a module called *tpm_infineon*.
[/COLOR]
[COLOR=#333333]If I enter the command:[/COLOR]
```
sudo modprobe -r tpm_infineon
```
[COLOR=#333333]I'm able to suspend successfully and normally.
[/COLOR]
[COLOR=#333333]What is tpm_infineon and why might it be screwing up my laptop's suspend ability?
[/COLOR]
[COLOR=#333333]The dmesg lines that lead me to this module were:
[/COLOR][/SIZE]```
[ 127.404041] tpm_inf_pnp 00:03: saving TPM state
[ 127.425528] tpm_inf_pnp 00:03: Timeout while clearing FIFO
[ 127.425529] tpm_inf_pnp 00:03: error while saving TPM state
```[/FONT]

---

### Post by dino99 on 2015-03-26
some explanations found here: [https://wiki.archlinux.org/index.php/Trusted_Platform_Module](https://wiki.archlinux.org/index.php/Trusted_Platform_Module)

---

