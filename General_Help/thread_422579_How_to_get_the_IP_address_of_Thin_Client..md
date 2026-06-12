---
title: "How to get the IP address of Thin Client."
date: 2007-04-25
forum: General Help
---

### Post by tin_truc22 on 2007-04-25
I'm using Edubuntu. I want to install iTalc. But the version include edubuntu doesn't work (i don't know how to make it work).I have compiled the new version of iTalc and there are a code to Start iTalc when Thin Client is starting up. 
```
#!/usr/bin/perl -w
#
#
# written by Patrick Winnertz 11.12.05
# licensed under GPL2+
#
use Socket;
use strict;
#Figure out your DISPLAY
my $display = $ENV{'DISPLAY'};
#Delete :* at the end of the string
my $displayname = $display ;
$display =~s/:[^:]*$//;
my $log = $display ;
my $address = 0;
#if this script is started on the server $address is empty:
my $port = 11000;
if (length($display) > 0) {
        #convert name into ipaddress
        $address = inet_ntoa(inet_aton($display));
        #Save only the last part (yyy) of the IP: xx.xx.xx.yyy
        $address =~ s/(\d*).(\d*).(\d*).(\d*)/$4/;
        #Set the port:
        my $IVSBASEPORT = 11000;
        my $ISDBASEPORT = 11400;
        $ivsport = $BASEPORT+$address;
        $isdport = $BASEPORT+$address;
}
#Finally start ICA:
system("/usr/bin/ica -noshm -rfbport $port -display $displayname  &");



```
"$address = inet_ntoa(inet_aton($display))" has value 127.0.0.1. But when boot LTSP the Ip of the network card is 192.168.0.250. I use ifconfig to get out the IP but this is the IP of the Server's network card.
Are there someone to help me install and using iTalc or let me how to get the IP address of Thin Client.
Sorry 4 my bad English.

---

### Post by tin_truc22 on 2007-04-30
Up.

---

### Post by kaingeo on 2008-07-17
The same problem here! 
you can get the ip address of the client in the right bottom corner of the ldm boot screen (the screen you log in).

The problem is that when i make a new computer in iTalc that ip address doesnt work either.
The only ip address which worked was my ip!

I use the default iTalc 1.0.7 from edubuntu addon cd.

---

