---
title: "nginx not working"
date: 2024-02-07
forum: General Help
---

### Post by randomnumber3 on 2024-02-07
Hello,
I followed this tutorial  [https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04) to install and set up nginx.
But when I load my web page with the browser, it's only loading...
There is no problem with the DNS because I can ping it. Also, I made a custom server listening to port 10000 and that worked...
Following the tutorial, at step 3, I had no results, then I did all the next steps about setting up server blocks, but nothing happens, this is making me mad.

I have to mention that the VSP it is hosted by hostinger if this can help. It has also cloudpanel at port 8443,
there doesn't seem to be errors with nginx service.

Thanks a lot for your help

---

### Post by The Cog on 2024-02-07
You could use **[FONT=Courier New]ss -ltp[/FONT]** to see what address:port the VMis listening on, if at all.  
And **[FONT=Courier New]nc -vzw3 <hostname> 80[/FONT]** or **[FONT=Courier New]nc -vzw3 <hostname> 443[/FONT]** to see if you can connect at all.
And **[FONT=Courier New]sudo tcpdump -nl tcp port 80[/FONT]** (or 443 of course) to see if packets for your server are actually reaching it.

---

### Post by randomnumber3 on 2024-02-07
OOOK very interesting

root@srv469606:~# ss -ltp
State      Recv-Q     Send-Q         Local Addressport           Peer Addressport    Process                                                            
LISTEN     0          4096               127.0.0.1:17000               0.0.0.0:*        users ("php-fpm8.2",pid=686,fd=8))                               
LISTEN     0          4096               127.0.0.1:13000               0.0.0.0:*        users ("php-fpm7.3",pid=682,fd=7))                               
LISTEN     0          511                127.0.0.1:redis               0.0.0.0:*        users ("redis-server",pid=692,fd=6))                             
LISTEN     0          1024               127.0.0.1:11211               0.0.0.0:*        users ("memcached",pid=674,fd=22))                               
LISTEN     0          4096               127.0.0.1:18000               0.0.0.0:*        users ("php-fpm8.3",pid=687,fd=8))                               
LISTEN     0          4096               127.0.0.1:14000               0.0.0.0:*        users ("php-fpm7.4",pid=683,fd=7))                               
LISTEN     0          4096               127.0.0.1:8787                0.0.0.0:*        users ("php-fpm8.1",pid=665,fd=8))                               
LISTEN     0          4096               127.0.0.1:8788                0.0.0.0:*        users ("php-fpm8.1",pid=665,fd=9))                               
LISTEN     0          128                  0.0.0.0:ftp                 0.0.0.0:*        users ("proftpd",pid=830,fd=0))                                  
LISTEN     0          4096           127.0.0.53%lo:domain              0.0.0.0:*        users("systemd-resolve",pid=624,fd=14))                         
LISTEN     0          128                  0.0.0.0:ssh                 0.0.0.0:*        users("sshd",pid=772,fd=3))                                     
LISTEN     0          4096               127.0.0.1:11000               0.0.0.0:*        users("php-fpm7.1",pid=679,fd=7))                               
LISTEN     0          4096               127.0.0.1:15000               0.0.0.0:*        users("php-fpm8.0",pid=684,fd=8))                               
LISTEN     0          100                  0.0.0.0:smtp                0.0.0.0:*        users("master",pid=1819,fd=13))                                 
LISTEN     0          10                 127.0.0.1:37403               0.0.0.0:*        users("varnishd",pid=724,fd=10))                                
LISTEN     0          511                  0.0.0.0:8443                0.0.0.0:*        users("nginx",pid=810,fd=6),("nginx",pid=804,fd=6))             
LISTEN     0          4096               127.0.0.1:16000               0.0.0.0:*        users("php-fpm8.1",pid=685,fd=8))                               
LISTEN     0          4096               127.0.0.1:12000               0.0.0.0:*        users("php-fpm7.2",pid=681,fd=7))                               
LISTEN     0          1024                 0.0.0.0:6081                0.0.0.0:*        users("cache-main",pid=982,fd=3),("varnishd",pid=724,fd=3))     
LISTEN     0          10                     [::1]:45257                  [::]:*        users("varnishd",pid=724,fd=9))                                 
LISTEN     0          512                        *:mysql                     *:*        users("mysqld",pid=866,fd=22))                                  
LISTEN     0          511                    [::1]:redis                  [::]:*        users("redis-server",pid=692,fd=7))                             
LISTEN     0          128                     [::]:ssh                    [::]:*        users("sshd",pid=772,fd=4))                                     
LISTEN     0          100                     [::]:smtp                   [::]:*        users("master",pid=1819,fd=14))                                 
LISTEN     0          511                     [::]:8443                   [::]:*        users("nginx",pid=810,fd=7),("nginx",pid=804,fd=7))             
LISTEN     0          1024                    [::]:6081                   [::]:*        users("cache-main",pid=982,fd=5),("varnishd",pid=724,fd=5))     
LISTEN     0          70                         *:33060                     *:*        users("mysqld",pid=866,fd=20))       


why nginx seems to be listening to 8443?? (cloud panel)

and nothing is reachable

moreno@zephyr:~$ nc -vzw3 kitetripscanner.com 443
nc: connect to kitetripscanner.com (193.203.169.16) port 443 (tcp) timed out: Operation now in progress
moreno@zephyr:~$ nc -vzw3 kitetripscanner.com 80
nc: connect to kitetripscanner.com (193.203.169.16) port 80 (tcp) timed out: Operation now in progress

---

### Post by randomnumber3 on 2024-02-07
Thank for your help, it helped me,
I found: in   /etc/nginx/nginx.conf
there was an include: include /etc/nginx/sites-enabled/*.conf
but I did not name it with the suffic .conf, so I changed  include /etc/nginx/sites-enabled/*.conf to  include /etc/nginx/sites-enabled/* 
....

---

