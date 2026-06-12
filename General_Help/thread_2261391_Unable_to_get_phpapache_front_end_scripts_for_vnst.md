---
title: "Unable to get php/apache front end scripts for vnstat to work"
date: 2015-01-18
forum: General Help
---

### Post by davaweb on 2015-01-18
Ubuntu 1404
vnstat (works well)
php5
apache2

I have installed vnstat and am trying to get the graphical front end to work.
I followed these instructions:
 [http://www.upubuntu.com/2011/09/vnstat-console-and-graphical-network.html](http://www.upubuntu.com/2011/09/vnstat-console-and-graphical-network.html)

As I received the message it could not resolve my domain name I followed the last reply in this post 
[http://askubuntu.com/questions/454497/apache2-could-not-reliably-determine-the-servers-fully-qualified-domain-name](http://askubuntu.com/questions/454497/apache2-could-not-reliably-determine-the-servers-fully-qualified-domain-name)
 and changed my hosts file to read:

> 127.0.0.1    localhost
127.0.1.1    ubuntuwork.anydomain.com    ubuntu-140401B

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Also, I did 
> sudo ufw allow 80
though I never touch ufw - I assume it runs by itself?

When I try to run the interface, using:
[http://localhost/vnstat/](http://localhost/vnstat/) (same as [http://localhost:80/vnstat](http://localhost:80/vnstat))
or
[http://127.0.0.1/vnstat/](http://127.0.0.1/vnstat/)
or
[http://127.0.1.1/vnstat/](http://127.0.1.1/vnstat/)
or
[http://192.168.x.x/vnstat/](http://192.168.x.x/vnstat/)

I get:
Not Found

The requested URL /vnstat/ was not found on this server.
Apache/2.4.7 (Ubuntu) Server at localhost Port 80
or
Apache/2.4.7 (Ubuntu) Server at 127.0.0.1 Port 80
or
Apache/2.4.7 (Ubuntu) Server at 127.0.1.1 Port 80
or
Apache/2.4.7 (Ubuntu) Server at 192.168.x.x Port 80


I would really appreciate any help - many thanks.
David

---

### Post by Doug S on 2015-01-18
In that link you provided, where it says this:```
2. Run now this command:

cd /var/www

3. Inside this folder (/var/www) run these commands to download and unpack the script files (root permissions required):
```Do this instead:```
2. Run now this command:

cd /var/www[COLOR=#ff0000]/html[/COLOR]

3. Inside this folder (/var/www[COLOR=#ff0000]/html[/COLOR]) run these commands to download and unpack the script files (root permissions required):
```Why? Because the default document root location changed very late in the 14.04 release cycle.

---

### Post by davaweb on 2015-01-18
Many thanks Doug S,

It's got me closer, but:
> sudo wget [http://www.sqweek.com/sqweek/files/vnstat_php_frontend-1.4.1.tar.gz](http://www.sqweek.com/sqweek/files/vnstat_php_frontend-1.4.1.tar.gz) I received: > unable to resolve host ubuntu-140401B

The output of the commmands was:[HTML]david@ubuntu-140401B:~$ cd /var/www/html
david@ubuntu-140401B:/var/www/html$ sudo wget http://www.sqweek.com/sqweek/files/vnstat_php_frontend-1.4.1.tar.gz
sudo: unable to resolve host ubuntu-140401B
[sudo] password for david: 
--2015-01-19 10:00:36--  http://www.sqweek.com/sqweek/files/vnstat_php_frontend-1.4.1.tar.gz
Resolving www.sqweek.com (www.sqweek.com)... 164.138.27.72
Connecting to www.sqweek.com (www.sqweek.com)|164.138.27.72|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 57226 (56K) [application/x-gzip]
Saving to: 'vnstat_php_frontend-1.4.1.tar.gz’

100%[======================================>] 57,226      79.8KB/s   in 0.7s   

2015-01-19 10:00:38 (79.8 KB/s) - 'vnstat_php_frontend-1.4.1.tar.gz’ saved [57226/57226]

david@ubuntu-140401B:/var/www/html$ sudo tar xvzf vnstat_php_frontend-1.4.1.tar.gz
sudo: unable to resolve host ubuntu-140401B
vnstat_php_frontend-1.4.1/
vnstat_php_frontend-1.4.1/config.php
vnstat_php_frontend-1.4.1/graph.php
vnstat_php_frontend-1.4.1/vnstat_red.css
vnstat_php_frontend-1.4.1/VeraBd.ttf
vnstat_php_frontend-1.4.1/COPYING
vnstat_php_frontend-1.4.1/index.php
vnstat_php_frontend-1.4.1/vnstat.css
vnstat_php_frontend-1.4.1/graph_svg.php
vnstat_php_frontend-1.4.1/vera_copyright.txt
vnstat_php_frontend-1.4.1/vnstat.php
vnstat_php_frontend-1.4.1/README
david@ubuntu-140401B:/var/www/html$ 
david@ubuntu-140401B:/var/www/html$ sudo mv vnstat_php_frontend-1.4.1 vnstat
sudo: unable to resolve host ubuntu-140401B
david@ubuntu-140401B:/var/www/html$[/HTML]


When I ran it in the browser, The output was: > \n"; foreach ($iface_list as $if) { print "
"; if (isset($iface_title[$if])) { print $iface_title[$if]; } else { print $if; } print "

    \n"; foreach ($page_list as $pg) { print "
    ".$page_title[$pg]."
    \n"; } print "

\n"; } print "\n"; } function kbytes_to_string($kb) { $units = array('TB','GB','MB','KB'); $scale = 1024*1024*1024; $ui = 0; while (($kb < $scale) && ($scale > 1)) { $ui++; $scale = $scale / 1024; } return sprintf("%0.2f %s", ($kb/$scale),$units[$ui]); } function write_summary() { global $summary,$top,$day,$hour,$month; $trx = $summary['totalrx']*1024+$summary['totalrxk']; $ttx = $summary['totaltx']*1024+$summary['totaltxk']; // // build array for write_data_table // $sum[0]['act'] = 1; $sum[0]['label'] = 'This hour'; $sum[0]['rx'] = $hour[0]['rx']; $sum[0]['tx'] = $hour[0]['tx']; $sum[1]['act'] = 1; $sum[1]['label'] = 'This day'; $sum[1]['rx'] = $day[0]['rx']; $sum[1]['tx'] = $day[0]['tx']; $sum[2]['act'] = 1; $sum[2]['label'] = 'This month'; $sum[2]['rx'] = $month[0]['rx']; $sum[2]['tx'] = $month[0]['tx']; $sum[3]['act'] = 1; $sum[3]['label'] = 'All time'; $sum[3]['rx'] = $trx; $sum[3]['tx'] = $ttx; write_data_table('Summary', $sum); print "
\n"; write_data_table('Top 10 days', $top); } function write_data_table($caption, $tab) { print "\n"; print "\n"; print ""; print ""; print ""; print ""; print ""; print "\n"; for ($i=0; $i"; print ""; print ""; print ""; print ""; print "\n"; } } print "
$caption     In    Out    Total
$t    $rx    $tx    $total
\n"; } validate_input(); get_vnstat_data(); // // html start // header('Content-type: text/html; charset=utf-8'); print ''; ?>
Traffic data for
\n"; } else { print "\"graph\"/\n"; } if ($page == 's') { write_summary(); } else if ($page == 'h') { write_data_table('Last 24 hours', $hour); } else if ($page == 'd') { write_data_table('Last 30 days', $day); } else if ($page == 'm') { write_data_table('Last 12 months', $month); } ?>
vnStat PHP frontend 1.4.1 - ©2006-2008 Bjorge Dijkstra (bjd _at_ jooz.net)

In /var/www there is a folder vnstat_php_frontend-1.5.1. It is not in /var/html   - should it be? If so should I simply move it or re-install from scratch?

I'm confused why it can't resolve host ubuntu-140401B


Thank you for your help and explaining - I learn more that way than by just copying and pasting! ;)
David

---

### Post by Doug S on 2015-01-18
> **davaweb said:**
> In /var/www there is a folder vnstat_php_frontend-1.5.1. It is not in /var/[COLOR=#ff0000]www/[/COLOR]html   - should it be? If so should I simply move it or re-install from scratch?

I'm confused why it can't resolve host ubuntu-140401BI would try to just move it. If that doesn't work start from scratch. If that doesn't work, you could also just change document root back to /var/www. I guess you need to make an entry for ubuntu-140401B. All of my computers resolve via my internal DNS. You should be able to do it via the hosts file (I think). Example for mine:```
doug@s15:~$ [COLOR=#ff0000]host s15[/COLOR]
s15.smythies.com has address 192.168.111.112
```

---

### Post by davaweb on 2015-01-20
Apologies for the days to reply - I had to re-install the system.

I haven't improved the situation.

My hosts file now is: > 127.0.0.1    localhost
127.0.1.1    ubuntu-140401B.dnr.com    ubuntu-140401B
192.168.1.2    ubuntu-140401B.dnr.com    ubuntu-140401B

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters]

apasche2, php5 php5-gd installed without error.

It doesn't seen to matter where I put 'vnstat_php_frontend-1.5.1' - in /var/www/vnstat or  /var/www/html/vnstat.

The **only **way of getting anything is by using[http://ubuntu-140401b]("http://<strong>ubuntu-140401b</strong>")/vnstat/
Is there something wrong with the hosts file?

The attached screenshot shows the output is obviously not picking up the graphics interrface.

config.php is:[HTML]<?php
    //
    // vnStat PHP frontend (c)2006-2010 Bjorge Dijkstra (bjd@jooz.net)
    //
    // This program is free software; you can redistribute it .....
    ...
    // for more information.
    //
    error_reporting(E_ALL | E_NOTICE);

    //
    // configuration parameters
    //
    // edit these to reflect your particular situation
    //
    $locale = 'en_US.UTF-8';
    $language = 'en';

    // list of network interfaces monitored by vnStat
    $iface_list = array('eth0');

    //
    // optional names for interfaces
    // if there's no name set for an interface then the interface identifier
    // will be displayed instead
    //    
    $iface_title['eth0'] = 'Internal';
    $iface_title['sixxs'] = 'SixXS IPv6';

    //
    // There are two possible sources for vnstat data. If the $vnstat_bin
    // variable is set then vnstat is called directly from the PHP script
    // to get the interface data. 
    //
    // The other option is to periodically dump the vnstat interface data to
    // a file (e.g. by a cronjob). In that case the $vnstat_bin variable
    // must be cleared and set $data_dir to the location where the dumps
    // are stored. Dumps must be named 'vnstat_dump_$iface'.
    //
    // You can generate vnstat dumps with the command:
    //   vnstat --dumpdb -i $iface > /path/to/data_dir/vnstat_dump_$iface
    // 
    $vnstat_bin = '/usr/bin/vnstat';
    $data_dir = './dumps';

    // graphics format to use: svg or png
    $graph_format='svg';
    
    // Font to use for PNG graphs
    define('GRAPH_FONT',dirname(__FILE__).'/VeraBd.ttf');

    // Font to use for SVG graphs
    define('SVG_FONT', 'Verdana');

    // Default theme
    define('DEFAULT_COLORSCHEME', 'light');

?>[/HTML]

David

---

