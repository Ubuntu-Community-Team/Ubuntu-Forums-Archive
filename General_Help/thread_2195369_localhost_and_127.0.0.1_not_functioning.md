---
title: "localhost and 127.0.0.1 not functioning"
date: 2013-12-23
forum: General Help
---

### Post by benjamin.richards on 2013-12-23
I am trying to see if the apache instalation is working and I run into an error message in which both local host and 127.0.0.1 are not found in both firefox and chromium. I have tried restarting the machine loging out and logging in, updating the dns and dhcp as well as NetworkManager.conf line ```
dns=dnsmasq
``` has been commented with a hash character and uncommneted

the following is a copy paste of 
firefox:
 > Unable to connect

Firefox can't establish a connection to the server at 127.0.0.1.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer's network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.

chromium:
> [CENTER][COLOR=#000000][FONT=Helvetica][h=1]
This webpage is not available[/h]LessReload[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica][COLOR=#444444]Chromium's connection attempt to **127.0.0.1** was rejected. The website may be down, or your network may not be properly configured.
**Check your Internet connection.**
[COLOR=#777777]Check any cables and reboot any routers, modems, or other network devices you may be using.[/COLOR]

**Allow Chromium to access the network in your firewall or antivirus settings.**
[COLOR=#777777]If it is already listed as a program allowed to access the network, try removing it from the list and adding it again.[/COLOR]

**If you use a proxy server...**
[COLOR=#777777]Check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server: Go to the Chromium menu > Settings > Show advanced settings... > Change proxy settings... and make sure your configuration is set to "no proxy" or "direct."[/COLOR]

[COLOR=#A0A0A0]Error code: ERR_CONNECTION_REFUSED
[/COLOR]
[/COLOR]
[/FONT][/COLOR][/CENTER]


---

### Post by steeldriver on 2013-12-23
Hello and welcome to the forums

The localhost connection should go via the loopback interface (lo) so it shouldn't be affected by whatever NetworkManager / DNS / DHCP settings you have - if browsers aren't able to connect via localhost it's more likely that the web server simply isn't listening at all, or isn't listening on the standard port (port 80) - you can check using netstat e.g.

```
sudo netstat -nlp | grep apache
```

---

### Post by benjamin.richards on 2013-12-23
hello steeldriver, 
 I tried the line starting with 'sudo' and ending in 'apache' and received nothing in return.
> **steeldriver said:**
> ...

```
sudo netstat -nlp | grep apache
```

---

### Post by steeldriver on 2013-12-23
so apache2 is likely not running - what does

```
service apache2 status
```

say? if that says 'stop/waiting' then try

```
sudo service apache2 start
```

and see if there are any error messages

---

### Post by benjamin.richards on 2013-12-23
this is the message I receive when i tried
```
sudo service apache2 start
```
```

 * Starting web server apache2                                                                                                             
Action 'start' failed.
The Apache error log may have more information.


```

---

### Post by steeldriver on 2013-12-23
how about 

```
tail /var/log/apache2/error.log
```

---

### Post by benjamin.richards on 2013-12-23
After disabling a site and only enabling the default site with a2dissite and a2ensite respectivley I was able to start apache2 and load localhost

---

### Post by Iowan on 2013-12-23
Sounds like you're narrowing the problem to a virtual host (site) configuration.

---

