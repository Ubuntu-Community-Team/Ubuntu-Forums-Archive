---
title: "Libreoffice Writer will not launch..."
date: 2017-06-20
forum: General Help
---

### Post by afiggis on 2017-06-20
Hello there,  I was wondering if anyone would be able to help me. I'm an longterm Ubuntu user, but I'm not technical enough to know how to troubleshoot with this one...  I'm running the latest Xubuntu. For no apparent reason that I can think of, Libreoffice Writer just will not launch. I just tested Impress, it opens fine, as well as the Libreoffice "home" launch.  I've purged the config files, reinstalled Libreoffice. Still it won't start up. Would anyone have any suggestions? And if I need to access a crash log, where would it be?  Many thanks,  Arthur

---

### Post by howefield on 2017-06-20
Try opening the application from the terminal, you may get a clue as to what is wrong..

```
libreoffice --writer
```

---

### Post by afiggis on 2017-06-20
Hello, Thanks for that. Unfortunately I get no error messages in Terminal while trying that. I just tried launching in safe mode, and Writer still just disappears after the loading bar. I've tried opening documents directly and by terminal but still the same result. It's odd...

---

### Post by vanadium on 2017-06-20
Something might be wrong in your user configuration. Try moving out your user configuration folder. Makse sure LO is shut down. Open your file manager and have it show hidden files, ie.e files where the name starts with a dot. Find the .config folder, and there you will find the .libreoffice folder. Rename that to something like libreoffice_old. If you now restart LO, it will create a new libreoffice folder with a fresh configuration and start with a default configuration.

---

### Post by nameinuse on 2017-06-21
Same here - since I updated to new kernel. Writer was perfectly fine minutes before update. Found this report on my system "soffice.bin crash SIGSEGVin_expand_stack_to()" 

Seems other people are having similar problems but not all with Writer; some with Calc. Not considered to be urgent at the moment apparently but I hope someone will be after fixing it soon as I am not really expert enough to use a different kernel.

---

### Post by afiggis on 2017-06-22
> **vanadium said:**
> Something might be wrong in your user configuration. Try moving out your user configuration folder. Makse sure LO is shut down. Open your file manager and have it show hidden files, ie.e files where the name starts with a dot. Find the .config folder, and there you will find the .libreoffice folder. Rename that to something like libreoffice_old. If you now restart LO, it will create a new libreoffice folder with a fresh configuration and start with a default configuration.  Hi Vanadium,  Thanks for that - I tried your suggestion but that doesn't make any difference

---

### Post by afiggis on 2017-06-22
> **nameinuse said:**
> Same here - since I updated to new kernel. Writer was perfectly fine minutes before update. Found this report on my system "soffice.bin crash SIGSEGVin_expand_stack_to()"   Seems other people are having similar problems but not all with Writer; some with Calc. Not considered to be urgent at the moment apparently but I hope someone will be after fixing it soon as I am not really expert enough to use a different kernel.  Hi naminuse,  Thanks for bringing that to my attention - so it's not just me then. Looks like I'll just wait and see... I suppose I can use Google Docs or Abiword if need a proper word processor for the moment.  Cheers

---

### Post by schmidt-z on 2017-09-18
Are there any news on this topic? :/

---

### Post by CodeJoker on 2017-10-29
Check the following link:  [https://askubuntu.com/questions/927859/libreoffice-writer-crashes-on-start](https://askubuntu.com/questions/927859/libreoffice-writer-crashes-on-start)  Disabling java worked for me on xubuntu.

---

