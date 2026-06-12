---
title: "Renew the IP-adress from Terminal"
date: 2013-07-14
forum: General Help
---

### Post by leopoldbirkholm on 2013-07-14
Hello everyone,

Thank you for looking into my thread.

I have a problem with my router. The router is a Thomson TG789vn from my ISP. It is something funky with the WiFi. With Windows I use these two commands in the command prompt.
```

ipconfig /release ENTER
ipconfig /renew Enter
exit ENTER (because writing exit is so much more cool then clicking on the X :))

```
Well, yes, I can troubleshot the router but it works most of the time so it is quite far down on my to-do-list.

In Linux Ubuntu I know I should use the
```

ifconfig

```
command, but my two favorite is not working, the release and renew. I know, it is a shot-gun method, but it works.

So, I look around. Googled it. But I got mostly "my WiFi not working" or "Ubuntu is not seeing my WiFi". Nothing on my favorite method.

Anyone have any idea of a shot-gun method of releasing IP-addresses and then renewing them in Ubuntu?

Kind regards
Leopold

---

### Post by The Cog on 2013-07-14
I think the command you are looking for is **dhclient**. Something like:
```
sudo dhclient -r wlan0
sudo dhclient wlan0
```

---

### Post by peredur on 2013-07-14
Dunno if it helps, but the equivalent command in Linux for the Windows ipconfig is ifconfig.  Try 

[FONT=Courier New]$> info ifconfig[/FONT]

---

### Post by leopoldbirkholm on 2013-07-16
These two commands are the beginning of the mystery of renewing IP-addresses in Ubuntu
```
sudo dhclient
``` and ```
ifconfig
```. Onto more searching I found an interesting article. Unfortunately, it was from 2008 and thus outdated and caused my 13.04 to crash. So I won't be posting that as a solution.

Another maybe solution was 
```
ifconfig down ENTER 
ifconfig up ENTER

``` and 
```
sudo ifconfig down ENTER 
sudo ifconfig up ENTER

``` but when entering the ```
ifconfig wlan0
``` I still got the same IP-address. But at least I am making progress thanks to a wonderful community. :)

---

### Post by varunendra on 2013-07-16
DHCP assigned IPs are leased for a definite amount of time. The ifconfig up/down or ifup/ifdown commands just disable or enable the interface, and get the same address again if the lease is not expired yet (and not taken by another device yet).

The dhclient commands that The Cog suggested, explicitly requests for a new IP, so that's what you want.For details on this command, use -
```
man dhclient
```
..in terminal.
[LIST]
[*]The '*[COLOR="#0000CD"]man <some command>[/COLOR]*' is the best way to find details on the usage of a command (other than looking up internet, which is often even better).
[*]For short description of usage, use - "*[COLOR="#0000CD"]<command> --help[/COLOR]*".
[*]To get a list of possible commands for a task, use "*[COLOR="#0000CD"]apropos <keyword>[/COLOR]*". For example - "*[COLOR="#0000CD"]apropos network[/COLOR]*".
[/LIST]


**PS:**
By the way, the correct usage of those ifconfig commands is - "*[COLOR="#0000CD"]sudo ifconfig <interface name> <action>[/COLOR]*". For example, for interface wlan0 -
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

---

### Post by Warren Hill on 2013-07-16
> **varunendra said:**
> DHCP assigned IPs are leased for a definite amount of time. The ifconfig up/down or ifup/ifdown commands just disable or enable the interface, and get the same address again if the lease is not expired yet (and not taken by another device yet).


Not only is this statement true most decent DHCP servers will try to assign the same IP to a given device each time it connects.  It's not guaranteed because there is a limited pool of IP addresses available but where its possible preserving connections makes things easier.

It's normal even if you turn your computer off for several hours that you will get the same IP next time you turn back on even if the DHCP time-out has expired.  At least in situations where you have relatively few devices.

In a public place such as a university library however where lots of devices are connecting for relatively short periods of time however this is probably not true.

---

