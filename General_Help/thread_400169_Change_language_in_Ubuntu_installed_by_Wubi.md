---
title: "Change language in Ubuntu installed by Wubi"
date: 2007-04-03
forum: General Help
---

### Post by hrparra on 2007-04-03
Dear Sirs,
I have a laptop in English. Id tried to install Ubuntu trougth Wubi, in this case I could not select another language (for me Spanish). I ran Ubuntu, after the installation and I could not change the language from the application.
How can I exchange English by Spanish
Kind Regards

---

### Post by sisco311 on 2007-04-03
open a terminal (Applications->Accessories->Terminal)
write:
```
sudo aptitude install language-pack-es
```
this will install Spanish language
now in the login screen you can change the language
press Ctrl-Alt-Backspace for login 
select your language from the language menu

---

### Post by hrparra on 2007-04-03
Hello
Thank you for answer. Because the computer with Ubuntu is at home, I will try today later.
Cheers

[http://www.ubuntuforums.org/images/smilies/guitar.gif](http://www.ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

### Post by hrparra on 2007-04-03
It is working, thnak you very much.
Administrator you can, now, close the thread
Greetings

---

### Post by suniyo on 2009-07-22
What are the ISO Codes for Indian Languages like Hindi, Gujarati, Punjabi? Is it like in-hi, in-gu or directly hi or gu ??

---

### Post by michy99 on 2009-07-22
> **suniyo said:**
> What are the ISO Codes for Indian Languages like Hindi, Gujarati, Punjabi? Is it like in-hi, in-gu or directly hi or gu ??

hi - Hindi
gu - Gujarati
pa - Panjabi (Punjabi)

---

### Post by Dedi Landsman on 2009-11-01
Hi, and What are the ISO Codes for the Hebrew Language?

---

### Post by oboeoho on 2010-03-16
for the sake of me and other user, how or where can i have the complete list of such language 'codes', best regards.

---

### Post by stevelim on 2010-05-17
Hi there

May I also know what are the ISO codes for Chinese? Thanks.

---

### Post by Dayofswords on 2010-05-17
> press Ctrl-Alt-Backspace for login 
i think this is disabled by defualt since 9.04

> May I also know what are the ISO codes for Chinese? Thanks. 
zh_CN  or just zh  i beileve

> Hi, and What are the ISO Codes for the Hebrew Language?
he

---

### Post by PolkaMan on 2010-11-20
This doesn't work for me. When I change the language to English it's still in Swedish for me. Is there any other way?

---

### Post by numlosk on 2011-04-28
ive installed the language package, how do i change from command, becasuse im usin server edition, thanks

---

### Post by ast3citos on 2012-11-08
> **numlosk said:**
> ive installed the language package, how do i change from command, becasuse im usin server edition, thanks

Not meaning to bring up old thread, but this thing still unanswered and as I got here from searches, so do many other people.

In Ubuntu Server, you check if the desired language is installed either by

```
sudo dpkg-reconfigure locales
```

if it is installed it will show up as *updated *or as *up-to-date*

You can also

```
sudo apt-get remove language-pack-
```

and TAB TAB for autocompletion. It will autocomplete listing the langpacks available for removal, thus installed.

If yours does not show...

```
sudo apt-get install language-pack-xx
```

where xx is your language

Now it is installed but not configured.

Configure it in

```
nano /etc/default/locale
```

Finally reboot to apply changes...

```
sudo reboot
```

---

