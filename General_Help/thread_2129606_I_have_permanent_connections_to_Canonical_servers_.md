---
title: "I have permanent connections to Canonical servers How to turn them off?"
date: 2013-03-26
forum: General Help
---

### Post by Psil0cybin on 2013-03-26
[FONT=Ubuntu Beta][COLOR=#333333]After installing ubuntu 12.04, removing the video lens, etc I still notice that running
[/COLOR][/FONT]
[FONT=Ubuntu Beta][COLOR=#333333] lsof -i
[/COLOR][/FONT]
gives me

> ubuntu-ge 
>mulberry.canonical.com:http (CLOSE_WAIT)

Thus I seem to be always constantly calling home...
Why are there permanent connections, and how could I stop this from starting up on my machine?
I understand its for timezones, but If my computer is only within one constant area, should I really be wasting my bandwidth on that?

I was wondering if there is a method for turning this off in 12.04

Is it a bad idea to turn it off by the following method: (as I heard it might only work for 12.10?)


[LIST=1]
[*]Open your dconf editor: $ dconf-edditor
[*]Navigate to the com/ubuntu/geoip option
[*]Set the value of geoip-url to nothing "".
[/LIST]
or

$ gsettings set com.ubuntu.geoip geoip-url ""# check success    $ gsettings list-recursively | grep geoipcom.ubuntu.geoip geoip-url ''[COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR]

---

### Post by matt_symes on 2013-03-26
Hi
> 
[FONT=Ubuntu Beta][COLOR=#333333]lsof -i
[/COLOR][/FONT]
gives me

                                                         ubuntu-ge 
>mulberry.canonical.com:http (CLOSE_WAIT)

The port is in a CLOSE_WAIT state.

> Thus I seem to be always constantly calling home...

Are you sure ? Have you checked by using netstat to get the port and the using iftop with a filter to view traffic on that port and interface ?

```
sudo apt-get install iftop
```

```
matthew-S206:/home/matthew % netstat -plan | grep WAIT     
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        1      0 192.168.0.111:44939     81.171.118.141:119      CLOSE_WAIT  4468/slrn       
tcp        1      0 192.168.0.111:**38400**     66.196.66.213:80        CLOSE_WAIT  2629/firefox    
matthew-S206:/home/matthew % 

```

```
sudo iftop -i eth0 -f "src port **38400**"
```

My wireless interface is currently called eth0. I suspect yours is most probably called wlan0 (assuming you are connecting wirelessly).

> Why are there permanent connections, and how could I stop this from starting up on my machine?

Are you sure it's not just a bug in the program where it's not sending it's FIN ACK to close the connection correctly ? 

> I understand its for timezones, but If my computer is only within one  constant area, should I really be wasting my bandwidth on that?

My point is, have you actually checked to see if this is a bug or if there actually is traffic going across ?

If there is no traffic then you are not wasting bandwidth.

The fix you posted should stop the connection as far as i am aware. I have not seen it being 12.10 specific but i may be wrong here as i cannot check. So i am open to correction.

Kind regards

---

### Post by Psil0cybin on 2013-03-27
I keep getting this result
$ gsettings set com.ubuntu.geoip geoip-url ""
No such schema 'com.ubuntu.geoip'

I looked in the dconf settings and i cannot find the ones specified...what does this mean?
Upon typing it again
it now says

mistletoe.canonical.com:http (ESTABLISHED)
so I know its an active connection.

---

