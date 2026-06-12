---
title: "Simple Contact List Server"
date: 2008-06-15
forum: General Help
---

### Post by eangulus on 2008-06-15
Hi all, I have been researching and have come accross LDAP as a possible system for me to have a shared and private address book.
 
What I would like to do is simply have a shared and private address books for myself and my wife. SO all up there would be 3 books, hers, mine and ours. I hope to be able to setup SyncML for our mobiles to sync these contacts and even import them into my Google Apps.
 
My only problem is this, any OpenLDAP tutorials I am finding are geared towards higher end domain controlling or something on a much higher level than what I really need. I did try going thru one of the tutrials on howtoforge but now have my windows files sharing broken and now in the middle of fixing it.
 
I am not a strong linux user, but I do have a small Ubuntu server used for web development and media streaming. I am comfortable with terminal. But I am still only ver new to linux (12 months or so).
 
Incase someone has a better idea here is the full system I hope to setup, basically I want my ver own "mobileme" system. I want to have my contacts including a global address book, calender, email, files, to all be accesable from my mobiles, laptops, UMPC, and desktops. I currently use Google Apps for your domain so I have got IMAP for mail, but there seems to be only free readonly access to my calendar and the contacts can't have a shared book and have to be exported manually.
 
Any ideas on a system or a group of systems that would help me obtain this functionality.
 
Any help is fully appreciated.

---

### Post by eangulus on 2008-06-15
BUMP.

Does anyone have any information?

---

### Post by kalesh7 on 2008-06-16
check this out for sharing addressbook with thunderbird and LDAP [http://www.sudleyplace.com/LDAP/index.en.html]("http://www.sudleyplace.com/LDAP/index.en.html")

and handyaddressbook seems to be able to do it as well(but I'm not sure how well it fits your needs) [http://www.handyaddressbook.com/mi_features.html]("http://www.handyaddressbook.com/mi_features.html")

It should also be easy to write a script for it(contacts that is) but the calender would be more difficult.

---

### Post by eangulus on 2008-06-16
Handy address book would work functionally but it seems to be for windows and not linux.
 
Thunderbird option seems to do what I need but doesn';t go into enough details on how to get the said address book from a mobile phone or other remote devices.

---

### Post by kalesh7 on 2008-06-16
> **eangulus said:**
> Handy address book would work functionally but it seems to be for windows and not linux.
 
there are two versions, the CGI version will work on linux (you will have to install some extra stuff such as perl, apache, and do some config changes, if they are not installed already)

---

### Post by eangulus on 2008-06-17
Just wondering if anyone has made a linux server that is suited o the home use and or SOHO use.
 
From what I read most Server tutorials seem to be geared more towards the enterprise user.
 
As a home or SOHO point oif view, something that has a simple webmin interface, Samba File sharing, and Sync for Contacts, Notes, Calendar and mail, between mobile phones and laptops, UMPC's etc, all in a pre install package would be ideal.

---

