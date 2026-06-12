---
title: "slrn character encoding"
date: 2007-03-12
forum: General Help
---

### Post by Da_Timsta on 2007-03-12
Hi there.

I recently started with the quest of making the SLRN news reader work on xubuntu. According to the quick-start guide in the readme i got it setup to fetch news from my local dorm server, and everything seemed to work but the character encoding. I'm from Denmark and thus use the odd chars 'æøå'. The charset i usually need to use is 'iso-8859-15'.

In my .slrnrc i've set up the following options wich seemed related to my problem

```
set charset isolatin
set use_mime 1
set mime_charset "iso-8859-15"
set use_metamail 1
```

I don't know if this is the right place to ask, but any help would be appreciated. I'm running Xubuntu 6.10 on a thinkpad if that makes any difference.

---

### Post by andrew.46 on 2007-07-22
Hi,

 Many character issues are solved in the cvs version of slrn which comes as:

```
andrew@ilium:~$ slrn --version
Slrn 0.9.8.1pl2 [2005-02-17]
        * Note: This version is a developer preview.
S-Lang Library Version: 2.0.5
Compiled at: Jul 16 2007 09:18:31
Operating System: Linux

```

 Do you need the cvs details? I have added a sample screenshot of the cvs slrn and a Danish group which shows ?correct Danish text.

               Andrew

---

