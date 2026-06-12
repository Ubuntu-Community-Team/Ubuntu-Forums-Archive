---
title: "Changing the default save location for cups-pdf?"
date: 2013-01-31
forum: General Help
---

### Post by AwaitingUserInput on 2013-01-31
Ubuntu 12.10 64 bit edition.

I just installed cups-pdf 1.3.11 and successfully printed a test page. It saved it in the default location which is ~/PDF.

I would like to be the default save location ~/Documents/Printouts

So I went to System Settings-->Printers-->PDF

In the "settings" section I typed in /home/myusername/Documents/Printouts

However, it is still saving in ~/PDF.

Any idea how to change the default save location?

---

### Post by mp035 on 2013-08-04
I know this thread is long dead, however, here is the answer for anyone (like me) who found this on google.

Open a terminal window and enter:
```
 sudo nano /etc/cups/cups-pdf.conf 
```

Enter your password.

Find the line in the file which is:

```
 Out ${HOME}/PDF 
```

and change it to:

```
 Out ${HOME}/Documents/Printouts 
```

Note that this changes the settings for all users of the machine, not just you.

---

### Post by graeme-launchpad on 2013-11-22
> **mp035 said:**
> I know this thread is long dead, however, here is the answer for anyone (like me) who found this on google.

.

Long dead, but not forgotten ... just what I was looking from ,thanks.

---

