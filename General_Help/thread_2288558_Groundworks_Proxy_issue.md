---
title: "Groundworks Proxy issue"
date: 2015-07-28
forum: General Help
---

### Post by aaron27 on 2015-07-28
I am having an issue with our Groundworks install on a 14.04 ubuntu server.

the only change i have made recently is running the sudo apt-get autoclean and sudo apt-get clean commands to free up some space. whenever we try to access the console we are presented with this error:

Proxy Error
The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request get/portal/classic/dashboard

Reason DNS lookup failure for: localhost

I haven't setup a proxy server and being new to linux i didnt know if there was a proxy that came as default?

I know this forum isnt specifically for groundworks, but i am unable to post anything on the groundworks forum (even after asking to be assigned correct permissions)

Is anyone on here able to help?

---

### Post by Habitual on 2015-07-28
> **aaron27 said:**
> 
Reason DNS lookup failure for: localhost
Can you show us this output please?
```
grep ^127.0.0.1 /etc/hosts
```

---

### Post by aaron27 on 2015-07-31
Thank you for your reply.

The output is:

```

**[COLOR=#ff0000]127.0.0.1[/COLOR] **localhost

```

---

### Post by aaron27 on 2015-08-04
I dont know if it is related but we are also getting a message that we have low disk space (200mb remaining) i have already run the commands:

```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

I also downloaded a program called bleachbit which deleted a fair amount.
However the message still comes up that we have low disk space.

Groundworks is all that runs on this machine (VM through hyper v)

---

