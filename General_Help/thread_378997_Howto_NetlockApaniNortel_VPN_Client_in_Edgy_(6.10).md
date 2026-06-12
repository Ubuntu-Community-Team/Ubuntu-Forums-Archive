---
title: "Howto: Netlock/Apani/Nortel VPN Client in Edgy (6.10)"
date: 2007-03-08
forum: General Help
---

### Post by jkeyes0 on 2007-03-08
Note: this information has been taken in part from [http://ubuntuforums.org/showthread.php?t=110843](http://ubuntuforums.org/showthread.php?t=110843), expanded on and updated for Edgy. I compiled the data from the entire thread, along with my personal experience.


Untar the Redhat version of the client (cvc_linux-rh-gcc3-3.3.tar.gz) wherever you would like to, and then cd to that directory.

Edit src/linux_wrapper.c. Find the line that says 
	```
return ip_rcv(skb, skb->dev,pt);
```
and change it to
	```
return netif_rx(skb);
```

Find the following lines, and change them to whatever the next line says:
Change from:
	```
new_skb->stamp = skb->stamp;
```
to:
	```
new_skb->tstamp = skb->tstamp;
```
Change from:
	```
skb_to->stamp = skb_from->stamp;
```
to:
	```
skb_to->tstamp = skb_from->tstamp;
```
Change from:
	```
new_skb->security = skb->security
```
to:
	```
/* new_skb->security = skb->security; */
```

Look for the lines that contain:
```
#if (LINUX_VERSION_CODE >= 0x020500)

  #include <net/flow.h>
  struct rtable;
```

Change them to:

```
#if (LINUX_VERSION_CODE >= 0x020500)

  #include <net/flow.h>
  #include <net/route.h>
  #include <linux/in_route.h>
  //struct rtable;
```

Save the linux_wrapper.c file.
Run &#8220;sudo make&#8221; from the command line.

In the following files, change the first line (it should say #!/bin/sh now) to #!/bin/bash:

netlock
install.sh
uninstall.sh
scripts/netlock
scripts/start_cvc

In the install.sh file, change the line that says
	  ```
$rcd/init.d/init.d/netlock start
``` (should be around line 223)
to say:
	  ```
$rcd/init.d/netlock start
```

Save and close the install.sh file, then from the command prompt, run:
	sudo bash install.sh

I'd say &#8220;sudo ./install.sh&#8221; would work as well. Just reporting it as I performed it.

Once you've agreed to the license, it will install and run the netlock service. It should give you very minimal warnings during the make process, and no errors while installing. After it is completed, it will tell you netlock is running. Open your firefox browser, and point it to &#8220;[http://127.0.0.1:9161&#8221;](http://127.0.0.1:9161&#8221;). It should ask you to set up your VPN connection at this point. You will need the VPN connection info provided by your networking staff or administrator.

Good luck!

---

### Post by etank on 2007-03-08
Nice job. I'm glad that you were able to get a working solution.

---

### Post by MaineDave on 2007-03-09
Some notes on installing the Nortel (Apani) Connectivity VPN client on Ubuntu 6.10 (Edgy).

Note, I have a clean install of Ubuntu. The command "uname -r" returns "2.6.17-11-generic".

Get the client from Apani ([www.apani.com](www.apani.com), and navigate to their Nortel VPN client). I bought the client, and the file that I got was **cvc_linux-3.5.tar.gz** . This version is recent. I purchased it within the last week.  This accounts for the differences between what worked for me and what worked for jkeyes0.

Unzip this file, then unzip **cvc_linux-rh-gcc3-3.5.tar.gz** contained within it.

Open a terminal window and cd to the unzipped cvc_linux-rh-gcc3-3.5 directory, which will be called here "dev-home".

There is no need to change any files that will be compiled, or to compile the Ubuntu kernel.

Build the code, by executing the command:
```

sudo make

```
I saw one warning about a missing ?.a.cmd file. Since I didn't know what to do about this, I ignored it. For me, this caused no apparent ill effect.

You must make corrections in the scripts before running the install.

Change the first line, 
```

#!/bin/sh

```
to
```

#!/bin/bash

```
in the files: 
[INDENT]dev-home/scripts/netlock
dev-home/scripts/start_cvc
dev-home/netlock
dev-home/uninstall.sh
dev-home/install.sh.
[/INDENT]
In addition, there are two other changes that must be made in dev-home/install.sh.

At line 49, where it reads,
```

elif [-d /etc/rc0.d ]; then

```
a space must be inserted so that it reads,
```

elif [ -d /etc/rc0.d ]; then

```
Furthermore, at line 87, the line that starts as,
```

install -m 744 scripts/start_cvc 

```
must be changed so that it starts as,
```

install -m 755 scripts/start_cvc

```
With these changes in place, run: 
```

sudo ./install.sh

```
You should not see any errors. After this you should find an applications-> other-> Netlock CVC entry in your menus which will start up Firefox to make the connection.

I found I had to reboot to get the newly installed software to work.

After the reboot, go to the Apani test site, and test your VPN client against their test site. Apparently, switch administrators can apply various filters to restrict access, including filtering for operating systems. Therefore, you may want to test against the Apani site before testing against your company's site, since the Apani site is wide open.

The Apani test site info:

Name: Test
Destination: 63 dot 192 dot 85 dot 15
(subsitute "." for " dot " above.)
Authentication: username and password
username: netlocktest
password: netlocktest

Although Apani does not support Ubuntu, I found them willing to lend some helpful advice. I think it would be quite easy for them to support Ubuntu. Encourage them to do so when you purchase their product.

---

### Post by jkeyes0 on 2007-05-01
Update: I have installed and tested this product on Feisty. Following the instructions given by MaineDave, I managed to get everything working. For some odd reason I couldn't ping anything, but after a reboot it started working (not immediately, but after I enabled Trace logging). Either way, I've got a functional client, and I'm ecstatic.

I'm sort of considering purchasing the client, but $90 is a bunch to shell out for one license. Perhaps I can talk my work into paying for it, since I'm not the only one using Ubuntu at work.

Thanks again, MaineDave!

---

### Post by Prometheus7 on 2007-08-01
thank you for posting a working solution!

I have tried multiple times to make vpnc work with the nortel contivity client. No luck with that. I even had some trouble compiling this and had to resort to falling back to 32-bit (have an amd 64). Not sure if there was another solution but everything seems to be running just as quickly and I can now connect to work.

now I just have to ask my manager to buy the full version for me :grin:

---

### Post by Prometheus7 on 2007-10-16
I didn't have problems in Feisty and I used the client for a few months. Upon upgrading to gutsy, the client no longer worked. I thought that something was wrong with my upgrade so I did a clean install of gutsy from cd, followed the same instructions again for installing the client, but something still appears to be wrong with mishim.o.

When I run "sudo make" for the src file I get the following errors...


cd k2.6 && make
make[1]: Entering directory `/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘init_misc’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: error: ‘dev_base’ undeclared (first use in this function)
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: error: (Each undeclared identifier is reported only once
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: error: for each function it appears in.)
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘nl_ip_rcv’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:435: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘dev_next’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:498: error: ‘net_device_t’ has no member named ‘next’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘nl_skb_dup’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:550: error: ‘struct sk_buff’ has no member named ‘h’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:550: error: ‘struct sk_buff’ has no member named ‘h’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:551: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:551: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:552: error: ‘struct sk_buff’ has no member named ‘mac’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:552: error: ‘struct sk_buff’ has no member named ‘mac’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘nl_skb_hdr_copy’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:577: error: ‘struct sk_buff’ has no member named ‘h’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:577: error: ‘struct sk_buff’ has no member named ‘h’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:578: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:578: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:579: error: ‘struct sk_buff’ has no member named ‘mac’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:579: error: ‘struct sk_buff’ has no member named ‘mac’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘nl_skb_iph’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:596: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘nl_send_skb’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:617: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:620: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘do_checksum_offload’:
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:753: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:769: error: ‘struct sk_buff’ has no member named ‘nh’
/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:773: error: ‘struct sk_buff’ has no member named ‘nh’
make[3]: *** [/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o] Error 1
make[2]: *** [_module_/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [kmod_build] Error 2
make[1]: Leaving directory `/home/xyz/Desktop/cvc_linux-rh-gcc3-3.5/src/k2.6'
make: *** [all] Error 2

any ideas?

---

### Post by mbeierl on 2007-10-17
Sadly, while I've seen a few patches floating around out there, none of them actually work...

And, while I was all for getting Apani to work, my company has since offered PPTP instead, so I fear I am no longer active in this thread :(

---

### Post by jkeyes0 on 2007-10-24
> **mbeierl said:**
> Sadly, while I've seen a few patches floating around out there, none of them actually work...

And, while I was all for getting Apani to work, my company has since offered PPTP instead, so I fear I am no longer active in this thread :(

I no longer work for my previous company, and the company I work for now uses OpenSwan for their VPN connectivity, so I'm afraid I won't be able to help out anymore either. Very sorry.

---

### Post by billionmonkeys on 2007-11-07
[http://ubuntuforums.org/showthread.php?t=110843&page=7](http://ubuntuforums.org/showthread.php?t=110843&page=7)

note a fix for the gutsy problems has been posted in the above thread.

---

