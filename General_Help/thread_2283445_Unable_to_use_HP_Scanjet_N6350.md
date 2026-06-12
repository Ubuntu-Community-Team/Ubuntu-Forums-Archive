---
title: "Unable to use HP Scanjet N6350"
date: 2015-06-22
forum: General Help
---

### Post by majalee on 2015-06-22
Hello there,

My ubuntu (14.04 LTS) is able to detect the HP Scanjet N6350.

Output of sane-find-scanner is :

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

**found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x4805 [HP Scanjet N6350]) at libusb:001:003**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

But "xsane" is unable to detect the scanner.

Can anyone provide a solution for this ?

Thanks in advance.
Regards,
Majalee

---

### Post by Bucky Ball on 2015-06-22
Let's start from the beginning. I'm presuming it is a USB scanner. Switch the machine off and unplug the scanner. Boot the machine. When you are at a desktop, plug the scanner in and before doing anything else, open a terminal, wait a minute and:

```
dmesg
```

Check at the bottom. What does it output about the plugging in of the scanner? Which driver is it loading, if any? Is the scanner recognised correctly by Ubuntu only when you plug it in?

Have you actually tried it with Simple Scan or any other scanning software rather than just poking around in xsane files?

PS: According to [this]("http://sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD"), your scanner is supported by sane if it is the 6350C. See [here]("http://www.sane-project.org/man/sane-hp.5.html").

---

### Post by majalee on 2015-06-22
Dear Bucky,

This is the output of dmesg :

[ 6383.852043] usb 1-8: new high-speed USB device number 3 using ehci-pci
[ 6384.009100] usb 1-8: New USB device found, idVendor=03f0, idProduct=4805
[ 6384.009108] usb 1-8: New USB device strings: Mfr=10, Product=11, SerialNumber=12
[ 6384.009112] usb 1-8: Product: HP Scanjet N6350
[ 6384.009116] usb 1-8: Manufacturer: Hewlett-Packard
[ 6384.009120] usb 1-8: SerialNumber: CN13HC602G05

Tried gscan2pdf, but even this says "no device found". I understand that the scanner supported by sane is 6350C, but what I have is the network version of the same scanner. Thought that sane will be able to work.

But, it is so frustrating that HP supports only Windows/Mac and is not bothered about Linux users.

Regards,
Majalee

---

### Post by Bucky Ball on 2015-06-22
> **majalee said:**
> 
But, it is so frustrating that HP supports only Windows/Mac and is not bothered about Linux users.

Before you leap there ... in your case, perhaps, but when it comes to printers and printers/scanners HP are very Linux friendly. In fact, along with Brother, recommended printers here. There's always a model here and there, though, for whatever reason. Have a look at the [HPLip site]("http://hplipopensource.com/hplip-web/supported_devices/index.html"). The scanjet is, in fact, listed, but sends a redirection message to sane website.

How old is your scanner?

(PS: See the last link in my signature for using code tags when posting terminal output. :))

---

### Post by majalee on 2015-06-24
The scanner is about 4-5 years old. But works perfectly when connected to a Windows PC. Being a network scanner, wanted to connect it onto a network wherein people in our group can access from Linux machines. But alas, it is not so.

Thanks for reminding me how to include the "terminal outputs". :-) 

After googling for the solution, tried installing "VueScan" ([http://www.hamrick.com](http://www.hamrick.com)) which lists that HP Scanjet N6350 is one of the scanners supported. Downloaded a vuex6495.tgz and its contents were extracted in a folder "Vuescan" which had three files.

1. vuescan (pre-compiled executable)
2. vuescan.8ba 
3. vuescan.ds

Software launches the application GUI. But this software was also unable to detect the scanner when connected through USB cable. Also was not able to find what to do with the other two files vuescan.8ba and vuescan.ds ?????

Regards,
Majalee

---

