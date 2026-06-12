---
title: "Shorewall Help"
date: 2015-10-26
forum: General Help
---

### Post by eric95 on 2015-10-26
I have been browsing these forums for that last few weeks. I am currently in school and I am being tasked with building an Ubuntu Web server. I am not a real experienced user of Linux or Ubuntu this is actually my  first go at configuring a web server in Ubuntu so everything I have learned is  either from here or google. I have everything going well except I am running in to a problem with Shorewall. I have installed it and configured it (well at least I thought it was configured correctly) but when I have it running I can not ssh in to the web server. I have set in the rules to allow ssh. When I stop shorewall I can ssh in just fine. Thank you in advance for any help that anyone can provide and if I am leaving information out please let me know and I can either provide screen shots or do my best to answer any questions.

---

### Post by QDR06VV9 on 2015-10-26
> [SIZE=2][COLOR=#000000][FONT=sans-serif]Answer [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]courtesy of Ryan: Assume that the IP address of your local firewall interface is 192.168.1.1. If you configure SSHD to only listen on that address and add the following rule, then you will have access on port 4104 from the net and on port 22 from your LAN.[/FONT][/COLOR][/SIZE][FONT=sans-serif][COLOR=#000000]#ACTION SOURCE  DEST                    PROTO   DEST PORT(S)
DNAT    net     fw:192.168.1.1:22       tcp     4104[/COLOR][/FONT][COLOR=#222222][FONT=Verdana]

Shorewall Faqs [/FONT][/COLOR][FONT=sans-serif][SIZE=3][COLOR=#000000]http://shorewall.net/FAQ.htm#Connections
Written in the Quotes may not be the exact text you need but more of a clue.
[/COLOR][/SIZE][/FONT]Connect to a remote SSH server
[http://ubuntuguide.org/wiki/Ubuntu_Trusty_Networking#Connect_to_a_remote_SSH_server](http://ubuntuguide.org/wiki/Ubuntu_Trusty_Networking#Connect_to_a_remote_SSH_server)

---

### Post by eric95 on 2015-10-26
Thank you for your response. I have been messing with this and doing some more research. Right now as long as I have Shorewall turned off I can use putty and ssh in to my web server. I can connect to the ip address via a web browser but I cannot connect using https. If I start Shorewall I cannot connect in any fashion. I am at a loss here. I went though the link you gave but I did not help. Again thank you for your response. 

Also I did not mention this. I am building this in a VM right now so all the connections have been made or not made using my host computer.

---

