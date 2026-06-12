---
title: "Printer Driver"
date: 2015-12-03
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-12-03
I'm trying to install the driver for my Brother printer and it's a shell script and I don't know how to do that.  Can someone please help me?

---

### Post by sandyd on 2015-12-03
Hi,
What is your printer model. You can download drivers for the brother printers from [http://support.brother.com/g/s/id/linux/en/download_prn.html](http://support.brother.com/g/s/id/linux/en/download_prn.html) (search for your model). Download the LPR and CUPS deb files.

Go to a terminal and navigate to where you downloaded the files to, and install the two downloaded DEB files.
```

dpkg  -i  --force-all *lpr-driver-deb*
dpkg  -i  --force-all *cups-driver-deb*
```

If you provide the printer model, exact instructions can be provided.

---

### Post by shane_faulkinbury2 on 2015-12-03
Will do and I'll report back that it worked!

What if it's a .gz file?

Sorry forgot I already extracted the file!  This is what I get.

---

### Post by sandyd on 2015-12-03
> **shane_faulkinbury2 said:**
> Will do and I'll report back that it worked!

Which printer are you trying to install?

---

### Post by shane_faulkinbury2 on 2015-12-03
Mfc-j475dw

---

### Post by SeijiSensei on 2015-12-03
First, rename the file to get rid of the "(2)".  You can either do this from the GUI with Nautilus or from the command prompt with
```
sudo mv -f 'linux-brprinter-installer-2.0.0.1 (2)' linux-brprinter-installer-2.0.0.1
```
Now make sure the file is executable with
```
sudo chmod a+x linux-brprinter-installer-2.0.0.1
```
Then you just need to run the script with
```
sudo ./linux-brprinter-installer-2.0.0.1
```
and answer the questions it asks.  It should download and install the correct drivers for your printer.

---

### Post by shane_faulkinbury2 on 2015-12-03
What's URI?

---

### Post by sandyd on 2015-12-03
A URI is used to identify the location and name of a resource such as a network device or a printer.

Type 8, you have the printer connected via USB and it is detected.

---

### Post by shane_faulkinbury2 on 2015-12-03
I really appreciate your quick response!  Thank you!

---

