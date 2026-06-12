---
title: "proxyfier? - Proxychains error."
date: 2007-03-01
forum: General Help
---

### Post by Flavian on 2007-03-01
Hi guys.
I've got the following problem: I am bound to use windows only because of one program :(
The program is a decoder for [www.onlinetvrecorder.com](www.onlinetvrecorder.com) (all legal as far as German law goes) In my student flat I got a crappy internet connection where I am forced to connect out through a proxy!
Now the LINUX decoder works great (at home) but doesn't in my student flat, because it does not support proxy!
Now here's the deal. I tried "proxychains" but no success, maybe I did something wrong, I dunno... It's just that the program always sais "provide more proxies" or the decoder can't simply connect out! :(
Is there another easy to use linux program which can forcee applications that don't support proxies to connect through them?

I seriously hope someone can help me maybe I did something wrong as well, I don't know
I'll just post my proxychains config file.
Here's the way I start the decoder with proxychains:
> sudo proxychains /home/florian/otrdecoder-bin-linux-v221/otrdecoder-gui

until that point the program starts up but can't connect out :(

Here's my config file:

```
# proxychains.conf  VER 2.0
#
#        HTTP, SOCKS4, SOCKS5 tunneling proxifier.
#

# The option below identifies how the ProxyList is treated.
# only one option should be uncommented at time,
# otherwise the last appearing option will be accepted
#
# Dynamic - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# at least one proxy must be online to play in chain
# (dead proxies are skipped)
# otherwise EINTR is returned to the app
#
# Strict - Each connection will be done via chained proxies
# all proxies chained in the order as they appear in the list
# all proxies must be online to play in chain
# otherwise EINTR is returned to the app
#
# Random - Each connection will be done via random proxy
# (or proxy chain, see  chain_len) from the list
# this option is good for scans

#dynamic_chain
#strict_chain
random_chain

# Make sense only if random_chain
chain_len = 2

# Quiet mode (no output)
#quiet_mode

# Write stats about good proxies to proxychains.stats
#write_stats

#Some timeouts in milliseconds
#
tcp_read_time_out 15000
tcp_connect_time_out 10000

[ProxyList]
# ProxyList format
#       type  host  port [user pass]
#       (values separated by 'tab' or 'blank')
#
#
#        Examples:
#
#            	socks5	192.168.67.78	1080	lamer  secret
#		http	192.168.89.3	8080	justu	hidden
#	 	socks4	192.168.1.49	1080
#	        http	192.168.39.93	8080	
#		
#
#       proxy types: http, socks4, socks5
#        ( auth types supported: "basic"-http  "user/pass"-socks )
#
##http 	10.0.0.5 3128
##http 	10.0.0.3 3128
##http 	10.0.0.5 3128
#socks5 192.168.1.4 1080
#socks4 10.5.81.143 1080
#http	192.168.203.18 8080 


http	192.168.248.1 82	lhs26	lhs26

```

---

