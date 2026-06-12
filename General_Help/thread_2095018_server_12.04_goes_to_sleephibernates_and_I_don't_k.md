---
title: "server 12.04 goes to sleep/hibernates and I don't know why"
date: 2012-12-15
forum: General Help
---

### Post by sowdust on 2012-12-15
Hi everyone,

I have an Ubuntu server at my house that I use to stream music, host my web/mail/mysql server and simple things like that.

Since a few weeks ago the computer started going off very often. Actually is not completely off since the led light is still yellow (instead of green) but I cannot wake it up from ssh nor using the usb keyboard.

I'm afraid it might be caused by an intrusion but I don't really know where to look; I have installed snort and ossec (even though ossec's interface is not working properly).

Can I please have an hint on where to start looking?

Thanks

---

### Post by Rexilion on 2012-12-15
Well, to rule out an intrusion. Why not disconnect it from the internet and see if it stays running?

This could be a kernel issue, since when did you last update?

---

### Post by sowdust on 2012-12-17
Hello, thanks for the reply and sorry for the delay, I forgot to set email notifications : )

Now the server has been up and running for a couple of days without me changing anything.

The system gets updated daily.

---

### Post by sowdust on 2012-12-21
Hello again,

after a few days of running smoothly, again this morning the system was shut down (meaning that the led light was blinking yellow instead of steady green and that the system couldn't be woken up).

Checking the log files, the shutting down seems to have happened around 9am this morning, dec 21; very strange thing (to me): kern.log jumps from dec 20 to dec 21 at 14 (when i restarted the server)

> Dec 20 15:59:31 okovita.fastwebnet.it kernel: [88673.104037] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
Dec 21 14:52:01 okovita.fastwebnet.it kernel: [    0.000000] Initializing cgroup subsys cpuset

All other log files:

sys.log: > 
Dec 21 09:09:01 okovita.fastwebnet.it CRON[26675]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Dec 21 09:17:01 okovita.fastwebnet.it CRON[26713]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: DHCPREQUEST of 192.168.1.128 on eth0 to 192.168.1.254 port 67
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: DHCPACK of 192.168.1.128 from 192.168.1.254
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: bound to 192.168.1.128 -- renewal in 849 seconds.
Dec 21 14:52:01 okovita.fastwebnet.it kernel: [    0.000000] Initializing cgroup subsys cpuset

deamon.log: > 
Dec 21 09:08:52 okovita.fastwebnet.it dhclient: bound to 192.168.1.128 -- renewal in 890 seconds.
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: DHCPREQUEST of 192.168.1.128 on eth0 to 192.168.1.254 port 67
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: DHCPACK of 192.168.1.128 from 192.168.1.254
Dec 21 09:23:42 okovita.fastwebnet.it dhclient: bound to 192.168.1.128 -- renewal in 849 seconds.
Dec 21 14:52:01 okovita.fastwebnet.it kernel:    7.769007] udevd[102]: starting version 175

mail.log: > 
Dec 21 09:17:01 okovita.fastwebnet.it postfix/pickup[26569]: 9305F4D7DD: uid=0 from=<root>
Dec 21 09:17:01 okovita.fastwebnet.it postfix/cleanup[26737]: 9305F4D7DD: message-id=<20121221081701.9305F4D7DD@mattia.xxx>
Dec 21 09:17:01 okovita.fastwebnet.it postfix/qmgr[2801]: 9305F4D7DD: from=<root@mattia.xxx>, size=1059, nrcpt=1 (queue active)
Dec 21 09:17:01 okovita.fastwebnet.it postfix/local[26739]: 9305F4D7DD: to=<root@mattia.xxx>, orig_to=<root>, relay=local, delay=0.21, delays=0.15/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Dec 21 09:17:01 okovita.fastwebnet.it postfix/qmgr[2801]: 9305F4D7DD: removed
Dec 21 14:52:09 okovita.fastwebnet.it postfix/master[1624]: daemon started -- version 2.9.3, configuration /etc/postfix

messages.log and auth.log do not contain anything of interest; as others, they stop at dec 21 around 9, when the server shut down, and then catch up at 14 when it was restarted.

I've been told by a friend who's "in the environment" that the postal police does this kind of jobs (at least in Italy).
Of course I don't do any illicit, but maybe they have noticed something strange in the streaming of movies or music or in a mail/web server within a home?

I really wouldn't know where to look, so any ideas would be much appreciated. Meanwhile, the server has just shut down :rolleyes:

After restarting, this is the content of kern.log:

> Dec 21 14:52:15 okovita.fastwebnet.it kernel: [   52.316065] device eth0 entered promiscuous mode
Dec 21 14:52:20 okovita.fastwebnet.it kernel: [   57.300603] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
Dec 21 14:52:20 okovita.fastwebnet.it kernel: [   57.314255] EXT4-fs (sdb1): recovery complete
Dec 21 14:52:20 okovita.fastwebnet.it kernel: [   57.314777] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Dec 21 15:33:40 okovita.fastwebnet.it kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 21 15:33:40 okovita.fastwebnet.it kernel: [    0.000000] Initializing cgroup subsys cpu

perhaps I should also mention that I had detected a few access attempts which I have blocked by ip.

---

### Post by Rexilion on 2012-12-21
Please, run it without an internet connection and see if it happens again. That way, we know if you are being DDOSed or are just suffering from bad hardware.

And 'detected a few access attempts which I have blocked by ip' is kind of important... Care to elaborate?

---

### Post by sowdust on 2012-12-21
Concerning ip attacks, in the log files I've seen many attempts from Chinese/Vietnamese people trying to get access with fake usernames. Also, a few weeks ago much web traffic pointed to phpmyadmin and its administration web pages.
Sometimes, in my messages.log I see this worrying line:
> device eth0 entered promiscuous mode but I don't know if it's an actual problem.

As a side note, sometimes I hear the server's fan speeding up much although the temperature is not hot (the case is open) and not much activity is shown by ps.

I am leaving for some days tomorrow and will leave the server running but unplugged to the net to be sure it's not a hardware problem.

---

### Post by Rexilion on 2012-12-22
> **sowdust said:**
> Concerning ip attacks, in the log files I've seen many attempts from Chinese/Vietnamese people trying to get access with fake usernames.

Change default ports, maybe use fail2ban? Iptables also has a 'recent' module which you could use to block requests. It creates file nodes in /proc where you can add ip addressess to with a simple:

echo +888.888.888.888 > /proc/net/xt_recent/BADGUYS

> **sowdust said:**
> Also, a few weeks ago much web traffic pointed to phpmyadmin and its administration web pages.

Make sure it's up 2 date I guess. Also, maybe it's better to introduce another layer of security as you seem to be an 'interesting target'.

> **sowdust said:**
> Sometimes, in my messages.log I see this worrying line:

> device eth0 entered promiscuous mode

but I don't know if it's an actual problem.

Could be a symptom, could be nothing. I also get that when I use tcpdump or wireshark on eth0. I think this also happens with hostapd on wlan* devices, which is used for making a wireless access point.

My point is, the message itself is not disturbing. It means that your card changes it's operational behaviour to some respect. This allows you to inspect/intercept traffic flowing through your card.

If you did not do anything at the time the message occurred, it could be an attacker that has been trying to sniff for passwords and looking for ways to crawl through your network.

> **sowdust said:**
> As a side note, sometimes I hear the server's fan speeding up much although the temperature is not hot (the case is open) and not much activity is shown by ps.

Could be a kernel bug. Could be something using CPU for a botnet.

> **sowdust said:**
> I am leaving for some days tomorrow and will leave the server running but unplugged to the net to be sure it's not a hardware problem.

I sure do hope it exhibits the same problem. Taken all the above into consideration, things look pretty disturbing :/ .

---

### Post by sowdust on 2012-12-22
Rexilon, thank you very much for the experience and insight you just shared; I will be able to put my hands on the server in about a week and see what happened meanwhile.

I guess the hardest but most important part will now be to decide the case for all those alternatives (could be a bug/could be an intrusion).

---

### Post by sowdust on 2013-01-07
Hello everyone,

just to give a quick update on the situation:

leaving the server on but disconnected from the net, it didn't have any sort of problems and stayed on the whole time.
After a few hour I plugged it back into the net, same old problems appeared and it got shut off.
It is surely a problem of intrusion.

A few days ago a security update was released: after I have installed that, no more trouble appeared (the server is ok and running ok) even though access attempts ( in messages.log ) are still many.

---

### Post by Rexilion on 2013-01-07
I'm really curious which server pieces were updated. If it's a root exploit, I suggest you do a reinstall though.

You can check in /var/log/dpkg.log if I'm not mistaken.

---

### Post by sowdust on 2013-01-07
Hello,

I think the interesting lines from dpkg.log are the following: 

> 013-01-05 14:17:21 upgrade grub-pc 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-05 14:17:22 upgrade grub-pc-bin 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-05 14:17:23 upgrade grub2-common 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-05 14:17:24 upgrade grub-common 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-05 14:18:03 upgrade mountall 2.36 2.36.3
2013-01-05 14:18:14 upgrade unattended-upgrades 0.76 0.76ubuntu1

i remember installing a package having "security upgrades" as a description, but I'm not sure it's among the one above or which one could be.

Also, I'm very glad the situation seems to be solved, but I'd like very much to find out at least where from someone got in, (how, why, and who would be all welcome). The problem is that I really do not know where to look. Reading log messages didn't give me too much insight (although I admit having a S.O. exam soon)... a hint on where to start looking would be much appreciated : )

---

### Post by Rexilion on 2013-01-07
The packages you mentioned are not exactly web services.

Unless you were infected by a rootkit in your mbr/grub, then you have simply deleted the rootkit but are still infected.

I'm not even sure if the Grub installation/upgrade procedure rebuilds the MBR of your disk/partition.

It's highly likely those packages did not solve your problem.

---

### Post by sowdust on 2013-01-08
ok, thanks for the warning. when I have time I might do a clean reinstall after backing up all my data.
But I would really really like to understand how this happened...... is it that difficult to analyze these situations? thanks!

---

### Post by Rexilion on 2013-01-08
I'm not familier with computer forensics. What I would do:

- disable each service one by one see which one is vulnerable
- on the percieved vulnerable service narrow down ip source
- attach tcpdump for that ip
- see what he/she/it is doing

Long shot, but should not take *much* effort. Furthermore, you could check all your logs and such. Look for unfamiliair kernel messages, segvaults and users logging on and off.

Maybe set up an external box for logging over UDP. In case the server crashed you have everything till it shuts down. Maybe you can see a pattern in there.

---

### Post by sowdust on 2013-01-08
Thanks for your suggestion.
I tried cross checking system logs and tcpdump (via snort/acid base).

picking one particular ip, this is what I found in auth.log (repeatedly during the day, apparently with no success)

> 
Jan  8 11:31:53 okovita.fastwebnet.it sshd[11926]: Invalid user r00t from 220.172.107.211
Jan  8 11:31:53 okovita.fastwebnet.it sshd[11926]: input_userauth_request: invalid user r00t [preauth]
Jan  8 11:31:53 okovita.fastwebnet.it sshd[11926]: pam_unix(sshd:auth): check pass; user unknown
Jan  8 11:31:53 okovita.fastwebnet.it sshd[11926]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=220.172.107.211 
Jan  8 11:31:55 okovita.fastwebnet.it sshd[11926]: Failed password for invalid user r00t from 220.172.107.211 port 3648 ssh2
Jan  8 11:31:55 okovita.fastwebnet.it sshd[11926]: Received disconnect from 220.172.107.211: 11: Bye Bye [preauth]

same ip, in snort, has hundreds of log alerts saying:

> 
COMMUNITY SIP TCP/IP message flooding directed to SIP proxy - attempted dos-attack

but I'm not really sure how to interpret it. Looking for it didn't give me too much insight


Also, using snort I am able to see what the "attackers" sent. Packages data is exadecimal: should I try put all these packages sent together to recreate the instructions they're sending and eventually understand it?

the instructions (omitting NOP) are something like
> 
ts 0002533303FB4F03
sack EE068060EE068608
ts 0003F42403FF610E
ts 0003F42403FF610E
ts 0004107303FFA80E
ts 0004107303FFA80E
ts 000421C703FFD27A
ts 000421C703FFD27A
ts 00043755040008F3
sack EF699C15EF69A765
ts 00043755040008F3
sack EF699C15EF69A765


---

### Post by Rexilion on 2013-01-09
Then that probably is not the cause of your box shutting down.

Ever considered using the 'recent' firewall module? I find it quite nifty. You can allow an access attempt every 10 minutes by filtering tcp syn packets.

---

### Post by sowdust on 2013-02-03
Hi Rexilon,

I think I have understood the problem. My ISP - called Fastweb - uses the same IP for more clients; I found out there is the possibility of renting a public IP, which is though ridiculously expensive. I believe I have been kicked out by the ISP itself. What really intrigues me is how can they almost shut my server down (if this is the case)

And again thank you for your help : )

---

### Post by Rexilion on 2013-02-04
> **sowdust said:**
> What really intrigues me is how can they almost shut my server down (if this is the case)

That is a crime in my country... :o

Glad you somewhat worked it out :) .

---

