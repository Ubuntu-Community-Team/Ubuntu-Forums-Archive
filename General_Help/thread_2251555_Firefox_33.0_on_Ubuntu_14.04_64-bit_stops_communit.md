---
title: "Firefox 33.0 on Ubuntu 14.04 64-bit stops communitcating with the Internet"
date: 2014-11-04
forum: General Help
---

### Post by cigtoxdoc on 2014-11-04
I have three PCs on my desk.  Two homebuild desktops based on Intel i7-4770K processors on either side of my DELL Vostro 3500 laptop.  All run 14.04 64-bit, all 8 GB RAM, and all updated to latest whatever Ubuntu sends.  The two desktops are used mainly for web browsing and dowloading PDF files I need to read., while the laptop is for e-mail and serious writing.

The left desktop has been developed a strange quirk.  After a day or two of being on with roughly the same websites, Firefox ceases to commuincate with the Internet.  Evolution still communicates with the Internet as does vlc player and web browsing using Konqueror.  I cannot figure out what is the cuase of the problem.  If I close all Firefox windows and restart Firefox the problem goes away.

Thank you,

John

---

### Post by cigtoxdoc on 2014-12-05
SECOND REQUEST FOR HELP

I am still having this problem after the Firefox upgrade to 34.0  It happened again last night.  I leave my PCs on 24/7.  This morning webpages that were operating normally last night were not refreshing this morning.  These include not only major news sites (BBC, CNN), but also local news websites and one hobbyist website (trainorders.com).  Any ideas on how to troubleshoot this problem?

John

---

### Post by nerdtron on 2014-12-05
Have you tried clearing the cache on firefox.
Menu>History>Clear Recent History

You can try clearing everything. This sometimes happens to me on windows too. The old cache seems to affect the websites.

---

### Post by cigtoxdoc on 2014-12-07
Than you for your reply.  I have treid clearing the cache and setting Firefox to use internal fonts (elimnates problems waiting for Google fonds) and clearing history (even though Firefox is set not to remember history).  Those changes have not solved the problem.

John

---

### Post by bapoumba on 2014-12-07
Preferences > Network Tab >  Settings > Do you use a proxy ? Please try auto detect proxy settings.

---

### Post by nerdtron on 2014-12-07
Also, try resetting your firefox profile. On your home folder, show the hidden files and you'll see the .mozilla folder.
Rename of move that folder to a new location. When you launch firefox again, a new profile will be created (must like a fresh install) and settings wiped.

---

### Post by cigtoxdoc on 2014-12-07
Thank you for your suggestions.

None of my PCs go through a proxy.  The three on my desk go right to the Cox Business Modem Router (No proxy for localhost 127.0.0.1).  Remainder go through a D-Link 16-port switch that is hooked to the fourth port on the router.  I have set up a new .mozilla folder.  No Wi-Fi.

John

---

### Post by bapoumba on 2014-12-07
No wifi or no internet access with Firefox ? From the first post I understand the problems are isolated to FF on this machine and all the other ones have no problem.
Any error message if you start Firefox from the terminal ? Can you ping ?
```
ping ubuntuforums.org
```

---

### Post by cigtoxdoc on 2014-12-07
ohn@john-MSI-7846:~$ ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=55 time=149 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=55 time=100 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=55 time=100 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=55 time=145 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=5 ttl=55 time=104 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=6 ttl=55 time=167 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=7 ttl=55 time=146 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=8 ttl=55 time=98.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=9 ttl=55 time=96.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=10 ttl=55 time=105 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=11 ttl=55 time=102 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=12 ttl=55 time=96.9 ms
^C
--- ubuntuforums.org ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11015ms
rtt min/avg/max/mdev = 96.660/117.827/167.530/25.094 ms
john@john-MSI-7846:~$

---

### Post by bapoumba on 2014-12-07
Thanks so what do you mean when you say no wifi ?

---

### Post by cigtoxdoc on 2014-12-07
My home/office is totally hardwired (just like the R&D lab where I worked before retirement in 2004).

Also, starting firefox from the CLI gave:

john@john-MSI-7846:~$ firefox

(process:21867): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory

Firefox did start correctly.

John

---

### Post by bapoumba on 2014-12-07
The first error I also get, and have no issue with FF, so just watching [https://bugzilla.mozilla.org/show_bug.cgi?id=833117](https://bugzilla.mozilla.org/show_bug.cgi?id=833117)
The second one I never heard about, maybe this : [https://bugs.launchpad.net/ubuntu/+source/libvdpau/+bug/1300215](https://bugs.launchpad.net/ubuntu/+source/libvdpau/+bug/1300215)

But that should not explain your internet access problem. Any extension ?

---

### Post by pfeiffep on 2014-12-07
Concerning *Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory* - try this [post]("http://ubuntuforums.org/showthread.php?t=2191669")

I know that you said you don't use a proxy, but have you checked the FF Preferences | Advanced | Network | Connections | Settings ?  
     I also do NOT use a proxy, but my settings (by default FF 34 config)  state "Use system proxy settings"

---

### Post by cigtoxdoc on 2014-12-07
I have set all three desktop PCs to use system proxy settings with remote DNS.  Two of the three use the Intel graphics while the third one uses nVidia graphics.  All three have the usual set of Firefox windows open.

John

---

### Post by bapoumba on 2014-12-08
If all the 3 Firefox configurations are the exact same ones, you do not use specific extensions, do not use a proxy, a clean Firefox profile does not help and this computer has otherwise Internet access, I'm not sure where to look. Do you use DHCP or fixed IPs ?

---

### Post by nerdtron on 2014-12-08
What is mostly the Error when you browse the net using firefox?

If "Server Not Found" - probably DNS issues, either the system is not configured with the correct DNS or firefox settings have incorrect DNS, this error can occur even if you have internet connection

If "Connection Timeout" - probably firefox itself can't connect to the gateway/internet router. Another thing to check is firefox not in "Work Offline" mode?

---

### Post by cigtoxdoc on 2014-12-09
First, thank you to all who replied to my request for help.

Second, when Firefox misbehaved, there were no error messages.  Only notice was all the widows (each pointing to a different website) would not refresh.  Evolution (3.10.4) would still send and receive.  Konqueror would still work as a web browser and would refresh pages normally.  VLC, if used, would still receive a streaming radio station.

Third, this problem did not occur with my Dell Vostro 3500 laptop (also 14.04 64-bit).  Laptop uses nVidia graphics.  The desktops use Intel graphics as they use the Intel i7-4770K processors.

Fourth, the apparent solution is to "Use system proxy settings" and tick the box "Remote DNS"

Fifth, my ISP is Cox Business Cable.  Supposedly, I have a fixed IP address.

Sixth, all my PCs are hardwired to the the modem/router supplied by Cox.  The two desktop PCs and my laptop are directly connected to the modem/router.   The fourth port on the modem/router goes to a D-Link 16-port switch.  All other Ethernet connections in my home/office lead back to that switch.  There are three other active PCs right now that go through the 16-port switch (yes, my local electrical contractor has made some money on the wiring, but protection of my client's data is more important).

Seventh, I hope that I have answered all the questions that have been raised.

Thank you again for your help.

John

---

### Post by bapoumba on 2014-12-09
What do you mean by "would not refresh" ? What happens when hitting F5 ?

---

### Post by dragonfly41 on 2014-12-09
I'll chip in with a few ideas ... which might add further confusion!

In Firefox 34.0 (not sure about version 33) there are these options you could try under Firefox > Help


[LIST]
[*]Help
[*]Fix slowness, crashing, error messages and other problems
[*]Firefox Health Report
[*]Troubleshooting Information
[/LIST]
        see button "Reset Firefox to its default state"

[LIST]
[*]Restart with Options Disabled
[/LIST]

...

> 
These include not only major news sites (BBC, CNN), but also local news websites and one hobbyist website (trainorders.com). 

If you have a number of tabs open then you might find some problems with flash plugin used in background tabs.

There are add-ons to disable each flash enabled site (until you are ready to use flash .. e.g. in BBC or CNN).

...


Here is a link on running Firefox in safe mode as a start ...

[https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode](https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)

firefox -safe-mode

...

If you have name server problems .. and you are up for an experiment .. you could try opening a free [www.OpenDNS.com](www.OpenDNS.com) account.

Then go to your Ubuntu wired connection editor (icon top right Ubuntu toolbar).

select IPv4 settings.

set Method: Automatic (DHCP) addresses only

set DNS Servers: 208.67.222.222, 208.67.220.220

...

If you are using Cox router (I have a Belkin router so I don't know anything about Cox) then you will probably have to set DNS in your Cox router.

208.67.222.222, 208.67.220.220

However I don't see any advice for Ubuntu here ..

[http://www.cox.com/residential/support/internet/article.cox?articleId=c4a3a030-643b-11df-ccef-000000000000](http://www.cox.com/residential/support/internet/article.cox?articleId=c4a3a030-643b-11df-ccef-000000000000)

This is where you test if OpenDNS is working.

[https://support.opendns.com/entries/25897009-How-to-Test-for-Successful-OpenDNS-Configuration-](https://support.opendns.com/entries/25897009-How-to-Test-for-Successful-OpenDNS-Configuration-)

...

Referring back to your opening post ...

> 
GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed ... 

there is this bug discussed in this long thread ...

[https://bugzilla.mozilla.org/show_bug.cgi?id=1075079](https://bugzilla.mozilla.org/show_bug.cgi?id=1075079)

but it appears to be an assertion warning.

...

Here is a similar but shorter thread in ubuntu forum ..

[http://ubuntuforums.org/showthread.php?t=2250166](http://ubuntuforums.org/showthread.php?t=2250166)

pointing to this ...

[https://bugzilla.mozilla.org/show_bug.cgi?id=833117#c7](https://bugzilla.mozilla.org/show_bug.cgi?id=833117#c7)

This explains this message when you started firefox through CLI (your first post).

...

I hope you can make some sense out of all these snippets.

---

