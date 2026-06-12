---
title: "General Daemon and Logging Questions"
date: 2014-01-27
forum: General Help
---

### Post by Ackis on 2014-01-27
I'm running Ubuntu 13.10 on a headless server.  Server is primarily for media streaming but I'm using it to play around and relearn linux.

I have some questions that I haven't been able to find answers for in all my googling.  I'm not sure if it's just I'm not using the right terms, or I'm missing something that's obvious.

On to the questions:

[LIST=1]
[*]Is there a definite way to determine what programs or daemons aren't needed any longer on the system?  An example that I ran into was that I was running both ntpd and ntpdate at the same time.
[*]Similar to question 1, what about configuration files?  My goal is to keep my system "clean" and remove unneeded files/etc.
[*]I installed a program called Tiger which incorporates Tigercron.  I believe after I did this my normal cron jobs aren't running.  Is that expected behaviour?
[*]Speaking of cron, I know all cron output is logged to cron.log.  I wasn't able to find a way to log hourly/daily/etc jobs to their own file.  Is that possible?
[*]I have syslog-ng running on the system (in server mode collecting logs from a couple NASes and routers that support syslog).  I noticed rsyslog was on the system as well.  Can that be removed?
[*]I'm currently using logwatch and logrotate.  Is there a way to determine if any log files are not included in those two processes?
[*]Similar to question 6, right now I'm catching log files for programs on an ad-hoc basis.  For example program 1 will log in /opt/program 1/logs whereas program 2 logs in /var/lib/program 2/stuff/logs and program 3 logs in to /var/log.  What I've done so far is create symlinks to /var/log for program 1/2 so all logs are in one spot.  Is that a "good" behaviour to have?  Is there a way to find out where everything is being logged to so I can combine them all into a single location?
[*]I have two NAS devices, 3 Windows PC's and the Ubuntu server.  I'm currently using Samba/Windows file shares to share files between the devices.  The NASes also support NFS.  Should I have both methods enabled on the NAS devices and connect from Ubuntu to them using NFS or are the Samba shares okay?
[*]How can I log/measure system performance over time?  I found a module for webmin, however after letting it run overnight there were 100+ processes of it checking my system, which made the system unusable and unstable.
[*]I generally try to only install packages via apt-get... I've found that it makes things "cleaner" overall.  However I've found that many of those packages are out of date and I need to use something from a more current version.  Is there a simple way to "update" the package locally so I can use a later version but also use the packaged version (e.g. I update from 1.0 to 1.1 with source, and then the package gets 1.1, and eventually 1.2, I want to update with the package to 1.2)?
[*]Is there anyway to simulate a reboot without actually rebooting the system?  I have a few daemons that I think are causing problems on boot that I want to diagnose.
[*]Is there a prefered method to add a delay when starting a daemon?  I want specific daemons to wait until the NAS drives are mounted/usable before starting up.
[/LIST]

My final question has to deal with some entries in boot.log:

```

 * Starting DenyHosts denyhosts                                                                                                [ OK ]
/usr/lib/python2.7/dist-packages/pygments/plugin.py:39: UserWarning: Module cherrypy was already imported from /opt/headphones/cherrypy/__init__.pyc, but /usr/lib/python2.7/dist-packages is being added to sys.path import pkg_resources

```

My googling didn't come up with a solution to that warning.  How can I silence/configure my process properly to deal with it?

```

 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                   [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                   [fail]

```

I haven't had a whole lot of time to look into this error in the boot.log, should I be concerned?


```

Jan 23 13:54:08 Ubuntu kernel: [   24.904044] mei_me 0000:00:03.0: wait hw ready failed. status = -110
Jan 23 13:54:08 Ubuntu kernel: [   24.904091] mei_me 0000:00:03.0: hw_start failed disabling the device
Jan 23 13:54:08 Ubuntu kernel: [   24.904132] mei_me 0000:00:03.0: host is not ready.
Jan 23 13:54:08 Ubuntu kernel: [   24.904162] mei_me 0000:00:03.0: link layer initialization failed.
Jan 23 13:54:08 Ubuntu kernel: [   24.904200] mei_me 0000:00:03.0: init hw failure.
Jan 23 13:54:08 Ubuntu kernel: [   24.904473] mei_me 0000:00:03.0: initialization failed.
Jan 23 13:54:08 Ubuntu kernel: [   25.665152] CIFS VFS: Error connecting to socket. Aborting operation.
Jan 23 13:54:08 Ubuntu kernel: [   25.665285] CIFS VFS: cifs_mount failed w/return code = -101
Jan 23 13:54:08 Ubuntu kernel: [   25.667549] CIFS VFS: Error connecting to socket. Aborting operation.
Jan 23 13:54:08 Ubuntu kernel: [   25.667683] CIFS VFS: cifs_mount failed w/return code = -101
Jan 23 13:54:08 Ubuntu kernel: [   25.668441] CIFS VFS: Error connecting to socket. Aborting operation.
Jan 23 13:54:08 Ubuntu kernel: [   25.668588] CIFS VFS: cifs_mount failed w/return code = -101

```

Finally this is from my error log.  I think it has to do with the mounting of my NAS devices, but nothing I've searched for has told me if I should be worried about it, if there's something I can do to solve the problem or anything else.


Thanks for reading.

---

### Post by tomearp on 2014-01-27
Item 1: ntpdate is called once at boot to sync the system clock. You can periodically call it from a crontab, but if you want your clock to be that accurate you may as well use ntpd. Also ntpdate can result in inconsistent logs due to 'jumps' in time, ntpd uses slewing to keep the clock in sync. [See here]("https://help.ubuntu.com/lts/serverguide/NTP.html") for more info. If ntpd is running then ntpdate will be aware that it is not needed and won't make adjustments.

---

### Post by tgalati4 on 2014-01-27
For question 2:  In general, leave the configuration files in /etc alone.  You can break things if you start deleting config files without knowing what you are doing.  If you want a slim distro, then don't use Ubuntu.  It's a full-fledged operating system and it has a lot of stuff in it.

---

### Post by tomearp on 2014-01-27
Item 11: it is generally possible to enable logging with greater detail for a daemon, and a reboot is not always required. For example, with pptpd you uncomment the debug option in /etc/pptpd.conf and then restart the service; all new connections will be logged in detail, existing connections remain in place. I would suggest referring to the documentation for the daemon(s).

---

### Post by Ackis on 2014-01-27
> **tomearp said:**
> Item 1: ntpdate is called once at boot to sync the system clock. You can periodically call it from a crontab, but if you want your clock to be that accurate you may as well use ntpd. Also ntpdate can result in inconsistent logs due to 'jumps' in time, ntpd uses slewing to keep the clock in sync. [See here]("https://help.ubuntu.com/lts/serverguide/NTP.html") for more info. If ntpd is running then ntpdate will be aware that it is not needed and won't make adjustments.

What spurred me asking that question was my ntpd wasn't starting and the error log said something along the lines of can't bind to 0.0.0.0 another service is already in place.  I removed ntpdate and that error no longer appeared.

> **tgalati4 said:**
> For question 2:  In general, leave the configuration files in /etc alone.  You can break things if you start deleting config files without knowing what you are doing.  If you want a slim distro, then don't use Ubuntu.  It's a full-fledged operating system and it has a lot of stuff in it.

It's really about cleanup more-so than wanting a small distro.  The main reason for the server is a media server with the secondary benefit of being something that I can play around with and "learn".

> **tomearp said:**
> Item 11: it is generally possible to enable logging with greater detail for a daemon, and a reboot is not always required. For example, with pptpd you uncomment the debug option in /etc/pptpd.conf and then restart the service; all new connections will be logged in detail, existing connections remain in place. I would suggest referring to the documentation for the daemon(s).

I didn't even know that was an option.  Aside from disk space (which can be dealt with by logrotate) are there any downsides to leaving debug options on all the time?

---

### Post by ian-weisser on 2014-01-27
> **Ackis said:**
> 
Is there a definite way to determine what programs or daemons aren't needed any longer on the system? 

No easy way. Only research or experience.
For example, the system knows if you tell it to broadcast Avahi or CUPS services to the network, but has no way to tell if anyone is actually using those services or not.





> **Ackis said:**
> what about configuration files?  My goal is to keep my system "clean" and remove unneeded files/etc.
Ubuntu tries to provide a useful, flexible, functioning environment for most users. But that means it may include services you won't use.
Do NOT remove configuration files manually. The package manager will remove them (with the --purge flag) when you remove the appropriate package...after you figure out the correct package.



> **Ackis said:**
> I installed a program called Tiger which incorporates Tigercron.  I believe after I did this my normal cron jobs aren't running.  Is that expected behaviour?
Is it normal that cron jobs do not run? Yes, if your cron jobs are malformed, or if the applications triggered by the cron job require permissions or resources that cron cannot provide. A very common problem with users learning cron. 
Is it normal that cron fails to operate? Extremely rare.
Is it normal that you believe you changed your system? Insufficient data.




> **Ackis said:**
> Speaking of cron, I know all cron output is logged to cron.log.  I wasn't able to find a way to log hourly/daily/etc jobs to their own file.  Is that possible?
Using rsyslogd? Yes, fairly easily. See man rsyslogd.
I don't know about syslog-ng.




> **Ackis said:**
> I have two NAS devices, 3 Windows PC's and the Ubuntu server.  I'm currently using Samba/Windows file shares to share files between the devices.  The NASes also support NFS.  Should I have both methods enabled on the NAS devices and connect from Ubuntu to them using NFS or are the Samba shares okay?This seems like a matter of opinion. Both are great ways to share files.



> **Ackis said:**
> Is there anyway to simulate a reboot without actually rebooting the system?  I have a few daemons that I think are causing problems on boot that I want to diagnose.
Reproduce your system in a VM.
Or ask a more detailed question in a new thread in this forum.




> **Ackis said:**
> Is there a prefered method to add a delay when starting a daemon?  I want specific daemons to wait until the NAS drives are mounted/usable before starting up.

The preferred method is to use the Upstart configuration file properly. Simply set the start criteria for the daemon to when mounting is complete. No delay necessary.

---

### Post by tomearp on 2014-01-28
> I didn't even know that was an option. Aside from disk space (which can be dealt with by logrotate) are there any downsides to leaving debug options on all the time?

It depends how annoying you find the debug output! For example with pptpd, it is very useful for troubleshooting but rapidly overtakes everything else making the syslog difficult to read for any other purpose.

e.g:
```
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #8
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #9
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #10
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #11
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #12
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pppd[17861]: peer from calling number 92.40.248.175 authorized
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #13
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #14
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #15
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #16
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #17
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pppd[17861]: found interface eth0 for proxy arp
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pppd[17861]: local  IP address 192.168.1.53
Jan 28 09:27:34 rick-HP-Compaq-nc6220-PU982ET-ABU pppd[17861]: remote IP address 192.168.1.80
Jan 28 09:27:37 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #18
Jan 28 09:28:03 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17535]: MGR: dropped small initial connection
Jan 28 09:28:04 rick-HP-Compaq-nc6220-PU982ET-ABU pptpd[17860]: GRE: accepting packet #19
```

---

### Post by Ackis on 2014-01-28
> **ian-weisser said:**
> No easy way. Only research or experience.
For example, the system knows if you tell it to broadcast Avahi or CUPS services to the network, but has no way to tell if anyone is actually using those services or not.


What about disabling something that's "needed"?  Way back when something I was told is that "Linux is so nice, you can get it to delete itself".  Now I'm not talking about a rm -rf /.  Most likely it will come down to being pure research or experience and I've done a lot of it.  It's quite overwhelming at first.

> **ian-weisser said:**
> 
Ubuntu tries to provide a useful, flexible, functioning environment for most users. But that means it may include services you won't use.
Do NOT remove configuration files manually. The package manager will remove them (with the --purge flag) when you remove the appropriate package...after you figure out the correct package.


I was aware of the --purge flag but I forget to use it... possibly time to alias it?  I also know about clean, autoclean and autoremove but haven't found something like "auto purge" (goes back, looks at removed packages and removes the "stuff" that's been left over).  I'll have to look into that along with the idea of getting the package manager to be aware of compiled software.

> **ian-weisser said:**
> 
Is it normal that cron jobs do not run? Yes, if your cron jobs are malformed, or if the applications triggered by the cron job require permissions or resources that cron cannot provide. A very common problem with users learning cron. 
Is it normal that cron fails to operate? Extremely rare.
Is it normal that you believe you changed your system? Insufficient data.


Cron jobs that don't run will appear on the error log?  I fixed a few of my jobs that way but I've only been able to experience it by manually running cron.

> **ian-weisser said:**
> 
Using rsyslogd? Yes, fairly easily. See man rsyslogd.
I don't know about syslog-ng.


I didn't see anything myself for syslog-ng but it doesn't mean it doesn't exist.  If rsyslogd can do it,, syslog-ng should be able to as well.  That's a starting point for me to find out on my own at least (it's very frustrating searching for something only to find out that it's impossible/doesn't exist).

> **ian-weisser said:**
> 
This seems like a matter of opinion. Both are great ways to share files.


When I was originally researching this question there were some comparisons between the two... I think it was Samba was faster, NFS was more secure but the bottom line was what is easier to deal with in your network.  For me that'd be Samba but I have an issue with one of my NAS devices and "Windows Shares" (not relevant to this forum but the NAS reports block size higher than it is to make Windows writes more efficient, so the net result is that the drive is a 3TB drive and the "space on disk" is 4.5TB which causes issues for me).

> **ian-weisser said:**
> 
Reproduce your system in a VM.
Or ask a more detailed question in a new thread in this forum.


I never consider VM's.  I don't know why.  It's also the more secure way to run different services if I recall correct.

> **ian-weisser said:**
> 
The preferred method is to use the Upstart configuration file properly. Simply set the start criteria for the daemon to when mounting is complete. No delay necessary.

Again I didn't know this option existed.  When I was researching the suggested way was to add a "sleep" command in, however that became real annoying when I had to start/stop multiple times when playing with the configuration.

> **tomearp said:**
> It depends how annoying you find the debug output! For example with pptpd, it is very useful for troubleshooting but rapidly overtakes everything else making the syslog difficult to read for any other purpose.
e.g:
```
*snip log file output*
```

Thanks that confirms what I thought may be the drawbacks.

Again thank you everyone for the posts, I appreciate the advice/help/pointers/warnings. :D

---

