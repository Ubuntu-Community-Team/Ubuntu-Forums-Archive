---
title: "Change io-charset for local device on ltsp clients"
date: 2007-06-25
forum: General Help
---

### Post by jonnoob on 2007-06-25
I am working on setting up an ltsp enviroment on a school. I am using Edubuntu and everything is working perfectly. My only problem is that we are Danish and that gives problems with filenames.

When a user save a document with the danish characters ÆØÅ on a Windows machine it will be displayed as weird characters and OpenOffice will say the file the file doesn't exist.

I know the problem is that Windows uses ISO-8859-1 and Ubuntu(Edubuntu) uses UTF-8.

So I changed the default to ISO-8859-15 in the installation. It solved the problem locally on the server. But the problem persist on the LTSP clients. I believe it has something to do with udev but i am not sure.

Anybody have any ideas?

---

