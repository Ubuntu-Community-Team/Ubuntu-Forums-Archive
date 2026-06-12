---
title: "Samba pdc problem."
date: 2007-03-16
forum: General Help
---

### Post by Severloh on 2007-03-16
I have next type of problem with samba pdc. When i try to login into windows with any of listed users on samba windows says that it doesnt have rights to save \server_name\profile\user_name.pds. What would be a problem configs or i dont have proper rights on folder ?

> [global]

; palvelimen nimi
netbios name = skoda.hopto.org
log level = 3

; domain name
workgroup = B306

; pdc domain role
security = USER
os level = 65
domain logons = yes
domain master = yes
local master = yes
preferred master = yes
wins support=yes
   
; minne tallennetaan profiilit
    logon path = \\%N\profiles\%u

   
; missä on käyttäjän kotihakemisto ja mihin asemaan se liitetään
    logon drive = H:
    logon home = \\%N\%u

;
; jos verkossa myös win9x koneita, käytä tätä, sillä 9x laittaa profiilinsa home kansioon - jaiks!!
;
; logon home =\\%N\%u\.profiles
;
   
; logon skripti, ajetaan loggauksen yhteydessä. pitää olla dos muodossa
  logon script = logon.bat

; logon skripti, ajetaan loggauksen yhteydessä. pitää olla dos muodossa
    logon script = logon.bat

; aikapalvelin käyttöön
    timeserver = yes
   
;  ääkköstöä varten
    valid chars = Ä:ä Ö:ö Å:å

    client code page = 850
    character set = iso8859-1
; jos samba 3, niin; Tämä korjaa ongelmat myös MacOsX:n kanssa
; dos charset = CP850
; unix charset = ISO8859-1
; tai (tai UTF-8 tai ISO8859-15)

; jos halutaan käyttää winssiä
    wins support=true
    wins proxy=yes
   
    dos filetime resolution=yes


; käyttäjätunnukset _jotka_ ovat järjestelmänvalvojia
admin users = root ismo heikki severloh adminstrator
add user script = /usr/sbin/useradd -m %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/usermod -G %g %u
add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null %u


[print$]
        comment = Printer Drivers
        path = /tmp
        write list = root### 306 kansiot ###
        printer admin = root*******

[printers]
        path = /home/smbprint
        create mask = 0700
        guest only = Yes
        guest ok = Yes
        printable = Yes
        browseable = No

[HP]
        comment = HP LaserJet Series CUPS v1.1
        path = /home/smbprint
        printer admin = root
        read only = No
        create mask = 0700
        guest only = Yes
        guest ok = Yes
        printable = Yes
        printer name = HP
        oplocks = No
        share modes = No

### 306 kansiot ###

[B306]
   guest account =
   printable = no
   write list = adminstrator,heikki,ismo,severloh,@opettajat,@severloh,@adminstrator
   path = /home/oppilaat/
   comment = B306 OPPILASPALVELIN
   valid users = sac04,sac05,sac06,sac07,@oppilas,@adminstrator,@severloh,@root,@opettajat
   user = @oppilas
   create mode = 0750
   directory mode = 0750

[tavarat]
   writeable = yes
   printable = no
   write list = adminstrator,heikki,ismo,severloh,@adminstrator,@sac04,@severloh,@opettajat
   path = /home/tavara
   create mode = 0750
   public = yes
   directory mode = 0750

 ; tämä tarvitaan domain kontrollerille
[netlogon]
   path = /home/netlogon/%u
   create mask = 0755   
   write list = root
   
; jaetut profiilit, säilytyspaikka
[profiles]
    path = home/profiles/
   read only = no
   create mask = 0600
   directory mask = 0700 

Im needing help fast because im building my school graduate job (student server) so i need little advisoring.

---

