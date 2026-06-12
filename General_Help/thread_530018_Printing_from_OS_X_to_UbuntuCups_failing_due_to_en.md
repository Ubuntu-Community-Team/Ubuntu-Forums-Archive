---
title: "Printing from OS X to Ubuntu/Cups failing due to encryption error"
date: 2007-08-20
forum: General Help
---

### Post by mcstayinskool on 2007-08-20
I am trying to get printing working from a Mac OS X client to a Ubuntu Edgy Cups server (1.2.8), but printing fails and I keep getting these errrors in /var/log/cups/error_log:

E [19/Aug/2007:22:44:21 -0500] encrypt_client: Unable to encrypt connection from 192.168.1.126!
E [19/Aug/2007:22:44:21 -0500] encrypt_client: A record packet with illegal version was received.
E [19/Aug/2007:22:44:30 -0500] encrypt_client: Unable to encrypt connection from 192.168.1.126!
E [19/Aug/2007:22:44:30 -0500] encrypt_client: A record packet with illegal version was received.
E [19/Aug/2007:23:27:27 -0500] encrypt_client: Unable to encrypt connection from 192.168.1.126!
E [19/Aug/2007:23:27:27 -0500] encrypt_client: A record packet with illegal version was received.
E [19/Aug/2007:23:27:50 -0500] encrypt_client: Unable to encrypt connection from 192.168.1.126!
E [19/Aug/2007:23:27:50 -0500] encrypt_client: A record packet with illegal version was received.

I have searched these and other forums and haven't come up with a solution that works. Is it possible to not use encryption? I have set a
Encryption Never
param in my cupsd.conf and restarted, but no effect.

Or, do I need to setup something for encrypting this from the OS X side? I have no reason to need encryption here, but I'll try anything that might work.

](*,)

cheers,
#!/ben

---

### Post by tgalati4 on 2007-08-20
I can print fine from a powerbook (using Tiger 10.4.8) to several Dapper machines running CUPS 1.2.2.  Perhaps there was a change in CUPS from 1.2.2 to 1.2.8 that is causing the problem?

Are you printing through a wireless connection?  I had to port forward IP port 631 on my netgear wireless router for my printing to work correctly.

---

### Post by mcstayinskool on 2007-08-20
I think it's definitely an issue with cups 1.2.8, and particularly Ubuntu's implementation of it. I finally found this post, [http://ubuntuforums.org/showthread.php?p=2674183#post2674183](http://ubuntuforums.org/showthread.php?p=2674183#post2674183), which I'm in the middle of working through. Not sure if it's going to work yet...will post back results.

cheers,
#!/ben

---

### Post by mcstayinskool on 2007-08-20
Pfooey, that didn't work either. It seems like I'm farther, in that I no longer get encryption failure messages, but instead see this in my Ubuntu cups error_log:

E [20/Aug/2007:11:14:32 -0500] Bad request line "ML-2250" from 192.168.1.126!
E [20/Aug/2007:11:17:11 -0500] Bad request line "" from 192.168.1.126!
E [20/Aug/2007:11:22:25 -0500] Bad request line "Raw" from 192.168.1.126!
E [20/Aug/2007:11:23:18 -0500] Bad request line "lp" from 192.168.1.126!

those lines represent 4 tries to print from OS X -> Ubuntu, configuring the OS X printer to use 4 different queues (ML-2250 and Raw exist as print queues in my printers.conf, "" is when I left the queue name blank, and "lp" was just a last ditch try to see if I could get it to work).

FWIW, I have no trouble printing locally from this machine.

Any insight appreciated...

cheers,
#!/ben

---

### Post by UltraMathMan on 2007-08-20
I kept getting "Bad request line" as long as I had Listen 515 in /etc/cups/cupsd.conf. Listen 515 conflicts with the cups-lpd backend and prevents it from binding from the port. Check your cupsd.conf and if you're still having problems please post it and I'll be happy to take a look.

---

### Post by mcstayinskool on 2007-08-20
Nope, nothing on that port in my cupsd.conf...I'm only listening on 631.

```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
#DefaultAuthType None

# Restrict access to the server...
<Location />
  Encryption Never
  Order allow,deny
  Allow localhost
  Allow @LOCAL
        Allow 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
        Allow 192.168.1.*
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
#  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
        Allow 192.168.1.*
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType None
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

#
# PrintcapFormat: the format of the printcap file, currently either
# BSD or Solaris.  The default is "BSD".
#

#PrintcapFormat BSD
#PrintcapFormat Solaris

#
# PrintcapGUI: the name of the GUI options panel program to associate
# with print queues under IRIX.  The default is "/usr/bin/glpoptions"
# from ESP Print Pro.
#
# This option is only used under IRIX; the options panel program
# must accept the "-d printer" and "-o options" options and write
# the selected printer options back to stdout on completion.
#

#PrintcapGUI /usr/bin/glpoptions

```

any insight appreciated...

cheers,
#!/ben

---

### Post by UltraMathMan on 2007-08-20
The server is down at the moment so I can't check the cupsd.conf file on there to be sure, but as I recall, DefaultAuthType should be basic, and so long as you have Allow @LOCAL, Allow 192.168.1.* is unnecessary - @LOCAL will allow all incoming requests on local interfaces. If changing that doesn't work I'll post my cupsd.conf file for you when I'm at the server tomorrow.

---

