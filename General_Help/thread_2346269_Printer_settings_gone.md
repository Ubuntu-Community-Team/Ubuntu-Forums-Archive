---
title: "Printer settings gone"
date: 2016-12-13
forum: General Help
---

### Post by eduardoflsantos on 2016-12-13
[IMG]https://s24.postimg.org/cehzoqxqd/Captura_de_ecr_de_2016_12_12_18_43_17.png[/IMG]


The icon of the printers should be there ^^, but is gone. I don't know what happened.

Edit: Ubuntu 16.04

---

### Post by howefield on 2016-12-13
What is the output of the following terminal command..

```
apt-cache policy system-config-printer-indicator
```

---

### Post by eduardoflsantos on 2016-12-13
Hi,

(I'm translating)
"It wasn't possible to find the package system-config-printer-indicator."

---

### Post by howefield on 2016-12-13
> **eduardoflsantos said:**
> "It wasn't possible to find the package system-config-printer-indicator."

OK, then try installing it..

```
sudo apt-get update
```
```
sudo apt-get install system-config-printer-indicator
```

and then check system settings again.

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ sudo apt-get update
[sudo] senha para eduardo: 
Atingido:1 http://pt.archive.ubuntu.com/ubuntu xenial InRelease
Atingido:2 http://pt.archive.ubuntu.com/ubuntu xenial-updates InRelease        
Atingido:3 http://pt.archive.ubuntu.com/ubuntu xenial-backports InRelease      
Atingido:4 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease   
Obter:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]   
Obtidos 102 kB em 0s (138 kB/s)                               
A ler as listas de pacotes... Pronto
```
(worked)

```
eduardo@eduardo-desktop:~$ sudo apt-get install system-config-printer-indicator
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
**E: Não foi possível encontrar o pacote system-config-printer-indicator**
eduardo@eduardo-desktop:~$ 
```
This one didn't work. Error (bold): it wasn't possible to find system-config-printer-indicator package.

---

### Post by howefield on 2016-12-13
The package should be in the MAIN repository, do you have it enabled ?

What's the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by slickymaster on 2016-12-13
You can always use the CUPS web interface. Point your browser to [http://localhost:631/](http://localhost:631/), then follow the links to add the printer. You'll be prompted to enter your username and your password along the way just as you would if you were using sudo.

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main

```

I went to Ubuntu software and searched for "printers", found the one with the logo and installed. Now the logo is there again, but when I click, this appears:

[IMG]https://s30.postimg.org/4j1zh6nq9/Captura_de_ecr_de_2016_12_13_10_22_55.png[/IMG]

Print service not available. Start the service in this computer or connect to another server.
("start service" button grayed out) (connect button)

---

### Post by eduardoflsantos on 2016-12-13
> **slickymaster said:**
> You can always use the CUPS web interface. Point your browser to [http://localhost:631/](http://localhost:631/), then follow the links to add the printer. You'll be prompted to enter your username and your password along the way just as you would if you were using sudo.

Hi,

Firefox is unable to connect bla bla bla (general error) ;)

---

### Post by slickymaster on 2016-12-13
Check if your CUPS service is running. In a terminal window run```
sudo service cups status
```If not start it and the recheck the "Iniciar serviço" to see if it gets enabled.

---

### Post by eduardoflsantos on 2016-12-13
> **howefield said:**
> The package should be in the MAIN repository, do you have it enabled ?

Now that you mention it... check the image of the 1st post again. "Software & Updates" isn't there either. I can't check my repositories using the setting options.

OMG, something went very wrong with this Ubuntu :/

---

### Post by eduardoflsantos on 2016-12-13
> **slickymaster said:**
> Check if your CUPS service is running. In a terminal window run```
sudo service cups status
```If not start it and the recheck the "Iniciar serviço" to see if it gets enabled.

```
eduardo@eduardo-desktop:~$ sudo service cups status
[sudo] senha para eduardo: 
&#9679; cups.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)


```

---

### Post by slickymaster on 2016-12-13
> **eduardoflsantos said:**
> ```
eduardo@eduardo-desktop:~$ sudo service cups status
[sudo] senha para eduardo: 
&#9679; cups.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)


```

It's odd that the service is masked. try to unmask it```
sudo systemctl unmask cups.service
```and afterwards check if it all went as intended```
systemctl list-unit-files --type=service | grep cups
```

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ sudo systemctl unmask cups.service
[sudo] senha para eduardo: 
Removed symlink /etc/systemd/system/cups.service.
eduardo@eduardo-desktop:~$ systemctl list-unit-files --type=service | grep cups
cups-browsed.service                       enabled 
eduardo@eduardo-desktop:~$ sudo service cups status
&#9679; cups.service - LSB: CUPS Printing spooler and server
   Loaded: loaded (/etc/init.d/cups; bad; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-sysv-generator(8)

```

Still dead, I think?

---

### Post by slickymaster on 2016-12-13
Try to start it now```
sudo service cups start
```

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ sudo service cups start
[sudo] senha para eduardo: 
eduardo@eduardo-desktop:~$ sudo service cups status
&#9679; cups.service - LSB: CUPS Printing spooler and server
   Loaded: loaded (/etc/init.d/cups; bad; vendor preset: enabled)
   Active: active (exited) since Ter 2016-12-13 11:18:02 WET; 27min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3179 ExecStart=/etc/init.d/cups start (code=exited, status=0/SUCCESS)

Dez 13 11:18:02 eduardo-desktop systemd[1]: Starting LSB: CUPS Printing spooler 
Dez 13 11:18:02 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
Dez 13 11:40:21 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
Dez 13 11:45:37 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
```

Ok, seems to be running now.

"iniciar serviço" still greyed out and localhost link you provided is still getting an error.

---

### Post by slickymaster on 2016-12-13
> **eduardoflsantos said:**
> ```
eduardo@eduardo-desktop:~$ sudo service cups start
[sudo] senha para eduardo: 
eduardo@eduardo-desktop:~$ sudo service cups status
&#9679; cups.service - LSB: CUPS Printing spooler and server
   Loaded: loaded (/etc/init.d/cups; bad; vendor preset: enabled)
   Active: active (exited) since Ter 2016-12-13 11:18:02 WET; 27min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3179 ExecStart=/etc/init.d/cups start (code=exited, status=0/SUCCESS)

Dez 13 11:18:02 eduardo-desktop systemd[1]: Starting LSB: CUPS Printing spooler 
Dez 13 11:18:02 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
Dez 13 11:40:21 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
Dez 13 11:45:37 eduardo-desktop systemd[1]: Started LSB: CUPS Printing spooler a
```

Ok, seems to be running now.

"iniciar serviço" still greyed out and localhost link you provided is still getting an error.
Please past into the thread the error you get when navigating into [http://localhost:631/](http://localhost:631/) and the output of ```
systemctl list-unit-files --type=service | grep cups
```

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ systemctl list-unit-files --type=service | grep cups
cups-browsed.service                       enabled
```


[IMG]http://i.share.pho.to/887cec43_o.png[/IMG]


Thanks for all the help.

---

### Post by slickymaster on 2016-12-13
Try to access it with your IP address localhost. In a terminal window run **ifconfig** to find out what it is. It will be listed as (for example)```
inet addr:127.0.0.1
``` 
Use it in the browser [http://127.0.0.1:631](http://127.0.0.1:631)

---

### Post by eduardoflsantos on 2016-12-13
```
eduardo@eduardo-desktop:~$ ifconfig
enp1s0    Link encap:Ethernet  Endereço de HW d0:50:99:95:d5:69  
          inet end.: 192.168.1.10  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::7fbe:a4e3:a17b:b7ef/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:79919 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:58573 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:93883858 (93.8 MB) TX bytes:7654904 (7.6 MB)

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:65536  Métrica:1
          pacotes RX:25979 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:25979 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1 
          RX bytes:1622572 (1.6 MB) TX bytes:1622572 (1.6 MB)
```


Both 192.168.1.10 and 127.0.0.1 give me error.

---

### Post by slickymaster on 2016-12-13
Do you have any firewall rules active that's denying access to localhost?

---

### Post by eduardoflsantos on 2016-12-13
not that I remember. When I type firewall in the search (top left corner) I get nothing.

---

### Post by slickymaster on 2016-12-13
To be honest, I'm starting to run out of suggestions. I'd suggest you to check your **/etc/cups/cupsd.conf** file and the value of the listen for connections from the local machine parameter.

This is from a Xubuntu VBox```
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
```

---

### Post by eduardoflsantos on 2016-12-13
This was in my computer at the work, so I can't try anything else today, in any case.

It's so odd that some things just disappeared from the settings. I used Ubuntu Software to install back the "Software & Updates" that was also missing. Might ending up doing a clean install.


Some days ago my Ubuntu at home also went crazy (although I think Nvidia drivers are the ones to blame there, it had nothing to do with this thread) and I ended up switching Ubuntu for another distro for the first time in years. Now it's the Ubuntu from the office, which has been rock solid and super fast for months. Bah, the Ubuntu gods seem to be mad at me for some reason :P

De qualquer maneira, muito obrigado pela atenção e ajuda ;)

---

### Post by slickymaster on 2016-12-14
> **eduardoflsantos said:**
> This was in my computer at the work, so I can't try anything else today, in any case.

It's so odd that some things just disappeared from the settings. I used Ubuntu Software to install back the "Software & Updates" that was also missing. Might ending up doing a clean install.
well, you can try to reinstall cups before going on a clean install```
sudo apt-get purge cups
```then delete all of files in **/etc/cups **and reinstall cups with```
sudo apt-get install cups
```


> **eduardoflsantos said:**
> <---snip--->

De qualquer maneira, muito obrigado pela atenção e ajuda ;)
De nada. Estarmos aqui uns para os outros é a filosofia Ubuntu.

---

### Post by eduardoflsantos on 2016-12-15
> **slickymaster said:**
> To be honest, I'm starting to run out of suggestions. I'd suggest you to check your **/etc/cups/cupsd.conf** file and the value of the listen for connections from the local machine parameter.

This is from a Xubuntu VBox```
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
```


```
#
# File/directory/user/group configuration file for the CUPS scheduler.
# See "man cups-files.conf" for a complete description of this file.
#

# List of events that are considered fatal errors for the scheduler...
#FatalErrors config

# Do we call fsync() after writing configuration or status files?
#SyncOnClose Yes

# Default user and group for filters/backends/helper programs; this cannot be
# any user or group that resolves to ID 0 for security reasons...
#User lp
#Group lp

# Administrator user group, used to match @SYSTEM in cupsd.conf policy rules...
# This cannot contain the Group value for security reasons...
SystemGroup lpadmin


# User that is substituted for unauthenticated (remote) root accesses...
#RemoteRoot remroot

# Do we allow file: device URIs other than to /dev/null?
#FileDevice No

# Permissions for configuration and log files...
#ConfigFilePerm 0640
#LogFilePerm 00640

# Location of the file logging all access to the scheduler; may be the name
# "syslog". If not an absolute path, the value of ServerRoot is used as the
# root directory.  Also see the "AccessLogLevel" directive in cupsd.conf.
AccessLog /var/log/cups/access_log

# Location of cache files used by the scheduler...
#CacheDir /var/cache/cups

# Location of data files used by the scheduler...
#DataDir /usr/share/cups

# Location of the static web content served by the scheduler...
#DocumentRoot /usr/share/cups/doc-root

# Location of the file logging all messages produced by the scheduler and any
# helper programs; may be the name "syslog". If not an absolute path, the value
# of ServerRoot is used as the root directory.  Also see the "LogLevel"
# directive in cupsd.conf.
ErrorLog /var/log/cups/error_log

# Location of fonts used by older print filters...
#FontPath /usr/share/cups/fonts

# Location of LPD configuration
#LPDConfigFile 

# Location of the file logging all pages printed by the scheduler and any
# helper programs; may be the name "syslog". If not an absolute path, the value
# of ServerRoot is used as the root directory.  Also see the "PageLogFormat"
# directive in cupsd.conf.
PageLog /var/log/cups/page_log

# Location of the file listing all of the local printers...
#Printcap /var/run/cups/printcap

# Format of the Printcap file...
#PrintcapFormat bsd
#PrintcapFormat plist
#PrintcapFormat solaris

# Location of all spool files...
#RequestRoot /var/spool/cups

# Location of helper programs...
#ServerBin /usr/lib/cups

# SSL/TLS keychain for the scheduler...
#ServerKeychain ssl

# Location of other configuration files...
#ServerRoot /etc/cups

# Location of Samba configuration file...
#SMBConfigFile 

# Location of scheduler state files...
#StateDir /var/run/cups

# Location of scheduler/helper temporary files. This directory is emptied on
# scheduler startup and cannot be one of the standard (public) temporary
# directory locations for security reasons...
#TempDir /var/spool/cups/tmp
```

---

### Post by eduardoflsantos on 2016-12-15
> **slickymaster said:**
> well, you can try to reinstall cups before going on a clean install```
sudo apt-get purge cups
```then delete all of files in **/etc/cups **and reinstall cups with```
sudo apt-get install cups
```

It worked! I can add new printers, now.

Thank you! :D

/Solved

---

### Post by slickymaster on 2016-12-15
> **eduardoflsantos said:**
> It worked! I can add new printers, now.

Thank you! :D

/Solved

Sure, no problem.

Glad you got it working.

---

