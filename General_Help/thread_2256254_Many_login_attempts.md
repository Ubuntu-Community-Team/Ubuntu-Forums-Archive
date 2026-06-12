---
title: "Many login attempts"
date: 2014-12-11
forum: General Help
---

### Post by ELMIT on 2014-12-11
I have installed fail2ban and it works fine.

I got since two days an invasion of failed attempt to login. Each IP will be banned now for 1 week. 

Yesterday I started to change the strategy and bann the entire class c of that IP.

Still I get every 2 to 4 minutes a new IP address from a class I have not already banned before.


I wonder if I can do something better than that, or if it is completely wrong. 
Is it possible that the attacker just can spoof their IP address and I bann unnecessary the 650 class Cs from just the last 24 hours ????

---

### Post by ELMIT on 2014-12-11
I found a solution:



While it may be nice to be able to ssh into your system from arbitrary locations on the internet, there are automated password attack systems which will lock onto an open ssh port and apply various joe account and dictionary attacks against your system. This can be aggrevating to read in your nightly log summary and is a waste of your bandwidth.

If you have a web server on the same system, you can use php and tcp wrappers to restrict ssh inbound traffic to known systems, plus give you a back-door key to permit yourself access from arbitrary systems on the internet.

Here's how you do it:

deny all ssh connections in /etc/hosts.deny:

# /etc/hosts.deny fragment
sshd:  all

Allow known systems by IP in /etc/hosts.allow, plus add a file for temporary access:

# /etc/hosts.allow fragment
sshd:  10.0.10.2     # some system
sshd:  172.99.99.99  # some other system
sshd:  /etc/hosts.allow.temporary-sshd-access

Create a php file in your web server and give it a non-obvious name like my-sshd-access.php:

<?php
function get_ip()
{
    return getenv("REMOTE_ADDR"); 
}

?>

<?php
$out='/etc/hosts.allow.temporary-sshd-access';
$log='/var/log/sshd-access-addition-log';

print "Was:";
readfile($out);
print "<br>";
$ip=get_ip();
$fp=fopen($out,"w");
fputs($fp,$ip);
fclose($fp);

$lfp=fopen($log,"a");
fputs($lfp,$ip);
fputs($lfp,"n");
fclose($lfp);

print "Wrote: ";
readfile($out);
?>

Forgive the php code -- I swiped it from somewhere else, so it could probably stand to be cleaned up a whole bunch. All it does is add the IP address of the system accessing it to the /etc/hosts.allow.temporary-sshd-access file, which is read by sshd (due to its inclusion by /etc/hosts.allow) at connection time.

Now when you are at some arbitrary system on the web and want to ssh to this system, first use a web browser and hit this file (or use wget or equivilent):

$ wget [http://your.system.name/my-sshd-access.php](http://your.system.name/my-sshd-access.php)

Now you should be able to ssh in to your system. If this is somewhere you will likely be ssh'ing in from frequently, it would be trivial to read the contents of the /etc/hosts.allow.temporary-sshd-access file and permanently add the IP address to /etc/hosts.allow.



----
I followed above way with minor changes.

Fail2Ban did not report anything anymore (the past 20 minutes!) and I hope it remains so.

---

### Post by mörgæs on 2014-12-11
Good, please mark the thread 'solved'.

---

