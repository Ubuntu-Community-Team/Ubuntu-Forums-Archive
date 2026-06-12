---
title: "Swap over network  NBD-server client"
date: 2007-07-08
forum: General Help
---

### Post by 13ojo on 2007-07-08
Howdy all.

Thought i'd contribute this to all you diskless pc wannabes out there. I've finally got a decently stable system running.

I did this by using a network swap, 128mbram is a little to much for feisty to run nicely. Using the terminal and apt-get would crash it big time on the standard desktop.

This of course needs a server setup as always. (how are you booting diskless without it).
[B][U]
SERVER[/U][/B]

```
apt-get install nbd-server

```

You need to make a swap file to do this with, where you choose is up to you, i put mine inside the NFSroot directory of my netbooter, But i believe anywhere will do. (eg i input the next commands after cd'ing to the folder containing all the diskless clients files.)
```

mkdir swap/
dd if=/dev/zero of=swap/swap count=256 bs=1024k
chmod 777 swap
mkswap swap/swap

```

Next command initiliazes NBD server. the number is the port number.

```
nbd-server 1100 /*FULLPATHTOROOT*/swap/swap
```

_**CLIENT**_

```
apt-get install nbd-client
nbd-client 192.168.0.33 1100 /dev/nbd0
mkswap /dev/nbd0
swapon /dev/nbd0
cat /proc/swaps
>>Filename                                Type            Size    Used    Priority
>>/dev/nbd0                               partition       262136  0       -1

```


if your cat returns that it should be working nicely :D.

Hope that helps. If it ever asks for Negotiation and seems like a prompt or hangs, it means 1) wrong port 2) you didn't use mkswap on server side.

For some reason you need to do it on both client and server, that's not listed anywhere on the web but it's how i got it working :D.

ENJOY

---

