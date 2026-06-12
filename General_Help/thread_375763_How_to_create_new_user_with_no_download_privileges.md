---
title: "How to create new user with no download privileges?"
date: 2007-03-04
forum: General Help
---

### Post by Vistavenger on 2007-03-04
Is it possible to create a new user with no download privileges? I would like to create an account for my son who is 9 years old but I don't wnat him to download and install programs, change certain settings, etc. Basically the only thing he needs to do is surf the internet and send/receive email. Thanks in advance for your time and help!

---

### Post by bodyboarding_bum on 2007-03-04
I cant answer your question fully, as im only new to ubuntu. But with no download limits would not be possible. Every web page you go onto 'downloads' information, or packets of data to your computer. This is how it loads up, and displays the info and pictures. So it might be possible to use minimal downloads, but not none.
Goodluck

---

### Post by Vistavenger on 2007-03-05
Well, what I meant to say was download and install programs, software, applications, etc. Obviously each time you visit a web page you also 'download' images and whatever else but I mean downloading and installing software...

;)

---

### Post by petersjm on 2007-03-05
I'm not sure about this, but I imagine there must be some way to disallow downloads of certain file types? Like .bin, .tar.gz, .deb, etc...?

---

### Post by tagra123 on 2007-03-05
When adding a new user - I believe the default deny sudo access.  

By limiting sudo users this will prevent someone from installing to the root (programs). 

You can also change existing users

MENU  System - Administration - Users and Groups

Click on a user under the users tab - then click on properties.

On the Setting screen --click on the user-privileges tab and uncheck the items to deny the user access to. (adminstration tasks)

---

### Post by tagra123 on 2007-03-05
To be really clever you can edit the hosts file and deny sites this way too.

Enter your local IP followed by the sites name. Whenever that site is encountered in the browser it will do nothing.

127.0.0.1  [www.somebadsite.com](www.somebadsite.com)

---

