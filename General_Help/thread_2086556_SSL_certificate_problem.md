---
title: "SSL certificate problem"
date: 2012-11-21
forum: General Help
---

### Post by thomo2710 on 2012-11-21
Hi all,
   
  I am publishing my Nagios web console to be accessible over the interweb, now I need to make it secure.
   
  I have loaded a test VM with Nagios 3.4.1 on, on Ubuntu 12.04 desktop to test on rather than play with SSL on the live box.


Confirmed nagios web interface was working properly on port 80 before switching to SSL

   
  I have followed this guide:
  [http://blog.stefandanielschwarz.de/2010/02/howto-securing-nagios.html](http://blog.stefandanielschwarz.de/2010/02/howto-securing-nagios.html)
   
  But I cant get it to work………
   
  When I browse [https://localhost/nagios](https://localhost/nagios) firefox returns:
   
  ***Secure Connection Failed***
  ****
  ***An Error occurred during a connection to localhost***
  ****
  ***SSL received a record that exceeded the maximum permissible length***
  ****
  ***Error code: ssl_error_rx_record_too_long)***
   
  For the cert setup I entered localhost for the Common Name. 
  On the live box though I will enter the FQDN that I will hit over the internet abc.def.com for example
   
  Anybody give me any pointers on how to sort this out on the test box please?
   
  Thankyou

---

