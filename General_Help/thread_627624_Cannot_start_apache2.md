---
title: "Cannot start apache2"
date: 2007-11-30
forum: General Help
---

### Post by Adrian Birch on 2007-11-30
I now this has been dealt with before - but I still do not have a solution:

I have installed apache2.  I cannot start apache2:

adrian@ablinx1:/etc/apache2$ sudo `which apache2ctl` -k start
[Fri Nov 30 15:29:16 2007] [warn] module authn_file_module is already loaded, skipping
... several similar warnings.  

I then check that the daemon has started:

adrian@ablinx1:/etc/apache2$ ps aux | grep httpd
adrian    7308  0.0  0.0    304   104 pts/0    R+   15:30   0:00 grep httpd

It has not started,  For curiosity I try to stop httpd:

adrian@ablinx1:/etc/apache2$ sudo `which apache2ctl` -k stop
[Fri Nov 30 15:41:04 2007] [warn] module authn_file_module is already loaded, skipping
.. several similar messages
httpd (no pid file) not running

I have ensured that:
1) There is only ONE ports.conf file

I also sometimes get:
98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down

Having googled for this I have tried:
1) more /etc/apache2/ports.conf (to ensure no double entries etc.)
2) adrian@ablinx1:/etc/apache2$ sudo lsof | grep apache
bash      7133     adrian  cwd       DIR        3,4     4096    1864577 /etc/apache2
lsof      7409       root  cwd       DIR        3,4     4096    1864577 /etc/apache2
grep      7410     adrian  cwd       DIR        3,4     4096    1864577 /etc/apache2
lsof      7411       root  cwd       DIR        3,4     4096    1864577 /etc/apache2

I assume that this is fine

3) adrian@ablinx1:/etc/apache2$ lsof -i tcp:80
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
firefox-b 7115 adrian   44u  IPv4  55278       TCP ablinx1.local:38550->84.53.137.49:www (ESTABLISHED)
firefox-b 7115 adrian   45u  IPv4  55284       TCP ablinx1.local:38551->84.53.137.49:www (ESTABLISHED)

Well I am using firefox to post this!

4) adrian@ablinx1:/etc/apache2$ sudo netstat -lnp | grep '0.0.0.0:80'
adrian@ablinx1:/etc/apache2$ 
So no output from netstat

5) adrian@ablinx1:/etc/apache2$ netstat -na | grep LISTEN | grep 80
produced no output

6) adrian@ablinx1:/etc/apache2$ sudo netstat -an --program | grep 80

This showed many lines of the type:
tcp        0      0 192.168.0.3:38230       72.14.207.191:80        ESTABLISHED7115/firefox-bin

and also:

tcp        0      0 192.168.0.3:35744       168.75.68.97:80         TIME_WAIT  -                   
tcp        0      0 192.168.0.3:53877       216.239.122.227:80      TIME_WAIT  -                 

However I do not know the significance of TIME_WAIT above. 

7) adrian@ablinx1:/etc/apache2$ sudo `which apache2ctl` fullstatus
w3m: Can't load [http://localhost:80/server-status](http://localhost:80/server-status).

Any help on the above would be most welcome. 

TIA, Adrian Birch

---

