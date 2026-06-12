---
title: "Trouble installing LibreOffice"
date: 2017-02-28
forum: General Help
---

### Post by mosh-rob on 2017-02-28
desde que he hecho upgrade a mi ubuntu, todo va mal!
mi problema es que no puedo abrir documentos. intente varias veces desinstalar y instalar libreoffice y no funciona estos es mi ultimo error

:~$ sudo apt-get install <libreoffice-l10n>
bash: error sintáctico cerca del elemento inesperado `newline'

estoy inesperado........

---

### Post by QIII on 2017-02-28
Hello!

You have posted in an English-speaking area of the forums.  Can you translate your question into English?  If not, we can move your post to a more appropriate area of the Forums.

---

### Post by Portaro on 2017-02-28
> **QIII said:**
> Hello!

You have posted in an English-speaking area of the forums.  Can you translate your question into English?  If not, we can move your post to a more appropriate area of the Forums.

Translate to English &#8594;

I have a problem that comes with the last upgrade of software LibreOffice . Simplu I can't open any document with LibreOffice . I also try uninstall and reinstall LibreOffice to take a look if with this method I can solve the problem but nothing works.

Now I also have an errors on my terminal like:

:~$ sudo apt-get install <libreoffice-l10n>
Syntactic error in Bash unknown element newline

---

### Post by QIII on 2017-02-28
That's all well and good, but will the OP be able to carry on a conversation in English without a translator?  If not, they would be much better served in a sub-forum where they can use their native language.

---

### Post by mosh-rob on 2017-03-01
sorry i do speak english, i was upgrading my ubuntu to 16.04 and since then i have many problems....solve most of them but the open office i cant use at all. no even openning. went through some of the guides, uninstalling and installing deleting all and installing a gain nothing work 
my message when i open a doc(o excel) is
The application cannot be started. 
[context="shared"] caught unexpected com.sun.star.ucb.InteractiveAugmentedIOException: a folder could not be created

when i went through bug finding i reach to this message

:~$ sudo apt-get install <libreoffice-l10n>
bash: error sintáctico cerca del elemento inesperado `newline'

it seems my laptop is bi lingual.... ;) some is in english some spanish. i in any case have no clue what to do
some helppppp???

---

### Post by QIII on 2017-03-01
No need to apologize!  I just wanted to make sure you got help.

Do you have any PPAs in your sources?  Does one of them contain LibreOffice?

---

### Post by Portaro on 2017-03-03
What type of upgrade you do? - From 14, or 15 release points or you do a new clean install of 16.04?

In general users sugest do clean installs of each release.

Maybe you need to use a purge remove command to unistall libreoffice and then reinstall it maybe works. 
sudo apt-get remove --purge libreoffice

Ref:[http://askubuntu.com/questions/180403/how-to-uninstall-libreoffice](http://askubuntu.com/questions/180403/how-to-uninstall-libreoffice)

---

