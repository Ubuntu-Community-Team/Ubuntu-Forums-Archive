---
title: "No scanner detected"
date: 2015-02-11
forum: General Help
---

### Post by albaqui on 2015-02-11
Hi

I connected Brother MFC-240C printer-scanner. I opened simple scan. It shows no scanner detected. Can you advise me how to enable to scan?. Thanks

---

### Post by gifford on 2015-02-11
A couple of questions need to be answered to help you.
What version of Ubuntu are you using?
Did you install the Brother scanner drivers?
Is this a usb connection or network?
Is the printer recognized and working?

---

### Post by albaqui on 2015-02-11
Ubuntu 12.04 LTS
Please advise me how to install brother scanner. I tried as per Brother's website. When I downloaded and clicked to install, it could not. It showed failed.
It is USB printer/scanner. Brother MFC-240C.
Printer is shows not connected.

Thanks. Please reply.

---

### Post by albaqui on 2015-02-11
now it shows printer is connected to local host. But I can't print.

---

### Post by plucky on 2015-02-12
> **albaqui said:**
> now it shows printer is connected to local host. But I can't print.

Your printer has the printer drivers packaged in Ubuntu.

Open Software Centre and search for **brother printer** and in the list that it shows install the brother-lpr-drivers-bh7 and the brother-cups-wrapper-bh7.

If you install the brother-cups-wrapper-bh7 first,I think it might also install the Lpr drivers as well.

If you open a terminal and type ```
dpkg -l | grep -i brother
``` you should get the list of installed brother drivers.

Once that is done.delete the printer in the add printer GUI and add a new printer with the printer powered on and plugged into the USB port.You should now be able to select the correct printer driver as you go through the menus for adding a printer.

To get the scanner working requires getting the correct driver fom the [Brother website](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on) and following the install instructions on the website.

Good Luck

---

### Post by pdc on 2015-02-12
plucky has given you a very good how-to above; just for the record, if I put here another way to do it; 

Brother also now provide an installer script; it aims to automate the process; and as I understand it, it will install both the printer drivers; and the scanner drivers;

get it from here [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc240c_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc240c_all&os=128&dlid=dlf006893_000&flang=4&type3=625) ..........

if you click to download and save it, it comes down as [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR] and should end up in your [COLOR="#0000FF"]Downloads[/COLOR] folder 

so the commands to copy and paste from here; into a terminal; are:

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.0.0-1 MFC-240C
```

.............Brother think that should get all working for you ..................

---

