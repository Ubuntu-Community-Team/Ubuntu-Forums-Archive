---
title: "Netflix Desktop is not working"
date: 2014-08-07
forum: General Help
---

### Post by UncleMonty on 2014-08-07
Netflix Desktop has suddenly stopped working. I now get the error message:

"MS true type fonts are not properly installed, would you like to download and install them now? (requires an Internet connection and sudo permissions)"


If I accept the terms and try to install the fonts, I get the error message: 

"It appears that you still have not installed the MS true type fonts. You need to accept the licence agreement and install these fonts for Netflix Desktop to work properly."

Is there anyway of getting to work? Is there any other way of getting netflix to work in ubuntu?

---

### Post by coffeecat on 2014-08-07
Try this. Open a terminal and run this command:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Don't leave the terminal unattended while this operation proceeds. After a few minutes you will be presented with the Microsoft EULA which you must agree to otherwise the installation fails. Press the TAB key to highlight OK, and then press ENTER. Once the installation has finished, check Netflix again.

I have no experience of Netflix desktop in Ubuntu, but your problem sounds to be one of a partial install of the MS core fonts because the EULA was not agreed.

---

### Post by QIII on 2014-08-07
Hello!

If you continue to have trouble, I have had much better luck with this:

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

Be sure to read all the way through.  You need a user agent switcher for your browser.

For me, the changes made by Netflix Desktop caused problems when I tried to watch other content on different websites.

---

### Post by UncleMonty on 2014-08-07
I used pipelight and UA overider in the end (the above option did work but I then got a grey screen...)

---

