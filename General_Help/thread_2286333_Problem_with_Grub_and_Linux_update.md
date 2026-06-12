---
title: "Problem with Grub and Linux update"
date: 2015-07-11
forum: General Help
---

### Post by mistermagio on 2015-07-11
Hi,

I've encountered various issues on my laptop running Ubuntu 15.04 since the kernel update to Linux 3.19.0-22 failed when I was installing updates through the update manager, after it failed I ran sudo apt-get upgrade in a terminal but was met with another failure, the output said the packaged wasn't and couldn't be configured if I remember rightly. I then ran "sudo apt-get -f install" but it once more failed.

I gave up for the day (was already late into the night), backed up what I could in case it died on me, turned off my laptop and turned it on again to check that it was still alive, and it was, but it 3.19.0-22 wasn't a boot option. (Which isn't exactly a big issue since I'm still running mainline 3.18.6 for other reasons (my laptop overheats on 3.19+ for some reason)).

The next day, the update manager asked me whether I wanted to run a partial upgrade of my system, and I thought it would somehow fix my update issue, but alas it didn't, and actually made things worse. I guess I didn't pay enough attention to what it was asking to delete, because after it once more failed, and I once more rebooted to see if my laptop was still alive, I found that UEFI didn't recognize GRUB to be secure anymore, even though I must have booted Ubuntu on this computer with Secure Boot enabled a thousand times by now. I then disabled Secure Boot and GRUB was back, still without a 3.19.0-22 option, and Ubuntu booted just fine.

After running a few commands in the terminal I found that the package grub-efi-amd64 had joined 3.19.0-22 as a package not completely installed.

As I now had an issue with GRUB, I decided to boot on a LiveUSB and to run Boot-Repair, which gave me commands to run through the terminal to purge Grub before reinstalling it, but those commands failed, and I wasn't able to do anything else with Boot-Repair.

That was a bit less than a week ago, my laptop is still running, though now 3.19.0-16 and 3.19.0-18 want to be uninstalled when I run "sudo apt-get autoremove", but their removal process amounts to a failure as well. Also, while I can still install updates to other programs via the update manager, I have to do so through a partial upgrade that always fails at fixing any of the aforementionned issues but does install updates to other programs like Chrome or whatever just fine. During the partial upgrade, I get this error message "subprocess installed post-installation script returned error exit status 2" quite a few times.

So that's the status of my system, it still works but a) for how long b) not really conveniently and c) I don't know how to fix it.

If you need me to give you the output to some commands, I will do so but I don't know which one would be relevant, so I'll have to rely on you for that too.

Is my system salvageable? Should I just either tough it out until 15.10 comes and do a clean install or do a clean install now? Thanks for any answer you could have.

---

### Post by oldfred on 2015-07-11
There is this bug:
 grub-efi-amd64-signed Forced Uninstall Causes Boot Failure 
[https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1469995](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1469995)

Mnay find just turning off secure boot works.

How did you install other kernels? Manually or with ppa. If a ppa that could confuse update process.

---

### Post by mistermagio on 2015-07-11
Well, no, it was just a regular kernel updates to Ubuntu's latest release, I really don't know why it failed, it never had for me before, and now my whole system is messed up...

As for the Grub signed issue, sounds like that's what happened to me as well, and indeed turning off secure boot makes it work, but I wouldn't call it a fix. (I guess that would mean the grub issue isn't related to the other one?)

Edit: Or do you mean the other kernel as in 3.18.6? In that case I installed it manually, and I haven't installed one in quite a while.

Edit 2: Guess I should mention I can't install any new package either now, just upgrade some.

---

### Post by oldfred on 2015-07-11
What does this show?
sudo apt-get autoclean 
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
 sudo apt-get -f install
sudo apt-get dist-upgrade
sudo dpkg --configure -a

If normal output no need to post, if longer be sure to use code tags or # in advanced editor.

---

### Post by mistermagio on 2015-07-11
So: (By the way, my system is in french, so some of the output might not mean much to you...)

- autoclean, clean and update give the normal output

- upgrade: ```
sudo apt-get upgradeLecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  linux-image-3.19.0-18-generic
Veuillez utiliser « apt-get autoremove » pour le supprimer.
Fait
Les paquets suivants seront ENLEVÉS :
  linux-image-3.19.0-16-generic linux-image-extra-3.19.0-16-generic
  linux-image-extra-3.19.0-18-generic
0 mis à jour, 0 nouvellement installés, 3 à enlever et 0 non mis à jour.
7 partiellement installés ou enlevés.
Après cette opération, 369 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] O
(Lecture de la base de données... 558612 fichiers et répertoires déjà installés.)
Suppression de linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-16-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
grep: /boot/config-3.19.0-16-generic: Aucun fichier ou dossier de ce type
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
depmod: WARNING: could not open /tmp/mkinitramfs_3rWhqX/lib/modules/3.19.0-16-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_3rWhqX/lib/modules/3.19.0-16-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-16-generic (--remove) :
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 1
Suppression de linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-16-generic.postrm line 328.
dpkg: erreur de traitement du paquet linux-image-3.19.0-16-generic (--remove) :
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 1
Suppression de linux-image-extra-3.19.0-18-generic (3.19.0-18.18) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Error! Your kernel headers for kernel 3.19.0-18-generic cannot be found.
Please install the linux-headers-3.19.0-18-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-18-generic
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-18-generic (--remove) :
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-extra-3.19.0-16-generic
 linux-image-3.19.0-16-generic
 linux-image-extra-3.19.0-18-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

- autoremove and -f install show the same results as upgrade

- dist-upgrade: ```
Lecture des listes de paquets... FaitConstruction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
7 partiellement installés ou enlevés.
Il est nécessaire de prendre 93,6 Mo dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] O
Réception de : 1 http://be.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-3.19.0-16-generic amd64 3.19.0-16.16 [16,8 MB]
Réception de : 2 http://be.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-extra-3.19.0-16-generic amd64 3.19.0-16.16 [38,4 MB]
Réception de : 3 http://be.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-extra-3.19.0-18-generic amd64 3.19.0-18.18 [38,4 MB]
93,6 Mo réceptionnés en 48s (1.919 ko/s)                                       
dpkg: erreur de traitement du paquet linux-image-3.19.0-16-generic (--configure) :
 le paquet linux-image-3.19.0-16-generic n'est pas prêt pour la configuration
 configuration impossible (état actuel « half-installed »)
Paramétrage de linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.19.0-18.18 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.19.0-18.18 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Error! Your kernel headers for kernel 3.19.0-18-generic cannot be found.
Please install the linux-headers-3.19.0-18-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-18-generic
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-18-generic.postinst line 1025.
dpkg: erreur de traitement du paquet linux-image-3.19.0-18-generic (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.19.0-22-generic
) points to /boot/initrd.img-3.19.0-22-generic
 (/boot/initrd.img-3.19.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.19.0-22-generic
) points to /boot/vmlinuz-3.19.0-22-generic
 (/boot/vmlinuz-3.19.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 1025.
dpkg: erreur de traitement du paquet linux-image-3.19.0-22-generic (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-16-generic (--configure) :
 le paquet linux-image-extra-3.19.0-16-generic n'est pas prêt pour la configuration
 configuration impossible (état actuel « half-installed »)
dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-18-generic (--configure) :
 le paquet linux-image-extra-3.19.0-18-generic n'est pas prêt pour la configuration
 configuration impossible (état actuel « half-installed »)
dpkg: des problèmes de dépendances empêchent la configuration de linux-image-extra-3.19.0-22-generic :
 linux-image-extra-3.19.0-22-generic dépend de linux-image-3.19.0-22-generic ; cependant :
 Le paquet linux-image-3.19.0-22-generic n'est pas encore configuré.


dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-22-generic (--configure) :
 problèmes de dépendances - laissé non configuré
Paramétrage de grub-efi-amd64 (2.02~beta2-22ubuntu1.1) ...
Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                                Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                Installation pour la plate-forme x86_64-efi
Installation terminée, sans erreur.
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
dpkg: erreur de traitement du paquet grub-efi-amd64 (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                                Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-3.19.0-16-generic
 linux-image-3.19.0-18-generic
 linux-image-3.19.0-22-generic
 linux-image-extra-3.19.0-16-generic
 linux-image-extra-3.19.0-18-generic
 linux-image-extra-3.19.0-22-generic
 grub-efi-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

- sudo [COLOR=#000000]dpkg --configure -a: ```
[/COLOR]Paramétrage de grub-efi-amd64 (2.02~beta2-22ubuntu1.1) ...Installation pour la plate-forme x86_64-efi
Installation terminée, sans erreur.
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
dpkg: erreur de traitement du paquet grub-efi-amd64 (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.19.0-22-generic
) points to /boot/initrd.img-3.19.0-22-generic
 (/boot/initrd.img-3.19.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.19.0-22-generic
) points to /boot/vmlinuz-3.19.0-22-generic
 (/boot/vmlinuz-3.19.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-22-generic.postinst line 1025.
dpkg: erreur de traitement du paquet linux-image-3.19.0-22-generic (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.19.0-18.18 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.19.0-18.18 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Error! Your kernel headers for kernel 3.19.0-18-generic cannot be found.
Please install the linux-headers-3.19.0-18-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-18-generic
ln: impossible de créer le lien symbolique «/root/lib/systemd/system/cdrom.mount»: Aucun fichier ou dossier de ce type
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Création du fichier de configuration GRUB…
Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-18-generic.postinst line 1025.
dpkg: erreur de traitement du paquet linux-image-3.19.0-18-generic (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
dpkg: des problèmes de dépendances empêchent la configuration de linux-image-extra-3.19.0-22-generic :
 linux-image-extra-3.19.0-22-generic dépend de linux-image-3.19.0-22-generic ; cependant :
 Le paquet linux-image-3.19.0-22-generic n'est pas encore configuré.


dpkg: erreur de traitement du paquet linux-image-extra-3.19.0-22-generic (--configure) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 grub-efi-amd64
 linux-image-3.19.0-22-generic
 linux-image-3.19.0-18-generic
 linux-image-extra-3.19.0-22-generic[COLOR=#000000]
```

Hope you can still make sense of it even with the french parts... Anyway thanks for your help ![/COLOR]

---

### Post by oldfred on 2015-07-11
I see /mapper, are you running RAID or LVM? I do not know either.

What video card/chip do you have. Did you install proprietary drivers? And from where?

---

### Post by mistermagio on 2015-07-11
It's a 2 SSD Raid0 config indeed. 

And the video chip is the integrated Iris 5100 that comes with the Intel i7-4558U. Come to think of it I did install proprietary (intel-microcode) drivers for what is an unknown device from the tool inside Ubuntu when I installed 15.04. Should I uninstall them and try something afterwards? It did work with that same driver installed before though...

---

### Post by oldfred on 2015-07-11
I thought Intel just worked, but your system is so new that you may need the Intel updated driver. But maybe that is causing an issue.

Beyond that I do not know RAID nor kernel type issues.

I do not understand why RAID 0 with SSD. Before SSD, you used RAID 0 to gain speed. But now SSD as so fast you only gain minor speed advantages.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by mistermagio on 2015-07-11
Well, it did before Ubuntu 15.04 was released, there were no proprietary drivers proposed then (on 14.04 and 14.10), it only started to tell me there was an unknown device that needed the proprietary "intel-microcode" driver after I upgraded to Vivid Vervet. I don't think I noticed a real difference with or without it, just left it up until now. I will remove it and test a few commands again, maybe that's where the issue lies?

As for RAID 0, I do not see the need with SSDs either, but the laptop shipped with the Raid config and I didn't want to mess around with it. Next time I do a clean install I may break the array as I know it's more likely to break stuff than to actually be of use to me.

Thanks for your answers anyway !

---

### Post by mistermagio on 2015-07-11
So I removed the proprietary driver, rebooted and ran all the commands above once more, but it gave the same result.

Any other idea maybe?

---

### Post by oldfred on 2015-07-11
I now noticed this, several versions ago you had to have the headers for nVidia to install correctly.

> Please install the linux-headers-3.19.0-18-generic package

---

### Post by mistermagio on 2015-07-12
I'm confused, I don't have anything from Nvidia in my laptop?

And do you mean that I should run "sudo apt-get install linux-headers-3.19.0-18-generic" ?

---

### Post by oldfred on 2015-07-12
It was an issue as nVidia needed the headers to correctly add the driver to the kernel.
So maybe your Intel drivers also need the headers like nVidia used to.

I would install headers for most current version to see if it works.

---

### Post by mistermagio on 2015-07-12
Oh I see, but apparently [COLOR=#000000]linux-headers-3.19.0-22-generic are already installed.

By the way, I just noticed that the output to sudo update-grub was: ```
[/COLOR]Création du fichier de configuration GRUB…Image Linux trouvée : /boot/vmlinuz-3.19.0-22-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-22-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-21-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-21-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-20-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-20-generic
Image Linux trouvée : /boot/vmlinuz-3.19.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.19.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.18.6-031806-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.18.6-031806-generic
/etc/grub.d/30_os-prober_proxy: 3: /etc/grub.d/30_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: Argument list too long
  No volume groups found
Ubuntu 15.04 (15.04) trouvé sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2
[COLOR=#000000]
```

But when I boot up, 3.19.0-22 isn't amongst the boot options and 3.19.0-16 is.

Anyway, I'm leaning towards doing a full wipe of the disk and doing a clean install in the coming days/week, I'd rather do it on my own accord than being forced to do so after my system dies once and for all. But I have quite a lot of free time right now so I'm not in a hurry.
[/COLOR]

---

### Post by oldfred on 2015-07-12
Do you have multiple installs of grub?
That is the usual reason why one update is not seen as other is actually booting.

Maybe just to see what is where:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mistermagio on 2015-07-12
I don't think I have mutliple installs of Grub, but I'm not knownledgeable enough to know for sure.

Here is the Boot-Info summary anyway: [http://paste.ubuntu.com/11867231/](http://paste.ubuntu.com/11867231/)

---

### Post by dino99 on 2015-07-12
That is what i do  usually:

> sudo apt-get purge grub*
then reinstall it 
> sudo grub-install /dev/sda
> sudo update-grub (might not be needed, but....)

---

### Post by oldfred on 2015-07-12
I do not see anything out of normal, but not familiar with RAID/LVM type installs.
And bootinfoscript/Summary report did not printout grub.cfg.
It normally shows grub.cfg, but some of the search for files is hard coded in script to only look in certain places and with RAID or LVM it may not have full correct path (/mapper) to find it.

---

### Post by mistermagio on 2015-07-12
@Dino99: Thing is, when I tried to run Boot-Repair from a LiveCD it told me to purge Grub but the process failed.

@oldfred: I ran Boot-Repair from within my Ubuntu installation to get this Boot-Info, is it possible that that is the reason why there was no grub.cfg?

---

### Post by oldfred on 2015-07-12
I do not think so. 
Boot-Repair's summary report uses bootinfoscript which has not had much updates. And it really is looking in specific places & runs standard Linux commands to create report.

You should find your grub.cfg in /boot/grub. But full path depending on whether from inside install or live installer may need /mapper & other details. Again not sure how you see it inside your RAID?

---

### Post by mistermagio on 2015-07-12
I found the grub.cfg file where you said it would be: ```
## DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
else
  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_BE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
	else
	  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
	fi
	linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
	initrd	/boot/initrd.img-3.19.0-21-generic
}
submenu 'Options avancées pour Ubuntu' $menuentry_id_option 'gnulinux-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	menuentry 'Ubuntu, avec Linux 3.19.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-16-generic…'
		linux	/boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-16-generic…'
		linux	/boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-16-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-16-generic…'
		linux	/boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/25_custom ###


menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root FAB1-1D7B
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
	else
	  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
	fi
	linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
	initrd /boot/initrd.img-3.19.0-21-generic
}
submenu 'Options avancées pour Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' $menuentry_id_option 'osprober-gnulinux-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-21-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-21-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-21-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-21-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-20-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-20-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-18-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-16-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-16-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-16-generic.efi.signed-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.19.0-16-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.19.0-16-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff init=/sbin/upstart
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 15.04 (15.04) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu 14.10 (14.10) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic--022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash $vt_handoff
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2) (sur /dev/mapper/isw_bcdhffjeid_ASUS_OS2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.18.6-031806-generic-root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		linux /boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		initrd /boot/initrd.img-3.18.6-031806-generic
	}
}


set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

It's horribly long so I don't think there's much sense to make of it, but it's there... There's also a grub.cfg.new in that folder: ```
## DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
else
  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_BE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
	else
	  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
	fi
	linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
	initrd	/boot/initrd.img-3.19.0-22-generic
}
submenu 'Options avancées pour Ubuntu' $menuentry_id_option 'gnulinux-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
	menuentry 'Ubuntu, avec Linux 3.19.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-22-generic…'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-22-generic…'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-22-generic…'
		linux	/boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-22-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-21-generic…'
		linux	/boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-21-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-20-generic…'
		linux	/boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-20-generic
	}
	menuentry 'Ubuntu, avec Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.19.0-18-generic…'
		linux	/boot/vmlinuz-3.19.0-18-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.19.0-18-generic
	}
	menuentry 'Ubuntu, avec Linux 3.18.6-031806-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-advanced-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-init-upstart-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro quiet acpi_osi= quiet splash intel_pstate=enable $vt_handoff init=/sbin/upstart
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
	menuentry 'Ubuntu, with Linux 3.18.6-031806-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.6-031806-generic-recovery-022477ea-14c8-4b51-8546-fa0fa2c6084f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  022477ea-14c8-4b51-8546-fa0fa2c6084f
		else
		  search --no-floppy --fs-uuid --set=root 022477ea-14c8-4b51-8546-fa0fa2c6084f
		fi
		echo	'Chargement de Linux 3.18.6-031806-generic…'
		linux	/boot/vmlinuz-3.18.6-031806-generic root=UUID=022477ea-14c8-4b51-8546-fa0fa2c6084f ro recovery nomodeset quiet acpi_osi=
		echo	'Chargement du disque mémoire initial…'
		initrd	/boot/initrd.img-3.18.6-031806-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/25_custom ###


menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root FAB1-1D7B
chainloader (${root})/EFI/ubuntu/MokManager.efi
}
### END /etc/grub.d/25_custom ###


### BEGIN /etc/grub.d/30_os-prober_proxy ###
```

But I don't know what that one is supposed to be.

---

### Post by oldfred on 2015-07-12
You get grub.cfg.new if you have a typo somewhere so when sudo grub-update is run it does not fully run. That is why you are seeing one update, but another version when you boot. It is not really updated. 
It used to give a line number on the error to help figure out what is wrong. I do not see that in your post. Is there something more at end?

It may be that it does not like the = without anything else in your /etc/default/grub.

GRUB_CMDLINE_LINUX="quiet acpi_osi="

I had a typo in my 40_custom from near beginning of grub2 and it was for a boot stanza for an old install, so did not notice it was missing. Then after some grub2 update, it added the extra checking and update stopped working entirely. My error was just a missing } in my 40_custom.

Your current working grub.cfg looks like 30_os-prober is finding your install a second time and adding those boot entries?? But one with typo is not.

---

### Post by mistermagio on 2015-07-12
No, I copypasted the whole file here... 

The "[COLOR=#000000]GRUB_CMDLINE_LINUX="quiet acpi_osi=" " is because it's the only way I found to get the screen brightness keys working in Ubuntu. For some reason it does not work with other boot parameters, do you think I should change it?

[/COLOR]And I guess the 30_os-prober finding my install twice is bad? 

Could any of these issue be causing the trouble I've had with both Grub and Linux kernel update? And if so is it fixable?

---

### Post by oldfred on 2015-07-12
I do not know where typo may be.

 GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]

You do have quiet on both lines, now so it gets added twice. 

Or perhaps they improved parsing. and hanging = does not now work. You working version does have the = without anything after it, but that is not normal. These are typical entries.
Try changing second quiet and putting something after =.

acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by mistermagio on 2015-07-12
I removed the second quiet and changed the line to be "acpi_osi=vendor" and then ran sudo update-grub and rebooted, but the old one, without 3.19.0-22 and with 3.19.0-16 was still what I got.

Don't know if you'll have any other ideas, but I really want to thank you for your colossal help !

---

### Post by oldfred on 2015-07-12
I just noticed proxy files.
You used grub customizer which does some things ok and has gui, but adds its own scripts which then can cause issues.

Post this.
ls -l /etc//grub.d

---

### Post by mistermagio on 2015-07-12
Wow you're right, I didn't even remember I had it because I actually ended up doing nothing with it...

Here's the output: ```
total 244-rwxr-xr-x 1 root root   9424 jun 26 13:13 00_header
-rwxr-xr-x 1 root root   6058 oct 15  2014 05_debian_theme
-rwxr-xr-x 1 root root  12261 avr  6 22:43 10_linux
-rwxr-xr-x 1 root root  11082 avr  6 22:43 20_linux_xen
-rwxr-xr-x 1 root root    170 fév 12 16:47 25_custom
-rwxr-xr-x 1 root root 168647 jui  5 22:02 30_os-prober_proxy
-rwxr-xr-x 1 root root   1416 oct 16  2014 30_uefi-firmware
-rwxr-xr-x 1 root root    214 oct 16  2014 40_custom
-rwxr-xr-x 1 root root    216 oct 16  2014 41_custom
drwxr-xr-x 4 root root   4096 jun 19 15:55 backup
drwxr-xr-x 2 root root   4096 jun 19 15:55 bin
drwxr-xr-x 2 root root   4096 jui  5 22:02 proxifiedScripts
-rw-r--r-- 1 root root    483 oct 16  2014 README



```

---

### Post by oldfred on 2015-07-12
Everything with proxy in it is from Customizer.
The original files should be in the backup directory.
I might delete or rename the entire /etc/grub.d folder. 
But then if sudo update grub does not work, you will only be able to boot Boot-Repair.

I suggest totally un-installing Grub Customizer, backup or rename all current grub files & folders and use Boot-Repair or commands to do a total uninstall & reinstall of grub. Not sure if it works as well on your RAID?? Also not sure whether you install grub to MBR of sda or with RAID you normally install to root of RAID device if booting with RAID on. 

       # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda  ---> see note below for correct /dev/
sudo update-grub

I have this in my notes on another RAID or LVM install with /mapper. The /dev/mapper/...Volume_0 is the equivalent of /dev/sda or MBR (example above). Your /mapper root is shown in some of the scripts.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by mistermagio on 2015-07-12
What if I renamed the [COLOR=#000000]/etc/grub.d folder, ran update-grub, could I then somehow check without rebooting that it worked (if so, how?), or if it failed revert the [/COLOR][COLOR=#000000]/etc/grub.d folder to its original name and run update-grub again, to return to the situation I am in right now and still be able to boot? Is it possible that that would work?[/COLOR]

I've used Boot-Repair on this laptop with RAID before and it worked, however as I mentioned before I did already try to use it to solve these issues, and it wasn't able to purge Grub.

Grub-customizer was already removed when the problems arose, too, though it does check out that it would be the cause to my issues. I'm sorry I can't answer you on some of the finer details (like where my grub is installed), but I just don't have the knowledge necessary to do so.

---

### Post by oldfred on 2015-07-12
You need to get the grub customizer files out of grub.d.
You can see what is in the backup, that may be all the original files & you can just copy them back. Just make sure all the Customizer files are deleted or at least changed to not executeable.

       sudo chmod a-x /etc/grub.d/30_os-prober_proxy

 sudo chmod a-x /etc/grub.d/proxifiedScripts

---

### Post by mistermagio on 2015-07-13
There was nothing in the grub.d.bak, but there was a grub.d.ori that seemed to be in good state, so I renamed grub.d to something else and grub.d.ori to grub.d, ran update-grub and it worked !

I then ran sudo apt-get upgrade and it went through without any issue ! I then ran dist-upgrade and apt-get -f install because I wanted to be sure, but everything that had to be done was done and when I rebooted, 3.19.0-22 was one of the boot options.

It still does not work if Secure Boot is enabled, but that's apparently a bug somewhere else and really not that problematic.

Thanks a lot for your help, I could not have fixed my system without it. You saved me a full day of reinstalling stuff on a clean install ! 

I'll now mark this thread as solved, thanks again

---

### Post by oldfred on 2015-07-13
You are welcome, glad it worked. :)

---

