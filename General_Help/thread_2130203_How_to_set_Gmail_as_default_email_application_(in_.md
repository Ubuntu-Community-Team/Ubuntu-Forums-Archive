---
title: "How to set Gmail as default email application (in desktop and Shotwell)"
date: 2013-03-28
forum: General Help
---

### Post by moma on 2013-03-28
Hello,
Ubuntu 13.04:
I want to send pictures from Shotwell via email. Shotwell seems to start Thunderbird or Evolution instead of Gmail. 
This issue alienates a lot of ordinary users who want to send images to friends/family!

1) How can I set Gmail as default email-client in Shotwell? 
[[img]http://bildr.no/thumb/1426001.jpeg[/img]](http://bildr.no/view/1426001)

2) How do I set gmail as default in Ubuntu's settings?
[[img]http://bildr.no/thumb/1426014.jpeg[/img]](http://bildr.no/view/1426014)

Notice that "Gmail web app" is already installed in Ubuntu Raring, but Gmail is not listed. See the above image.

---

### Post by Frogs Hair on 2013-03-28
Have you installed the Gnome Gmail client and set it as default ? Both My Opera and Tbird  clients are options in Shotwell depending what I set as default ,but I can't send directly and bypass the client .

---

### Post by moma on 2013-03-29
Hello,
Obrigado.
I just installed "gnome-gmail" and set it as default mail-client in the settings.

$ apt-cache  search gnome | grep -i gmail
gnome-gmail - support for Gmail as the preferred email application in GNOME
gnome-gmail-notifier - A Gmail Inbox Notifier for the GNOME Desktop

$ sudo apt-get install gnome-gmail

Shotwell can now send images and .zip files to a gmail-account. It opens a browser-window. The message is initially saved as draft. That's ok.

**I think that [B]gnome-gmail** should be installed and set as default in Ubuntu, especially because Gmail web app is already present. This will avoid confusão among users.
[/B]
Boa Pàscoa.

---

### Post by Frogs Hair on 2013-03-29
Glad it worked . Keep in mind that not all people use Gmail or any Google services. Thunderbird is neutral and not tied to any particular email provider.

---

### Post by moma on 2013-03-29
Yes, Thunderbird and [Geary...]("http://www.indiegogo.com/projects/geary-a-beautiful-modern-open-source-email-client") are neutral. The default-app list could have an [Other...] option that lists all available email-clients that are in the package system. The selected email-app is then installed when first time requested. 

Most of ordinary users cannot handle the current complexity. They turn back to Windows.
All end-users I've seen try to send images from Shotwell / Camera -- and they fail.

[COLOR="#FF0000"]Why is Google web app installed by default, but its desktop integration package is not (gnome-gmail package)??[/COLOR]

---

