---
title: "Downloading from an ftp?"
date: 2008-01-12
forum: General Help
---

### Post by evilbuntu on 2008-01-12
at times when i go to download my media from my ftp it tries to automatically stream it instead of giving me the option to save (it did not always do this)

to save it to my laptop from my ftp i have to open an explorer window and enter the ftp that way and then do the drag and drop.

is there a way to set my proftp so while in an internet browser such as IE or mozilla it will only automatically download and not stream?

---

### Post by edm1 on 2008-01-12
right click, save link as.

---

### Post by HermanAB on 2008-01-12
I'm not sure what you mean, but the problem is on the client side.  You have to configure your browser properly.

Cheers,

Herman

---

### Post by evilbuntu on 2008-01-13
> **HermanAB said:**
> I'm not sure what you mean, but the problem is on the client side.  You have to configure your browser properly.

Cheers,

Herman

im sorry, 

i have an ubuntu server running with some of my fav stuff on it for anywhere access

if i access the ftp server from my windows xp laptop anyhere in Mozilla firefox and click on a file in it, it dooes not bring up the "open" or "save as" dialog box like when downloading anything else fomr the net. instead it will stream the video in the browser window using quicktime. this just recently started though. I used to be able to just click a file and it would give e the option to save it to my computer.

now instead of using a browser like mozilla, i have to open windows explorer and enter my fpt url. then when i am at the file i wish to take i will drap it out of my explorer and on to my desk top.

is there a way to set the server proftp to not stream but only offer file taking?

i have tried the right click, save as but that only saves a shortcut to the file, not the actual file.

---

### Post by evilbuntu on 2008-01-13
> **HermanAB said:**
> I'm not sure what you mean, but the problem is on the client side.  You have to configure your browser properly.

Cheers,

Herman

no im sure its server side. it happens from more than one system with my login. im thinking there has to be a setting somewhere in webmin for downloading over streaming.

---

### Post by edm1 on 2008-01-13
You could connect using nautilus rather than an internet browser. Go to 'Places>Connect to Server' enter details. Doing this will mount the ftp server and place an icon on your desktop for future reference.

---

