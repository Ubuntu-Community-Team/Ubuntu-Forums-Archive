---
title: "adding network printer"
date: 2006-10-19
forum: General Help
---

### Post by johnny9794 on 2006-10-19
first of all I like to say great job on ubuntu to all those that has put  hard effort and work into it. very nice...:)

ok i been working with ubuntu for about 5 days and i have no problems till i got stumped over "add network printer" i have been trying to add a network printer for 2 days now, i did everything that i can think of doing.

The printer is on another pc that has windows xp home on it...

Now on ubuntu I clicked New Printer Icon under System/administration/printing ... It brings me to step 1, so I tick "Network Printer" then select Windows Printer (SMB)... A window pops up asking for Authentication required so i type in my ubuntu username and password and click connect...
Now i enter in the hostname of the pc that has the printer hooked to it " \\DOWNSTAIRS " and followed below that I typed in the name of the printer " psc2100 " with my username and pw below that then I click forward 

STEP 2: i select my printer manufacturer "HP" then select the model " psc 2110 " then i cklick forward...

STEP 3: I give a description of hp psc 2100 series and the followed below that i type in the location " \\DOWNSTAIRS ' the i click Apply...

Now in Printers "where you add new printer" it says PSC-2110 Ready...
I right click on the new added printer and click properties, then i click "Print a Test Page" the a comfirmation pops up saying "A4 test page has been sent tp psc-2110" then i click OK...

then a little icon pops up in my system tray "the printer icon" so i right click the printer icon in the system tray and click properties...

Here is my problem

Status:
Printing: Unable to connect to CIFS host,will retry in 60 seconds...

how can i fix this?
I am sorry that this is so long but i wanted to give it in full detail to make sure that i am doing everything correct "which i believe i am" but don't know why this is happening.

Thank You

-Johnny

---

### Post by Fitzcarraldo on 2006-12-03
I have a PC running Windows XP Home with an HP PSC 2110 connected to it via USB, and a notebook PC running ubuntu Dapper Drake without a printer connected. These two PCs are connected to my home network.

The method given in the ubuntu documentation for configuring ubuntu to print to the remote printer did not work for me, but I found the following instructions in a Web blog, which did work:

Printing to Windows XP printer from Ubuntu
Enable &#8220;Print Services for Unix&#8221; on Windows XP machine and share printer. (I&#8217;m not actually sure that this is necessary, it might be a red herring&#8230;)
When you add the printer in Ubuntu,
     1. Choose &#8220;Network Printer&#8221; and &#8220;Windows Printer (SMB)&#8221;
     2. put your Workgroup in the Host field
     3. Put &#8220;guest@<host>/<printer>&#8221; in the Printer field (replacing <host> and <printer> with your host & printer names)
So, for example, if your Windows machine was called &#8220;Dozer&#8221; and your printer was called &#8220;LaserPrinter&#8221;, you would put &#8220;guest@Dozer/LaserPrinter&#8221;.
You should not need a name and password for the Windows machine for this to work.

---

### Post by tspoon1986 on 2006-12-05
Thankyou Fitzcarraldo, I have been trying to print to my EPSON C65 shared by my Windows XP Home computer from a wirelessly connected Ubuntu laptop for about a year. Your instructions worked perfectly! And fyi, I did not need to enable "Print Services for Unix". Hope it works for you too Johnny!

---

### Post by gbashore on 2006-12-27
Thank you Fitzcarraldo for that tip on getting Windows XP printer working.   :p 
Works great!  
I've been trying to set it up for 3 days.  :evil:

---

### Post by Kirce on 2008-04-20
ok now what if your printer isn't listed? b/c i have a laser jet 3150 and I'm not sure what to do. i tried looking for the ppd file but no success

---

