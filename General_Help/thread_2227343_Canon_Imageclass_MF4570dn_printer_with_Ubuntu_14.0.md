---
title: "Canon Imageclass MF4570dn printer with Ubuntu 14.04 LTS"
date: 2014-06-01
forum: General Help
---

### Post by ed_k2 on 2014-06-01
I new to Ubuntu and I must say I am very impressed.  It installs in a snap and I'm getting back into the command line.

I updated my wife's laptop this weekend with a new SSD and installed 64 Bit Ubuntu 14.04 LTS.  It runs like a champ and she is getting used to it.

My problem is that I cannot for the life of me figure out how to get the printer to work.  I have a Canon Imageclass MF4570dn printer on the network.  Installed the debian printer driver using the Ubuntu Software Center.

When I go to add a printer, it sees it and the ip address it is using, but nothing prints. 

Any help would be greatly appreciated as this function is a deal breaker for converting my wife to Ubuntu.  Thanks.

Ed

---

### Post by pdc on 2014-06-02
Hi Ed; welcome to the forums;

if you had installed the 32bit version, the install is just a little easier; 

______________________________________________________________



plan will be:

1) download and install the Canon linux drivers
2) tell your system about all of this

1) go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and download Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz         (Elect to **SAVE** it and by default it will go to your [COLOR="#0000FF"]Downloads[/COLOR] directory)

we need you to open a terminal and paste some commands into it: use the SEARCH (Dash) function to find a terminal; use your mouse and the menu line at the top of the terminal to paste commands in; (control V does not work........it is Shift Control V if you are coordinate all 3 fingers at once)

Commands are in red:

_______________________________________

before installing the drivers for 64bit, you need some 32bit libraries: there is quite a bit with the ia32; (Hit enter key after each paste ...................)

so 

> [COLOR="#FF0000"]sudo apt-get install ia32-libs[/COLOR]

> [COLOR="#FF0000"]sudo apt-get install libjpeg62:i386[/COLOR]

> sudo apt-get install libxml2:i386

_____________________________________________

so 32bit libraries installed for 64bit system, so on to Canon drivers .........

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz[/COLOR]        (that unpacks the compressed file and creates a new directory called Linux_UFRII_PrinterDriver_V280_uk_EN

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V280_uk_EN/64-bit_Driver/Debian[/COLOR]             and if you now type > ls   ...     you should see two files: [COLOR="#008000"]cndrvcups-common_2.80-1_amd64.deb[/COLOR] and [COLOR="#008000"]cndrvcups-ufr2-uk_2.80-1_amd64.deb[/COLOR] and we will install them and have your sudo password ready

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.80-1_amd64.deb[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-ufr2-uk_2.80-1_amd64.deb[/COLOR]

___________________

restart CUPS > [COLOR="#FF0000"]sudo /etc/init.d/cups restart[/COLOR]

________________________

**_Register the printer (PPD) with the print spooler._** It may be hard to complete it all at one go; 

we need to know what your printer is recognised as; to register it; 

if you paste this command > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] we are looking for a reply like > lpd://172.23.2.72/CANON-MF4570dn

please paste back what you get so we can see what you get; but press on and attempt to get it all going if you want

Canon say the structure to register is > sudo /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v lpd://[Device IP address or FQDN]/[Printer Name] -E

So I think:

printer name should be ........somethink like ..............Canon-MF4570DN
PPD file should be CNCUPSIR4570ZK.ppd

so the likely command will be > sudo /usr/sbin/lpadmin -p Canon-MF4570DN -m CNCUPSIR4570ZK.ppd  -v lpd://[COLOR="#EE82EE"][Device IP address or FQDN][/COLOR]/Canon-MF4570DN -E

..............and you should............have a recognised driver if the above were to all work .............. at least perhaps I can pass on the structure

_________________________________________

Canon supply a readme and a guide for installing; both within the UFR driver package you download

if we see how things go for you ........... I don't know how much computing you have done........you may have done heaps and it is all a breeze ..

---

