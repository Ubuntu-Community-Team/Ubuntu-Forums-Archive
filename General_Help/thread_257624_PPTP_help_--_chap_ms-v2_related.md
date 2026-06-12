---
title: "PPTP help -- chap ms-v2 related"
date: 2006-09-14
forum: General Help
---

### Post by sm00nie on 2006-09-14
Hey all,

I am experiencing some problems with pptp (connecting to SecureIX) and I'm using Ubuntu 6.06.1. Im trying to connect to a MS VPN server that requires authentication. From the looks of it, it looks like chap MS-V2 isn't being authenticated perhaps.
> moon@moon:sudo pon SecureIX debug dump logfd 2 nodetach
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
name [email]accountlogin[/email]               # (from /etc/ppp/peers/SecureIX)
remotename PPTP         # (from /etc/ppp/peers/SecureIX)
                # (from /etc/ppp/options.pptp)
pty pptp vpn.secureix.com --nolaunchpppd                # (from /etc/ppp/peers/SecureIX)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam SecureIX                # (from /etc/ppp/peers/SecureIX)
proxyarp                # (from /etc/ppp/options)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)

Using channel 39
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2b7af573> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1408> <asyncmap 0x0> <auth chap MS-v2> <magic 0xacc4f284> <pcomp> <accomp>]
**No auth is possible**
sent [LCP ConfRej id=0x1 <auth chap MS-v2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x2b7af573> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <mru 1408> <asyncmap 0x0> <magic 0xacc4f284> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <mru 1408> <asyncmap 0x0> <magic 0xacc4f284> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x2b7af573]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [LCP TermReq id=0x3 "peer refused to authenticate"]
LCP terminated by peer (peer refused to authenticate)
sent [LCP TermAck id=0x3]
Script pptp vpn.secureix.com --nolaunchpppd finished (pid 10547), status = 0x0
Modem hangup
Connection terminated.
I checked out the diagnosis page for pptp ([http://pptpclient.sourceforge.net/howto-diagnosis.phtml#no_auth_is_possible](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#no_auth_is_possible)) and it shows two possible reasons for the "No auth is possbile" error:

**1** - pppd could not find a matching entry in the chap-secrets file, (see below for causes)
**chap-secrets file**: > # client        server  secret                  IP addresses
accountlogin password * 
Thats the info I have in there (actual info changed for postings sake).

**2** - pppd was built without MS-CHAP-V2 support (quite uncommon). 
I'm not exactly sure how to verify this :/.

Current versions:
pptp - v1.7.0
ppp - v2.4.4 (came with Ubuntu 6.06.1 installation)

I'm new to linux and would appreciate any tidbits of information you may have to offer,

Thanks,
Shawn

---

