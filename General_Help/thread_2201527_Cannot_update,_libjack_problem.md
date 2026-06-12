---
title: "Cannot update, libjack problem"
date: 2014-01-24
forum: General Help
---

### Post by odee2 on 2014-01-24
Hi all, I every day use update through terminal,
I using always apt-get autoclean, autoremove, update and at least upgrade.
7days without problem, but today i got an error:

```
lubo@lubo:~$ sudo su
[sudo] password for lubo: 
root@lubo:/home/lubo# apt-get clean
root@lubo:/home/lubo# apt-get autoclean
Na&#269;ítavajú sa zoznamy balíkov... Hotovo
Vytvára sa strom závislostí             
Na&#269;ítavajú sa stavové informácie... Hotovo
root@lubo:/home/lubo# apt-get autoremove
Na&#269;ítavajú sa zoznamy balíkov... Hotovo
Vytvára sa strom závislostí             
Na&#269;ítavajú sa stavové informácie... Hotovo
Mo&#382;no to budete chcie&#357; napravi&#357; spustením &#8222;apt-get -f install&#8220;.
Nasledovné balíky majú nesplnené závislosti:
 libjack-jackd2-0 : Kazí: libjack-jackd2-0:i386 (!= 1.9.8~dfsg.1-1ubuntu2) ale nain&#353;talovaný je 1.9.8~dfsg.2-1precise1
 libjack-jackd2-0:i386 : Kazí: libjack-jackd2-0 (!= 1.9.8~dfsg.2-1precise1) ale nain&#353;talovaný je 1.9.8~dfsg.1-1ubuntu2
E: Nesplnené závislosti. Skúste pou&#382;i&#357; -f.
root@lubo:/home/lubo# apt-get -f install
Na&#269;ítavajú sa zoznamy balíkov... Hotovo
Vytvára sa strom závislostí             
Na&#269;ítavajú sa stavové informácie... Hotovo
Opravujú sa závislosti... Hotovo
Nain&#353;talujú sa nasledovné extra balíky:
  libjack-jackd2-0
Navrhované balíky:
  jackd2
Nasledovné balíky sa aktualizujú:
  libjack-jackd2-0
1 aktualizovaných, 0 nových nain&#353;talovaných, 0 na odstránenie a 3 neaktualizovaných.
1 iba &#269;iasto&#269;ne nain&#353;talovaných alebo odstránených.
Je potrebné stiahnu&#357; 197 kB archívov.
Po tejto operácii sa na disku pou&#382;ije &#271;al&#353;ích 3 072 B.
Chcete pokra&#269;ova&#357; [Y/n]? Y
Získava sa:1 http://ppa.launchpad.net/dns/sound/ubuntu/ precise/main libjack-jackd2-0 amd64 1.9.8~dfsg.2-1precise1 [197 kB]
197 kB sa stiahlo za 8 s (23,5 kB/s)                                           
(&#268;íta sa databáza ... momentálne je nain&#353;talovaných 273016 súborov alebo adresárov.
Pripravuje sa nahradenie libjack-jackd2-0 1.9.8~dfsg.1-1ubuntu2 (pomocou .../libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb) ...
Rozba&#318;uje sa náhrada libjack-jackd2-0 ...
dpkg: chyba pri spracovávaní /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb (--unpack):
 './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system
Nezapí&#353;e sa správa apport, preto&#382;e u&#382; bol dosiahnutý limit MaxReports
                                                                     dpkg-deb: chyba: podproces vlo&#382;i&#357; ukon&#269;ený signálom (Preru&#353;ená rúra)
Vyskytli sa chyby po&#269;as spracovania:
 /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can somebody tell me what is that?
Last program what i this week installed is lmms
 I use latest Ubuntu 12.04 LTS 64bit version

---

### Post by odee2 on 2014-01-24
I dont know if it helps, 
i had 32bit 12.04 LTS ubuntu and i had installed lmms without any problems.
I formatted my hdd and i now have already Ubuntu 12.04 64bit LTS.
At lmms are no sounds in bank :(
so i tryied reinstall lmms and install again, but from this site:
[http://ubuntuguide.net/linux-multimedia-studio-0-4-13-ubuntu-12-0411-1010-04](http://ubuntuguide.net/linux-multimedia-studio-0-4-13-ubuntu-12-0411-1010-04) 
but also does not work

---

### Post by ian-weisser on 2014-01-24
The system is telling you why.

> **odee2 said:**
> dpkg: chyba pri spracovávaní /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb (--unpack):
 './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system

The easy way to resolve is to disable that PPA.

---

### Post by jeanjd63 on 2014-01-25
Hello 
you can try to force the install :
[B][COLOR=#000000][FONT=Ubuntu Mono]sudo  dpkg -i --force-all  /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb

[/FONT][/COLOR][/B][COLOR=#000000][FONT=Ubuntu Mono]Then do :[/FONT][/COLOR][B][COLOR=#000000][FONT=Ubuntu Mono]
sudo  apt-get install -f[/FONT][/COLOR][/B]

---

### Post by odee2 on 2014-01-25
ok, i removed ppa dns/sound, and used help from jeanjd63, it looks like is all fine. Thank you.
Again is error repaired just from terminal and not mouse

---

