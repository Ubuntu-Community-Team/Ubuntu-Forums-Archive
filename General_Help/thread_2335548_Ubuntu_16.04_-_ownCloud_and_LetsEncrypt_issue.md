---
title: "Ubuntu 16.04 - ownCloud and LetsEncrypt issue"
date: 2016-08-30
forum: General Help
---

### Post by joelstitch on 2016-08-30
I am having issues running ownCloud on Ubuntu 16.04. Installing it is no issue but trying to access it through http or https . I follow the directions for installing ownCloud from [HERE]("https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-owncloud-on-ubuntu-16-04") and follow the directions for setting up SSL from [HERE]("https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-16-04") but whenever I try to access it trough **http** I get this:

```
**Not Found**

 The requested URL /owncloud was not found on this server.
 [HR][/HR] Apache/2.4.18 (Ubuntu) Server at localhost Port 80

```

And whenever I try to access it trough **https** I get this:

```
Secure Connection Failed

An error occurred during a connection to localhost. SSL received a record that exceeded the maximum permissible length. Error code: SSL_ERROR_RX_RECORD_TOO_LONG

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.
```

When I follow the LetsEncrypt guide I get stuck in the command **./letsencrypt-auto --apache -d MYDOMAIN.com **with this error:

```
Failed authorization procedure. MYDOMAIN.com (tls-sni-01): urn:acme:error:connection :: The server could not connect to the client to verify the domain :: Failed to connect to **MYIP**:443 for TLS-SNI-01 challenge

IMPORTANT NOTES:
 - The following errors were reported by the server:

   Domain: **MYDOMAIN**.com
   Type:   connection
   Detail: Failed to connect to **MYIP**:443 for TLS-SNI-01
   challenge

   To fix these errors, please make sure that your domain name was
   entered correctly and the DNS A record(s) for that domain
   contain(s) the right IP address. Additionally, please check that
   your computer has a publicly routable IP address and that no
   firewalls are preventing the server from communicating with the
   client. If you're using the webroot plugin, you should also verify
   that you are serving files from the webroot path you provided.
```

Any suggestions?! Thanks

---

### Post by joelstitch on 2016-08-30
So I ended up removing and purging Apache2 and PHP and reinstalling it. LetsEncrypt worked fine after that and now I am able to access ownCloud but cant access it trouygh https. I am getting this error now:

```
[h=1]Forbidden[/h] You don't have permission to access /owncloud on this server.

 Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.


```

---

