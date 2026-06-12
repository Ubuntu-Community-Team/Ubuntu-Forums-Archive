---
title: "Gutsy not syncing to time servers."
date: 2007-10-26
forum: General Help
---

### Post by mjpatey on 2007-10-26
This is the same problem I had in Feisty, and it's still not fixed.  The worse issue is, I have no idea how I fixed it in Feisty, because doing what I did back then doesn't fix it now.

Since my Gutsy install, my system time has crept behind by about 7 minutes (this is only since last week when Gutsy went public).

I right-click the clock on the taskbar, and go to "Adjust Date & Time".  Next to "Configuration" I select "Keep synchronized with Internet servers".  Then I select 5 or 6 servers.  I click "Close".  The time doesn't budge.  I reboot.  Still nothing.  I wait 2 days.  No change, and it's continuing to creep farther behind.  It's obviously not syncing with anybody's servers.

I type in a Terminal:  ntpq -p, and get the response:  "No association ID's returned."  I think this should show me my time servers.

I sudo gedit ntp.conf, and see this near the top of the file:
```

# You do need to talk to an NTP server or two (or three).
```

...under which was listed just the Ubuntu server, rather than my selected servers.  I deleted it, and entered manually the names of the servers in my list.  Then I noticed at the end of the file:

```
#broadcastclient
server clock.psu.edu 
server louie.udel.edu
server ntp.cmr.gov
server ntp0.cornell.edu
server ntp-0.cso.uiuc.edu

```

...which were the servers I'd selected in the GUI.  So now they're in there twice, once manually typed by me (in the place they seem they ought to be) and once automatically (near the end of the file under #broadcastclient)

I'm sick of this.  When I tell the system clock to sync itself to Internet servers, it ought to do it!!!  I shouldn't have to fiddle around in config files unless I want to.  The GUI has essentially lied to me by offering these options, then doing nothing when I set them.

I hate to sound so bitter, but I run up against this every time I re-install Ubuntu, and it's getting very old.  The problem, and therefore the solution, seems to change every time it happens.  Again, I apologize for my tone, but I'm about to pull my hair out.

Does anyone know what I need to do to truly sync my system clock with Internet time servers?

Thanks for any help you may have.

-Mark

---

### Post by TidusBlade on 2007-10-26
I have the exactly same problem :( I used to keep on going to Manual and then Sync Now, but now it's getting annoying, I sure hope somebody knows how to fix this :)

---

### Post by fjgaude on 2007-10-26
Yes, it is doing the same thing, not syncing, with both the 32- and 64-bit Gusty releases, a bug.

---

### Post by mjpatey on 2007-10-26
If it's a bug, it's been around since at least Feisty!

I'm going to launchpad to try to file it now.

-Mark

---

### Post by C64MAN on 2007-10-28
I had the same problem under feisty, and gusty too. But i think i have the solution.

I think the problem is caused by the firewall. As I added ntp.ubuntu.net to "permit all connection from that computer" (i translated that text from Hungarian, so that can be different to the real english text) in the firestarter. Than it began to work.

---

### Post by mjpatey on 2007-10-28
Well, I've filed this as a bug in Launchpad.  So far it's gotten a few confirmations from users, so hopefully we're onto something!

Here's the link to the bug:

[https://bugs.launchpad.net/bugs/157608]("https://bugs.launchpad.net/bugs/157608")

I'm not familiar with the rules of decorum on Launchpad, but my instinct would be to encourage everyone who's having this problem to visit the bug's page and put in your two cents if you'd like to see it fixed.

Oh, and C64MAN, very good name.  :-)  I'll try your firewall workaround.

-Mark

---

### Post by sgenchev on 2007-10-28
Default /etc/ntp.conf in gutsy has these lines:

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

They describe what can any IPv4 and IPv6 host do to ntp server on this box.
 `nomodify` here prevents ntp from trusting any host.
 
 The easiest fix is to remove nomodify from these lines; if you want to be more paranoid you could read up more and configure just the options fro just the servers you are talking to..

 I agree this is a bug..

---

### Post by jm9gt on 2007-10-29
Here's my tuppence worth.

This is not an ntpd bug! If you restart it with /etc/init.d/ntp restart it works correctly!

john@athlon:/etc/init.d$ ntpq -p
No association ID's returned
john@athlon:/etc/init.d$ sudo /etc/init.d/ntp restart
[sudo] password for john:
 * Stopping NTP server ntpd                                                                         [ OK ]
 * Starting NTP server ntpd                                                                         [ OK ]
john@athlon:/etc/init.d$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 ntp1.****.org   195.66.241.10    2 u    2   64    1   38.306  -919.74   0.001
 admin.islay.bit 195.66.241.10    2 u    1   64    1   37.849  -922.59   0.001
 lumberjack.magi 130.159.196.118  3 u    1   64    1   34.581  -923.17   0.001
 ingsoc.eu       .INIT.          16 u    -   64    0    0.000    0.000   0.001
john@athlon:/etc/init.d$

the problem is that ntp is trying to start before the dhcp has completed, looking in my syslog there are bind errors and the following (what to me is a ) dead giveaway

Oct 29 22:10:54 athlon ntpd_initres[5524]: host name not found: 0.uk.pool.ntp.org
Oct 29 22:10:54 athlon ntpd_initres[5524]: couldn't resolve `0.uk.pool.ntp.org', giving up on it
.......

and

Oct 29 22:10:55 athlon dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 22:10:55 athlon dhclient: DHCPACK from 192.168.1.254

i.e. I didn't get an IP address until after ntp tried to start looking for servers! So it's not surprising that ntp doesn't work!

---

### Post by jm9gt on 2007-10-29
bad form to reply to one's own post but here's how I got round it; based on what I found before investigated and changed the configuration of the network card.

go to 

system->network settings->wired network

press 'properties'

deselect 'Enable roaming mode' and for configuration choose 'automatic configuration (DHCP)'

rebooted the machine, when it comes up start terminal session and type 'ntpq -p' - hey presto 4 servers shown ntp working.

---

