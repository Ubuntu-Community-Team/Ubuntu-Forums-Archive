---
title: "gnucash in other lang than OS"
date: 2015-06-27
forum: General Help
---

### Post by cosy2 on 2015-06-27
i asking if there is anyway to change the language on gnucash on the same say is done under windows ?

the OS language is english but i want to run gnucash in russian is there anyway to permanently set gnucash in russian ?

---

### Post by llamabr on 2015-06-27
Generally, you should change the language on linux, and let gnucash get the cue from there.  Is there a reason you want to run linux in english, but gnucash in russian?  Here:
[http://wiki.gnucash.org/wiki/Locale_Settings#Changing_the_Language_on_Linux]("http://wiki.gnucash.org/wiki/Locale_Settings#Changing_the_Language_on_Linux")

---

### Post by cosy2 on 2015-06-28
in windows the option is permanent 

this $ LANGUAGE=de_DE LANG=de_DE gnucash option is not permanent i need something to be permanent so when gnucash starts is starts in russian

---

### Post by llamabr on 2015-06-28
If you want to set the environment locally, you can do it in your .bashrc file:
[http://unix.stackexchange.com/questions/26695/refresh-env-variables-after-editing-bashrc-file](http://unix.stackexchange.com/questions/26695/refresh-env-variables-after-editing-bashrc-file)
If you want to make the change to your entire system (for all users) edit /etc/environment:
[http://askubuntu.com/questions/4667/where-to-declare-environment-variables](http://askubuntu.com/questions/4667/where-to-declare-environment-variables)
Here's a nice discussion about the environment variables:
[http://askubuntu.com/questions/4667/where-to-declare-environment-variables](http://askubuntu.com/questions/4667/where-to-declare-environment-variables)

Let us know what happens

---

### Post by cosy2 on 2015-06-28
thx 


solved

---

