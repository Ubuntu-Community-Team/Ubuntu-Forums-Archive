---
title: "UTF8 over SSH from Feisty -&gt; Feisty Server"
date: 2007-06-16
forum: General Help
---

### Post by Moeity on 2007-06-16
I'm trying to read some email on my remove feisty server that is in utf-8. When I connect  from my home feisty system to the remote feisty system with ssh in a gnome-terminal, all utf-8 Japanese characters appear as ????? or other non-readable characters. If I download the email to my home computer, I can read those emails without problem in gnome-terminal.

I think both machines should be setup to handle utf-8. Running locale on my local machine gives:

LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=


Running the same locale on my remote machine gives:
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=

They both give the same output, so I believe they should be speaking the same language. However, writing in Japanese over the ssh terminal to the remote machine gives ???? characters, but works locally. Reading is the same.

Does anyone know how to enable utf-8 across an ssh connection?

---

### Post by sonicbuddha on 2007-11-22
I don't know if you've resolved this by now but I can add two things for you to think about:

1) The output of the two are not the same.  The second, the remote machine, is missing "LANGUAGE=en_CA:en".

2) Consider looking at this article and this thread, specifically in relation to transmitting locale and lang values when sshing to your Ubuntu machine:

[http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting](http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting)
[http://ubuntuforums.org/showthread.php?t=545176&highlight=locale+ssh](http://ubuntuforums.org/showthread.php?t=545176&highlight=locale+ssh)
[http://ubuntuforums.org/showthread.php?p=3816870#post3816870](http://ubuntuforums.org/showthread.php?p=3816870#post3816870)

---

