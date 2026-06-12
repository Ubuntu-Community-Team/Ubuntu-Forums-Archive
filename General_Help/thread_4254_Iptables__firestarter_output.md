---
title: "Iptables / firestarter output"
date: 2004-11-13
forum: General Help
---

### Post by ubik on 2004-11-13
hi,
I've just installed firestarter, works fine but there's something that's bugging me:
it generates lots of output on my tty's. I call it polution :-? :
```
IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:0c:31:f1:f4:54:08:00 SRC=10.51.192.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=28236 PROTO=2
IN=eth0 OUT= MAC=00:0c:76:e4:58:38:00:0c:31:f1:f4:54:08:00 SRC=81.220.186.223 DST=81.220.71.202 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=45314 DF PROTO=TCP SPT=1745 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0
and so on...
```
I just change to tty2 to have a clear screen but the "polution" followed me ](*,) 

So my question is: is there a way to redirect this output to only one tty (which i don't use, for exemple tty6) or in a log file??  (i'd prefer the tty solution because the log file may become big very quickly...)

Thanks in advance

---

### Post by ynef on 2004-11-13
I am not familiar with firestarter, but if I'm not mistaken it's a program/frontend for configuring iptables. 

What you've got there is output from your system log deamon, or syslogd for short. I suggest reading the syslog.conf manpage, which will tell you exactly what you want to know.

---

### Post by Magneto on 2004-11-13
i dont know the particulars of firestarter but there has to be a config file or script with the iptables commands you should edit the logging entries

iptables will process your script from top to bottom - what you need to do is figure out how firestarter works and find which CHAIN is logging that crap to standard output and insert something like this

```
 $IPT -t nat -I PREROUTING -p udp --dport 68 -s 172.26.120.5 -j DROP
$IPT -t nat -I PREROUTING -p udp --dport 68 -s 10.133.0.33 -j DROP
$IPT -t nat -I PREROUTING -p udp --dport 68 -s 10.136.192.1 -j DROP
```

$IPT is just iptables
- t  is for table
nat  is the CHAIN name
-I is to insert a rule
PREROUTING is used in NAT setups

-p is for protocol
udp is the protocol this rule affects

--dport is the destination port  - the port that something remotely is trying to connect with on your system

68 is the port number

-s is the source
 then you have the source IP addy or a wildcard

-j means to jump or perform an action if the packet matches what we have specified so far

DROP means drop that crap- no logging because its in the firewall script prior to the logging rules- 

basically these rules drop packet storm trash from my ISP's dns servers and they fill up my logs if I don't do this.
If you want to redirect logging youre gonna have to alter whatever rules they have setup regarding logging and remove the parts that are dumping to standard output

Its easier and better in the long run to not use crap like firestarter and just write your own script or adapt one u find on the internet IMO

---

### Post by p!=f on 2004-11-13
```

apt-cache show shorewall

```

Easy to setup, easy to maintain...

---

### Post by ynef on 2004-11-13
While doing what Magneto says will get rid of your "pollution", you will lose the logging info which could prove to be valuable to you if you get hacked. You should not disable logging completely, but perhaps you've set an option in firestarter incorrectly or something that is causing it to log ALL traffic.

If you read the manpage I suggested you will find out how to only make the really critical messages from syslogd appear on your console.

---

### Post by p!=f on 2004-11-13
```

 * 19:45:32 * pef @ agonicus *
[~] > tail -22 /etc/syslog.conf
#
# [b]I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.[/b]
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.crit;news.err;news.notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole


```

---

### Post by Magneto on 2004-11-13
i never told him to do as i do- he only posted two entries

im sure firestarter has alot of documentation on how they have logging setup someone needs to rtfm :) 
there's a firestarter script or config file somewhere with a  few lines with "--log-level" set at too high a level - 

he needs to  man iptables and man syslogd - if he knew how iptables was logging he wouldnt have posted either

i always setup a separate log for iptables- i like keeping syslog clean

---

### Post by ubik on 2004-11-13
Thank you for all your replies, i'll look at that in a moment (too hungry to do that now:))
I'll take a look at syslog conf file, that should do the trick.

by the way, is shorewall easier/better than firestarter ?? 
All those gui'ed firewall are nice but it doesn't help to understrand all iptables stuff, maybe i should build a script... yes, i'll do that, later.

---

### Post by Magneto on 2004-11-13
[QUOTE=ubik]Thank you for all your replies, i'll look at that in a moment (too hungry to do that now:))
I'll take a look at syslog conf file, that should do the trick.

by the way, is shorewall easier/better than firestarter ?? 
All those gui'ed firewall are nice but it doesn't help to understrand all iptables stuff, maybe i should build a script... yes, i'll do that, later.[/QUOTE]

If youre gonna go to a script try this one its sound  and easy to follow [http://www.linuxhelp.ca/guides/iptables/](http://www.linuxhelp.ca/guides/iptables/)

firestarter sucks- i looked at it - the rules section doesnt mention logging and the hits section makes me think it shouldnt be dumping crap to the console and it even mentions it logs everything to a separate file and not syslog-

---

### Post by ubik on 2004-11-13
After reading syslog's man page, i've modified the conf file to do what i wanted (redirect kern.warn to /dev/tty12) but that didn't change anything, seems like firestarter is overruling syslog stuff... 
Also tried this syslog-ng (i'm more familliar with it) but no changes.
I give up firestarter and start making a custom script, there's a lot of docs about such script so it shouldn't be too difficult. I always wanted to make such a script and i guess it's the moment.

---

### Post by Magneto on 2004-11-13
did u restart syslogd?

but id still suggest doin it yourself but might as well have firestarter working in the interim

---

### Post by Klibre on 2008-04-15
hi,

maybe too late but you just need to uncomment the "kernel.printk" line in the /etc/sysctl.conf (debian) ;)

need a reboot (not a networking reboot, a REAL reboot)

---

