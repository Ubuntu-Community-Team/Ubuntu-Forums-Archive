---
title: "RSYSLOG rules not working"
date: 2015-09-03
forum: General Help
---

### Post by amish_otaku on 2015-09-03
I've got a RSYSLOG mysql server and a client that I am trying to get working properly. I cannot get the rules to work however. I am wanting to for instance drop all messages of security.info, auth.info, news, mail, and kern.debug, but I can't figure out how to write the rules and get them to take effect. They simply will not ignore the messages. 

[ATTACH=CONFIG]264208[/ATTACH]

So I want to ignore this message from my central server. No matter if I add the rules to the server or the client. still the messages persist. Can anyone provide some insight to this as all the documentation is laughably terrible and unhelpful. Thank you.

---

### Post by Habitual on 2015-09-03
> **amish_otaku said:**
> No matter if I add the rules to the server or the client. still the messages persist. Show us these rules you have tried please.
And identify each as 'server' or 'client', and its path and file name.
 Thank you.

---

### Post by amish_otaku on 2015-09-03
MYSQL SERVER
IP 172.31.0.184

```

#  /etc/rsyslog.conf    Configuration file for rsyslog.#
#            For more information see
#            /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################


$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support
#$ModLoad immark  # provides --MARK-- message capability


# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514


# provides TCP syslog reception
$ModLoad imtcp
$InputTCPServerRun 514


# Enable non-kernel facility klog messages
$KLogPermitNonKernelFacility on


###########################
#### GLOBAL DIRECTIVES ####
###########################


#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
#$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat
$ActionQueueType LinkedList # use asynchronous processing


$ActionQueueFileName dbq # set file name, also enables disk mode


$ActionResumeRetryCount -1 # infinite retries on insert failure


# Filter duplicated messages
$RepeatedMsgReduction on


#
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog


#
# Where to place spool and state files
#
$WorkDirectory /var/spool/rsyslog


#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf
*.*       :ommysql:127.0.0.1,Syslog,rsyslog,rsyslog
$AllowedSender TCP,127.0.0.1, 172.31.0.0/24

```

10-rsyslog-rules.conf
```

*.info;mail.none;authpriv.none;cron.none;security.info      /var/log/messages

```

SYSLOG CLIENT
IP: 172.31.0.147
```

#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#                       For more information see
#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html




#################
#### MODULES ####
#################


$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support
#$ModLoad immark  # provides --MARK-- message capability


# provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514


# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514




###########################
#### GLOBAL DIRECTIVES ####
###########################


#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat


#
# Set the default permissions for all log files.
#
$FileOwner root
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022


#
# Where to place spool and state files
#
$WorkDirectory /var/spool/rsyslog


#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf




###############
#### RULES ####
###############


###############
### LOGSERV ###
###############
*.*  @@172.31.0.184




```

10-rsyslog-rules.conf
```

if $syslog-severity >= '4' then /dev/null
& stop

```

---

### Post by Habitual on 2015-09-03
> **amish_otaku said:**
> 
10-rsyslog-rules.conf
```

if $syslog-severity >= '4' then /dev/null
& stop

```

Sorry, that's not correct for rsyslog. 

Try
```
if $syslog-severity >= '4' then ~
& stop
```in 10-rsyslog-rules.conf

don't forget to restart rsyslog on the same host.

Let us know.

You can watch traffic on the same machine as 10-rsyslog-rules.conf
using 
```
tcpdump -nn -i eth1 dst 172.31.0.184 and port 514
```

---

### Post by amish_otaku on 2015-09-03
I made a slight change to your suggestion as I had the keyword wrong. it should be $syslogseverity instead of what I had listed. I also did find a way to to change how it dumps to the server in modifying the *.* @@172.31.0.184 to *.error @@172.31.0.184

The end result isn't quite what I was wanting to do, but it does work. I think I can see how to make it do what I want to do using more advanced rules syntax.

---

### Post by Habitual on 2015-09-03
> **amish_otaku said:**
> I made a slight change to your suggestion as I had the keyword wrong. it should be $syslogseverity instead of what I had listed. I also did find a way to to change how it dumps to the server in modifying the *.* @@172.31.0.184 to *.error @@172.31.0.184I'd be disappointed if you didn't make change to my suggestion, or at least try and you showed some initiative. Good Job. Well done. Even if "partial"
@@ = tcp
@ = udp
and you have both 'open'
> **amish_otaku said:**
> MYSQL SERVER
IP 172.31.0.184
```

$UDPServerRun 514
$InputTCPServerRun 514

```
Is that intentional?

> **amish_otaku said:**
> The end result isn't quite what I was wanting to do, but it does work. I think I can see how to make it do what I want to do using more advanced rules syntax.But it's working, 'sorta'. :)
I have every confidence you will be okay.

I also notice your graphic shows Facility = "SECURITY". Where'd that come from?

---

### Post by amish_otaku on 2015-09-04
Sorry I perhaps explained it wrong. I simply changed the word from "$syslog-severity" to "$syslogseverity" as I had it wrong after re-consulting the documentation at the rsyslog site. The TCP and UDP setup was accidental as I had just followed a generic guide to get it running on mysql. I will change it to be TCP only as I'm not so much concerned about the slight protocol overhead with regards to TCP vs UDP.

While I was originally waiting to hear back from you with regards to the first reply was when I was continuing to play around with different ways to try  and get it to work. That was when I tried the *.error as an alternative to the main *.* that I had posted to the original *.conf.

With regards to the original intent of this FORUM post was that I was trying to figure out how to Slice and Dice on the logs that were sent to the server or at least how to filter some out without resorting to the base ":msg, contains, "SOME INFO HERE"" I was trying to make it slightly more elegant and refined.

---

### Post by Habitual on 2015-09-04
It took me a couple of days to get a functioning setup going also.
Most of it was concepts and keywords and construction of rsyslog elements.

Mad respect for using 
> **amish_otaku said:**
> MYSQL SERVER
IP 172.31.0.184

```

$AllowedSender TCP,127.0.0.1, 172.31.0.0/24

```

---

### Post by amish_otaku on 2015-09-04
Better to be over secured than over exploited. Perhaps you would be willing to share some of your settings so that I can maybe further my own configuration and customization. I would love to increase both the customization and usefulness of the setup. I am trying to use one of my RPI2's as a security CAM and would love to have a central logging aspect hence the RSYSLOG config and such.

---

### Post by amish_otaku on 2015-09-04
I just realized that graphic you were referring to and I hadn't told you where it was from. That particular one was from the client machine and was triggered because I was SSH'ing to the machine and was wanting to suppress those messages from flooding the log.

---

### Post by Habitual on 2015-09-04
> **amish_otaku said:**
> Perhaps you would be willing to share some of your settings so that I can maybe further my own configuration and customization.
Not a problem. But let me explain my setup. I used to use rsyslog to forward my apache access and error logs to another host to be processed by logstash, used in what is called an "ELK stack". (Elasticsearch, Logstash, and Kibana).
When my Kibana3 took a dump, I stepped up my game and installed and configured logstash-forwarder to send the same two apache log files.

I have archives of my rsyslog setups that you are welcome to. There are all very plain and wholly taken from examples found from search engine results.
I haven't a need for using rsyslog forwarded stuff anymore, Thankfully.

If you want the setup details for my former arrangement, shoot me a PM and I'll stick up in a pastie somewhere, or whatever is clever.
If you're intested in the ELK stack, well, I got mine up and running from examples found from search engine results. ;)
And Kibana4 is far easier to install/setup/get going than Kibana3 was.

Peace.

[URL="http://ubuntuforums.org/private.php?do=newpm&u=504341"]
[/URL]

---

### Post by amish_otaku on 2015-09-08
I am looking into the ELK stack now. Rsyslog seems like a decent system to setup, but it's really hit or miss when it comes to getting the relevant info that I want. It's kind of inflexible when it comes to getting this thing working 100% without issues

---

### Post by Habitual on 2015-09-08
> **amish_otaku said:**
> it's really hit or miss when it comes to getting the relevant info that I want. It's kind of inflexible when it comes to getting this thing working 100% without issues Define "relevant info" please. Kibana[4] is perfect for creating relevant info!

I tried to stick with 'defaults' and it took me a while to learn which files to edit and where (and on what host!?!) Yikes.
Well. Rsyslog over udp to a central log host. udp packets with rsyslog is not the 'recommended' way, as they tell us that udp packets can get 'lost',
or am I caffeine deficient again this morning? Read something like that...

```
$InputTCPServerRun 514
*.error @@172.31.0.184
```

the 514 port *I think*? is assumed on either tcp or udp.

If you hate looking at system logs, and only want to 'search once' in one place, you'll love Kibana. ;)
Good job so far.

Subscribed with interest.

---

### Post by amish_otaku on 2015-09-08
The Double @@ specifies TCP only. I am just not a fan of how rsyslog handles everything from configuration to implementation. I will attempt to get an ELK stack setup and try to play around with it so that I can hopefully get more usable info instead of the normal uninteresting stuff.

---

### Post by Habitual on 2015-09-08
No worries.
If you get sideways somewhere, I believe you can [PM]("http://ubuntuforums.org/private.php?do=newpm&u=504341") me.
and if not, fire away. There are way smarter folks here than myself.

Sometimes, I'm surprised my own stuff works!

---

