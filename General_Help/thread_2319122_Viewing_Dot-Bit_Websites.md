---
title: "Viewing Dot-Bit Websites"
date: 2016-04-01
forum: General Help
---

### Post by grace3 on 2016-04-01
Hello,

Is anyone on the forums familiar with Dot-Bit technology?  More specifically, I am tring to configure FireFox to view these  websites. Supposedly there is a firefox extension available at the  following site:

[https://dot-bit.org/files/FreeSpeechMe.xpi](https://dot-bit.org/files/FreeSpeechMe.xpi)

This fails  with 403 Forbidden. Alternatively, the NMControl package can be downloaded from here:

[https://github.com/namecoin/Convergence](https://github.com/namecoin/Convergence)

The README instructs Linux  users to:

```

### Running from source: Linux / Mac OS X
Unfortunately we currently need to be started privileged with sudo so that we can open the local DNS port.  
```
    # install pip on Linux
    sudo apt-get install python-pip

    # install pip on Mac OS X
    sudo easy_install pip

    sudo pip install bottle
    
    git clone https://github.com/namecoin/nmcontrol/
    cd nmcontrol
    sudo python ./nmcontrol.py

    # alternatively start in debug mode:
    sudo python nmcontrol.py --daemon=0 --debug=1 start
```


### DNS config on Linux / Mac OS X / Manual DNS config Windows 7 and below
Point  your primary system DNS to 127.0.0.1 (leave the secondary empty). This  will redirect ALL your DNS requests to NMControl so you should to tell  NMControl how to handle things as follows.  
In `%appdata%/Nmcontrol/conf/service-dns.conf`:  
set `disable_standard_lookups` to 0 (and make sure there is no semicolon ";" in front)  
optional:  set `resolver` to your favorite DNS server if you don't like the Google  default ones. (often this is a router IP address, e.g. 192.168.0.1). ;  There has to be a comma at the end!  
Restart NMControl  
You can test on the command line like this: `nslookup namecoin.org 127.0.0.1` or `nslookup nx.bit 127.0.0.1`.  
  

```
; service-dns.conf example

[dns]
; Launch at startup
;start=1

; Listen on ip
;host=127.0.0.1

; Disable lookups for standard domains
disable_standard_lookups=0

; Listen on port
;port=53

; Forward standard requests to your standard DNS
; There has to be a comma at the end!
; e.g. lokal router ip: resolver=192.168.0.1,
; e.g. Google DNS: resolver=8.8.8.8, 8.8.4.4,
resolver=192.168.0.1,
```

```

This  seems a lot like running i2p from the command line, which I can deal  with; but other documentation, that I have not been able to relocate,  states that a NameCoin client is also necessary, which the GitHub  package does not include. Also, the readme indicates that  a manual  proxy must be used pointing to 127.0.0.1, with no port specified. I  already have firefox configured for i2p with local host and a port  configured and I don't want to touch this; so it looks like I will have  to install another browser, with its own poxy settings, to run this  from. Goodness, how determined do I have to be? I also have FreeNet and TOR available, so things are starting to  get a little crowded.

Please oh network dieties, show this wretch the way and get me the hookup.

[IMG]http://sr.photos1.fotosearch.com/bthumb/CSP/CSP866/k25622675.jpg[/IMG]


Thanks, Grace

---

### Post by ajgreeny on 2016-04-01
When I go to te first link in your post I get this:-> Your connection is not secure

The owner of dot-bit.org has configured their website improperly. To protect your information from being stolen, Firefox has not connected to this website. with a couple of links, one **Advanced** button going to:-
> dot-bit.org uses an invalid security certificate. The certificate expired on 13/01/15 23:26. The current time is 01/04/16 15:33. Error code: SEC_ERROR_EXPIRED_CERTIFICATE 
the other, a **Learn more**  link, taking me to a Mozilla help page telling me what it all means.

Is that what you see?

---

### Post by oldos2er on 2016-04-01
Moved to General Help.

---

### Post by grace3 on 2016-04-01
> **ajgreeny said:**
> When I go to te first link in your post I get this:- with a couple of links, one **Advanced** button going to:-

the other, a **Learn more**  link, taking me to a Mozilla help page telling me what it all means.

Is that what you see?

Yes, exactly.

Once I confirm the security exeception I get the you do not have permission to view files on this server message.

---

