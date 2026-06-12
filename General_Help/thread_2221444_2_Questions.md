---
title: "2 Questions"
date: 2014-05-02
forum: General Help
---

### Post by N.C.K on 2014-05-02
G'day,

I have 2 questions.

1.  I have forgotten my admin password, Can I get it back or how do I re-set it?

2. I have recently downloaded a new browser and can't find it where is it?

Ps. I am a window$ user and trying to get used to using LINUX.

---

### Post by bapoumba on 2014-05-02
1- Well, this one is going to be tricky. How can we be sure you are genuinely asking a question about your own computer and you are not trying to get over someone else's ?
2- Which browser and how did you "download it" ? Did you install it ? How ?

---

### Post by N.C.K on 2014-05-02
1. How can I give you the info you need to verrify that I am the ONLY user of this computer?
2. I downloaded something similar to "google chrome" by clicking on the automitic download link in the Ubuntu Software centre.

---

### Post by bapoumba on 2014-05-02
> **N.C.K said:**
> 
2. I downloaded something similar to "google chrome" by clicking on the automitic download link in the Ubuntu Software centre.

Please open a terminal and post the output to :
```
apt-cache policy chromium-browser
```

---

### Post by N.C.K on 2014-05-02
??

?? I am VERRY VERY new to Ubuntu afer expereminting with ubunty 8.??  Currentlu I am using Ubuntu 14.04

---

### Post by bapoumba on 2014-05-02
You can look for Terminal from the Ubuntu menu or it should be in Accessories depending on the desktop you are running :
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Once the Terminal is open, highlight the command from my above post, middle click to paste in Terminal and hit <enter>. Highlight the output from Terminal and middle click to paste in here.
My guess is that you have installed chromium-browser from the Software Center. Alternatively, you can search for Chromium from the Ubuntu menu, if it is installed correctly, it should be there.

This is what the output should look like :

```
 apt-cache policy chromium-browser
chromium-browser:
  Installed: 34.0.1847.116-0ubuntu2
  Candidate: 34.0.1847.116-0ubuntu2
  Version table:
 *** 34.0.1847.116-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Impavidus on 2014-05-02
As to question 1, I think we can give you this link to psychocats's password reset page: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by philinux on 2014-05-02
> **N.C.K said:**
> G'day,

I have 2 questions.

1.  I have forgotten my admin password, Can I get it back or how do I re-set it?

2. I have recently downloaded a new browser and can't find it where is it?

Ps. I am a window$ user and trying to get used to using LINUX.


Can you still log in as normal with your original username?

---

### Post by buzzingrobot on 2014-05-02
> **N.C.K said:**
> ??

...I am using Ubuntu 14.04

Ubuntu uses an interface called Unity.  To launch applications once they are installed, tap the Super (aka Windows) key and begin typing the name of the application (or even something descriptive related to its function). An icon used to launch that app will be displayed.

So, odds are you installed Chromium, which is an opensouce version of Chrome. (Chrome is available from Google.) To run it, tap the Super key, start typing "C-h-r-o-m-....." and click on its icon.

In Unity, once an app is launched, its icon appears in the Launcher on the left of the screen.  If you want that icon to remain permanently in the Launcher for easy access, right click on it and select the "Lock to Launcher" option.

In general, applications that have been properly packaged and installed for Ubuntu can be accessed this way. We don't need to go seaching for a program's specific location in the file system.

---

