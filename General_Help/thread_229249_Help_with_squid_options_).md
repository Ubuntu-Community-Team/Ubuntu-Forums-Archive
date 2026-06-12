---
title: "Help with squid options :)"
date: 2006-08-04
forum: General Help
---

### Post by kvonb on 2006-08-04
I installed squid yesterday in order to provide a local cache for downloaded updates and also anything else that is downloaded over the shared connection.

It seems to be caching web pages, but nothing else, here is the access.log output:

1154610829.285 1582552 192.168.0.2 **TCP_MISS**/200 5190992 GET [http://archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.2-0ubuntu6.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.2-0ubuntu6.2_i386.deb) - DIRECT/82.211.81.151 application/x-debian-package
1154613504.922 217811 192.168.0.2 **TCP_MISS**/206 505462 GET [http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb) - DIRECT/82.211.81.182 application/x-debian-package
1154613717.024 212101 192.168.0.2 **TCP_MISS**/200 651463 GET [http://archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.14.4-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.14.4-0ubuntu1_i386.deb) - DIRECT/82.211.81.151 application/x-debian-package
1154613744.824  27798 192.168.0.2 **TCP_MISS**/200 276628 GET [http://archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3-0ubuntu1_i386.deb) - DIRECT/82.211.81.182 application/x-debian-package
1154623931.239 158102 192.168.0.2 **TCP_HIT**/200 1483 GET [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) - NONE/- text/plain
1154659098.607    748 192.168.0.5 **TCP_HIT**/200 1483 GET [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) - NONE/- text/plain
1154659354.069 138013 192.168.0.5 **TCP_MISS**/200 507952 GET [http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb) - DIRECT/82.211.81.182 application/x-debian-package
1154660015.542    927 192.168.0.5 **TCP_HIT**/200 1483 GET [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) - NONE/- text/plain
1154684226.262     51 192.168.0.3 **TCP_DENIED**/400 1447 OPTIONS / - NONE/- text/html
1154689249.786      0 192.168.0.2 **TCP_MEM_HIT**/200 529 GET [http://zen:3128/squid-internal-periodic/store_digest](http://zen:3128/squid-internal-periodic/store_digest) - NONE/- application/cache-digest

Can anyone decipher this output?  I thought I set the filesize quite high so that it would catch just about everything!

These are the only modifications I made to squid.conf:

http_port 192.168.0.1:3128
http_port 192.168.0.1:80
cache_dir ufs /work/squid 6000 16 256   (chowned to proxy:proxy)
refresh_pattern -i .deb$ 129600 100% 129600
refresh_pattern -i .rpm$ 129600 100% 129600
refresh_pattern -i .tgz$ 129600 100% 129600
refresh_pattern -i .exe$ 129600 100% 129600
refresh_pattern -i .cab$ 129600 100% 129600
refresh_pattern -i .zip$ 129600 100% 129600
refresh_pattern -i .rar$ 129600 100% 129600
refresh_pattern -i .arj$ 129600 100% 129600
refresh_pattern -i .jpg$ 129600 100% 129600
refresh_pattern -i .gif$ 129600 100% 129600
refresh_pattern -i .bmp$ 129600 100% 129600
refresh_pattern -i .mov$ 129600 100% 129600
refresh_pattern -i .avi$ 129600 100% 129600
refresh_pattern -i .mpg$ 129600 100% 129600
refresh_pattern -i .mpeg$ 129600 100% 129600
refresh_pattern -i .wmv$ 129600 100% 129600
refresh_pattern -i .mp3$ 129600 100% 129600
refresh_pattern -i .wav$ 129600 100% 129600
refresh_pattern -i .bin$ 129600 100% 129600
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl our_networks src 192.168.0.0/24
http_access allow our_networks
http_access allow localhost
http_reply_access allow all
icp_access allow all

The rest are all default.  The "refresh_pattern" I got from a post on Ubuntuforums somewhere, it originally had "refresh_pattern -i *.bin$ 129600 100% 129600" but squid borked at the "*" and loaded once I'd gotten rid of it.

I want to cache EVERYTHING, if anyone can tell me what I am doing wrong I will be extremely grateful.

Regards,  Kev :)

---

### Post by kvonb on 2006-08-06
Well it seems that no-one knows how to configure squid, oh well.

I did in fact manage to get it working to a reasonable extent, and to save someone else the headaches, I will post what I did:

1) ```
sudo apt-get install squid
```

2) ```
sudo mkdir /hd-with-lots-of-space/squid
```

3) ```
sudo chown proxy:proxy /hd-with-lots-of-space/squid
```

4) ```
sudo gedit /etc/squid/squid.conf
```
   
   make sure you change the following lines:

      http_port 192.168.0.1:3128 (add BOTH of these lines)
      http_port 192.168.0.1:80 (if you want to also cache web pages)
      cache_mem 32 MB
      maximum_object_size 153600 KB #150meg
      cache_replacement_policy heap LFUDA
      cache_dir ufs /hd-with-lots-of-space/squid 6000 16 256 #6000=<>6gig
      acl our_networks src 192.168.0.0/24 #YOUR network range
      visible_hostname zen #YOUR hostname (the one that is runing squid) or IP address

   the next several lines are SUPPOSED to keep the following lines almost permanently in the cache, although I'm not quite sure of their effectiveness:

      refresh_pattern -i .deb$ 129600 100% 129600
      refresh_pattern -i .rpm$ 129600 100% 129600
      refresh_pattern -i .tgz$ 129600 100% 129600
      refresh_pattern -i .exe$ 129600 100% 129600
      refresh_pattern -i .cab$ 129600 100% 129600
      refresh_pattern -i .zip$ 129600 100% 129600
      refresh_pattern -i .rar$ 129600 100% 129600
      refresh_pattern -i .arj$ 129600 100% 129600
      refresh_pattern -i .jpg$ 129600 100% 129600
      refresh_pattern -i .gif$ 129600 100% 129600
      refresh_pattern -i .bmp$ 129600 100% 129600
      refresh_pattern -i .mov$ 129600 100% 129600
      refresh_pattern -i .avi$ 129600 100% 129600
      refresh_pattern -i .mpg$ 129600 100% 129600
      refresh_pattern -i .mpeg$ 129600 100% 129600
      refresh_pattern -i .wmv$ 129600 100% 129600
      refresh_pattern -i .mp3$ 129600 100% 129600
      refresh_pattern -i .wav$ 129600 100% 129600
      refresh_pattern -i .bin$ 129600 100% 129600

   save and exit.

5) ```
sudo /etc/init.d/squid restart
``` (-or- stop, then start)

6) Load synaptic, go to menu->settings->preferences->network, and select "manual proxy configuration, enter the IP address of your squid machine (do this on the squid machine as well) in both boxes, save, exit, and you should be good to go :).

You can keep an eye on the workings of squid by opening a term (or3) and running the following commands:

   ```
sudo tail -F /var/log/squid/access.log
```
   ```
sudo tail -F /var/log/squid/cache.log
```
   ```
sudo tail -F /var/log/squid/store.log
```

Or if you just want to see when you are getting hits (ie the cache is actually doing it's job!), use the following:

   ```
sudo tail -F /var/log/squid/access.log | grep HIT
```

This will spit out a line ONLY when a file is served from the cache, this is ONE of the many things I LOVE about Linux/Unix, the way simple commands can be used together to form extremely useful tools!

I have included my squid.conf and also a little script for doing the "tailing" easily, for the "tailing" you will have to copy it to your /sbin/ directory and chmod it to be executable as so:

   ```
sudo cp ./squihitlog /sbin/
```
   ```
sudo chmod +x /sbin/squidhitlog
```

Then you can simply type:

   ```
squidhitlog
```

...and watch the magic (or lack of if it's not working :(  )

I should mention that on my server, I also run dhcp3, dnsmasq, ipmasq, and ppp (pppoe), at the same time; and EVERYTHING works well together.  I expected a conflict with dnsmasq as squid has it's own DNS proxy, but it seems to be working well.

Regards,

Kev :)

---

### Post by satbunny on 2006-10-18
In your example above you suggest:

http_port 192.168.0.1:3128 (add BOTH of these lines)
http_port 192.168.0.1:80 (if you want to also cache web pages)

Do you mean to give fixed IP addresses (192.168.0.1) or is that meant to be the server/router/firewall/local host? I have no 192.168.0.1 on my network since I use a different IP range. What is the IP address for, especially since the squid.conf seems to suggest no IP, just a port.

---

### Post by kvonb on 2006-10-18
Try it without the IP address, only the port number, but if you want more than one port, I believe you should put multiple lines, ie:

http_port 80
http_port 3128

...and so on.

If it doesn't work, then put the IP address of the computer that squid is running on, ie:

http_port x.x.x.x:80
http_port x.x.x.x:3128

I'm no expert, this is what I did on my server, and it works.

Regards, Kev :)

---

