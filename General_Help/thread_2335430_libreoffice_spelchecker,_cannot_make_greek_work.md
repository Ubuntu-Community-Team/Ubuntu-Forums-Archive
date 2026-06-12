---
title: "libreoffice spelchecker, cannot make greek work"
date: 2016-08-28
forum: General Help
---

### Post by bobptz on 2016-08-28
I am using ubuntu 16.04.  When I go to  LO -> Tools/Options/Language Settings/Languages, at "default  languages for documents". Next to the Greek label I do not see the blue  letters "ABC".  How do I add them?


  I went to Ubuntu -> System Settings/Language support. Removed and  added back the Greek language.  Then the system did download some  libreoffice greek packages.  Still the greek spelcheck did not work...!

  

  Can you please help fix this?

---

### Post by coldraven on 2016-08-29
Hi, from this page in Libreoffice help:
[https://help.libreoffice.org/Common/Selecting_the_Document_Language](https://help.libreoffice.org/Common/Selecting_the_Document_Language)

> [h=2]Adding More Text Languages[/h] 
[LIST=1]
[*]Dictionaries are supplied and installed as extensions. Choose **Tools - Language - More Dictionaries Online** to open the dictionaries page in your default web browser.
[*]Select a dictionary in the list of descriptions. Click the heading in a dictionary description that you want to get.
[*]In the next page, click the Get It icon to download the dictionary  extension. Note the folder name to which your browser downloads the  file. Download additional dictionaries as you like.
[*]In LibreOffice, choose **Tools - Extension Manager** and click Add to install the downloaded extensions.
[*]After you installed the extensions, you should close LibreOffice (including the Quickstarter), and restart.
[/LIST]

Hope that helps.

---

### Post by Impavidus on 2016-08-29
There are several spellcheckers around and dictionaries for those spellcheckers can be installed from the repositories (Ubuntu software or other interface). I'm not sure which one you need, but you can experiment. I just searched in synaptic and I found **aspell-el** for the aspell checker, **hunspell-el** for the hunspell checker (the description suggests this is the one you need for libreoffice) and **myspell-el-gr** for the myspell checker. If you install the right one and restart libreoffice, I think the spell checker should be available.

---

### Post by bobptz on 2016-08-29
Hello coldraven 

I went to that page and found nothing.

See image:
[URL="https://s17.postimg.io/56cquybin/greek_dictionaries.png"]https://s17.postimg.io/56cquybin/greek_dictionaries.png
[/URL]
Then I searched for "greek" and "ANY version" and it gave me stuff like "ancient greek".  This is not what I want.

I want a plain modern greek dictionary.

---

### Post by bobptz on 2016-08-29
I managed to install the Greek dictionary.  Here are the commands to do it:
[B]sudo apt-get update
sudo apt-get install myspell-el-gr
sudo apt-get install hyphen-el[/B]

Detailed guide here:
[http://bbb-solutions.blogspot.gr/2016/06/libreoffice-spelling-problems.html](http://bbb-solutions.blogspot.gr/2016/06/libreoffice-spelling-problems.html)

---

### Post by coldraven on 2016-08-31
> **bobptz said:**
> Hello coldraven 

I went to that page and found nothing.

See image:
[URL="https://s17.postimg.io/56cquybin/greek_dictionaries.png"]https://s17.postimg.io/56cquybin/greek_dictionaries.png
[/URL]
Then I searched for "greek" and "ANY version" and it gave me stuff like "ancient greek".  This is not what I want.

I want a plain modern greek dictionary.

I don't think you looked hard enough, above "Ancient Greek" was "Greek Polytonic Spell Checker".
[http://extensions.libreoffice.org/extension-center/greek-polytonic-spelling-checker](http://extensions.libreoffice.org/extension-center/greek-polytonic-spelling-checker)

---

### Post by bobptz on 2016-08-31
> **coldraven said:**
> I don't think you looked hard enough, above "Ancient Greek" was "Greek Polytonic Spell Checker".
[http://extensions.libreoffice.org/extension-center/greek-polytonic-spelling-checker](http://extensions.libreoffice.org/extension-center/greek-polytonic-spelling-checker)

I did see "Greek Polytonic Spell Checker", however it is not what I am looking for.  The Polytonic system was replaced by the Monotonic system at around 1975.  I was looking for the Monotonic system spell checker.

---

### Post by coldraven on 2016-08-31
> **bobptz said:**
> I did see "Greek Polytonic Spell Checker", however it is not what I am looking for.  The Polytonic system was replaced by the Monotonic system at around 1975.  I was looking for the Monotonic system spell checker.
Sorry about that, at least I've learned a new fact :)

---

