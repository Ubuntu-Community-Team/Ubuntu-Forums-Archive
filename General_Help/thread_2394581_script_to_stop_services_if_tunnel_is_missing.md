---
title: "script to stop services if tunnel is missing"
date: 2018-06-18
forum: General Help
---

### Post by derekcentrico on 2018-06-18
I'd like to have specific processes if the VPN tunnel connection is lost.

I created a service for openvpn.  However, it won't recognize a stale openvpn connection where it's still showing as connected but essentially dead, or one that has terminated to restart it.

I'm not sure how to write in something to check the status like by sending a ping or something through the tunnel.  But, I took a stab at the no TUN0 things though.  I haven't tested this as I'm just trying to learn what I can and piece something together.

```
#bin/bash

for i in tun0
  do OUT="$(ip a show $i up)";


    if [[ $OUT == *"does not exist."* ]]; then
      echo "$i is down"


#stop tunnel-using services
    service NAMEHERE stop

    service NAMEHERE stop


#restart tunnel
    service openvpn start


#retart tunnel-using services
    service NAMEHERE start
    service NAMEHERE start

    else
      echo "$i is up"    
    fi

done
```

Any advice on being able to stop services when tun0 is basically dead or totally gone would be greatly appreciated.

---

### Post by derekcentrico on 2018-06-19
Allright trying to educate myself and came up with this solution.  The only negative I can think of would be if the IP on the VPN interface changes it will end up having a problem.

Thoughts?

```
#bin/bash

for i in tun0
  do OUT="$(ip a show $i up)";




    if [[ $OUT == *"does not exist."* ]]; then
      echo "$i is down"




#stop tunnel-using services
    service NAMEHERE stop


    service NAMEHERE stop




#restart tunnel
    service openvpn start




#retart tunnel-using services
    service NAMEHERE start
    service NAMEHERE start


    else
      echo "$i is up"    
    fi








ping -c1 -w5 -q 10.7.7.228  > /dev/null; echo $?
 
if [ $? -eq 0 ]
then
	echo "ok"
else


killall openvpn
  service NAMEHERE stop
    service NAMEHERE stop


  service NAMEHERE start
  service NAMEHERE start
    service NAMEHERE start


fi


done



```

---

