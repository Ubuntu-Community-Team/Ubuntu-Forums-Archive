---
title: "software centre problem please help"
date: 2013-06-10
forum: General Help
---

### Post by jetli68 on 2013-06-10
hi there i  was installing  software through  software centre on  12.04 

and all was ok  but now  one app is stuck  in the prosess  tab its been sitting there for  15 hours  at the same  spot 

i have tried  .and now it will not let me install any thing esles  with the deb package installer  or  via terminal 

i get  a mess age saying can not use   more than  one   program at  the time  please close  one  this is when i  use GDEBI

i have closed  it  ended the prosses in system monitor  i have even restarted  the system but  still no look nd every time i open the software centre   the app is still there in prossing 

and  i can not  use  terminal  as i get this mes 

```
can not lock admin dir  is there another prosses using it ?
```

tia

for any help with this

jet

---

### Post by Frogs Hair on 2013-06-10
Hello [COLOR=#000000]jetli68,

Close the software center, open the terminal , copy and paste the output of the following command here using code tags.  ```
sudo apt-get update [/COLOR]
``` This should give an idea of what the problem is and possible instructions in the form of further commands.

---

### Post by jetli68 on 2013-06-10
i can not use  terminal i get this   error message 


can not lock admin dir  is there another prosses using it ?

---

### Post by jetli68 on 2013-06-10
terminal message after i type  that is
unable to lock directory /var/dpkg/lock/ -open (11: resource temerarily unaviable

---

### Post by Frogs Hair on 2013-06-10
I don't know if it will help but what was the package you were installing ?  If you can open  the terminal try the following . ```
sudo apt-get -f install
```

If that fails try the following one at a time .```
 sudo rm -rf /var/lib/apt/lists/*
``````
sudo apt-get clean
``````
 sudo apt-get update
```

---

### Post by jetli68 on 2013-06-10
none i typing to teminal works i keep getting the same message

```
unable to lock directory /var/dpkg/lock/ -open (11: resource temerarily unaviable
```

the program i was trying to install was

xextractor   

tia

jet

---

### Post by Frogs Hair on 2013-06-10
From this source : [http://mirkolofio.wordpress.com/2012/03/28/unlock-varlibdpkglock-when-youre-locked-out/](http://mirkolofio.wordpress.com/2012/03/28/unlock-varlibdpkglock-when-youre-locked-out/)



 ```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
```

---

### Post by jetli68 on 2013-06-10
> **Frogs Hair said:**
> From this source : [http://mirkolofio.wordpress.com/2012/03/28/unlock-varlibdpkglock-when-youre-locked-out/](http://mirkolofio.wordpress.com/2012/03/28/unlock-varlibdpkglock-when-youre-locked-out/)



 ```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
```


thank you  so much that worked spot on  thank you

---

### Post by Frogs Hair on 2013-06-10
Glad it worked !  If the software center gets stuck don't attempt to use other package managers such as Gdebi or synaptic.

---

