---
title: "Set mailto: to gmail in FF3 in Hardy."
date: 2008-05-05
forum: General Help
---

### Post by Bastanteroma on 2008-05-05
According to [this post]("http://michalberman.typepad.com/my_weblog/2008/01/protocol-handle.html") FF3 has gmail as a mailto: option, but instead Evolution opens by default, and yahoo mail is the only alternative. The gui in FF preferences/applications doesn't seem to offer any way to add other webmail apps.

---

### Post by fragos on 2008-05-06
I use Epiphany and configured evolution for send only through Gmail imap. Mailto does give an evolution send window but the email is sent through Gmail's smtp. Not exactly what I wanted but it's workable without additional operational steps. I had used Firefox 2 but grew tired of the problems. Gmail mailto was provided by the Firefox Google toolbar. I'd use my work around or check Google labs for a Firefox 3 toolbar. It had other useful features as well.

---

### Post by wwomack on 2008-08-11
Try following the directions from [http://gmailblog.blogspot.com/2008/07/power-tip-set-gmail-as-your-default.html](http://gmailblog.blogspot.com/2008/07/power-tip-set-gmail-as-your-default.html).  This worked for me.   I don't know why they didn't include gmail in the list by default like they did for yahoo.  Hopefully this is something they'll do in the next release.

> 1) Go to Gmail and sign in.

2) While in Gmail, copy and paste the following into your browser's address bar and hit enter.

javascript:window.navigator.registerProtocolHandler("mailto","https://
mail.google.com/mail/?extsrc=mailto&url=%s","Gmail")

3) Click "Add Application" when you are prompted1. Congrats, you just added Gmail to your browser's list of mail clients.


---

### Post by ezramorris on 2008-08-27
> **wwomack said:**
> Try following the directions from [http://gmailblog.blogspot.com/2008/07/power-tip-set-gmail-as-your-default.html](http://gmailblog.blogspot.com/2008/07/power-tip-set-gmail-as-your-default.html).  This worked for me.   I don't know why they didn't include gmail in the list by default like they did for yahoo.  Hopefully this is something they'll do in the next release.

If it doesn't work, make sure
```
gecko.handlerService.allowRegisterFromDifferentHost
```
is set to **true** in about:config, then run that javascript: code again.

---

