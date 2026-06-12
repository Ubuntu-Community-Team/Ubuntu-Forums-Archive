---
title: "libre office &quot;an error has occurred in language tool 2.5&quot;"
date: 2014-11-13
forum: General Help
---

### Post by SuperFreak on 2014-11-13
I am getting the following error message when using Libre Writer
```
an error has occurred in language tool 2.5
Java.Lang.NoClass DefFoundError: org/languagetool/chunking/ EnglishChunkFilter$ChunkType
Stack Trace....... 
```

This message pops up  every time I try and type a document making it impossible to continue. Using Libre Office Version: 4.2.7.2
Build ID: 420m0(Build:2)

---

### Post by amanchesterman on 2014-11-13
You obviously have the Language Tool Extension, which is an add-on to LibreOffice Writer, not part of Writer itself.

Since the latest version of Lanugage Tool is 2.7, and it's advertised as including 'bug fixes', I suggest you install that as a first step.
While you're about it you might want also to update to the latest version of Writer, which (on my machine) is 4.3.3.2.
I believe that using outdated software is a common cause of malfunctions.

---

### Post by SuperFreak on 2014-11-13
Upgraded to  latest 4.3 LO but problem persists. I am not sure how to update language tool and wonder if it would be better to uninstall it completely. Clueless at this point

---

### Post by amanchesterman on 2014-11-13
I don't use LibreOffice extensions so I don't know how to install and uninstall them, sorry. However there is a website dedicated to them [http://extensions.libreoffice.org/](http://extensions.libreoffice.org/) which presumably explains it. Since you installed the extension originally I assume you know more than me! Uninstalling and then re-installing the latest version sounds like a good idea.

However I suggest you also look here: [https://languagetool.org/issues/](https://languagetool.org/issues/) . In the section headed 'common problems with Libre Office integration' the third bullet down specifically mentions a 'NoClassDefFoundError' which is perhaps similar to the message on your screen? The advice on that page indicates that it arises from a problem with Java -- either the wrong version of Java installed, or LibreOffice not registering it properly. So I suggest that you check that you have the latest version of Java installed as well.

---

### Post by SuperFreak on 2014-11-13
Thanks for your help. I was able to install the latest Language Tool 2.7 using Extension Manager in Tools menu  and the problem seems to be gone

---

