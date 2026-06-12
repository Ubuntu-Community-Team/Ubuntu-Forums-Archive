---
title: "Help with Dell 5100cn network printer"
date: 2005-04-11
forum: General Help
---

### Post by shakin on 2005-04-11
I'm using kcontrol's printer config wizard to setup this network printer, but it's not working... probably because the exact model isn't in the driver database. I think it's a Dell-branded Xerox printer, but not sure what the equivalent Xerox model number would be.

info:

kcontrol set it up using CUPS with device socket://10.53.25.200:515
current driver is the Dell M5200 (closest I could find).

This printer is on a Windows domain and might require authentication through the domain, but my Linux box is not on the domain. I have synced my username and password with what is on the domain.

Printer nmap:
21/tcp   open  ftp
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect
MAC Address: 08:00:37:2A:63:17 (Fuji-xerox CO.)

Any help getting this thing to print would be great.

Thanks.

---

### Post by shakin on 2005-04-11
Apparently this printer works as a remote LPD queue with postscript, so that solves all but one of my problems: how do I get the queue name? When settings up an LPD printer it asks for the host and  queue, but I don't know the queue.

I do have access to the web admin panel, but I don't see anything in there for setting up an LPD queue.

---

### Post by shakin on 2005-04-11
My apologies for posting a question that I was clearly able to answer myself with a bit of legwork. Hopefully somebody else trying to get the Dell 5100cn to work can read this and figure it out.

The solution was to simply setup an LPD queue connection (rather than TCP that I was trying before). I input the IP of the printer and entered 'LPD' as the queue. Instead of choosing a driver I just checked 'This is a Postscript printer'.

The printer now works in both color and black and white.

---

### Post by oraknabo on 2006-04-05
I was having this same problem with an M5200 and setting it up with LPD seems to have completely solved my problem. I was occasionally printing short files and some web stuff, but nothing of any significant size would print. It also wouldn't print the test page over TCP/IP. It only did the spinning wheels with no output and a busy signal. Now every thing I try to print goes through just fine.

I'm glad you posted this because I didn't see a solution anywhere else.

---

### Post by ChakRa on 2006-07-05
shakin, 
you are my hero. This is such a big help to me. Like said before, no where u can find help on 5100cn with Linux. Well i followed the directions as you posted and got a victory :) 

Just want to share the whole "add a printer" process with Ubuntu Dapper. 

Go to 
System --> Administration --> Printing
Double Click New Printer (it will check the CUPS database...)
On the Add a printer screen select network printer. From the drop down menu select UNIX Printer (LPD). 
For the URL just type in the ip XX.XX.XXX.XX (ip of the network printer. If you dont know the IP, you can always look it up in the printer network settings)
For the manufacturer select DELL. For Model select M5200 and finally for drivers select PostScript (recommended). After this the printer should be added and good to go. Like oraknabo mentioned DO NOT print a test page from printer properties it will make the roller spin forever and will tell you to load A4 paper in the tray. You haver to change the paper size to 11x17. 

shakin i owe you big one. I just wanted to post this descriptive version of exactly what you have already explained. Just making it more simpler for new ubuntu users like myself :)

---

### Post by sprocket87 on 2006-07-11
Wow, thanks shakin and ChakRa, this is just what I needed! Actually I had managed to communicate with the printer on my own but it kept doing the "Load A4" thing and when I got it to print a page it would print the same page (garbage header) ad infinitum. I noticed ChakRa's tip to change the paper source to 11x17 and it works beautifully now!

Note - I have it working using LPD and using Windows SMB printing. If you're connected to a Windows Domain and want to print to a Windows networked printer, do this:

-- System > Administration > Printing
-- Double-click New Printer
-- Choose the "Network Printer" option and in the drop-down box choose -- "Windows Printing (SMB)"
-- For the "Host" type in the machine name of the Windows server/computer that the printer is installed on/hosted from (ex: PRINTSRV). Alternatively you can click the drop-down box and choose the server from the list, assuming it auto populates.
-- In the "Printer" drop-down list, choose the appropriate printer. The names should come up as the Windows printer names, like LPxxx or however it is named. You can type the name manually if you know it.
-- If a box doesn't pop up and prompt you for username/password authentication for the domain then you can enter it manually
-- Click Forward to go to the driver screen
-- Choose Dell as the manufacturer and the M5200 model, and set it as PostScript (recommended) driver
-- Click "Forward" to name the new printer
-- Click "Apply" to finish adding the new printer
-- Right click on the printer you just added and go to Properties
-- Click the "Paper" tab at the top. Change the "Paper Size" drop-down from A4 to 11x17. DON'T PRINT A TEST PAGE. Click Close.
-- Try printing from an application!


That's basically just a reiteration of ChakRa's instructions, but the first part is changed for SMB printing. HTH, and thanks again for your assistance shakin and ChakRa!


Jesse

---

### Post by crjackson on 2007-06-04
Is there any way to make this work with a USB connection rather than using it as a networked printer?

I converted the dell provided RPM drive to a DEB and that did nothing for me.  It says that it loaded the driver and all, but when I finish with the add printer dialog, no printer ever gets added.

I did select the 5200 printer and it does get added, but I stopped when I found it kept giving me the error where the drum keeps spinning, it asks for A4 papaer and the endless cycle continued.

I wonder if changing the paper size as mentioned would work in USB mode.  I'll try that.

Why in the world would 17" paper setting work when I'm using 8.5x11 ?

---

### Post by stchman on 2007-06-05
> **crjackson said:**
> Is there any way to make this work with a USB connection rather than using it as a networked printer?

I converted the dell provided RPM drive to a DEB and that did nothing for me.  It says that it loaded the driver and all, but when I finish with the add printer dialog, no printer ever gets added.

I did select the 5200 printer and it does get added, but I stopped when I found it kept giving me the error where the drum keeps spinning, it asks for A4 papaer and the endless cycle continued.

I wonder if changing the paper size as mentioned would work in USB mode.  I'll try that.

Why in the world would 17" paper setting work when I'm using 8.5x11 ?

You paid for the print server in the printer.  Use the networked interface over the USB.  Also since you have the 5200 driver installed go to the properties of the printer and select US Letter.

---

### Post by crjackson on 2007-06-06
> **stchman said:**
> You paid for the print server in the printer.  Use the networked interface over the USB.  Also since you have the 5200 driver installed go to the properties of the printer and select US Letter.

I didn't particularly pay for it for that function it just happen to be there.  I don't really know how to set it up as you mention I'll have to figure that out.  I did change the properties to US Letter but that did noting.

---

### Post by stchman on 2007-06-06
> **crjackson said:**
> I didn't particularly pay for it for that function it just happen to be there.  I don't really know how to set it up as you mention I'll have to figure that out.  I did change the properties to US Letter but that did noting.

To use the networking ability you need to give the printer an IP address.  If you have a router (which many do) the IP will start with 192.168

Give the printer an IP of say 192.168.1.200 and plug it into the router.

Go to System-Administration-Printing and select Add a printer.  Feisty will detect it.  If the printer is a postscript printer you can select generic postscript color.

---

### Post by StooJ on 2008-01-30
Like to add my thanks to the people who posted solutions in this thread. Our printer prints!

---

