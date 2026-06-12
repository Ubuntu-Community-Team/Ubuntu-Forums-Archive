---
title: "Lexmark X125 Printer"
date: 2007-03-09
forum: General Help
---

### Post by sq3r on 2007-03-09
I really really need to get my Lexmark X125 printer working.

Im running Ubuntu 6.10

The driver itself does not work. I have tried to install it many times by going to system, printer, new printer but that does not work.

I have tried [this]("http://www.ubuntuforums.org/showthread.php?t=230496&highlight=x125+dapper")
multiple times but that just gives me an error code.

How can i get this desperately needed printer to work?

---

### Post by sq3r on 2007-03-09
bump for answer

---

### Post by sq3r on 2007-03-09
bump, i really would love to print!!

---

### Post by sq3r on 2007-03-09
anybody got an answer?

---

### Post by ramjet_1953 on 2007-03-10
Follow this link:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125)

Hope it helps.

Regards,
Roger :cool:

---

### Post by sq3r on 2007-03-10
no
i saw that
still nothing

ive tried changing the location to /dev/usblp0 and all that stuff, it just wont work.

any one else have any ideas?

---

### Post by sq3r on 2007-03-11
bump for an answer:confused:

---

### Post by MAZDA on 2007-03-18
I have just successfull installed my Lexmark X125 Printer on Ubuntu Dapper 6.06.
The Time that i have needed was about 15 to 30 Minutes.

The following howto is a update of this solutions here
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X125)
[http://www.ubuntuforums.org/showthread.php?t=230496&highlight=x125+dapper](http://www.ubuntuforums.org/showthread.php?t=230496&highlight=x125+dapper)

Step 1:

> Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

cd Desktop
mkdir prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd drv_x125
cd src
make (ignore warnings you may see here)
sudo make install

sudo /etc/init.d/cupsys restart

close the terminal


Step 2:
> *******
Open your Printers by using the menu (System-Printing)

Click on New Printer

STEP 1
Even though this is a local printer we will set it up as a network printer using LPD by entering the information below.

Choose Network Printer
Select UNIX Printer (LPD)

HOST: localhost
Queue Type: /dev/null

Click on the Forward button.

STEP 2
Specify your printer by using the information below.
Select Lexmark as the manufacturer
Select X125 as the model
Select drv_x125(recommended) as the driver

Click on the Apply button

The printers window should now have the x125 listed as your printer.


Step 3:
> *****
Open a new terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

sudo gedit /etc/cups/printers.conf

If you've followed the steps above you should have an X125 section.

Delete the X125 section and replace it with the following.

[HTML]<Printer X125>
Info X125
Location usb://usblp0
DeviceURI file:///dev/null
State Idle
StateTime 1174228313
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>[/HTML]

Save the file and close the text editor.

*****
from the terminal and type the following
*****

sudo gedit /etc/cups/ppd/X125.ppd
 
Change **/dev/usb/lp...** to **/dev/usblp...** or paste the following text section over yours.
you need this change in ubuntu dapper other wise the printing will not work.

[HTML]
*Device usb_lp0//dev/usblp0: "%% FoomaticRIPOptionSetting: Device=usb_lp0"
*FoomaticRIPOptionSetting Device=usb_lp0: "/dev/usblp0"
*Device usb_lp1//dev/usblp1: "%% FoomaticRIPOptionSetting: Device=usb_lp1"
*FoomaticRIPOptionSetting Device=usb_lp1: "/dev/usblp1"
*Device usb_lp2//dev/usblp2: "%% FoomaticRIPOptionSetting: Device=usb_lp2"
*FoomaticRIPOptionSetting Device=usb_lp2: "/dev/usblp2"
*Device usb_lp3//dev/usblp3: "%% FoomaticRIPOptionSetting: Device=usb_lp3"
*FoomaticRIPOptionSetting Device=usb_lp3: "/dev/usblp3"
*CloseUI: *Device
[/HTML]

Save the file and exit.



Step 4:

> Reboot the computer just to prove if everything has be updated.

Step 5:
> 
Open your Printers by using the menu (System-Printing)

The printers window should now have the x125 listed as your printer.

Right click on the printer and select properties.

Make sure that you have this here in the settings

General:
Location: usb://usblp0

Advanced:
Device: /dev/usblp0

Driver:
X125

Network:
URI: file:///dev/null


Click on Print Test Page and the printer should print.


---

