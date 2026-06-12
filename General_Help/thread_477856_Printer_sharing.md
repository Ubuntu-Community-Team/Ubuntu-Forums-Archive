---
title: "Printer sharing"
date: 2007-06-18
forum: General Help
---

### Post by muggins on 2007-06-18
I have a dual boot computer xp/xubuntu with a printer installed on it. I can print with it whether I am in xp or xubuntu. What I would like to have as well is the ability for my wife's computer xp to be able to use the same printer when I am running xubuntu without having to reboot into xp. Is there an easy way to do this as everything I have read looks very complicated.

---

### Post by muggins on 2007-06-18
I have just installed samba and swat, but I can't find either one under the 
applications menu. I have rebooted but still can't find them, tried appfinder as well, any ideas.

---

### Post by scrooge_74 on 2007-06-18
samba runs as a deamon, the config file is /etc/samba/smb.conf

if the only thing you need to do is print then go to samba.org and go into the Howto and check the section for the impatience and copy the references for enabling cups under samba so your wife can print.

any questions let me know, I just did that same thing to two computers this afternoon.

---

### Post by drpaul on 2007-06-19
It's even simpler if you install cups and set up the cups config file to service clients on your local network. You don't need Samba.

HTH

Paul

---

### Post by scrooge_74 on 2007-06-19
Can you explain more on the subject since I did not know you could make window PCs see printers without using samba.  That could save me some work

---

### Post by muggins on 2007-06-20
Would you or someone walk me through on how to do this. I have read/researched forever on this and just can't seem to figure it out. My head feels like it's swimming in circles as it seems very confusing.

---

### Post by scrooge_74 on 2007-06-20
to use SWAT open your browser, type localhost:901

It is suppose to work by given the root password, but try your user and pasword.  If not then you need to enable the root account.

Anyway I rather make changes from command line

from terminal go to /etc/samba/

sudo cp smb.conf smb.conf.bk

gksudo gedit smb.conf

from SAMBA.org [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)


Anonymous Print Server

An anonymous print server serves two purposes:

    *

      It allows printing to all printers from a single location.
    *

      It reduces network traffic congestion due to many users trying to access a limited number of printers. 

In the simplest of anonymous print servers, it is common to require the installation of the correct printer drivers on the Windows workstation. In this case the print server will be designed to just pass print jobs through to the spooler, and the spooler should be configured to do raw pass-through to the printer. In other words, the print spooler should not filter or process the data stream being passed to the printer.

In this configuration, it is undesirable to present the Add Printer Wizard, and we do not want to have automatic driver download, so we disable it in the following configuration. ??? is the resulting smb.conf file.

Get rid of all in the file and use the following

Example 2.3. Anonymous Print Server smb.conf
# Global parameters
[global]
workgroup = MIDEARTH
netbios name = LUTHIEN
security = share
printcap name = cups
disable spoolss = Yes
show add printer wizard = No
printing = cups
[printers]
comment = All Printers
path = /var/spool/samba
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = No

save, close gedit, then go to /etc/init.d and type sudo sh samba stop
sudo sh samba start

if you have configure your printer through cups give  it a few seconds up to a minute and then from the XP machine check the network and if you see the server then user your add printer wizard.  Rember to change the WORKGROUP to be the same as in XP and NETBIOS to something the XP system can read

Hope this helps

---

### Post by drpaul on 2007-06-20
To set up with CUPS
I have the following in /etc/cups/cupsd.conf

# Listen localhost:631
Listen *:631

I also have the following

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

which may or may not be part of the standard conf.

I have a Win XP machine on my local network and was able to browse to the printer on the Ubuntu machine when setting up a new printer.

It was very easy!

HTH

Paul

---

### Post by drpaul on 2007-06-20
OBTW

If you want a copy of the cupsd.conf file I'll send it.

Paul

---

### Post by mdurham on 2007-06-20
Here is some info that I saved from somewhere a while ago that 'might' be useful. It worked okay for me.
> Quote:
Originally Posted by dbrum 
I have a HP printer on my Ubuntu works fine locally. I shared it and my user home directory with samba.

From my windows box, I can see my ubuntu machine in the same workgroup no problems. Problem is, when I try and access the Ubuntu from win, it asks me for a user/pw, which I typed in the user combo, the root, tried everything. Can't "log in". What have I done wrong? What login information is it authenticating against and how do I set it properly?
thanks.


Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)
Code:
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
Restart the cups daemon:
Code:
sudo /etc/init.d/cupsys restart
On the Windows box:
1.Start the Add Printer wizard 
2.Click Next 
3.Select A network printer, or a printer attached to another computer 
4.Select Connect to a printer on the Internet or on a home or office network 
5.Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number! 
6.Click Next and run through the driver installation to complete 

Should work just fine.

---

### Post by muggins on 2007-06-21
> **mdurham said:**
> Here is some info that I saved from somewhere a while ago that 'might' be useful. It worked okay for me.

Thanks for replying, I did as you suggested and it actually worked once, it printed one sheet of paper and then nothing else since. Restarted the printer, nothing.

---

### Post by mdurham on 2007-06-21
Have you had a look at [http://localhost:631/printers/]("http://localhost:631/printers/") there might be something that you can adjust. Does the second print job arrive at the print queue?
Cheers, Mike

---

### Post by scrooge_74 on 2007-06-21
Firewalls anyone?  That can give problems some time

---

### Post by muggins on 2007-06-21
> **scrooge_74 said:**
> Firewalls anyone?  That can give problems some time

There is a firewall in my router, would I have to open a port in it for the printer?

Also this is a dual boot setup, xp/xubuntu. In the xp portion there is a software firewall, would I have to change anything in there also?

Thanks for your help.

---

### Post by muggins on 2007-06-21
> **mdurham said:**
> Have you had a look at [http://localhost:631/printers/]("http://localhost:631/printers/") there might be something that you can adjust. Does the second print job arrive at the print queue?
Cheers, Mike

Yes,I have a printer icon now with a document queued.

When I went to [http://localhost:631](http://localhost:631), I arrived at the cups page for my printer and chose print test page which it started to do, then it stopped part way through.

---

### Post by scrooge_74 on 2007-06-21
What printer you have connected to your Linux box?

---

### Post by muggins on 2007-06-21
> **scrooge_74 said:**
> What printer you have connected to your Linux box?

The printer is a HP PSC 1510 All-in-One.

Have opened port 631 in my firewall also.

---

### Post by scrooge_74 on 2007-06-21
Check this info just in case the drivers are giving problems [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by muggins on 2007-06-21
When I installed my printer initially I used HPLIP instead of Cups, could this be causing a conflict. Do you think I should uninstall from HPLIP and use Cups instead?

---

### Post by scrooge_74 on 2007-06-21
Sometimes the soup receipe does not work the same.  Try using CUPS instead you never know.

---

