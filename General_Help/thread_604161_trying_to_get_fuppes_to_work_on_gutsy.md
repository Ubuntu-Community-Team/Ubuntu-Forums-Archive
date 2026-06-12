---
title: "trying to get fuppes to work on gutsy"
date: 2007-11-05
forum: General Help
---

### Post by lime4x4 on 2007-11-05
i've installed fuppes from svn and got it installed but when i start it i get this error message

john@john-feisty:~$ fuppes
            FUPPES - SVN-r551
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] 
failed to bind socket to : 192.168.1.101 (lib/HTTP/HTTPServer.cpp, 126)
[exiting]

---

### Post by mpierce on 2007-11-05
RTM at Fuppies under FAQ seems that it will need to be configured to use your network adapter ip address.

---

### Post by lime4x4 on 2007-11-05
Did that. Should've included the network section of the config file here it is

<network>
    <interface>eth1</interface>
    <ip_address>192.168.1.101</ip_address>
    <http_port>8888</http_port>
  </network>

---

### Post by Octagonal on 2007-11-06
I had the same problem--it worked after I killed my other upnp server running.  I had a twonky server running which seems to prohibit fuppes from starting...

---

### Post by lime4x4 on 2007-11-06
will i got it to work had to change the http port to 5000

---

### Post by Xizorbg on 2008-05-04
Thanks, LIME!!!!

---

