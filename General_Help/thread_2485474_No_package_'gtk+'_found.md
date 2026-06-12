---
title: "No package 'gtk+' found"
date: 2023-03-30
forum: General Help
---

### Post by satimis on 2023-03-30
Ubuntu 20.04

On installing iscan-2.10.0 driver

$ sudo ./configure
```

.....
.....
......
checking for GTK... configure: error: Package requirements (gtk+) were not met:

No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Please advise how to fix the problem.  Thanks

Regards

---

### Post by Dennis N on 2023-03-30
the '+' was dropped from GTK+ project a few years ago. 
[https://lwn.net/Articles/779305/](https://lwn.net/Articles/779305/)
Now its just gtk, gtk2, gtk3, gtk4 depending on the version. The actual libraries start with libgtk.

See the installed packages on your Ubuntu version with [B]dpkg --list libgtk*
[/B]
Your driver could be old.

Sorry, no suggestions on any possible workaround.

---

### Post by satimis on 2023-03-30
> **Dennis N said:**
> the '+' was dropped from GTK+ project a few years ago. 
[https://lwn.net/Articles/779305/](https://lwn.net/Articles/779305/)
Now its just gtk, gtk2, gtk3, gtk4 depending on the version. The actual libraries start with libgtk.

See the installed packages on your Ubuntu version with [B]dpkg --list libgtk*
[/B]
Your driver could be old.

Sorry, no suggestions on any possible workaround.

Thanks for your advice.

This is an old driver (iscan_2.10.0-1.tar.gz), stored in my database, for my old scanner Epson Perfection 3490 Photo

Epson Perfection 3490 Photo
[https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux](https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Linux)

Previously it worked on Ubuntu 20.04.  After upgrade the OS to Ubuntu 22.04.  It couldn't work anymore.

Now I test this driver on an Ubuntu 20.04 VM but I can't install it.

$ dpkg --list libgtk* > libgtk.txt
Please see attached file.

Regards.

---

### Post by Dennis N on 2023-03-30
Epson 3490 should work with SnapScan and the firmware file specified. See this:
[https://snapscan.sourceforge.net/](https://snapscan.sourceforge.net/)

---

### Post by satimis on 2023-03-31
> **Dennis N said:**
> Epson 3490 should work with SnapScan and the firmware file specified. See this:
[https://snapscan.sourceforge.net/](https://snapscan.sourceforge.net/)

Hi,

Thanks for your advice and link.

I'll run following commands on Terminal to install SANE:-```

sudo add-apt-repository ppa:sane-project/sane-release
sudo apt update
sudo apt-get -y install sane
```

But I can't resolve where to download the driver?  Is it on following link;

**[COLOR="#FF0000"]SANE Backends 1.2.1[/COLOR]** 
[https://gitlab.com/sane-project/backends/-/releases](https://gitlab.com/sane-project/backends/-/releases)

If YES, which package shall I download?

Thanks

Regards

---

### Post by Dennis N on 2023-03-31
I had a similar struggle with my old Acer 620UT scanner. It's in that same list.

What you need is the firmware file given in that list: esfw52.bin 
You have to find it with an internet search.

You also need to have these packages installed from the Ubuntu Repository. They might be in the default installation:

simple-scan
sane-utils
libsane
libsane-common

Based on my notes on what i did (dated Oct 9, 2020), you should copy the downloaded firmware file to 
/usr/share/sane/snapscan and make it executable.

Than edit /etc/sane.d/snapscan.conf and under "# firmware upload is needed by the scanner" add a line:
firmware /usr/share/sane/snapscan/esfw52.bin

Then, turn on the scanner first and then open the simple-scan application. It should find the scanner, load the firmware file to the scanner and then its ready to scan.

simple-scan was the only reliable scanning application that worked for me. There is also xsane, but it did not work well.

---

### Post by Holger_Gehrke on 2023-03-31
Do you read German ? There's a step by step explanation in the German [ubuntuusers wiki]("https://wiki.ubuntuusers.de/Scanner/Epson_Perfection/"). It's especially useful because it has a download link for the firmware file. Basically: install the packages libsane, sane-utils, and xsane. Create a directory /usr/share/sane/snapscan/ and put the firmware file there. Edit /etc/sane.d/snapscan.conf and change the line starting with "firmware" to point to your firmware file. Important hint: connect the scanner to power before connecting the USB, otherwise the upload of the firmware to the scanner will fail.

Holger

---

### Post by satimis on 2023-03-31
> **Dennis N said:**
> I had a similar struggle with my old Acer 620UT scanner. It's in that same list.

What you need is the firmware file given in that list: esfw52.bin 
You have to find it with an internet search.

You also need to have these packages installed from the Ubuntu Repository. They might be in the default installation:

simple-scan
sane-utils
libsane
libsane-common

Based on my notes on what i did (dated Oct 9, 2020), you should copy the downloaded firmware file to 
/usr/share/sane/snapscan and make it executable.

Than edit /etc/sane.d/snapscan.conf and under "# firmware upload is needed by the scanner" add a line:
firmware /usr/share/sane/snapscan/esfw52.bin

Then, turn on the scanner first and then open the simple-scan application. It should find the scanner, load the firmware file to the scanner and then its ready to scan.

simple-scan was the only reliable scanning application that worked for me. There is also xsane, but it did not work well.
Hi,

Thanks for your advice.

Now I have Esfw52.bin download on following link

**[COLOR="#FF0000"]How to: get your Epson Perfection 3490 scanner working on Ubuntu Linux[/COLOR]**
[https://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/](https://www.autodidacts.io/how-to-get-epson-perfection-3490-flatbed-scanner-working-on-ubuntu-linux/)

simple-scan
sane-utils
libsane
libsane-common
**[COLOR="#FF0000"]all are on repo[/COLOR]**

$ ls /usr/share/sane/```

xsane

```

Whether I need to remove xsane first before install snapscan ?

Please advise.  Thanks

Regards

---

### Post by satimis on 2023-03-31
> **Holger_Gehrke said:**
> Do you read German ? There's a step by step explanation in the German [ubuntuusers wiki]("https://wiki.ubuntuusers.de/Scanner/Epson_Perfection/"). It's especially useful because it has a download link for the firmware file. Basically: install the packages libsane, sane-utils, and xsane. Create a directory /usr/share/sane/snapscan/ and put the firmware file there. Edit /etc/sane.d/snapscan.conf and change the line starting with "firmware" to point to your firmware file. Important hint: connect the scanner to power before connecting the USB, otherwise the upload of the firmware to the scanner will fail.

Holger
Hi Holger,

I haven't read German for long time.

My German is not good
I'll try```

Mein Deutsch ist nicht gut
Ich werde versuchen

```

Vielen dank

---

### Post by Dennis N on 2023-03-31
> Whether I need to remove xsane first before install snapscan ?
No. I have both folders.
```
dmn@Sydney:/usr/share/sane$ ls
snapscan  xsane

```

---

