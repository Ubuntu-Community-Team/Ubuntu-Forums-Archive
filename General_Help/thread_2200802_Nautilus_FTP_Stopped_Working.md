---
title: "Nautilus FTP Stopped Working"
date: 2014-01-21
forum: General Help
---

### Post by adam17 on 2014-01-21
Hi, 

I used Nautilus to access the FTP of my webpage nearly every day and even this morning. However I installed Samba & Dropbox applications on my laptop and now I get the error message 

'Could not display "ftp://MyWebAddress.co.uk/".

Error: Error resolving ":No address associated with hostname
Please select another viewer and try again.

I have tried to uninstall and purge dropbox and sambe but this has not made a difference. 

I know the website server is still running as filezilla can access it however nautilus allows me to edit the html file with geany by right clicking and opening them so I would rather have Nautilus working again. 

Can anyone help me with this? Not sure what to try.

Thanks in Advance

Adam

---

### Post by adam17 on 2014-01-21
After hours of searching I cam across this posted on a site somewhere.

By typing these commands into the terminal it resets the proxy settings to normal.

I have added them below for anyone who is having the same issues.


gsettings set org.gnome.system.proxy autoconfig-url ''
gsettings set org.gnome.system.proxy ignore-hosts ['localhost', '127.0.0.0/8']
gsettings set org.gnome.system.proxy mode 'none'
gsettings set org.gnome.system.proxy use-same-proxy false
gsettings set org.gnome.system.proxy.ftp host ''
gsettings set org.gnome.system.proxy.ftp port 0
gsettings set org.gnome.system.proxy.http authentication-password ''
gsettings set org.gnome.system.proxy.http authentication-user ''
gsettings set org.gnome.system.proxy.http enabled false
gsettings set org.gnome.system.proxy.http host ''
gsettings set org.gnome.system.proxy.http port 8080
gsettings set org.gnome.system.proxy.http use-authentication false
gsettings set org.gnome.system.proxy.https host ''
gsettings set org.gnome.system.proxy.https port 0
gsettings set org.gnome.system.proxy.socks host ''
gsettings set org.gnome.system.proxy.socks port 0

Thanks to everyone who viewed this thread I hope this helps.

Adam

---

