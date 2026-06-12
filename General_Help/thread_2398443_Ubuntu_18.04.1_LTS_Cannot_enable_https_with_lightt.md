---
title: "Ubuntu 18.04.1 LTS: Cannot enable https with lighttpd and Let's Encrypt certificate"
date: 2018-08-12
forum: General Help
---

### Post by ixnari on 2018-08-12
Hi. I'm currently trying to set up a simple stack on my Ubuntu box consisting of Ubuntu (obviously), lighttpd, php and sqlite. I think I've succeeded in setting up a basic installation, as I was successfully able to set up and run FreshRSS, which needs all four mentioned technologies.

The next step I want to take is to secure the connection to my server with an SSL certificate from Let's Encrypt. I installed certbot from the official repositories and was able to get the certificates for my server. This is the guide I've been following so far:

[https://www.vultr.com/docs/setup-let-s-encrypt-with-lighttpd-on-ubuntu-16-04](https://www.vultr.com/docs/setup-let-s-encrypt-with-lighttpd-on-ubuntu-16-04)

I'm currently stuck on step four. I have merged the privkey.pem and cert.pem into a file called combined.pem and pointed lighttpd.conf to their location as instructed. This is how the conf file looks like right now:

[https://0bin.net/paste/vpE0zVCVcifWqDSj#L4M2KI-adU/mGYHDjl9o9fdL6n5cyATWTfgzJXocQA0](https://0bin.net/paste/vpE0zVCVcifWqDSj#L4M2KI-adU/mGYHDjl9o9fdL6n5cyATWTfgzJXocQA0)

 You will notice the last few lines are commented out. This is because if I enable them, the lighttpd daemon refuses to run, as mentioned below. Upon adding the five lines mentioned in step four, lighttpd stopped working. The systemctl log wasn't telling me much, so I decided to run it as root, which produced an error regarding server.pem:

```
# lighttpd -f /etc/lighttpd/lighttpd.conf 
2018-08-12 15:38:32: (network.c.598) SSL: BIO_read_filename('/etc/lighttpd/server.pem') failed
```

I was able to solve this by copying the aforementioned combined.pem to /etc/lighttpd and renaming it to server.pem. This is still a bit puzzling to me, as I was under the impression that the lighttpd.conf file was supposed to point to another directory. But at least it worked. Now, however, I get another error:

```
# lighttpd -f /etc/lighttpd/lighttpd.conf 
2018-08-12 15:42:27: (network.c.464) can't bind to port:  443 Address already in use
```

Running # netstat -anp | grep 443 does not produce anything relevant, only a few processes that have the string 443 in their PID. Can anyone give me any pointers as to what I did/am doing wrong? Any help would be greatly appreciated.

---

