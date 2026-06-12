---
title: "GPA: GPGME Unexpected Error!"
date: 2013-11-28
forum: General Help
---

### Post by chsados2 on 2013-11-28
Ubuntu 13.10
  This is driving me mad!
  Have GPA(v0.9.4) and Seahorse(v3.8.2)installed.  

  As soon as I open GPA I get the following error:

> GPA ERROR  
  The GPGME library returned an unexpected error. The error was:
     Unsupported Certificate
This is probabbly a bug in GPA.
GPA will now try to recover from this error.  

Image of error, right upon opening: 
[IMG]http://i.imgur.com/xJmw2oF.png[/IMG]



  I have tried googling this error but am falling short on luck.

  Can anyone point me in the right direction?  I just want simple encryption/decryption and not have to use thunderbird+enigmail.

  If anyone could point me towards a tutorial on setting up something similar to Tails OS's [gpgApplet]("https://tails.boum.org/doc/encryption_and_privacy/gpgapplet/") that would be extremely awesome!  I just want something simple and sweet like gpgApplet!  Hell, even if I could get GPA to would I would be happy!

  Thunderbird + Enigmail is giving me zero problems and working  wonderfully, but I would like a way to simply encrypt/decrypt from  within gEdit or the clipboard.

---

### Post by chsados2 on 2013-11-28
So I just tried 

> sudo gpa    

From the command line and it worked flawlessly!

How do I get GPA to run by simply clicking the icon? 

Why is it forcing me to open it via sudo - is this normal?

---

### Post by rafi365 on 2014-05-08
A simple way is to install alacarte, which is the old menu editor for Ubuntu and where you can specify parametrs for launching the gpa.
```
sudo apt-get install alacarte
```
Simply run it, find the shortcut (Applications -> Accessories -> gpa), click Proprties, and add your argument to the command. In this case we have to disable unsupported x509 certificates.
```
gpa --disable-x509
```

---

### Post by squirrel2003 on 2014-12-08
thanks that makes the program work. Just annoying that it does not work plug and play.

---

