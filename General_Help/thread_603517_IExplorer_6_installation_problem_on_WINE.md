---
title: "IExplorer 6 installation problem on WINE"
date: 2007-11-05
forum: General Help
---

### Post by aldav on 2007-11-05
I've recently installed IE6 (the official MS installation)on my Gutsy distro. Why I need IE6 is irrelevant, but I&#314;l say it anyway. My school email server is Exchange (probably 2007), so there has been no way for me to check the email comfortably from any of the mail clients available, let's no say Firefox (it's awful the way it renders exchange web mail client) so I had no other remedy than to try to install IE6 to at least check the web mail comfortably. Anyway, everything looked fine during install but when it finished, I had no iexplorer.exe in my wine "program files" folder, nor outlook express .exe. When I tried to uninstall it, IExplorer appeared on the Wine Uninstall Menu, but it just doesn't uninstall itself.

Any help is appreciated.

Thanks

---

### Post by zaphod777 on 2007-11-05
check out IES4 linux they do all of the hard work for you it should work like a charm.

[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

You have to enable universe packages first. It is also recommended that you use the official winehq ubuntu package: 

1) Open a terminal 

2) Open /etc/apt/sources.list 

 sudo gedit /etc/apt/sources.list
3) Uncomment (or add) following lines: 

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
4) Add this line: 

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
5) Close gedit. Update and install wine and cabextract: 

 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract
6) Download IEs 4 Linux and install 

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux
Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu. 

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by aldav on 2007-11-05
Thanks, ies4linux worked fine. 
But what about the other problem, the no ".exe" files for iexplorer and outlook after I installed them?

---

### Post by zaphod777 on 2007-11-06
they are kind of hidden under homefolder\.wine
there is a c:\ etc

but ies4 linux creats some sort of script so now you can just type ie6 in the terminal.

---

### Post by Mithrilhall on 2007-11-06
Have you tried using Evolution to get your mail via your Exchange webmail? I've done this in the past and it worked perfectly for me.

---

