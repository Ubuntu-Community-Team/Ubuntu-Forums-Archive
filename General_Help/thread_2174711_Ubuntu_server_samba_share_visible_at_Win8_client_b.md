---
title: "Ubuntu server samba share visible at Win8 client but not accessible"
date: 2013-09-15
forum: General Help
---

### Post by MarcusL on 2013-09-15
Hi all,
I am a little stuck and appreciate your advice.

I have set up an APACHE2 web development server using Ubuntu 13.04 and have also set up SAMBA for file sharing. I have successfully managed to set up shares for folders / files, but what I was now trying to do is set up a file share for my web site address, so as I develop the site I can edit the HTML / PHP files directly off the server. 

Basically I followed the instructions given to me in one of my [previous ]("http://ubuntuforums.org/showthread.php?t=2155990")[questions]("http://ubuntuforums.org/showthread.php?t=2155990")  but the result is not the same! I can "see" the share in W8 but when I try and access it I get told by Windows the "site name may be mispelled".

Here's what I have done:

1. Created a new folder for my test site at /etc/apache2/sites-available/opencart
2. Added the smbd.conf the folder specifications:
```
[ocsite]
    comment = Ubuntu File Server Share For Web Server
    path = /etc/apache2/sites-available/opencart
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755
    read list = lf

```
3. restarted both smbd and nmbd
```

sudo restart smbd
sudo restart nmbd

```
4. Set up access rights to the folder (for user "tm" as owner, only user with rw access, others can read only) as follows:
```

sudo chown tm:tm /etc/apache2/sites-available/opencart
sudo chmod 755 /etc/apache2/sites-available/opencart

```

The result is I can "see" the share but Windows cannot connect to it and says it may be mispelled.

Thanks in advance for any help you provide.

M

---

