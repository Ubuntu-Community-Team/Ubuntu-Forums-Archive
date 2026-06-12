---
title: "[SOLVED] kopete yahoo buddies see black video"
date: 2007-11-21
forum: General Help
---

### Post by trash on 2007-11-21
Has anybody had the problem of yahoo contacts getting only black video. My cam works fine otherwise.

---

### Post by trash on 2007-11-22
nobody's had this problem?

---

### Post by trash on 2007-11-23
Maybe somebody can give me some idea on what the problem might be, here's what running kopete in a terminal tels me.. keep in mind my cam is working fine in kopete...

 kopete
kenji@kenji-laptop:~$ QMetaObject::findSignal:ClientStream: Conflict with Stream::readyRead()
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: ListTask
CLIENT: RequestPictureTask: Task::done()
CLIENT: RequestPictureTask: emitting finished
Transfer ACCEPTED by: StatusNotifierTask
Transfer ACCEPTED by: MailNotifierTask
QGArray::find: Index 0 out of range
KPopupMenu: title() called with non-title id 0.
Transfer ACCEPTED by: WebcamTask
CLIENT: SendNotifyTask: Task::done()
CLIENT: SendNotifyTask: emitting finished
error: JPEG decoder not available
The IJG JPEG library is required for JPEG decoding support.
The source code for the IJG JPEG library can be downloaded from:
    [http://www.ijg.org](http://www.ijg.org)
error: cannot load image data
error: JPEG decoder not available
The IJG JPEG library is required for JPEG decoding support.
The source code for the IJG JPEG library can be downloaded from:
    [http://www.ijg.org](http://www.ijg.org)
error: cannot load image data
error: JPEG decoder not available.....

The error just keep repeating about 10 times. Everything related to jpeg is installed

---

### Post by trash on 2007-12-29
:confused:

anybody with any insight??
Even the kopete forum has nothing similar:(

---

### Post by harold4 on 2008-02-28
Do you have jasper installed?

---

### Post by trash on 2008-02-28
> **harold4 said:**
> Do you have jasper installed?

seems so, libjasper1, dev and runtime.

I may have read somewhere that UVC cams will work but only with KDE 4, which i haven't installed.

---

### Post by harold4 on 2008-02-28
Not the case.  I'm on uvc using kopete in kde 3.5.8.

Double check the version of kopete you have.  Also, have you gone to [www.ijg.org](www.ijg.org) and installed?

---

### Post by trash on 2008-02-28
don't remember where i got it from but i had installed jasper-1.900.1.zip.

thanks i'll check out the other versions. My version is 0.12.7 using kde 3.5.8 and I don't see a newer version on their site unless you have kde 4

---

### Post by harold4 on 2008-02-28
Jasper from the repo versions works fine.

Since it's complaining about the IJG JPEG library

```

sudo apt-get install libjpeg62

```

---

### Post by trash on 2008-02-28
> **harold4 said:**
> Jasper from the repo versions works fine.

Since it's complaining about the IJG JPEG library

```

sudo apt-get install libjpeg62

```

No joy:( I have libjpeg62 installed and installed jpeg-6b from ijg.org... i see my cam in kopete but in gyache it will not recieve the image from kopete:(

---

### Post by harold4 on 2008-02-28
My only uses are kopete to kopete and kopete to the official yahoo client.  Have you checked the bug in gyache?

---

### Post by trash on 2008-02-28
> **harold4 said:**
> My only uses are kopete to kopete and kopete to the official yahoo client.  Have you checked the bug in gyache?

just did and i'm still getting the no jpeg decoder in kopete. gyache tells me waiting for permission and windows tells me waiting for images.
This sucks!

---

### Post by trash on 2008-02-29
Just upgraded to KDE 3.5.9 but didn't make a difference.:(

---

### Post by harold4 on 2008-02-29
What webcam are you using?

EDIT: May want to do a "sudo make uninstall" in the directory you installed jasper from the .zip file.  Then do a reinstall of the jasper packages in the repo.

---

### Post by trash on 2008-02-29
> **harold4 said:**
> What webcam are you using?

EDIT: May want to do a "sudo make uninstall" in the directory you installed jasper from the .zip file.  Then do a reinstall of the jasper packages in the repo.

It's a built in Orbicam.... Uninstalled as you said AND IT WORKS!!!! thank you so much! Dude I am so happy right now you can't imagine hehe!

---

### Post by harold4 on 2008-02-29
Slick.  Don't forget to mark the thread solved.

---

### Post by trash on 2008-02-29
> **harold4 said:**
> Slick.  Don't forget to mark the thread solved.

Thanks for the reminder!
Cheers.

---

