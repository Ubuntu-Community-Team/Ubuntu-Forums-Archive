---
title: "sa-exim with exim4 not working"
date: 2006-10-03
forum: General Help
---

### Post by nevyndweomer on 2006-10-03
Hi  

I have followed (as best I can) the various howtos' on setting up spamassassin  
This has involved installing spamassassin and sa-exim then making varous changes in the config files  
all the howtos' say to expect errors when there is something wrong  but I get no entries in my logs and mail/spam is still arriving with no extra headers  

This suggests to me that it is not being scanned but I am lost to understand why 

when I install sa-exim are there any changes I need to make to the exim config file to make it work? 
for your info I am running the monolithic config file and I have users on virtual hosts who do not have sysytem accounts
I will worry about how to get the mail to a different folder later. First I just want to see the extra headers being inserted by assassin 

please help 

Nevyn

---

### Post by nevyndweomer on 2006-10-06
Quick update for any that are interested 

I managed to get it working (ish)  
I needed to put an additional line in my config file to call the sa scanner  because I am using monolithic file as opposed to split  
this command is added automatically with split  

regards
Nevyn

---

