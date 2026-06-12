---
title: "How to solve getting repeatedly “hacked” on basic 18.04 VPS setup"
date: 2021-03-30
forum: General Help
---

### Post by andy3777 on 2021-03-30
I have VPS with clean installation of Ubuntu 18.04 (provided by hosting) to host my private testing website. I set it up (Apache, MySQL...) three times, but I always get shut down by host provider because of complaints from other places.


They give me logs of attempted connections from my server to other servers:

```

6 connection attempts from xxx.xxx.xxx.xxx
xxx.xxx.xxx.xxx 32928 -> xxx.xxx.xxx.xxx 7001
xxx.xxx.xxx.xxx 54944 -> xxx.xxx.xxx.xxx 8983
xxx.xxx.xxx.xxx 34258 -> xxx.xxx.xxx.xxx 9001

```


I'm not sure if problem is server OS getting compromised or it is web application itself (Laravel 7).

To set up server I basically do:

```

ufw app list
ufw allow OpenSSH
ufw enable
ufw status


sudo apt update
sudo apt install apache2


sudo ufw app list
sudo ufw app info "Apache Full"
sudo ufw allow in "Apache Full"


sudo apt install mysql-server
sudo mysql_secure_installation
mysql
SELECT user,authentication_string,plugin,host FROM mysql.user;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; //I change this...
FLUSH PRIVILEGES;
exit


sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update


sudo apt-get install php7.3 libapache2-mod-php7.3 php7.3-cli php7.3-mysql php7.3-gd php7.3-imagick php7.3-recode php7.3-tidy php7.3-xmlrpc php7.3-common php7.3-curl php7.3-mbstring php7.3-xml php7.3-bcmath php7.3-bz2 php7.3-intl php7.3-json php7.3-readline php7.3-zip


sudo apt-get update
sudo apt-get install git composer -y




sudo nano /etc/apache2/apache2.conf
<Directory /var/www/> Options Indexes FollowSymLinks //delete "Indexes"
sudo systemctl restart apache2


sudo a2enmod rewrite
sudo systemctl restart apache2
sudo nano /etc/apache2/apache2.conf
<Directory /var/www/> 
    Options Indexes FollowSymLinks
    AllowOverride None // change None to All
    Require all granted
</Directory>
sudo systemctl restart apache2

```


[COLOR=#242729][FONT=Arial]Then I pretty much create database, upload website files to /html/ and get shut down few days later.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Am I'm doing something obviously wrong? How can I troubleshoot this?[/FONT][/COLOR]

---

### Post by HermanAB on 2021-03-31
Well, first of all, configure a network packet filter and only allow connections that are strictly required.

---

### Post by SeijiSensei on 2021-03-31
I'd start with a simple iptables rule that blocks outbound connections originating on "high" ports > 1023 and directed to high ports on remote machines.

```
sudo iptables -I OUTPUT -p tcp --sport 1024-65535 --dport 1024-65535 -j REJECT
```

I'm assuming these are TCP packets; your report doesn't say.  If UDP is also involved, then include a copy of that command with "-p udp" instead.

Next, I'd try a different version of Ubuntu like the current 20.04LTS. No stock version of Ubuntu that I know of would display this behavior out of the box. If you're still having issues, try another provider. I use Linode.

---

### Post by TheFu on 2021-03-31
Are you using a password to login?  Don't.  Use ed25519 ssh-keys. If still being cracked, create new keys and check your workstation for issues.

Don't allow any access to the system except from subnets you control.  Don't put the website on the internet. Don't allow SQL connections from anywhere that doesn't need it.

Be certain the default deny rule is set.

Setup fail2ban, to prevent brute force attacks.

See of that doesn't solve it for a week.  Watch the logs, carefully.

I've been seeing a bunch of php attacks recently. Thousands every hour.  What's funny is that I don't have any php websites that can be accessed over the internet ... except for ~4 minutes, every 77 days when certs get renewed.  Let's Encrypt doesn't like all the subnet blocking I do, so I'm forced to relax it to get certs.  Their servers are in some subnets that I routinely block by policy. With tens of thousands of subnets blocked, it was just too hard to figure out where their infrastructure might come in from across the different certs, so I got lazy and shutdown the firewall for those 3:40 seconds.

If after you do all this, and stay patched, but still get cracked, switch VPS companies. Their infrastructure may have been cracked.  One of your neighbors on the same physical machine may be doing nefarious things.

After all, using a VPS has the same liabilities as using cloudy services. They are programs running on someone else's network, on someone else's computers, stored on someone elses's storage, inside someone else's building.

---

### Post by andy3777 on 2021-03-31
Thank you, I'll look at it.

1. I don't understand why are you suggesting to block/filter outgoing traffic. The problem is getting hacked. Outgoing traffic is just a symptom?

2. Are there some default log files, that could help me find out how is it getting in/what is it doing/what it is?

---

### Post by TheFu on 2021-03-31
The point of cracking a server on a VPS it for command and control uses. If a firewall has been penetrated like this system's firewall seems to be, then connections will be outbound to odd places.  If you allow outbound connections, the attacker can use a reverse ssh connection to bypass anything you do after the initial crack. Don't allow outbound traffic, except to subnets you control. Don't allow inbound connections except to subnets you control. There are millions and millions of IPs that shouldn't be allowed any access.  Blocking them 1 at a time is counter productive.  Block everything and use a whitelist for access inbound and outbound. See how much easier that would be?

Please avoid the "hacking" term - since hacking isn't criminal/illegal, but what is happening to your VPS is illegal.  
Cracking = criminal hacking.

On Unix systems, log files are under /var/log/.  Check them all.  I'd use egrep, but do it however you like.

---

### Post by SeijiSensei on 2021-04-01
> **andy3777 said:**
> I don't understand why are you suggesting to block/filter outgoing traffic. The problem is getting hacked. Outgoing traffic is just a symptom?
Yes, blocking outbound traffic only fixes a symptom, but it is the one that is triggering problems with your provider.

> 
They give me logs of attempted connections from my server to other servers:

```

6 connection attempts from xxx.xxx.xxx.xxx
xxx.xxx.xxx.xxx 32928 -> xxx.xxx.xxx.xxx 7001
xxx.xxx.xxx.xxx 54944 -> xxx.xxx.xxx.xxx 8983
xxx.xxx.xxx.xxx 34258 -> xxx.xxx.xxx.xxx 9001

```


You'll notice I suggested a fresh install of the OS and, if that doesn't help, perhaps changing providers. If the problem is with something contained in the provider's OS image, then reinstalling that same image shouldn't help. If it does, then you need to work on security.

What does this server do? That might help us suggest where the problem might lie.

---

