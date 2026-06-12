---
title: "Error when installing any application"
date: 2007-10-03
forum: General Help
---

### Post by fusion.fake on 2007-10-03
This is the error i get: E: Sub-process /usr/bin/dpkg returned an error code (1)

```
fusion@fusion-desktop:~$ sudo apt-get install wine
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  libgnorbagtk0 libgtk-jni libcairo-java libdb4.3++c2 libglib-java
  python-wxversion liborbit0 libswt3.2-gtk-jni
Gebruik 'apt-get autoremove' om deze te verwijderen.
De volgende pakketten zullen opgewaardeerd worden:
  wine
1 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 4 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 10,6MB aan archieven opgehaald worden.
Na het uitpakken zal er 2386kB extra schijfruimte gebruikt worden.
Ophalen:1 http://wine.budgetdedicated.com feisty/main wine 0.9.46~winehq0~ubuntu~7.04-1 [10,6MB]
10,6MB opgehaald in 10s (993kB/s)                                              fusion@fusion-desktop:~$ sudo apt-get -f install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  libgnorbagtk0 libgtk-jni libcairo-java libdb4.3++c2 libglib-java
  python-wxversion liborbit0 libswt3.2-gtk-jni
Gebruik 'apt-get autoremove' om deze te verwijderen.
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 4 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Instellen van linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.31 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.31 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: fout bij afhandelen van linux-image-2.6.20-16-generic (--configure):
 subproces post-installation script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

(Database inlezen ... 143434 bestanden en mappen geïnstalleerd.)
Voorbereiden om wine 0.9.33-0ubuntu1 te vervangen (door .../wine_0.9.46~winehq0~ubuntu~7.04-1_i386.deb) ...
Uitpakken van vervangende wine ...
Instellen van linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.31 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.31 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: fout bij afhandelen van linux-image-2.6.20-16-generic (--configure):
 subproces post-installation script gaf een foutwaarde 2 terug
Instellen van wine (0.9.46~winehq0~ubuntu~7.04-1) ...

Fouten gevonden tijdens behandelen van:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I read i should try sudo dpkg - -configure -a but i still got the sane error.

now i cant install anything :/ i always get that error, i dont know what the problem could be, can anyone please help me

what i find is strange i see linux-image-2.6.20-16-generic (2.6.20-16.32) in the code, how can that be there ? or is that standard when updating/installing new applications?

---

### Post by zvacet on 2007-10-03
**synaptic>edit>fix broken packages**

```
sudo aptitude update && sudo aptitude upgrade
```

If all goes as it should install wine.You can do it with synaptic.

---

