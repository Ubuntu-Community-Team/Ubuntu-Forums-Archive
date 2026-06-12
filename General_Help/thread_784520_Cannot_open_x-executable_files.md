---
title: "Cannot open x-executable files"
date: 2008-05-06
forum: General Help
---

### Post by albymilan on 2008-05-06
Hi, 2 days ago I installed Ubuntu with unetbootin.
Everything was ok, when today afternoon Firefox started blocking every 30 second for 2-3 sec., and I saw that I couldn't open x-executable files. I double-clicked many times, I tried rightclick-Open but nothing happened.

I'm not sure of the causes of these things, but I have some hypothesis.

I thinked at the things that I did from yesterday evening (when everythink worked - but I'm not sure of executable files, I didn't try to open one) until today afternoon. If I remember right, there are:
-Upgrade of some Synaptic Packages
-some changes to FF ,that i read on this tutorial[http://www.elart.it/mozilla/velocizzare.php]("http://www.elart.it/mozilla/velocizzare.php")
-some changes to some Ubuntu files:
```
Disabilitare l'IPv6:
sudo nano /etc/modprobe.d/aliases
Modificare la riga dell'ipv6 come sotto:
alias net-pf-10 off # ipv6
aggiungiamo questa riga:
alias ipv6 off
poi forziamo il kernel a non caricare il modulo per gestire l'IPv6
sudo nano /etc/modprobe.d/blacklist
ed aggiungiamo a fine file questa riga:
blacklist ipv6
possiamo rendere più veloce Firefox disabilitando fra le varie cose l'uso dell IPv6 per l'interrogazione dei DNS


Disabilitamo i caratteri orientali in Firefox: se non visitate siti con caratteri in lingue orientali disabilitate Pango
sudo nano /etc/environment
aggiungere questa riga:
MOZ_DISABLE_PANGO="1"
ed ottimizziamo Firefox

Installiamo preload:
sudo apt-get install preload
e configuriamo il servizio editando sudo nano /etc/preload.conf

Velocizziamo il caricamento dei programmi tramite prelink:
sudo apt-get install prelink
abilitiamo prelink alla funzione di prelinking editiamo il file /etc/default/prelink
sudo nano /etc/default/prelink
cerchiamo ad inizio file e modifichiamo la riga come qui sotto riportato:
PRELINKING=yes
quindi forziamo un primo prelink delle applicazioni come da specifiche del file di configurazione /etc/prelink.conf lanciando:
sudo /etc/cron.daily/prelink
```


Now I can't normally use Ubuntu.

I also tried to restore default settings in this way:
> at the login press Ctrl+Alt+F1
login
password
rm -rf .gnome .gnome2 .gconf .gconfd .metacity


I tried this in Recovery mode and in normal mode, but I noticed the same problems.

Sorry for my English and Big Thanks for the possible replies.

---

### Post by wpshooter on 2008-05-06
When you are saying x-executable files are you talking about files with .exe extensions as those used under M/S windows O/Ss ?

If so, then I don't think you are going to get those to run under Ubuntu/Linux !!!

---

### Post by RATM_Owns on 2008-05-06
I think he means .x files.

If that, then change to the directory where the .x file is and type
./(name of x-executable).x

---

### Post by albymilan on 2008-05-07
> **RATM_Owns said:**
> I think he means .x files.

If that, then change to the directory where the .x file is and type
./(name of x-executable).x
Yes, i didn't mean .exe files
I tried to do ./YamiPod.x (for example) but it says ```
libstdc++.so.5: cannot open shared object file: No such file or directory
```

I don't know what's happening, do I have to reinstall Ubuntu?

Also Firefox has problems, every 20-30 seconds he doesn't work for 2 seconds, also the mouse doesn't move.

Can I restore the default Ubuntu  factory settings ?

---

### Post by wpshooter on 2008-05-07
> **albymilan said:**
> Yes, i didn't mean .exe files
I tried to do ./YamiPod.x (for example) but it says ```
libstdc++.so.5: cannot open shared object file: No such file or directory
```

I don't know what's happening, do I have to reinstall Ubuntu?

Also Firefox has problems, every 20-30 seconds he doesn't work for 2 seconds, also the mouse doesn't move.

Can I restore the default Ubuntu  factory settings ?

I seriously doubt that the program you are trying to run is compatible with Ubuntu/Linux.  I see that it is mentioned as being compatible with Windows, MAC, & Linux.  But I doubt that Ubuntu is included.  There is probably a similar function included somewhere in Synaptic Package Manager.  Try doing a search in Synaptic or in add/remove software in your Ubuntu O/S.

---

### Post by albymilan on 2008-05-07
> **wpshooter said:**
> I seriously doubt that the program you are trying to run is compatible with Ubuntu/Linux.  I see that it is mentioned as being compatible with Windows, MAC, & Linux.  But I doubt that Ubuntu is included.  There is probably a similar function included somewhere in Synaptic Package Manager.  Try doing a search in Synaptic or in add/remove software in your Ubuntu O/S.
It isn't possible. Before, I had Linux installed with Wubi and the same program worked (it opened the window of YamiPod), also Floola worked and now doesn't.

I start thinking the only one solution is to reinstall Ubuntu.
Or I can try to restore default factory settings.
**Is there any way to restore default settings?**

---

### Post by albymilan on 2008-05-08
I reinstalled Ubuntu, but i tired redownloading Floola (for ex.) and with double-click it doesn't opne. But I noticed that during the Ubuntu installation at about 85% of installation, it says
> 
Un tentativo di configurare apt per installare ulteriori pacchetti dal CD-"
- "ROM è fallito

I've searched in the net for answers,but I only found this page [http://d-i.alioth.debian.org/spellcheck/level1/index.html]("http://d-i.alioth.debian.org/spellcheck/level1/index.html") where there are lists of error messages.
The English list unfortunately doesn't work.
So I post you the French, German and Spanish translation (I hope you know at least one of these languages)

> "Une tentative de configuration d'APT pour installer de nouveaux paquets "
- "depuis le CD ou le DVD a échoué."

> - "Ein Versuch apt zu konfigurieren, weitere Pakete von der CD/DVD zu "
- "installieren, schlug fehl"

> Ha fallado el intento de configurar apt para instalar paquetes adicionales "
- "del CD/DVD

What does it means? How can I see what packages it didn't install?

---

