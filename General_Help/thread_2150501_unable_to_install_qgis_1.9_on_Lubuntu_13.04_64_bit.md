---
title: "unable to install qgis 1.9 on Lubuntu 13.04 64 bit"
date: 2013-06-01
forum: General Help
---

### Post by ilFonta on 2013-06-01
Hello everybody
I tryied to install qgis 1.9 in my laptop. I use Lubuntu 13.04 (64bit).
I used the repository 
deb     [http://qgis.org/debian-nightly](http://qgis.org/debian-nightly) raring main
deb-src [http://qgis.org/debian-nightly](http://qgis.org/debian-nightly) raring main
and I didn't find any error during the installation.


When I try to start qgis I otain this message:


/usr/bin/qgis.bin: error while loading shared libraries: libgdal1.7.0.so.1: cannot open shared object file: No such file or directory


Ifa I try 
sudo apt-get update
Sudo apt-get upgrade 


I obtain those messages:
Configurazione di qgis-providers-common (1.9.0+git20130529+e0406e7~raring1)...


/usr/lib/qgis/crssync: error while loading shared libraries: libgdal1.7.0.so.1: cannot open shared object file: No such file or directory
dpkg: errore nell'elaborare qgis-providers-common (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 127
dpkg: problemi con le dipendenze impediscono la configurazione di qgis-providers:
 qgis-providers dipende da qgis-providers-common (= 1.9.0+git20130529+e0406e7~raring1); comunque:
  Il pacchetto qgis-providers-common non è ancora configurato.


dpkg: errore nell'elaborare qgis-providers (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di qgis:
 qgis dipende da qgis-providers (= 1.9.0+git20130529+e0406e7~raring1); comunque:
  Il pacchetto qgis-providers non è ancora configurato.


dpkg: errore nell'elaborare qgis (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di qgis-plugin-globe:
qgis-plugin-globe dipende da qgis (= 1.9.0+git20130529+e0406e7~raring1); comunque:
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
              
Segnalazione apport non scritta poiché è stato raggiunto il valore massimo di MaxReports
             
  Il pacchetto qgis non è ancora configurato.


dpkg: errore nell'elaborare qgis-plugin-globe (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di qgis-plugin-grass:
 qgis-plugin-grass dipende da qgis (= 1.9.0+git20130529+e0406e7~raring1); comunque:
  Il pacchetto qgis non è ancora configurato.


dpkg: errore nell'elaborare qgis-plugin-grass (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 qgis-providers-common
 qgis-providers
 qgis
 qgis-plugin-globe
 qgis-plugin-grass
E: Sub-process /usr/bin/dpkg returned an error code (1)




I apologize for the italian messages.


Could you help me?


Thank you

---

