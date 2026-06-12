---
title: "BIND9: Need help specifying a large amount of IP addresses"
date: 2017-03-29
forum: General Help
---

### Post by justin.powers on 2017-03-29
Pretty new to BIND DNS.  I've got one server configured for 2 sets of IP's but now there's a new requirement for a bunch more IPs.  I was hoping there was an easier way to input the information into the forward and reverse lookup files.

So, for example ( These are not the real IP's ):

I have -
 192.168.1.0/28          company01.domain.com
192.168.1.16/28        company02.domain.com


So the records look something like this (Just a very basic format and not really what it looks like ):

192.168.1.0      "FQDN"
192.168.1.1      "FQDN"
192.168.1.2      "FQDN"

etc etc

I can do forward and reverse lookups for those 2 ranges.  However, now there's at least 2000 more IP's I have to put into the DNS records.  I was hoping there was a way I could specify something like this:  

192.168.1.0/28   "FQDN
192.168.2.0/24   "FQDN"
192.168.3.0/22   "FQDN"



So basically use CIDR notation instead of having to manually list out every single IP address and map that IP address to the FQDN.  

Hope that makes sense.  Thanks!

---

### Post by SeijiSensei on 2017-03-29
Nope, A records pertain to individual hosts, not ranges.

This is the kind of task where a computer comes in handy.  Write a script to iterate over the hosts in a given subnet and generate the A and PTR records.  Here's a start using PHP, though most any language or bash could be used:
```

#!/usr/bin/php
<?
# company number for companyNN.example.com
$cn="01";

# where to put the records
$a_recs="/path/to/a_records.txt";
$p_recs="/path/to/ptr_records.txt";
$ap=fopen($a_recs,"w+");
$pp=fopen($p_recs,"w+");

for ($i=1; $i<15; $i++) 
     if($i<10) { $ii="0$i"; } else { $ii="1$1";}
     fwrite($ap,"host$ii\tIN\tA\t192.168.0.$i\n");
     fwrite($pp,"$i\tIN\tPTR\t$host$ii.company$cn.example.com\n");
}
fclose($ap);
fclose($pp);
?>

```
That writes records like
```
host01     IN     A     192.168.0.1
```
and
```
1     IN     PTR     host01.company01.example.com.
```
to their respective files.  This is just an idea to get you started.  You need to surround this with code to iterate over the various subnets.

Remember the first and last address in each subnet cannot be assigned to hosts.  For 192.168.0.0/28, the "network" address is 192.168.0.0, and the "broadcast address" is 192.168.0.15.  Neither of these can be assigned to hosts.  That's why I iterate from 1 to 14 in the script above.

---

