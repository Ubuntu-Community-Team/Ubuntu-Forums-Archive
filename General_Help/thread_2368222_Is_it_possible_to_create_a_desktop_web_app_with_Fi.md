---
title: "Is it possible to create a desktop web app with Firefox/Chromium?"
date: 2017-08-08
forum: General Help
---

### Post by miqrojamie on 2017-08-08
Hi,

Just wondering, is it possible to create a desktop web app that can be launched from the applications menu or desktop icon via Firefox or Chromium in Ubuntu? I'd like to do this with a few social media websites, as well, would it be possible to integrate desktop notifications with these? Been searching on Google to no avail of anything recent.

Thank you for any help!

---

### Post by dragonfly41 on 2017-08-08
If you mean launching an application from a link in Firefox or Chromium Web Browser you need to explore custom "URL protocol handlers".

The URL protocol handler then has to be registered by the user.

---

### Post by miqrojamie on 2017-08-08
I don't. :(

I meant running a web browser in a single window without the tabs, address bar or anything like that, running almost like a native app but it's just a rendered web interface, and being able to open said UI-less rendering from a shortcut.

An example is when you save Vimeo to your home screen in iOS and you can view it without any of the Safari borders and such.

---

### Post by dragonfly41 on 2017-08-08
If, then, you mean a web app without browser bells and whistles perhaps run a python app which launches a window.

There are many frameworks  .. [here are just a few]("https://wiki.python.org/moin/WebFrameworks").

Flask or Cherrypy are two to experiment with for wrapping microapps / widgets.

You can launch the window app from a launcher script.

More complex apps can be developed using Qt.

---

### Post by SeijiSensei on 2017-08-08
In Firefox, you can disable all the toolbars then hit F11 to display the page full-screen.

A bigger issue concerns how you intend to program this application.  If you want to use a scripting language like PHP, then you'll need to install a web server like Apache with the PHP module and access the page as [http://localhost/](http://localhost/).  The simplest way to do this is to install the "[LAMP stack]("https://help.ubuntu.com/community/ApacheMySQLPHP")" with
```
sudo apt-get install lamp-server^
```
(the tilde is not a typo).  That will get you Apache, PHP and MySQL should you need an SQL database in the back end as well.

For other suggestions search Google for "[ubuntu kiosk]("https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+kiosk&ie=utf-8&oe=utf-8")".

---

### Post by Furbybrain on 2017-08-08
One option might be to write it as a Progressive Web App- an example is [Twitter Lite]("http://www.omgubuntu.co.uk/2017/04/how-to-use-twitter-lite-desktop-app"). They start as a website, and then the browser will offer to save it as a desktop app. They're a LITTLE more involved than a standard website as you have to write a Service Worker to cache all the resources, but there are plenty of guides for that.

I believe Chrome is the main browser supporting this, hopefully Firefox gets on it.

---

### Post by monkeybrain20122 on 2017-08-08
It is very simple with chrome and I think the procedure is the same with chromium. Go to the site you want to make into a webapp. From the menu choose More Tools > Add to desktop and check the box "open as window". That's it. A .desktop file ("launcher icon") will appear on your desktop. Cut and paste it to ~/.local/share/applications and it will appear on your menu.

I have made a webapp from google-earth. [https://ubuntuforums.org/showthread.php?t=2365796](https://ubuntuforums.org/showthread.php?t=2365796)

---

