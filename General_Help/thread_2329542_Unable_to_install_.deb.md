---
title: "Unable to install .deb"
date: 2016-07-02
forum: General Help
---

### Post by Mazate on 2016-07-02
I'm trying to install a 3rd party .deb file.  When I double click it, the software center opens and I click the Install button.  After doing so, the Insall button then says "Installing...", the progress bar goes quickly over to about 10% and then disappears entirely and then the Install button is just there again to click.  It won't install for some reason.  If anyone knows a way around this or if I'm doing something wrong, any info would be most appreciated.

---

### Post by vasa1 on 2016-07-02
> **Mazate said:**
> I'm trying to install a **3rd party .deb file**. ...
Name? Source? Don't you agree that providing such information may help people help you?

---

### Post by Mazate on 2016-07-02
You could have been a little nicer in how you worded that. The name and source of the file is probably irrelevant since I've had this trouble with multiple Deb files but it's a file to install a vpn client. I also had the same trouble installing opera.

---

### Post by howefield on 2016-07-03
Try installing with the terminal, you will get more of a clue as to what the error(s) might be than the Software Centre will ever give you. As vasa1 alludes to, you have provided pitifully few details, if you are running 16.04 Ubuntu you could use

```
sudo apt install /path/to/deb/file
```

If you are using an earlier version of Ubuntu you could use dpkg to install.

---

### Post by mikodo on 2016-07-03
^^ I didn't know that. 

Another option might be using gdebi. I don't know how to use apt yet:

> sudo apt-get install gdebi

---

### Post by howefield on 2016-07-03
> **mikodo said:**
> ^^ I didn't know that. 

Another option might be using gdebi. I don't know how to use apt yet:

Indeed, the benefit in using apt or dpkg is that there is no need to install further packages just to install a third party .deb file, although as I understand it, gdebi does a much better job at managing dependencies than dpkg does:)

---

### Post by dragonfly41 on 2016-07-03
Again .. use Debi Package Installer (gdebi) as advised above.

---

### Post by Mazate on 2016-07-03
I've provided all the details that I have. I'm trying to install a deb that will install a vpn client or configuration on my desktop. I obtained the file from the vpn provider, however I also had this exact same problem yesterday when trying to install the deb file for Opera that I downloaded off the Opera website. 

I will try the install command in the terminal and report back.

---

### Post by howefield on 2016-07-03
> **Mazate said:**
> I've provided all the details that I have.

Shrug, good luck.

---

### Post by jeremy31 on 2016-07-03
I would use dpkg to install it in terminal, at least then if it fails to install you should see an error message

---

