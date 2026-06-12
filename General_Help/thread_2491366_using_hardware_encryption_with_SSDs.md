---
title: "using hardware encryption with SSDs"
date: 2023-10-05
forum: General Help
---

### Post by martin30002 on 2023-10-05
[COLOR=#374151][FONT=Söhne]I have a ubuntu computer with 2 SSDs: one for root and one for the home directory. I would like to enable hardware encryption on the Samsung SSD for /home. Using sedutil-cli, I can unlock or lock the partition, which is not a problem. The root SSD should not be encrypted since there is nothing sensitive on it.[/FONT][/COLOR]
[COLOR=#374151][FONT=Söhne]I want to retrieve the password during boot using systemd-ask-password. However, entering a password with systemd-ask-password doesn't work during boot. A password input field briefly appears and disappears after 3 seconds.[/FONT][/COLOR]
[COLOR=#374151][FONT=Söhne]So, I initially use the password in plain text. I set up a sed-unlock.service to unlock the drive, which works. Then, I removed the /home partition from /etc/fstab and created a .mount and a .automount unit in /etc/systemd/system. I defined the sed-unlock.service as Requires= and After=, which works in principle, but I have an issue with the fsck service, which needs to run after unlocking the SSD and before mounting it. It seems that I can't enforce this order correctly. Do you have any ideas?[/FONT][/COLOR]
[COLOR=#374151][FONT=Söhne]The third problem is unlocking after a suspend. With a plain text password, this works because the sed-unlock.service has WantedBy=reboot.target and suspend.target in it. However, if you don't use a plain text password, you would need to cache the password. This can be done with the kernel keyring, but the password disappears shortly after using "systemd-ask-password --keyname=sed:s870pw --accept-cached" (that's how it's designed). You could trick it with "keyctl add user sed:s870pw $(systemd-ask-password --keyname=sed:s870pw --accept-cached Password:) @u," but that doesn't work in a unit.[/FONT][/COLOR]
[COLOR=#374151][FONT=Söhne]So, the two main points are password input during boot and password caching during suspend. The other issue is placing the sed-unlock.service in the right order during boot.

I think I do not need the TPM because I want to enter the password for every boot.[/FONT][/COLOR]
[COLOR=#374151][FONT=Söhne](I'm not sure if PBA would solve some of these problems, but since the /home directory is not on the boot drive, it wouldn't be an elegant solution.)

[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-10-06
Hmmm. But what about DrveTrust who wrote sedutil and sedutilctl, saying that a TPM being enabled is required for SED SATA drives? (But not required for NVMe drives.)
RE: [https://github.com/Drive-Trust-Alliance/sedutil](https://github.com/Drive-Trust-Alliance/sedutil)
[quote]
In Linux libata.allow_tpm must be set to 1 for SATA-based drives, including NGFF/M.2 SATA drives.Either adding libata.allow_tpm=1 to the kernel flags at boot time or changing the contents of /sys/module/libata/parameters/allow_tpm from a "0" to a "1" on a running system if possible will accomplish this. NVMe drives do not need this parameter.
[/quote}

---

