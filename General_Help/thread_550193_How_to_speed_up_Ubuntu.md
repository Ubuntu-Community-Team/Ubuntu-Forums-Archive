---
title: "How to speed up Ubuntu"
date: 2007-09-13
forum: General Help
---

### Post by lamar_air on 2007-09-13
I've got ubuntu feisty loaded on an AMD 2200+ box with only 256mb or ram.  It seems to be slow sometimes bringing up a terminal window or folder browsers, etc.  It's a fresh install with 512mb swap.  I'm not using beryl or compiz.

I'm wondering if there are any background processes I can terminate to help speed things up?
Are there any other optimizations I can do to increase performance?

The systems only used for the net and word processing.

Thanks

---

### Post by r4ik on 2007-09-13
Maybe this might help,

[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

A bit more ram would not hurd also :)

---

### Post by tlacuache on 2007-09-13
Use Xubuntu. Its window manager and file manager are more lightweight. I've got a similar box which is running Xubuntu quite nicely.

-SG

---

### Post by rsambuca on 2007-09-13
I also find 256 a little tight for regular ubuntu.  Xubuntu will take a little less resources without losing much at all in terms of functionality.  As an alternative, you can do a minimal installation and just add the programs you want.  It is actually very easy to set up and you will find it much quicker than regular ubuntu.  Psychocats has an excellent tutorial for this.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by stchman on 2007-09-13
> **lamar_air said:**
> I've got ubuntu feisty loaded on an AMD 2200+ box with only 256mb or ram.  It seems to be slow sometimes bringing up a terminal window or folder browsers, etc.  It's a fresh install with 512mb swap.  I'm not using beryl or compiz.

I'm wondering if there are any background processes I can terminate to help speed things up?
Are there any other optimizations I can do to increase performance?

The systems only used for the net and word processing.

Thanks

I would install another 256MB.  256MB is the bare minimum for Ubuntu.

---

### Post by HermanAB on 2007-09-13
1. Add more RAM
2. Check the speed of your DNS using 'dig' and put the fastest one at the top in /etc/resolv.conf:
dig @dns.ip.add.ress [www.yahoo.com](www.yahoo.com)

Internet slowness is usually due to DNS lag time.  For ultimate speed, install a BIND slave on your machine.

Cheers,

H.

---

### Post by fragos on 2007-09-13
More RAM is the way to go.  You can run "free" in a terminal to see the status of memory useage.  Check the swap space used.  The less swap you use the faster your system will respond to opening new applications.  A total of 512 will yield much improved performance.  With my usage paterns, I found that with 1GB I vertualy never use swap.  I recommend you buy two matching 512 simms.  As well as 1GB your memory access perfoms increases by 10% with a pair of matching simms.

---

### Post by misfitpierce on 2007-09-13
Xubuntu prob better for ram described. XFCE interface is much lighter.

---

### Post by stinger30au on 2007-09-13
definately add more ram, if you can add an extra 512meg on what you have got, it will take off in a big way

---

### Post by lamar_air on 2007-09-14
Thanks for the good points of advice everyone.

---

### Post by gundumfx on 2007-09-14
well try  this web 
or link 
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)
this might help well if you want to make ubuntu faster get a  better prosser an more ram because i have a 2gb of ram an i got like 2 hd with 200 gb for each of um

---

### Post by mojoman on 2007-09-14
Xfce is good as desktops come and go (it's my personal favorite) but with that amount of ram you'd be better off with a window manager instead. I'd recommend a xubuntu-server install and then just add x-server, a wm (fluxbox is my favorite, really fast and light and very configurable) and if you want a graphical login I'd add that as well. You got the one used by gnome and xfce in the repos (gde I think it's called) and there is another one called slim as well but I don't think that's available for feisty (though it's in gutsy's repos). Check out psychocat's website that was recommended earlier on, you'll find some good tips there but I'd go for a vm instead of a desktop.

/mojoman

---

### Post by RedSquirrel on 2007-09-14
> **mojoman said:**
> if you want a graphical login I'd add that as well. You got the one used by gnome and xfce in the repos (gde I think it's called) 

gdm ;)

OP: Here's another link that might help:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by mojoman on 2007-09-14
> **RedSquirrel said:**
> gdm ;)


oops:oops:

Edit: maybe for the better, slim is less bloatware ;-)

---

### Post by John.Michael.Kane on 2007-09-14
This may help.
[Howto: Set up Feisty for speed.]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/")

---

### Post by Warren Watts on 2007-09-20
> **HermanAB said:**
> 1. Add more RAM
2. Check the speed of your DNS using 'dig' and put the fastest one at the top in /etc/resolv.conf:
dig @dns.ip.add.ress [www.yahoo.com](www.yahoo.com)
Internet slowness is usually due to DNS lag time.  For ultimate speed, install a BIND slave on your machine.


I was recenty experiencing similar slow DNS lookups, and your suggestion worked GREAT! 

I wrote a handy Perl script that extracts the DNS servers from /etc/resolv.conf, tests them with dig, then displays the results fastest to slowest...

The perl code is listed below along with sample output, and I attached the Perl script as a tarball to this post. 

```
#!/usr/bin/perl 

######################################################################################
# scan_dns.pl version 0.7 9/20/07
# Author: Warren Watts (kingbeetle_66(at)yahoo(dot)com

# This program will analyze the relative speeds of each of the DNS servers
# detected by dhcpcd (DHCP client daemon) through use of dig (a DNS lookup utility)
# and display a sorted list of DNS servers from fastest to slowest.
# This sorted list can then be used to tweak the /etc/resolv.conf file, providing
# faster DNS lookups while browsing, etc.
 
# I included three domains for dig to lookup.  They are stored in @domain_list.
# Feel free to add to the list or change the domain list to any domains you wish.
# Be aware that the more domains in the list, the longer the scan will take!
#######################################################################################

use strict;

my (@DNS,$IP,$time,$domain,$dig,%time,$key);

# Read the DNS list from /etc/resolv.conf and store the list in an array
my $resolv = `cat /etc/resolv.conf`;
while ($resolv =~ /nameserver (.*)\n/g) {push(@DNS,$1)}

#List the DNS servers listed in /etc.resolv.conf
print "+----------------------------------------------------------------------+\n";
print "The following DNS servers are listed in /etc/resolv.conf:\n";
foreach $IP (@DNS) {print "$IP\t"}
print "\n";

# Store list of domains to be looked up by dig in an array
my @domain_list = ('www.yahoo.com' ,'www.fasthit.net' ,'zz.nullwave.ru');

# List the domains to be used by dig during the scan
print "The following domains will be for this scan:\n";
foreach $domain (@domain_list) {print "$domain\t"}
print "\n";
print "+----------------------------------------------------------------------+\n";

# Count number of domains stored in the array
my $domain_count = @domain_list; 
# Go through the list of DNS servers and execute dig for each DNS server and each  
# domains in the domain list, extract the time taken and average the times together,
# then store the DNS and averaged time in a hash.
foreach $IP (@DNS) 
{
  print "Scanning $IP\n";
  $time = '';
  foreach $domain (@domain_list)
  {
    print "-->  $domain\n";
    $dig = `dig \@$IP $domain`;
    if ($dig =~ /Query time: (.*) msec/) 
    {
      $time = $time + $1;
    }
  }
  $time{$IP} = int(($time / $domain_count) +0.5);
}
print "+----------------------------------------------------------------------+\n";

# Display the results sorted by time in ascending order
foreach my $key (sort hashValueAscendingNum (keys(%time))) 
 {
  print "Average fetch time for $key : $time{$key}\n";
}

# Subroutine to sort by time rather than by DNS address
sub hashValueAscendingNum 
{
   $time{$a} <=> $time{$b}
}

```

Sample output:
> [root@arch warren]# perl scan_dns.pl
+----------------------------------------------------------------------+
The following DNS servers are listed in /etc/resolv.conf:
64.233.222.2    192.168.1.254   64.233.222.7
The following domains will be for this scan:
[www.yahoo.com](www.yahoo.com)   [www.fasthit.net](www.fasthit.net) zz.nullwave.ru
+----------------------------------------------------------------------+
Scanning 64.233.222.2
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
Scanning 192.168.1.254
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
Scanning 64.233.222.7
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
+----------------------------------------------------------------------+
Average fetch time for 64.233.222.2 : 10
Average fetch time for 192.168.1.254 : 3820
Average fetch time for 64.233.222.7 : 4066

---

### Post by fragos on 2007-09-20
My thanks to Warren.  I just had to try the script and it works well.

---

