---
title: "How do you check your IP address?"
date: 2006-08-05
forum: General Help
---

### Post by boom2k1 on 2006-08-05
How do you check your IP address if you are behind a router?

Thanks! I need that so I would know what my apache server is. Thanks!

---

### Post by fourchannel on 2006-08-07
on every linux distro there is a command you can type to find out the information of your network cards and loop-back interfaces.

Most distributions label the primary ethernet card as "eth0"

so if I want to find out my ip address for my desktop then I would open up a terminal and run this command: ```
ifconfig eth0
``` 
which in my case gives me ```
kev@Rei:~]$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:EF:79:9D
          inet addr:192.168.254.59  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feef:799d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:63993040 (61.0 MiB)  TX bytes:4181888 (3.9 MiB)
          Interrupt:22 Base address:0x2000

kev@Rei:~]$
```

---

### Post by h00s on 2006-08-07
For checking 'outside' ip address you can use a web page like [http://www.ipchicken.com/](http://www.ipchicken.com/) .

You may want to try dynamic dns services like dyndns.com for easier access to your machine. Nowadays, most routers supports dynamic dns services.

---

### Post by Christmas on 2006-08-07
You can also try out this [http://www.showmyip.com/](http://www.showmyip.com/)

---

### Post by fourchannel on 2006-08-07
> **Christmas said:**
> You can also try out this [http://www.showmyip.com/](http://www.showmyip.com/)
I'm amazed at how much information can be gleamed just from my browser like that.

---

### Post by h00s on 2006-08-07
> **fourchannel said:**
> I'm amazed at how much information can be gleamed just from my browser like that.
And that is just a half of it :D

---

### Post by boom2k1 on 2006-08-07
Thanks! That's very helpful>!

I am just wondering why my inet address (private ip the router assigned me) always change???
yesterday it was 192.168.1.13 and today is 192.168.1.14?

Is there any ways to fix this address because I am also configuring my Virtual network to direct my outside connection to this port? (I have to change it everytime I restart because it keeps giving me a new one). And I don't think it is because of DNS because it is just internal IP. 

Thanks!

---

### Post by shanepardue on 2006-08-07
> **boom2k1 said:**
> Thanks! That's very helpful>!

I am just wondering why my inet address (private ip the router assigned me) always change???
yesterday it was 192.168.1.13 and today is 192.168.1.14?

Is there any ways to fix this address because I am also configuring my Virtual network to direct my outside connection to this port? (I have to change it everytime I restart because it keeps giving me a new one). And I don't think it is because of DNS because it is just internal IP. 

Thanks!
well, you're probably running dhcp..you'd want to change it to static in the system>networking settings. if you've never done that, feel free to ask how!

---

### Post by NewWithoutClue on 2006-08-07
I've made a script to automagically obtain your public IPaddr and spit it out to the Terminal.

Create a file any old place and name it 'myip' (no quotes). Make this file executable with the command 'chmod +x myip' (again, no quotes).

Open the file for editing and paste the following lines of Python code in the file. Save the file when done.

```

#!/usr/bin/python 
from urllib import urlretrieve
from os import unlink

def myip():
	webpage_file = urlretrieve("http://checkip.dyndns.org/")[0]
	webpage = file(webpage_file, 'r').readlines()[0]
	unlink(webpage_file)
	return webpage.split(":")[1].split("<")[0].replace(' ', '')

if __name__ == '__main__':
	print myip()

```
Running this file will display your IP address.

After moving the file to /usr/bin using the command 'mv myip /usr/bin/myip' (no quotes and you need root,) every new shell session (including any new GNOME sessions, too) from this point forward will allow you to run the command 'myip' (without quotes) to see your IP on screen (Terminal screen).

Regards,
Paul

---

### Post by fourchannel on 2006-08-07
on the dyndns.com website you can download a script that will run as a daemon and automatically check and update your ip for you every 5 min or so. You can download the update client [here]("http://www.dyndns.com/download/clients/unix/ddclient.tar.gz"). You will need to create an account with dyndns.com. I've had a no problems using it.

Here is the configuration I used in my script.

```
######################################################################
##
## Define default global variables with lines like:
##      var=value [, var=value]*
## These values will be used for each following host unless overridden
## with a local variable definition.
##
## Define local variables for one or more hosts with:
##      var=value [, var=value]* host.and.domain[,host2.and.domain...]
##
## Lines can be continued on the following line by ending the line
## with a \
##
######################################################################
daemon=300                              # check every 300 seconds
syslog=yes                              # log update msgs to syslog
mail=root                               # mail all msgs to root
mail-failure=root                       # mail failed update msgs to root
pid=/var/run/ddclient.pid               # record PID in file.
#
#use=watchguard-soho,        fw=192.168.111.1:80        # via Watchguard's SOHO FW
#use=netopia-r910,           fw=192.168.111.1:80        # via Netopia R910 FW
#use=smc-barricade,          fw=192.168.123.254:80      # via SMC's Barricade FW
#use=netgear-rt3xx,          fw=192.168.0.1:80          # via Netgear's internet FW
#use=linksys,                fw=192.168.1.1:80          # via Linksys's internet FW
#use=maxgate-ugate3x00,      fw=192.168.0.1:80          # via MaxGate's UGATE-3x00  FW
#use=elsa-lancom-dsl10,      fw=10.0.0.254:80           # via ELSA LanCom DSL/10 DSL Router
#use=elsa-lancom-dsl10-ch01, fw=10.0.0.254:80           # via ELSA LanCom DSL/10 DSL Router
#use=elsa-lancom-dsl10-ch02, fw=10.0.0.254:80           # via ELSA LanCom DSL/10 DSL Router
#use=alcatel-stp,            fw=10.0.0.138:80           # via Alcatel Speed Touch Pro
#use=xsense-aero,            fw=192.168.1.1:80          # via Xsense Aero Router
#use=allnet-1298,            fw=192.168.1.1:80          # via AllNet 1298 DSL Router
#use=3com-oc-remote812,      fw=192.168.0.254:80        # via 3com OfficeConnect Remote 812
#use=e-tech,                 fw=192.168.1.1:80          # via E-tech Router
#use=cayman-3220h,           fw=192.168.0.1:1080        # via Cayman 3220-H DSL Router
#
#fw-login=admin,             fw-password=XXXXXX         # FW login and password
#
## To obtain an IP address from FW status page (using fw-login, fw-password)
#use=fw, fw=192.168.1.254/status.htm, fw-skip='IP Address' # found after IP Address
#
## To obtain an IP address from Web status page (using the proxy if defined)
use=web, web=checkip.dyndns.org/, web-skip='IP Address' # found after IP Address
#
#use=ip,                     ip=192.168.254.62  # via static IP's
#use=if,                     if=eth0            # via interfaces
#use=web                                        # via web
#
protocol=dyndns2                                # default protocol
#proxy=fasthttp.sympatico.ca:80                 # default proxy
server=members.dyndns.org                       # default server
#server=members.dyndns.org:8245                 # default server (bypassing proxies)

login=*******                               # default login
password=*******                          # default password
#mx=mx.for.your.host                            # default MX
#backupmx=no                            # host is primary MX?
#wildcard=no                            # add wildcard CNAME?

##
## dyndns.org dynamic addresses
##
## (supports variables: wildcard,mx,backupmx)
##
arael.ath.cx,fissure.ath.cx,leliel.ath.cx,schism.ath.cx

#
## dyndns.org static addresses
##
## (supports variables: wildcard,mx,backupmx)
##
# static=yes,                           \
# server=members.dyndns.org,            \
# protocol=dyndns2                      \
# your-static-host.dyndns.org

##
##
## dyndns.org custom addresses
##
## (supports variables: wildcard,mx,backupmx)
##
# custom=yes,                           \
# server=members.dyndns.org,            \
# protocol=dyndns2                      \
# your-domain.top-level,your-other-domain.top-level

##
## ZoneEdit (zoneedit.com)
##
# server=www.zoneedit.com,              \
# protocol=zoneedit1,                   \
# login=your-zoneedit-login,            \
# password=your-zoneedit-password       \
# your.any.domain,your-2nd.any.dom

##
## EasyDNS (easydns.com)
##
# server=members.easydns.com,           \
# protocol=easydns,                     \
# login=your-easydns-login,             \
# password=your-easydns-password        \
# your.any.domain,your-2nd.any.domain

##
## Hammernode (hn.org) dynamic addresses
##
# server=dup.hn.org,                    \
# protocol=hammernode1,                 \
# login=your-hn-login,                  \
# password=your-hn-password             \
# your-hn-host.hn.org,your-2nd-hn-host.hn.org

##
## dslreports.com dynamic-host monitoring
##
# server=members.dslreports.com         \
# protocol=dslreports1,                 \
# login=dslreports-login,               \
# password=dslreports-password          \
# dslreports-unique-id

##
## OrgDNS.org account-configuration
##
# use=web, web=members.orgdns.org/nic/ip
# server=www.orgdns.org                 \
# protocol=dyndns2                      \
# login=yourLoginName                   \
# password=yourPassword                 \
# yourSubdomain.orgdns.org

##
## dnspark.com
## (supports variables: mx, mxpri)
##
# use=web, web=ipdetect.dnspark.com, web-skip='Current Address:'
# protocol=dnspark,                     \
# server=www.dnspark.com,               \
# your-host.dnspark.com

##
## NameCheap (namecheap.com)
##
# protocol=namecheap,                           \
# server=dynamicdns.park-your-domain.com,       \
# login=my-namecheap.com-login,                 \
# password=my-namecheap.com-password            \
# myhost.namecheap.com

```

---

