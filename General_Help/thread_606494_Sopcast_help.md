---
title: "Sopcast help"
date: 2007-11-08
forum: General Help
---

### Post by illbashu on 2007-11-08
ok, i got sopcast working (the terminal one)... but the problem is when i used the code given to try it out and see if it was working, the channel got stuck, like how do i change the channel? this is the defult one given in the readme
```
./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908 > /dev/null
```

and this is the one that i am trying to get the code is 
```
./sp-sc-auth sop://broker.sopcast.com:3912/6003 3908 8909 > /dev/null
```

the sopcast link i am trying to get woking is 
```
sop://broker.sopcast.com:3912/6003
```

am i doing something wrong? any help will be greatly appreciated..

---

### Post by etola on 2007-11-08
> **illbashu said:**
> ok, i got sopcast working (the terminal one)... but the problem is when i used the code given to try it out and see if it was working, the channel got stuck, like how do i change the channel? this is the defult one given in the readme
```
./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908 > /dev/null
```

and this is the one that i am trying to get the code is 
```
./sp-sc-auth sop://broker.sopcast.com:3912/6003 3908 8909 > /dev/null
```

the sopcast link i am trying to get woking is 
```
sop://broker.sopcast.com:3912/6003
```

am i doing something wrong? any help will be greatly appreciated..

ok 2 questions :

1/ while trying to play the stream are you connecting to the correct port by :

mplayer [http://localhost:8908/tv.asf](http://localhost:8908/tv.asf) ---> this is the old stream
mplayer [http://localhost:8909/tv.asf](http://localhost:8909/tv.asf) ---> this is the new stream.

2/ are you killing the old stream ?

I wrote a small script that connects to a channel and kills the stream when you quit. 
You can get it from [http://cvlab.epfl.ch/~tola/files/code/sopcast](http://cvlab.epfl.ch/~tola/files/code/sopcast)

note: you can check if there is a stream still running by

```
ps uxaf | grep sp-sc-auth
```

and kill the process...

---

### Post by illbashu on 2007-11-08
after i ran your script i have not been able to run sopcast :(  this is what i get

```
raza@raza-desktop:~/Desktop/sp-auth$ ./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908
detect MTU=4c4
Connection=11   Connection=11
i=0   51
ipExternal:7a4defd8  Internal:20aa8c0  portLocal:36494    portExternal1:36494    External2:36494  linkType:51
tm2.sopcast.com proto=17
adv=400
TD1=4294966971-325:  1194567629:400:566720637
tm2.sopcast.com proto=17
adv=182
TD1=4294966970-326:  1194567629:182:566720856
Average difference=4294966970
4294966970
4294966970
3dbedaf0 28ba0b0d
Not valid ID
2ccc1b34 10b28d3c
sop://broker.sopcast.com:3912/99
system channelID=99
detect MTU=4c4
localaddr:      c0a80a02:29129, externaladdr:d8ef4d7a:29129
hook_broker_connect:msgType=22
hook_broker_connect:npeers=32
d92a3b1d 3965323a d92abb1d c75f--1dbb2ad9:51039/4501a8c0:5284 size=28
da016af6 d134ce6a da016af6 181f--f66a01da:6175/ce01a8c0:6175 size=28
da024055 bc259d40 da02c055 a9ec--55c002da:43500/202a8c0:5156 size=28
da0345b3 750b6e44 da0345b3 0fd2--b34503da:4050/f90b040a:8099 size=28
da037314 1e2c1372 da03f314 63a6--14f303da:25510/d1d1e6db:6886 size=28
da043052 4e79e030 da043052 049e--523004da:1182/d100a8c0:7288 size=28
da046d53 5b3b786c da04ed53 81c3--53ed04da:33219/200a8c0:5368 size=28
da072bc9 b871302a da072bc9 a88a--c92b07da:43146/c8f11bde:6459 size=28
da073103 3e49dd30 da073103 cfaf--33107da:53167/1d1f10ac:5979 size=28
da07464f 7eca2f8b da07464f 3440--4f4607da:13376/4f4607da:13376 size=28
da091fc6 8c509e1e da091fc6 0422--c61f09da:1058/6501a8c0:4254 size=28
da0a2b23 7f21552a da0a2b23 ed8c--232b0ada:60812/12ac01c0:7181 size=28
da0a4226 4231ead3 da0a4226 4d44--26420ada:19780/201a8c0:4764 size=28
da0e7fa1 5c50487e da0e7fa1 104d--a17f0eda:4173/a17f0eda:4173 size=28
da0f3835 3a400538 da0f3835 1581--35380fda:5505/a946a8c0:5505 size=28
da0f3fce 81504f3e da0fbfce c740--cebf0fda:51008/3bc1a8c0:5737 size=28
7bf91f71 c1296ff6 7bf91f71 a856--711ff97b:43094/ac5536de:9761 size=28
3d8d00d7 c155df00 3d8d00d7 33cf--d7008d3d:13263/5b090d0a:11090 size=28
7b347f5e c2118c7e 7b347f5e 2c78--5e7f347b:11384/5e7f347b:11384 size=28
db81446f c3021b44 db81c46f 39ef--6fc481db:14831/7700a8c0:9895 size=28
3d913c4a c3107e3c 3d913c4a 3efc--4a3c913d:16124/6701a8c0:6227 size=28
3cf13d47 c4743857 3cf1bd47 0fa9--47bdf13c:4009/200a8c0:4009 size=28
de55172d c549d316 de55972d 905a--2d9755de:36954/1b5528d2:6900 size=28
4c175411 c80ffc54 4c17d411 1975--11d4174c:6517/202a8c0:6517 size=28
deb53fc6 c813ea3e deb5bfc6 1d15--c6bfb5de:7445/c6bfb5de:7445 size=28
55e5481c c84d4648 55e5481c 2fa2--1c48e555:12194/1c48e555:12194 size=28
deed0622 c9131d06 deed8622 34e0--2286edde:13536/2286edde:13536 size=28
56852c81 c947642c 5685ac81 d9a7--81ac8556:55719/4101a8c0:13200 size=28
7d4334ce c953db34 7d43b4ce ddeb--ceb4437d:56811/b201a8c0:7201 size=28
75161887 c970b818 75161887 2a71--87181675:10865/87181675:10865 size=28
792e71e6 c97e4c70 792ef1e6 9e21--e6f12e79:40481/f5a130de:6126 size=28
da1a4131 ca02e040 da1a4131 5b4f--31411ada:23375/300a8c0:4264 size=28
broker connection closed retv=-13
check_peers_sysch:d92abb1d:51039:d92a3b1d 3965323a
check_peers_sysch:da016af6:6175:da016af6 d134ce6a
check_peers_sysch:da02c055:43500:da024055 bc259d40
check_peers_sysch:da0345b3:4050:da0345b3 750b6e44
check_peers_sysch:da03f314:25510:da037314 1e2c1372
check_peers_sysch:da043052:1182:da043052 4e79e030
check_peers_sysch:da04ed53:33219:da046d53 5b3b786c
check_peers_sysch:da072bc9:43146:da072bc9 b871302a
check_peers_sysch:da073103:53167:da073103 3e49dd30
check_peers_sysch:da07464f:13376:da07464f 7eca2f8b
check_peers_sysch:da091fc6:1058:da091fc6 8c509e1e
da024055 bc259d40  55c002da:43500 NEWACCEPT len=20
da024055 bc259d40  NEW ACCEPT
channel ID=6098
tk:00000000 00000000
streamID=17d2
STOP QUIT
retv = 0
        spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=0
CHLST blockSize=0
566722533:566720530
detect MTU=4c4
raza@raza-desktop:~/Desktop/sp-auth$ sudo '/home/raza/Desktop/usr/lib' 
[sudo] password for raza:
sudo: /home/raza/Desktop/usr/lib: command not found
raza@raza-desktop:~/Desktop/sp-auth$ cd '/home/raza/Desktop/usr/lib' 
raza@raza-desktop:~/Desktop/usr/lib$ sudo cp -a libstdc++.so.5* /usr/lib
raza@raza-desktop:~/Desktop/usr/lib$ ./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908
bash: ./sp-sc-auth: No such file or directory
raza@raza-desktop:~/Desktop/usr/lib$ cd '/home/raza/Desktop/sp-auth' 
raza@raza-desktop:~/Desktop/sp-auth$ ./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908
detect MTU=4c4
Connection=11   Connection=11
i=0   51
ipExternal:7a4defd8  Internal:20aa8c0  portLocal:42225    portExternal1:42225    External2:42225  linkType:51
tm4.sopcast.com proto=17
adv=294
TD1=4294967065-231:  1194567841:294:566932649
tm4.sopcast.com proto=17
adv=82
TD1=4294967062-234:  1194567841:82:566932864
Average difference=4294967063
4294967063
4294967063
3dbedaf0 28ba0b0d
Not valid ID
24ac70b2 4d7533d5
sop://broker.sopcast.com:3912/99
system channelID=99
detect MTU=4c4
localaddr:      c0a80a02:19957, externaladdr:d8ef4d7a:19957
hook_broker_connect:msgType=22
hook_broker_connect:npeers=32
d90a6cd2 9728880d d90a6cd2 1cca--d26c0ad9:7370/d26c0ad9:7370 size=28
d92a3b1d 3965323a d92abb1d c75f--1dbb2ad9:51039/4501a8c0:5284 size=28
da000152 6c236900 da000152 1da8--520100da:7592/1d30100a:7592 size=28
da0005ed 81067f04 da0005ed 1cc0--ed0500da:7360/aabe140a:7360 size=28
da016af6 d134ce6a da016af6 181f--f66a01da:6175/ce01a8c0:6175 size=28
da024055 bc259d40 da02c055 a9ec--55c002da:43500/202a8c0:5156 size=28
da0345b3 750b6e44 da0345b3 0fd2--b34503da:4050/f90b040a:8099 size=28
da037314 1e2c1372 da03f314 63a6--14f303da:25510/d1d1e6db:6886 size=28
da043052 4e79e030 da043052 049e--523004da:1182/d100a8c0:7288 size=28
da072bc9 b871302a da072bc9 a88a--c92b07da:43146/c8f11bde:6459 size=28
da073103 3e49dd30 da073103 cfaf--33107da:53167/1d1f10ac:5979 size=28
da07464f 7eca2f8b da07464f 3440--4f4607da:13376/4f4607da:13376 size=28
da0776b2 ac4d3376 da0776b2 2f7d--b27607da:12157/6401a8c0:7282 size=28
da0a2b23 7f21552a da0a2b23 ed8c--232b0ada:60812/12ac01c0:7181 size=28
da0a4226 4231ead3 da0a4226 4d44--26420ada:19780/201a8c0:4764 size=28
da0e7fa1 5c50487e da0e7fa1 104d--a17f0eda:4173/a17f0eda:4173 size=28
3b331982 1f77dc18 3b331982 d1fa--8219333b:53754/90210ac:6217 size=28
7c5c43a1 1f98aa03 7c5c43a1 ac00--a1435c7c:44032/6401a8c0:11136 size=28
dcff1a97 2048c21a dcff1a97 ce41--971affdc:52801/6501a8c0:10875 size=28
3b385458 20790781 3b38d458 043f--58d4383b:1087/6401a8c0:6847 size=28
3b375af1 2162905a 3b37daf1 34f4--f1da373b:13556/f1da373b:13556 size=28
d0785531 2277e654 d0785531 f2a2--315578d0:62114/6500a8c0:6629 size=28
51c13249 230a6f32 51c13249 1666--4932c151:5734/4932c151:5734 size=28
db857ece 230cd67e db85fece 516e--cefe85db:20846/401a8c0:5326 size=28
7d735f80 231a355e 7d735f80 f577--805f737d:62839/6d00a8c0:7556 size=28
63e767de 232e13a4 63e7e7de eb1a--dee7e763:60186/6601a8c0:5556 size=28
de3e7851 233abc78 de3ef851 1459--51f83ede:5209/51f83ede:5209 size=28
411e3c0b 242d193c 411ebc0b c6c6--bbc1e41:50886/207a8c0:4594 size=28
530c3eca 24da6daf 50373302 3515--2333750:13589/2f01a8c0:13589 size=28
3ca4429a 26688842 3ca4c29a 23cc--9ac2a43c:9164/701a8c0:4228 size=28
ca6875bb 271b4f74 ca68f5bb 1a8b--bbf568ca:6795/59270a0a:6795 size=28
dde404ca 27229804 dde484ca 8527--ca84e4dd:34087/201a8c0:3902 size=28
broker connection closed retv=-13
check_peers_sysch:d90a6cd2:7370:d90a6cd2 9728880d
check_peers_sysch:d92abb1d:51039:d92a3b1d 3965323a
check_peers_sysch:da000152:7592:da000152 6c236900
check_peers_sysch:da0005ed:7360:da0005ed 81067f04
check_peers_sysch:da016af6:6175:da016af6 d134ce6a
check_peers_sysch:da02c055:43500:da024055 bc259d40
check_peers_sysch:da0345b3:4050:da0345b3 750b6e44
check_peers_sysch:da03f314:25510:da037314 1e2c1372
check_peers_sysch:da043052:1182:da043052 4e79e030
check_peers_sysch:da072bc9:43146:da072bc9 b871302a
check_peers_sysch:da073103:53167:da073103 3e49dd30
d90a6cd2 9728880d  d26c0ad9:7370 NEWACCEPT len=20
d90a6cd2 9728880d  NEW ACCEPT
da024055 bc259d40  sio->hook:-30
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB


AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAa


Got CHannel list!!!!!!!!!!!
retv = -43
        spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=-43
CHLST blockSize=28648
566934588:566934588
channel ID=6098
tk:00000000 00000000
streamID=17d2
detect MTU=4c4
raza@raza-desktop:~/Desktop/sp-auth$ ./sp-sc-auth sop://broker.sopcast.com:3912/6098 3908 8908
detect MTU=4c4
Connection=11   Connection=11
i=0   51
ipExternal:7a4defd8  Internal:20aa8c0  portLocal:37698    portExternal1:37698    External2:37698  linkType:51
tm2.sopcast.com proto=17
adv=518
TD1=4294966971-325:  1194567876:518:566967519
tm2.sopcast.com proto=17
adv=151
TD1=642-4294966654:  1194567877:151:566967919
Average difference=158
158
158
3dbedaf0 28ba0b0d
Not valid ID
4a7614e6 906fb63b
sop://broker.sopcast.com:3912/99
system channelID=99
channel ID=6098
tk:00000000 00000000
streamID=17d2
detect MTU=4c4
localaddr:      c0a80a02:27061, externaladdr:d8ef4d7a:27061
STOP QUIT
retv = 0
        spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=0
CHLST blockSize=0
566970686:566968077
detect MTU=4c4
```

---

### Post by etola on 2007-11-08
wow. you got quite a message here. sorry to say but I have no idea what this is about.

---

### Post by illbashu on 2007-11-09
isn't there any way to reverse your code? is there like a roll back like in windows?

---

### Post by illbashu on 2007-11-10
BUMP! can someone help?

---

### Post by etola on 2007-11-10
> **illbashu said:**
> isn't there any way to reverse your code? is there like a roll back like in windows?

I didn't understand this message ...

---

