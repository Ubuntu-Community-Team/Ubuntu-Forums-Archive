---
title: "apt-get install -f would not work"
date: 2013-09-13
forum: General Help
---

### Post by ravc2 on 2013-09-13
rafal@rafal-Satellite-L500:~$ sudo su
[sudo] password for rafal: 
root@rafal-Satellite-L500:/home/rafal# apt-get -f install
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Naprawianie zale&#380;no&#347;ci... Gotowe
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  linux-headers-3.8.0-23 linux-headers-3.8.0-23-generic linux-headers-3.8.0-27
  linux-headers-3.8.0-27-generic linux-image-3.8.0-23-generic
  linux-image-3.8.0-27-generic linux-image-extra-3.8.0-23-generic
  linux-image-extra-3.8.0-27-generic tdb-tools
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "apt-get autoremove".
Zostan&#261; zainstalowane nast&#281;puj&#261;ce dodatkowe pakiety:
  linux-headers-3.8.0-30
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  linux-headers-3.8.0-30
0 aktualizowanych, 1 nowo instalowanych, 0 usuwanych i 59 nieaktualizowanych.
5 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0 B/12,2 MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 60,1 MB miejsca na dysku.
Kontynuowa&#263; [T/n]? t
(Odczytywanie bazy danych ... 661613 plików i katalogów obecnie zainstalowanych.)
Rozpakowywanie pakietu linux-headers-3.8.0-30 (z .../linux-headers-3.8.0-30_3.8.0-30.44_all.deb) ...
dpkg-deb (podproces): dekompresowanie cz&#322;onu archiwum: wewn&#281;trzny b&#322;&#261;d odczytu gzip: "<fd:4>: invalid code lengths set"
dpkg-deb: b&#322;&#261;d: podproces <dekompresja> zwróci&#322; kod b&#322;&#281;du 2
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb (--unpack):
 podproces dpkg-deb --fsys-tarfile zwróci&#322; kod b&#322;&#281;du 2
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@rafal-Satellite-L500:/home/rafal#

---

### Post by sandyd on 2013-09-13
try
```

sudo rm /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

If required, run
```

sudo apt-get -f install
```
again

---

