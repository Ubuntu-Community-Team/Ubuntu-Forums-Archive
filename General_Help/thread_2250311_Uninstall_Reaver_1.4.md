---
title: "Uninstall Reaver 1.4"
date: 2014-10-28
forum: General Help
---

### Post by praveshpushp on 2014-10-28
[COLOR=#333333][FONT=UbuntuRegular]I did install reaver 1.4 from the following two commands. Now I have to remove it, how can I do that ?[/FONT][/COLOR]


sudo apt-get install libpcap-dev sqlite3 libsqlite3-dev libpcap0.8-dev


wget [http://reaver-wps.googlecode.com/files/reaver-1.4.tar.gz](http://reaver-wps.googlecode.com/files/reaver-1.4.tar.gz)

---

### Post by sgoranov on 2014-10-28
rm -rf /location/where/Reaver/was/extracted
apt-get autoremove

Regards,
S.

---

### Post by praveshpushp on 2014-10-28
I dont know the extracted location. Then what should I do ?

---

### Post by sgoranov on 2014-10-28
What exactly did you do? Probably you didn't just download it using wget [http://reaver-wps.googlecode.com/fil...ver-1.4.tar.gz](http://reaver-wps.googlecode.com/fil...ver-1.4.tar.gz) but after that extract it then build it from source and then the installation? 
Tell us what exactly did you do and probably somebody will be able to help you?

---

