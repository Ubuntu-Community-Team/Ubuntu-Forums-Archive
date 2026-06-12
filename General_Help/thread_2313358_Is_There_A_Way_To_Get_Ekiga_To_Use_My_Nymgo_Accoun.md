---
title: "Is There A Way To Get Ekiga To Use My Nymgo Account?"
date: 2016-02-11
forum: General Help
---

### Post by grace3 on 2016-02-11
Hello,

Is there a way to get Ekiga to use my Nymgo Account?

Thanks

---

### Post by Vladlenin5000 on 2016-02-11
[http://www.nymgo.com/en/download/](http://www.nymgo.com/en/download/)

Nymgo has its own native app for Linux (32-bit but should also work in a 64-bit system with additional libraries). Nevertheless you should be able to configure it in any other SIP client like Ekiga. Clicking on SIP in the above link shows this:

```
**Connect your SIP device**

           To connect your SIP device to Nymgo, please use the configuration info below
           
[LIST]
[*]SIP Server or SIP Proxy Server: ata.nymgo.com 
[*]SIP User ID: nymgo username 
[*]Authenticate ID: nymgo username 
[*]SIP password: nymgo password 
[*]SIP Port: 5060 
[*]Codec Used: g729, g711 
[*]STUN Server: stun.nymgo.com 
[*]STUN port: 80 
[/LIST]
                      
**Nymgo supports Codecs G729 and G711**

           All done? You can test whether your SIP device is configured correctly **by dialling 111 (it's free!)**.

          You can also check your balance **by dialling 999 (it's free too!)**

(By the way, we'll give you the balance in US Dollars. Hope that's okay with you.)

          Any problems? Don't be shy. Just get in touch with the nice people at [EMAIL="support@nymgo.com"]support@nymgo.com[/EMAIL] and they'll help you out.
```

---

