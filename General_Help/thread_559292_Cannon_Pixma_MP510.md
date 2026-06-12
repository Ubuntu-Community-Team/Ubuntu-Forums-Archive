---
title: "Cannon Pixma MP510"
date: 2007-09-25
forum: General Help
---

### Post by hamishnz on 2007-09-25
Hi Everyone,

I have just got a new printer which is a Cannon Pixma MP510.
I have used the driver that was in the Ubuntu database which was the
"Multipass 500" or something. It printes text fine, great infact. It scans great also.
But when I print a photo/picture it has a bur or an imperfection in it. It has just like little bit of purple of something in it, whatever it is it should not be there. What drivers should I be using and how do I fix this problem ?

Cheers Hamish - Have a good day :)

---

### Post by Maestro23 on 2007-09-25
Check its entry at LinuxPrinting.org: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP510](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP510)

---

### Post by zero-9376 on 2007-12-01
just tried with the bjc-8200 after multipass 500 failed to print properly and it worked very well.

---

### Post by oliwally on 2007-12-12
After much looking around I have finally found some fairly comprehensive instructions on making the Canon Pixma MP510 Multi-Function Printer / Scanner work. I know other people have had the same issue and have resorted to Turboprint - also a good solution. 

The instructions come from the German based ubuntuusers wiki at [http://wiki.ubuntuusers.de/Canon-Drucker]("http://wiki.ubuntuusers.de/Canon-Drucker") and [http://wiki.ubuntuusers.de/Canon_Pixma_Scanner]("http://wiki.ubuntuusers.de/Canon_Pixma_Scanner"). All I have done here is to compress and translate the information at that site, and only the parts that talk about the MP510, According to the wiki, they also work for other Canon printers of similar configuration (listed on that website). I'm very thankful to whoever wrote those wikis. I almost turfed my new Canon printer in favour of at a HP printer. But then I found this solution. I think the people who wrote them go by the names 'der Geier' (the Vulture), and the scanner part 'Stadt' (city or town). Thanks dudes!!

Before you start, please note:

Firstly, the original wiki has a lot more information. I didn't translate it all. However, If you need me to translate more details from the wiki, I may be able to assist.

Secondly, I, myself  don't actually know how any of this works - I just followed the instructions, and I've had success with it. So, I'm in no position to help those with problems as a result of the following instructions. Perhaps someone else, more wise than I, could jump in and answer questions. 

Thirdly, I've kept it as brief as I could without too much other explanation as found at the wiki. It is quite long as it is and it looks a bit scary, but most of it is just checking that drivers are installed.

Fourthly, this all worked for me on a fairly fresh install of Gutsy Kubuntu. Older versions may be a tiny little bit different (explained at the original wiki).

And lastly, the scanner works well even at high resolution, but the print quality (especially for photos, and despite setting a higher resolution) is not as good as it is in Windows, although it's fine for what I need. Maybe you have better luck - let us know how.


Make sure the printer is connected and turned on before you continue.

According to the instructions, this is how I made my MP510 work (it's not as bad as it looks - you'll have it done in just a little while).

1. Enable the Universe repository and use Synaptic or similar to install libxml1, libglade0, libpng3 and libtiff4.

2. Make sure you have a package called 'alien' installed. Use Synaptic or similar to install if not present.

3. Downloading the Canon drivers: Go to [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp510_support.aspx]("http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp510_support.aspx") (or find printer support at a Canon site closer to you). Click the 'Driver Downloads' button. Now MP510 Printer Driver Ver. 2.70 (Linux)  and download cnijfilter-common-2.70-1.i386.rpm and cnijfilter-mp510-2.70-2.i386.rpm.
Go back and click on 'MP510 Scanner Driver Ver. 1.00 (Linux)' and download scangearmp-common-1.00-1.i386.rpm and scangearmp-mp510-1.00-1.i386.rpm. 

4. The drivers you just downloaded are rpm packages. They need to be converted to deb packages for K/Ubuntu, using the program called 'alien'.
Go to the directory where you saved the downloaded drivers and open a terminal there. Convert each of the rmp packages using the command: ```
sudo alien scangearmp-mp510-1.00-1.i386.rpm --to-deb --scripts
```   Obviously you'll have to change the package name to each of the four individual packages. You should now have 4 deb packages for the drivers.

5. Install the new deb packages. Sorry, I only know how to do this in KDE (someone help us out with Gnome here) using gdebi in a terminal (had no success using gui- keeps stalling). Open a terminal where the debs are. Install each of the four debs using command: ```
sudo gdebi scangearmp-mp510_1.00-2_i386.deb
```   Again, the package name needs to be changed each time to install each of the packages.

[COLOR="DarkOrange"][SIZE="3"]Links - libtiff & libpng[/SIZE][/COLOR]

6. The priter/scanner drivers are going to be looking for some old DLLs. To get around this problem symbolic links can be set up, linking the old ones to current DLLs. Luckily it appears that the DLL-APIs don't seem to have changed, so this works without problem.

To do this, the printer filter has to be found:

```
cd /usr/local/bin
ls -l
```

You sould now something like be something like:

```
ogin@rechner:~$ cd /usr/local/bin
login@rechner:/usr/local/bin$ ls -l
total 892
-rwxr-xr-x 1 root root  84571 2007-02-22 06:50 cifmp510
-rwxr-xr-x 1 root root  20166 2007-02-22 06:50 cngpij
-rwxr-xr-x 1 root root  96073 2007-02-22 06:50 cngpijmonmp510
-rwxr-xr-x 1 root root 106903 2007-02-22 06:50 lgmonmp510
-rwxr-xr-x 1 root root 578772 2007-02-22 06:50 printuimp510
```

From this it can be seen that the printer is mp510.

The TIFF- and PNG-DLLs, which are often present as newer versions, are needed. The needed versions can be called up by typing this into the terminal (make sure your still in /usr/local/bin):

```
ldd cifmp510
```

You should now see something like:

```
login@rechner:/usr/local/bin$ ldd cifmp510
        linux-gate.so.1 =>  (0xffffe000)
        libcnbpcmcm293.so => /usr/lib/libcnbpcmcm293.so (0xb7f45000)
        libcnbpess293.so => /usr/lib/libcnbpess293.so (0xb7efd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ed8000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ed4000)
        libtiff.so.3 => not found
        libpng.so.3 => not found
        libcnbpcnclapi293.so => /usr/lib/libcnbpcnclapi293.so (0xb7e57000)
        libcnbpcnclbjcmd293.so => /usr/lib/libcnbpcnclbjcmd293.so (0xb7e52000)
        libcnbpcnclui293.so => /usr/lib/libcnbpcnclui293.so (0xb7e4c000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb7e44000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cfa000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ce1000)
        /lib/ld-linux.so.2 (0xb7f64000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7cc1000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7cac000)
```

This tells you that the driver is missing the DLLs libtiff.so.3 and libpng.so.3, and the printer cannot print.

With the command 

```
cd /usr/lib
ls -l libtiff* libpng*
```

you can establish which DLLs need to be installed. For example:


```
login@rechner:/usr/lib$ ls -l libtiff* libpng*
-rw-r--r-- 1 root root 185926 2006-11-16 01:31 libpng12.a
lrwxrwxrwx 1 root root     13 2007-01-10 00:49 libpng12.so -> libpng12.so.0
lrwxrwxrwx 1 root root     19 2006-12-03 23:50 libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r-- 1 root root 146320 2006-11-16 01:31 libpng12.so.0.1.2.8
lrwxrwxrwx 1 root root     10 2007-01-10 00:49 libpng.a -> libpng12.a
lrwxrwxrwx 1 root root     11 2007-01-10 00:49 libpng.so -> libpng12.so
-rw-r--r-- 1 root root 404034 2006-08-08 10:53 libtiff.a
-rw-r--r-- 1 root root    971 2006-08-08 10:52 libtiff.la
lrwxrwxrwx 1 root root     16 2007-01-10 00:48 libtiff.so -> libtiff.so.4.2.1
lrwxrwxrwx 1 root root     16 2006-12-03 22:06 libtiff.so.4 -> libtiff.so.4.2.1
-rw-r--r-- 1 root root 335596 2006-08-08 10:53 libtiff.so.4.2.1
-rw-r--r-- 1 root root   5846 2006-08-08 10:53 libtiffxx.a
-rw-r--r-- 1 root root    997 2006-08-08 10:52 libtiffxx.la
lrwxrwxrwx 1 root root     18 2007-01-10 00:48 libtiffxx.so -> libtiffxx.so.0.0.6
lrwxrwxrwx 1 root root     18 2007-01-10 00:48 libtiffxx.so.0 -> libtiffxx.so.0.0.6
-rw-r--r-- 1 root root   6968 2006-08-08 10:53 libtiffxx.so.0.0.6
```

The installed version of the TIFF-DLL in this example is libtiff.so.4 instead of the expected/needed libtiff.so.3. Likewise the installed version of the PNG-DLL is libpng12.so instead of the expected/needed libpng.so.3. 

So, in this example symbolic links need to be set up to link the new existing DLLs to the old versions expected by the software. Do that like so:

```
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libpng12.so libpng.so.3
```

The list of TIFF- and PNG-DLLs in the /usr/lib directory should look like so:

```
login@rechner:/usr/lib$ ls -l libtiff* libpng*
-rw-r--r-- 1 root root 185926 2006-11-16 01:31 libpng12.a
lrwxrwxrwx 1 root root     13 2007-01-10 00:49 libpng12.so -> libpng12.so.0
lrwxrwxrwx 1 root root     19 2006-12-03 23:50 libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r-- 1 root root 146320 2006-11-16 01:31 libpng12.so.0.1.2.8
lrwxrwxrwx 1 root root     10 2007-01-10 00:49 libpng.a -> libpng12.a
lrwxrwxrwx 1 root root     11 2007-01-10 00:49 libpng.so -> libpng12.so
lrwxrwxrwx 1 root root     13 2007-01-06 19:14 libpng.so.3 -> libpng12.so.0
-rw-r--r-- 1 root root 404034 2006-08-08 10:53 libtiff.a
-rw-r--r-- 1 root root    971 2006-08-08 10:52 libtiff.la
lrwxrwxrwx 1 root root     16 2007-01-10 00:48 libtiff.so -> libtiff.so.4.2.1
lrwxrwxrwx 1 root root     12 2007-01-06 19:13 libtiff.so.3 -> libtiff.so.4
lrwxrwxrwx 1 root root     16 2006-12-03 22:06 libtiff.so.4 -> libtiff.so.4.2.1
-rw-r--r-- 1 root root 335596 2006-08-08 10:53 libtiff.so.4.2.1
-rw-r--r-- 1 root root   5846 2006-08-08 10:53 libtiffxx.a
-rw-r--r-- 1 root root    997 2006-08-08 10:52 libtiffxx.la
lrwxrwxrwx 1 root root     18 2007-01-10 00:48 libtiffxx.so -> libtiffxx.so.0.0.6
lrwxrwxrwx 1 root root     18 2007-01-10 00:48 libtiffxx.so.0 -> libtiffxx.so.0.0.6
-rw-r--r-- 1 root root   6968 2006-08-08 10:53 libtiffxx.so.0.0.6
```

To finalize this procedure, activate the Link-Cache (correct translation?) with ldconfig:

```
sudo ldconfig
```

With this command you can now check that everything is in order:

```
login@rechner:/usr/lib$ cd /usr/local/bin
login@rechner:/usr/local/bin$ ldd cifmp510 
        linux-gate.so.1 =>  (0xffffe000)
        libcnbpcmcm294.so => /usr/lib/libcnbpcmcm294.so (0xb7edf000)
        libcnbpess294.so => /usr/lib/libcnbpess294.so (0xb7e97000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e71000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e6d000)
        libtiff.so.3 => /usr/lib/libtiff.so.3 (0xb7e1b000)
        libpng.so.3 => /usr/lib/libpng.so.3 (0xb7df7000)
        libcnbpcnclapi294.so => /usr/lib/libcnbpcnclapi294.so (0xb7df1000)
        libcnbpcnclbjcmd294.so => /usr/lib/libcnbpcnclbjcmd294.so (0xb7dec000)
        libcnbpcnclui294.so => /usr/lib/libcnbpcnclui294.so (0xb7de6000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb7ddf000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cab000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c98000)
        /lib/ld-linux.so.2 (0xb7efc000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7c78000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c64000)
```

There should be no "not found' lines.

[SIZE="3"][COLOR="DarkOrange"]Further DLLs[/COLOR][/SIZE]

Should this not work and further DLLs with the name cnlib* are "not found", then links are missing. These links should be established in similar fashion as described above.

In such a case the command

```
ldd cifmp510
```

shows this:

```
login@rechner:/usr/local/bin$ ldd cifmp510 
        linux-gate.so.1 =>  (0xffffe000)
        libcnbpcmcm294.so => not found
        libcnbpess294.so => not found
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e71000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e6d000)
        libtiff.so.3 => /usr/lib/libtiff.so.3 (0xb7e1b000)
        libpng.so.3 => /usr/lib/libpng.so.3 (0xb7df7000)
        libcnbpcnclapi294.so => not found
        libcnbpcnclbjcmd294.so => not found
        libcnbpcnclui294.so => not found
        libpopt.so.0 => /lib/libpopt.so.0 (0xb7ddf000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cab000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c98000)
        /lib/ld-linux.so.2 (0xb7efc000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7c78000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7c64000)
```

To fix this, show all Canon-specific DLLs and then link with shortened names [I have no idea what that means]. To do this, check the DLLs with:

```

cd /usr/lib
ls -l libcn*
```

This should give:

```
login@rechner:/usr/bin$ cd /usr/lib
login@rechner:/usr/lib$ ls -l libcn*
-rwxr-xr-x 1 root root  40440 2007-02-22 06:50 libcnbpcmcm294.so.6.50.1
-rwxr-xr-x 1 root root  16304 2007-02-22 06:50 libcnbpcnclapi294.so.3.3.0
-rwxr-xr-x 1 root root  15348 2007-02-22 06:50 libcnbpcnclbjcmd294.so.3.3.0
-rwxr-xr-x 1 root root  23292 2007-02-22 06:50 libcnbpcnclui294.so.3.3.0
-rwxr-xr-x 1 root root 291400 2007-02-22 06:50 libcnbpess294.so.3.0.9
-rwxr-xr-x 1 root root  40228 2007-02-22 06:50 libcnbpo294.so.1.0.2
```

The necessary links in this example are established like this:

```

sudo ln -s libcnbpcmcm294.so.6.50.1 libcnbpcmcm294.so
sudo ln -s libcnbpcnclapi294.so.3.3.0 libcnbpcnclapi294.so
sudo ln -s libcnbpcnclbjcmd294.so.3.3.0 libcnbpcnclbjcmd294.so
sudo ln -s libcnbpcnclui294.so.3.3.0 libcnbpcnclui294.so
sudo ln -s libcnbpess294.so.3.0.9 libcnbpess294.so
sudo ln -s libcnbpo294.so.1.0.2 libcnbpo294.so
```

Checking of the Canon DLLs in the directory /usr/lib should give this output:


```
login@rechner:/usr/bin$ cd /usr/lib
login@rechner:/usr/lib$ ls -l libcn*
lrwxrwxrwx 1 root root     24 2007-04-26 00:43 libcnbpcmcm294.so -> libcnbpcmcm294.so.6.50.1
-rwxr-xr-x 1 root root  40440 2007-02-22 06:50 libcnbpcmcm294.so.6.50.1
lrwxrwxrwx 1 root root     26 2007-04-26 00:43 libcnbpcnclapi294.so -> libcnbpcnclapi294.so.3.3.0
-rwxr-xr-x 1 root root  16304 2007-02-22 06:50 libcnbpcnclapi294.so.3.3.0
lrwxrwxrwx 1 root root     28 2007-04-26 00:43 libcnbpcnclbjcmd294.so -> libcnbpcnclbjcmd294.so.3.3.0
-rwxr-xr-x 1 root root  15348 2007-02-22 06:50 libcnbpcnclbjcmd294.so.3.3.0
lrwxrwxrwx 1 root root     25 2007-04-26 00:43 libcnbpcnclui294.so -> libcnbpcnclui294.so.3.3.0
-rwxr-xr-x 1 root root  23292 2007-02-22 06:50 libcnbpcnclui294.so.3.3.0
lrwxrwxrwx 1 root root     22 2007-04-26 00:43 libcnbpess294.so -> libcnbpess294.so.3.0.9
-rwxr-xr-x 1 root root 291400 2007-02-22 06:50 libcnbpess294.so.3.0.9
lrwxrwxrwx 1 root root     20 2007-04-26 00:43 libcnbpo294.so -> libcnbpo294.so.1.0.2
-rwxr-xr-x 1 root root  40228 2007-02-22 06:50 libcnbpo294.so.1.0.2
```

[SIZE="3"][COLOR="DarkOrange"]Testing[/COLOR][/SIZE]

With the following command you can check that all DLLs are linked properly:

```
cd /usr/local/bin
ldd cifmp510
```

There should be no lines with "not found", otherwise something is missing. This is a common problem and the first thing to check.

You can now use the System Settings > Printers menu (in KDE - must be similar in Gnome, I'm guessing) to install the MP510 printer. Should it not appear in the list, it can be manually chosen in /usr/share/cups/model/canon(Printertype).ppd.

[SIZE="3"][COLOR="DarkOrange"]Additional entries to the printer driver[/COLOR][/SIZE]

Check that the folowing changes are made to both /usr/share/cups/model/canonmp510.ppd and /etc/cups/ppd/MP510.ppd

The .ppd can be enhanced with the following entries:

```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 1/Super High: "1"
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```

This enables adjustment of print quality

```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution
```

Enables adjustment to 1200dpi and 2400dpi resolutions [didn't seem to make a difference to mine]

```
*OpenUI *CNGrayscale/Grayscale: PickOne
*DefaultCNGrayscale: false
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale
```

Enables adjustment to Grey scales

OK, hopefully your printer now works. The German site list a few tips and bits'n'pieces for problem solving as well. I've skipped these for now.


[SIZE="3"][COLOR="DarkOrange"]Scanner installation:[/COLOR][/SIZE]

Apart from the .rpm drivers you downloaded, converted to .deb and installed earlier, the following needs to be installed using Synaptic or similar:

linux-headers-generic
libusb-dev

After that the scanner worked well with XSane

I just had one problem. After doing a ' Acquire preview' and then 'Scan', an error appears saying: "Error during read: Error during deviece I/O".

To avoid this, make sure to draw a scan boundary / scan area with your mouse in the preview window - even if you're scanning the whole page!!! This seems to fix it and you have beautiful scans.

I hope all this has brought your Canon MP510 to life like it did for me.

---

### Post by Chymera on 2007-12-15
has anyone tried this in a 64bit environment?

im asking this since one of the driver packages specifically states i368

---

### Post by Fitzcarraldo on 2007-12-15
A big "thank you" to *oliwally* for the detailed instructions. With these I managed to get a MP510 printing with Ubuntu 6.06. The MP510 is connected to a PC running Windows XP on my home network which also includes a PC running Ubuntu 6.06.

The symbolic links given in *oliwally*'s post are slightly different in my case because Ubuntu 6.06 has some earlier versions of the libraries, but the procedure was basically the same.

Despite my configuring the MP510 in the Ubuntu printer manager to use the front feeder, the printer still expects the rear feeder to be used, but I can live with that. The important thing is that it now prints.

( By the way, I configured the network printing using the procedure in the following thread:
[http://ubuntuforums.org/showthread.php?t=280624](http://ubuntuforums.org/showthread.php?t=280624) )

---

### Post by oliwally on 2007-12-16
> **Fitzcarraldo said:**
> A big "thank you" to *oliwally* for the detailed instructions. .....

The symbolic links given in *oliwally*'s post are slightly different in my case because Ubuntu 6.06 has some earlier versions of the libraries, but the procedure was basically the same.

Despite my configuring the MP510 in the Ubuntu printer manager to use the front feeder, the printer still expects the rear feeder to be used, but I can live with that. The important thing is that it now prints.

( By the way, I configured the network printing using the procedure in the following thread:
[http://ubuntuforums.org/showthread.php?t=280624](http://ubuntuforums.org/showthread.php?t=280624) )

Thanks for your encouragement. I was likewise thrilled when I found the instructions on the German wiki. That German wiki also talks about installing the printer (and other similar printers!!!) on older versions of ubuntu. Let me know if anyone needs further translation of the original. 

I managed to convince my printer to accept the front paper feeding - On top of switching it over on the printer I also found the option somewhere in the printer settings through the gui. I didn't have to hack any other configuration files. Have a look through the various printer settings through your system>printer settings dialog - it's there somewhere (can't look it up right now - I'm on my other computer).

---

### Post by Fitzcarraldo on 2007-12-16
As mentioned in my previous post, I configured the printer settings via the Ubuntu printer manager GUI (System > Administration > Printing) to select the front paper feeder but it was ignored by the printer. However, I have now found a way of forcing the printer to use the front feeder: I deleted the printer using the GUI printer manager, edited both the files /usr/share/cups/model/canonmp510.ppd and /etc/cups/ppd/MP510-Ver.2.70.ppd and changed the following:

```
*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: asf
*InputSlot asf/Auto Sheet Feeder: "<</MediaPosition 0>>setpagedevice"
*InputSlot front/Front Feeder: "<</MediaPosition 3>>setpagedevice"
*InputSlot frontplain/Front for Plain Paper: "<</MediaPosition 4>>setpagedevice"
*CloseUI: *InputSlot
```

to this:

```
*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: frontplain
*InputSlot asf/Auto Sheet Feeder: "<</MediaPosition 0>>setpagedevice"
*InputSlot front/Front Feeder: "<</MediaPosition 3>>setpagedevice"
*InputSlot frontplain/Front for Plain Paper: "<</MediaPosition 4>>setpagedevice"
*CloseUI: *InputSlot
```

and then re-installed the printer via the GUI printer manager. All I did in the two files was to change the default paper feeder from Auto Sheet Feeder to Front for Plain Paper. This time, after installing the printer using the GUI printer manager, the printer does use the front paper feeder. Why this worked but changing the InputSlot via the GUI printer manager after installing the printer driver did not, I do not know. Presumably the printer manager picks up the default from the file (Front for Plain Paper) when the printer is installed and forces the driver to use that setting. Anyway, everything is now set up the way I wanted it, so I'm very pleased. Thanks again for taking the time to post the translation from the German wiki you mentioned.

---

