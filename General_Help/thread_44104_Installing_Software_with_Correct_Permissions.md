---
title: "Installing Software with Correct Permissions"
date: 2005-06-24
forum: General Help
---

### Post by wadesmart on 2005-06-24
06242005 1206 GMT-5

After talking a length with a very nice chap, I learned that the reason I cant see videos is that I dont have the correct codecs. So, I downloaded the codecs and they have to be put into /usr/local/lib. I created (finally!) the folder codecs and now Im trying to install the files. I click on downloaded file and Archieve Manger File Roller came up. But when I chose where to put the files, I do not have the permissions to do so. How do you gain permissions for a single install when you are using a app and not the command line?

Wade

---

### Post by Lunde on 2005-06-24
[QUOTE=wadesmart]06242005 1206 GMT-5

After talking a length with a very nice chap, I learned that the reason I cant see videos is that I dont have the correct codecs. So, I downloaded the codecs and they have to be put into /usr/local/lib. I created (finally!) the folder codecs and now Im trying to install the files. I click on downloaded file and Archieve Manger File Roller came up. But when I chose where to put the files, I do not have the permissions to do so. How do you gain permissions for a single install when you are using a app and not the command line?

Wade[/QUOTE]
 Mostly things like that is done in the terminal with the **sudo** command, but here's a few tricks that might help:

here's a trick, add Open as root to right click in Nautilus:
[http://www.ubuntuguide.org/#openfilesasrootviarightclick](http://www.ubuntuguide.org/#openfilesasrootviarightclick)

And here's another one, Open Nautilus as root. The first is better I think
[http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus](http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus)

---

