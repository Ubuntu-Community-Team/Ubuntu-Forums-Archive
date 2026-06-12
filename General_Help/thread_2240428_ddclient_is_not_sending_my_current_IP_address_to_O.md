---
title: "ddclient is not sending my current IP address to OpenDNS"
date: 2014-08-20
forum: General Help
---

### Post by akoubu.9a on 2014-08-20
I turned on my laptop, after having set up ddclient several days ago. For the most part, I&#8217;ve followed the instructions given in [http://ubuntuforums.org/showthread.php?t=1264710&p=7938314#post7938314](http://ubuntuforums.org/showthread.php?t=1264710&p=7938314#post7938314).


I differed in a few areas. For one, when he suggests copying the init script
> sudo cp sample-etc_rc.d_init.d_ddclient.lsb /etc/init.d/ddclient

I instead used the sample-etc_rc.d_init.d_ddclient.ubuntu file.

 I am expecting my IP address to be registered with my OpenDNS account ([https://dashboard.opendns.com/settings/](https://dashboard.opendns.com/settings/)). But as I type this, there is no sync. I'm using OpenDNS's servers (as shown in [http://www.opendns.com/welcome/](http://www.opendns.com/welcome/)), but OpenDNS doesn't have my current IP address because ddclient seems to be having some errors.


In terminal, I ran```
sudo update-rc.d ddclient defaults 
```and I get this:
> update-rc.d: warning: ddclient stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
System start/stop links for /etc/init.d/ddclient already exist.

What's causing the "do not match" warning?


---
When I run 
```
sudo ddclient -daemon=0 -verbose

```The result is:
> CONNECT:  myip.dnsomatic.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: myip.dnsomatic.com
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Server: Varnish
RECEIVE:  Retry-After: 5
RECEIVE:  Content-Type: text/html
RECEIVE:  Content-Length: 12
RECEIVE:  Accept-Ranges: bytes
RECEIVE:  Date: Wed, 20 Aug 2014 05:11:40 GMT
RECEIVE:  X-Varnish: 719238977
RECEIVE:  Age: 0
RECEIVE:  Via: 1.1 varnish
RECEIVE:  Connection: close
RECEIVE:  
RECEIVE:  199.7.158.61
CONNECT:  myip.dnsomatic.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: myip.dnsomatic.com
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Server: Varnish
RECEIVE:  Retry-After: 5
RECEIVE:  Content-Type: text/html
RECEIVE:  Content-Length: 12
RECEIVE:  Accept-Ranges: bytes
RECEIVE:  Date: Wed, 20 Aug 2014 05:11:40 GMT
RECEIVE:  X-Varnish: 719239256
RECEIVE:  Age: 0
RECEIVE:  Via: 1.1 varnish
RECEIVE:  Connection: close
RECEIVE:  
RECEIVE:  199.7.158.61
INFO:     setting IP address to 199.7.158.61 for prepend
UPDATE:   updating prepend
CONNECT:  updates.opendns.com
CONNECTED:  using SSL
SENDING:  GET /nic/update?system=dyndns&hostname=prepend&myip=199.7.158.61 HTTP/1.0
SENDING:   Host: updates.opendns.com
SENDING:   Authorization: Basic ZG9tYguNjcuMjIwLVyczoyMDguNjcuMjIy5jIyMWluLWdmhbWUtc2VyLjIyMiwyMDDs=
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 401 Unauthorized
RECEIVE:  Server: nginx/1.2.7
RECEIVE:  Date: Wed, 20 Aug 2014 05:11:42 GMT
RECEIVE:  Content-Type: text/html
RECEIVE:  Content-Length: 7
RECEIVE:  Connection: close
RECEIVE:  WWW-Authenticate: Basic realm="RESTRICTED"
RECEIVE:  Vary: Accept-Encoding
RECEIVE:  Accept-Ranges: bytes
RECEIVE:  X-Varnish: 719240815
RECEIVE:  Age: 0
RECEIVE:  Via: 1.1 varnish
RECEIVE:  
RECEIVE:  badauth
FAILED:   updating prepend: authorization failed (HTTP/1.1 401 Unauthorized
FAILED:    Server: nginx/1.2.7
FAILED:    Date: Wed, 20 Aug 2014 05:11:42 GMT
FAILED:    Content-Type: text/html
FAILED:    Content-Length: 7
FAILED:    Connection: close
FAILED:    WWW-Authenticate: Basic realm="RESTRICTED"
FAILED:    Vary: Accept-Encoding
FAILED:    Accept-Ranges: bytes
FAILED:    X-Varnish: 719240815
FAILED:    Age: 0
FAILED:    Via: 1.1 varnish
FAILED:    


Why does it say "RECEIVE: HTTP/1.1 401 Unauthorized"?
Why "RECEIVE:  badauth"?
Why all the "Failed" lines?

-----
If it is helpful info, when I do 
```
ps aux | grep ddclient
```
I get
> 
root      1030  0.0  0.1  60336  7432 ?        S    09:52   0:02 ddclient - sleeping for 280 seconds
me       18061  0.0  0.0  13592   932 pts/0    S+   22:17   0:00 grep --colour=auto ddclient



How can I get this to work? How can OpenDNS automatically be updated of my IP address?

---

### Post by cj13579 on 2014-08-20
A 401 does what is says on the tin "Unauthorised". It means that your username or password that are needed to access that content are either wrong of have not been provided. Can you provide a redacted copy of your ddclient.conf file?

---

### Post by cj13579 on 2014-08-20
Also, take a look at the instructions on the OpenDNS website: [https://support.opendns.com/entries/23554765-Linux-IP-Updater-for-Dynamic-Networks](https://support.opendns.com/entries/23554765-Linux-IP-Updater-for-Dynamic-Networks)

Using the the config file from there will make sure that you have up-to-date server addresses and any configuration options that you may need.

---

### Post by akoubu.9a on 2014-08-20
cj13579, thanks for your reply.

Here is how my /etc/ddclient.conf looks.
> 
# Configuration file for ddclient generated by debconf

use=web, web=myip.dnsomatic.com
ssl=yes
server=updates.opendns.com
protocol=dyndns2
login=MyUserNameOnOpenDNS
password=MyPasswordForOpenDNS
woo
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
# the above prepend command is from [http://askubuntu.com/questions/149614/how-to-opendns-on-router-with-dynamic-ip#comment181346_149620](http://askubuntu.com/questions/149614/how-to-opendns-on-router-with-dynamic-ip#comment181346_149620)


---

### Post by cj13579 on 2014-08-21
Comparing your file to the sample one on the [OpenDNS website]("https://support.opendns.com/entries/23554765-Linux-IP-Updater-for-Dynamic-Networks") I think that you may be missing the "opendns_network_label". Have a look at the site and read how to get your network label. Additionally, I can't see the following line in the sample OpenDNS provide:

```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

---

### Post by akoubu.9a on 2014-08-22
> **cj13579 said:**
> Comparing your file to the sample one on the [OpenDNS website]("https://support.opendns.com/entries/23554765-Linux-IP-Updater-for-Dynamic-Networks") I think that you may be missing the "opendns_network_label". 
The line with the word **woo** is the "opendns_network_label"

> **cj13579 said:**
>  Additionally, I can't see the following line in the sample OpenDNS provide:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
It's not in the sample. It's in the. link that I added as a comment to the conf file.
And that link says that the OpenDNS instructions is probably not complete.

---

### Post by cj13579 on 2014-08-22
Yeah, I'm not sure that answer is helpful in your case. That line was supposed to be placed in the file "/etc/dhcp3/dhclient.conf" not in your ddclient configuration file. I would remove it and try again. Also, 401 Unauth normally just means that your username and password aren't correct so double check those :)

---

