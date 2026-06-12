---
title: "ftp client with proxy support"
date: 2007-02-18
forum: General Help
---

### Post by jake3988 on 2007-02-18
Hi.  I'm simply looking for a client with proxy support.  I can use proxy support on firefox, but I can't upload.  The plugin fireftp doesn't work at all.

After searching for at least an hour on the internet I found filezilla which claimed to support proxy, but it lied and doesn't at all.

Is there any graphical ftp clients out there that support proxy?  Thanks!!

You'd think this would be easy...

---

### Post by pvdg on 2007-02-20
I believe gFTP, available in the Ubuntu repositories, has proxy support.

---

### Post by jake3988 on 2007-02-23
thanks a bunch, I'll try it out.

---

### Post by jake3988 on 2007-02-23
Nope.  Nice try.  It connects to the proxy, then instantly disconnects from the real site.

Then the entire program hangs and I have to force quit.

So... no dice.  Oh well.  Its a real shame only my browser can support proxy and yet I can't upload.  *mutters*

---

### Post by Qew on 2007-02-23
If you're not scared of the command line, lftp can do what you want. The program's page can be found [here](http://lftp.yar.ru/). Use apt-get to install it from the Ubuntu repositories if it's not already installed.

---

### Post by morningboat on 2008-03-06
You may have a try on CrossFTP: [http://gnomefiles.org/app.php/CrossFTP_Client](http://gnomefiles.org/app.php/CrossFTP_Client)
It is a GUI FTP client, and it seems to support HTTP, FTP, and SOCKS proxy in its Pro version.

---

