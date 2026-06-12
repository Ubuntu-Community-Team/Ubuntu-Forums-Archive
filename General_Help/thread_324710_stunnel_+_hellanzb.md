---
title: "stunnel + hellanzb"
date: 2006-12-24
forum: General Help
---

### Post by uk539 on 2006-12-24
I am currently struggling to configure hellanzb to work with stunnel (in order to access newsgroups via ssl). Any tips / instructions on this would be much appreciated.

---

### Post by kd7swh on 2007-01-12
I would like this too

---

### Post by shadowuht on 2007-01-22
Me too!

---

### Post by asforme on 2007-01-25
Having trouble as well.  (Bump)

---

### Post by shookone on 2007-01-26
Would like to know about this too!

---

### Post by ghostcom97 on 2007-02-10
If you already got hellanzb working sans encryption the steps to get it working with encryption via stunnel are only a few.

Edit the /usr/etc/hellanzb.conf and change the host adress from your newsprovider dns/ip to 127.0.0.1. Keep the deleted dns/ip in memory because you're gonna need it later.

Install the 'stunnel4' package via preferred method. Create a empty config file in /etc/stunnel/snntp.conf and copy and paste the following into it:
```

      foreground=yes 

      client=yes

      [nntp]
      accept  = 127.0.0.1:119
      connect = your.usenetprovider.com:563 

```
Foreground enable/disable terminal output. Later on change it to 'no' to free up a terminal when you are confident the stunnel config works for you and let stunnel fork into the background.

Client mode is enabled due to the fact stunnel has to act at a client to a remote ssl service. 

The connect name is newsprovider specific. Replace 'your.usenetprovider.com' with your provider dns/ip from your original hellanzb config. 
Port 563 is default for secure nntp traffic but lately providers have opened up for the same service on 433. Nice for folks behind firewall because port 433 i more likely to be allowed because standard ssl traffic uses this port.

When the hellanzb and stunnelconfig is done all you need to do is start stunnel before hellanzb. Stunnel will connect to the encrypted usenet service and wait for any local client to connect to it. Hellanzb will connect to the local stunnel thinking it is a standart non-encrypted usenet server. Stunnel wraps the hellanzb traffic through itself to the encrypted usenet service.

This lets the magic flow:
```
sudo stunnel4 /etc/stunnel/snntp.conf
```

---

### Post by kd7swh on 2007-02-10
Thanks! It works wonderfully!

---

### Post by paulg on 2007-05-01
Very elegant solution. Love it!

---

