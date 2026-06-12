---
title: "set up ntp server on internal network - NO internet connection"
date: 2007-10-18
forum: General Help
---

### Post by kathys39 on 2007-10-18
I am trying to set up an ntp server on a closed, internal network - no Internet connection at all.  The packages are installed ok, just need help with setting up the server.  my ntp.conf files on the server has the following lines:

server 10.10.10.10  (my internal address)
fudge 10.10.10.10 stratum 1

When I start ntpd, it starts, but the following error message goes into the log file:
            10.10.10.10 is inapproriate adress for fudge command

It still starts anyway, but when I issue the "ntpdate -d 10.10.10.10" command from a client, it responds with 
          10.10.10.10: server dropped: strata too high
           ntpdate: no server suitable for sync found.

Iptables is wide open on both client and server, and there is no firewall.  Does anyway have any idea what I am doing wrong?

---

### Post by jmikola on 2008-03-03
I was experiencing what looks to be the same problem you were, and came across a solution.  I'll go through it in-depth, as it should address everything (I found this question through a google search, so hopefully it'll help out some others as well).

> **kathys39 said:**
> my ntp.conf files on the server has the following lines:

```
server 10.10.10.10  (my internal address)
fudge 10.10.10.10 stratum 1
```

When I start ntpd, it starts, but the following error message goes into the log file:

            ```
10.10.10.10 is inapproriate adress for fudge command
```


Firstly, you'll definitely want to resolve that error in order to get things working.  Consulting the man page for ntp.conf(5), we have:  

```
fudge 127.127.t.u [time1 sec] [time2 sec] [stratum int] [refid string]
	     [mode int] [flag1 0 | 1] [flag2 0 | 1] [flag3 0 | 1] [flag4 0 |
	     1]
	     This command can be used to configure reference clocks in special
	     ways.  It must immediately follow the server command which con-
	     figures the driver.  Note that the same capability is possible at
	     run time using the ntpdc(8) program.  The options are interpreted
	     as follows:

	     ...

	     stratum int
		     Specifies the stratum number assigned to the driver, an
		     integer between 0 and 15.	This number overrides the
		     default stratum number ordinarily assigned by the driver
		     itself, usually zero.

	     refid string
		     Specifies an ASCII string of from one to four characters
		     which defines the reference identifier used by the
		     driver.  This string overrides the default identifier
		     ordinarily assigned by the driver itself.

```

I skipped some documentation for the options that don't concern us.  The important thing to grasp is that the fudge directive need not have the same IP address as the server line.  By its nature it will apply itself to the server directive immediately preceding it (and by convention, we're required to start the IP address in the fudge directive with 127.127).  I suggest using the following server/fudge lines:

```
# Set the reference server to ourself (pretending to be a stratum 8 server)
server 127.127.1.1
fudge 127.127.1.1 stratum 8 refid NIST
```

If you ping that server IP, you'll find it goes right to the localhost.  The added benefit is that we don't have to hard-code our own IP address into ntp.conf (which might help if a local DHCP server has a habit of assigning us new IP's all the time).  Also, stratum 8 is an arbitrary assignment smack dab in the middle of the range (0 - 15), and refid tells our clients what device we're using to obtain our time value.

Lastly, I have the following lines in ntp.conf to ensure that all remote clients on my subnet have access to the server.  I also explicitly allow access from the localhost subnet, to ensure that the server can query itself.

```
# Default restrictions
restrict default notrust nomodify

# Restrict access to clients on our subnet and ourself
restrict 155.246.68.0 mask 255.255.255.0 nomodify
restrict 127.127.0.0 mask 255.255.0.0 nomodify
```

Saving these changes to ntp.conf and restart ntpd:

```
$ sudo /etc/init.d/ntp restart
```

If you attempt to query the freshly-restarted ntp server from another client, you'll likely still receive the same "Server dropped: strata too high" and "no server suitable for synchronization found" errors.  This is because the ntp server has yet to synchronize against itself.

We can either wait a "few minutes" or you can run the following two commands in a terminal to monitor the server's status:

```
$ tail -f /var/log/syslog
```

Provided you already have this running when you restart the ntp server, you'll see a block of output from ntpd telling you its start time, precision, listening interfaces, etc.  After the ntp server had been running for approximately 3 minutes (in my case), ntpd synchronized with itself and two more lines popped up in the syslog:

```
Mar  3 16:25:37 HOSTNAME ntpd[7199]: synchronized to LOCAL(1), stratum 8
Mar  3 16:25:37 HOSTNAME ntpd[7199]: kernel time sync status change 0001
```

The second command you can use to track the ntp server's initialization is:

```
$ watch ntpq -c lpee
```

The ntpq command, with said arguments, will plot a table of the server's status.  The important column to look at here will be "reach".  After resetting the ntp server, it will start at 0 and slowly climb up.  In my experience once the value hit 7, syslog reported that the ntp server had synchronized with itself.

Once the server has synchronized, you should have no problems running ntpdate on the other clients in your network.  The server's stratum should now be reported as 9, instead of 16 as it was formerly.  This is expected, because when the server syncs against itself, the fudge directive gave it a stratum of 8.  After synchronization, the stratum value is increased one notch to 9.  Ideally, this would tell us how far a particular ntp server in the real world is from an authoritative server in the first stratum - but for our purpose, the important factor is that this value is less than 16 and acceptable to the client.

> Iptables is wide open on both client and server, and there is no firewall.  Does anyway have any idea what I am doing wrong?

I realize you weren't, but in the event a firewall becomes a problem with restricting UDP port 123 used by NTP, you can use the "-u" option for ntpdate to force the query through an unprivileged port.  It likely won't be a problem on your internal network, but if you want the ntp server on your local network to synchronize manually with some external server, you might need it.

---

### Post by fozerol on 2008-03-12
excellent explanation, i was scrambling  same problem and your explanation helped me,
thanks


> **jmikola said:**
> I was experiencing what looks to be the same problem you were, and came across a solution.  I'll go through it in-depth, as it should address everything (I found this question through a google search, so hopefully it'll help out some others as well).



Firstly, you'll definitely want to resolve that error in order to get things working.  Consulting the man page for ntp.conf(5), we have:  

```
fudge 127.127.t.u [time1 sec] [time2 sec] [stratum int] [refid string]
	     [mode int] [flag1 0 | 1] [flag2 0 | 1] [flag3 0 | 1] [flag4 0 |
	     1]
	     This command can be used to configure reference clocks in special
	     ways.  It must immediately follow the server command which con-
	     figures the driver.  Note that the same capability is possible at
	     run time using the ntpdc(8) program.  The options are interpreted
	     as follows:

	     ...

	     stratum int
		     Specifies the stratum number assigned to the driver, an
		     integer between 0 and 15.	This number overrides the
		     default stratum number ordinarily assigned by the driver
		     itself, usually zero.

	     refid string
		     Specifies an ASCII string of from one to four characters
		     which defines the reference identifier used by the
		     driver.  This string overrides the default identifier
		     ordinarily assigned by the driver itself.

```

I skipped some documentation for the options that don't concern us.  The important thing to grasp is that the fudge directive need not have the same IP address as the server line.  By its nature it will apply itself to the server directive immediately preceding it (and by convention, we're required to start the IP address in the fudge directive with 127.127).  I suggest using the following server/fudge lines:

```
# Set the reference server to ourself (pretending to be a stratum 8 server)
server 127.127.1.1
fudge 127.127.1.1 stratum 8 refid NIST
```

If you ping that server IP, you'll find it goes right to the localhost.  The added benefit is that we don't have to hard-code our own IP address into ntp.conf (which might help if a local DHCP server has a habit of assigning us new IP's all the time).  Also, stratum 8 is an arbitrary assignment smack dab in the middle of the range (0 - 15), and refid tells our clients what device we're using to obtain our time value.

Lastly, I have the following lines in ntp.conf to ensure that all remote clients on my subnet have access to the server.  I also explicitly allow access from the localhost subnet, to ensure that the server can query itself.

```
# Default restrictions
restrict default notrust nomodify

# Restrict access to clients on our subnet and ourself
restrict 155.246.68.0 mask 255.255.255.0 nomodify
restrict 127.127.0.0 mask 255.255.0.0 nomodify
```

Saving these changes to ntp.conf and restart ntpd:

```
$ sudo /etc/init.d/ntp restart
```

If you attempt to query the freshly-restarted ntp server from another client, you'll likely still receive the same "Server dropped: strata too high" and "no server suitable for synchronization found" errors.  This is because the ntp server has yet to synchronize against itself.

We can either wait a "few minutes" or you can run the following two commands in a terminal to monitor the server's status:

```
$ tail -f /var/log/syslog
```

Provided you already have this running when you restart the ntp server, you'll see a block of output from ntpd telling you its start time, precision, listening interfaces, etc.  After the ntp server had been running for approximately 3 minutes (in my case), ntpd synchronized with itself and two more lines popped up in the syslog:

```
Mar  3 16:25:37 HOSTNAME ntpd[7199]: synchronized to LOCAL(1), stratum 8
Mar  3 16:25:37 HOSTNAME ntpd[7199]: kernel time sync status change 0001
```

The second command you can use to track the ntp server's initialization is:

```
$ watch ntpq -c lpee
```

The ntpq command, with said arguments, will plot a table of the server's status.  The important column to look at here will be "reach".  After resetting the ntp server, it will start at 0 and slowly climb up.  In my experience once the value hit 7, syslog reported that the ntp server had synchronized with itself.

Once the server has synchronized, you should have no problems running ntpdate on the other clients in your network.  The server's stratum should now be reported as 9, instead of 16 as it was formerly.  This is expected, because when the server syncs against itself, the fudge directive gave it a stratum of 8.  After synchronization, the stratum value is increased one notch to 9.  Ideally, this would tell us how far a particular ntp server in the real world is from an authoritative server in the first stratum - but for our purpose, the important factor is that this value is less than 16 and acceptable to the client.



I realize you weren't, but in the event a firewall becomes a problem with restricting UDP port 123 used by NTP, you can use the "-u" option for ntpdate to force the query through an unprivileged port.  It likely won't be a problem on your internal network, but if you want the ntp server on your local network to synchronize manually with some external server, you might need it.

---

