---
title: "Apache 2 Config problems"
date: 2006-10-02
forum: General Help
---

### Post by CameronCalver on 2006-10-02
Hello i i would like to set up a apache2 server and i am unsure of what to do.
This is what i have dont so far i did sudo apt-get install apache2 
changed the listen port to 5600 becuase my ip bannes port 80 and then forwared 5600 and then put a html in /var/www and then went on my browser 192.168.1.103:5600 and it did not work is there something i am missing

---

### Post by po0f on 2006-10-02
CameronCalver,

I'm guessing that since you are on your internal network, you just access it via port 80.  The outside world gets to it through 5600.

---

### Post by CameronCalver on 2006-10-02
ok well can u access it i just put a test html there go to 
 203.217.88.100:5600

---

### Post by po0f on 2006-10-02
CameronCalver,

Your router must not be forwarding it to you correctly because I cannot access your site.

---

### Post by CameronCalver on 2006-10-02
i cant even access it from my own network ?

---

### Post by Ronbo on 2006-10-02
Did you restart Apache after you changed the port it is listening on?  If not open a terminal and issue this command

sudo /etc/init.d/apache2 restart

When it restarts try accessing it then.

---

### Post by CameronCalver on 2006-10-02
yep i thought id might of been the proxy so i turned it off and if still does not work and i think we should try and get it working locally before getting in on the www

---

