---
title: "Dividing a MP3 file into differents parts"
date: 2005-05-22
forum: General Help
---

### Post by galder on 2005-05-22
Hello!

I have a problem. The matter is that I have a really large MP3 file (a conference of 4 hours) that I want to divide in 20 parts, in order to manage them more easily in my MP3 portable reproducer.

Do you know an easy application that can do this in Ubuntu or GNU/Linux?

Thank you in advance

---

### Post by kvidell on 2005-05-22
[QUOTE=galder]Hello!

I have a problem. The matter is that I have a really large MP3 file (a conference of 4 hours) that I want to divide in 20 parts, in order to manage them more easily in my MP3 portable reproducer.

Do you know an easy application that can do this in Ubuntu or GNU/Linux?

Thank you in advance[/QUOTE]
 Automagically? Not sure.
Audacity might have a feature to do it automagically but if naught else, you can do it by hand with it.

hope that helps some,
- Kev

---

### Post by galder on 2005-05-24
Hello,

kvidell thanks! I have installed Audacity and I have reached to divide the MP3 file into a lot of different parts. 

It was the program I needed! Thanks.

However, I have found some problems when I tried to export. 

I have written about this problem [in my website because libmp3lame.so file was not found](http://www.galder.net/modules/news/article.php?storyid=42). 

I hope it can be usefull, despite it is in Spanish.

Thanks kvidell again.

---

### Post by kracker on 2005-10-26
Bump,

I was looking for the same thing cause I couldn't seem to see how to get lame installed via dselect / apt to fullfill these audacity mp3 library dependancies.

Here is an english (or english like) [translation]("http://translate.google.com/translate?hl=en&sl=es&u=http://www.galder.net/modules/news/article.php%3Fstoryid%3D42&prev=/search%3Fq%3Dhttp://www.galder.net/modules/news/article.php%253Fstoryid%253D42%250A%26hl%3Den%26hs%3DPRq%26lr%3D%26client%3Dfirefox%26rls%3Dorg.mozilla:en-US:unofficial") via google's translation tool.

Which simply references enabling the `multiverse` aka `extra` repositories in your /etc/apt/sources.list 

Here is a guide for [Ubuntu 5.04]("http://ubuntuguide.org/#extrarepositories")

cheers,
//kracker

---

