---
title: "Skype instalation problem"
date: 2014-01-29
forum: General Help
---

### Post by odee2 on 2014-01-29
Hi all,
today i downloaded from skype.com a skype-ubuntu-precise_4.2.0.13-1_i386.deb file.
After sucessfull download i clicked with right button at a mouse - open with software centre.
I have Ubuntu 12.04 64bit

This error happen:
```
Errors were encountered while processing:
 /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
```

After that i tryied apt-get update, upgrade, install -f, autoremove and again install
but same error hapen.

```
root@lubo:/home/lubo# apt-get -f install
Na&#269;ítavajú sa zoznamy balíkov... Hotovo
Vytvára sa strom závislostí             
Na&#269;ítavajú sa stavové informácie... Hotovo
Opravujú sa závislosti... Hotovo
Nasledovné balíky boli nainštalované automaticky a už viac nie sú potrebné:
  libunistring0:i386 dh-apparmor libgomp1:i386 libcroco3:i386 libgettextpo0:i386 html2text
  libmail-sendmail-perl libsys-hostname-long-perl
Na ich odstránenie použite „apt-get autoremove“.
Nainštalujú sa nasledovné extra balíky:
  libjack-jackd2-0:i386
Navrhované balíky:
  jackd2:i386
Nainštalujú sa nasledovné NOVÉ balíky:
  libjack-jackd2-0:i386
0 aktualizovaných, 1 nových nainštalovaných, 0 na odstránenie a 2 neaktualizovaných.
Je potrebné stiahnu&#357; 0 B/170 kB archívov.
Po tejto operácii sa na disku použije &#271;alších 489 kB.
Chcete pokra&#269;ova&#357; [Y/n]? Y
(&#268;íta sa databáza ... momentálne je nainštalovaných 300905 súborov alebo adresárov.
Rozba&#318;uje sa libjack-jackd2-0:i386 (z .../libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb) ...
dpkg: chyba pri spracovávaní /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb (--unpack):
 './usr/share/doc/libjack-jackd2-0/changelog.Debian.gz' is different from the same file on the system
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can somebody help me?

---

