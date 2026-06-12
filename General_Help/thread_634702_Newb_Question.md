---
title: "Newb Question"
date: 2007-12-08
forum: General Help
---

### Post by Salazar420 on 2007-12-08
Call me stupid, but isn't the /tmp directory supposed to be empty upon installation? I just got a new laptop and it has certain things already in the tmp, even when running from the live CD. I reinstall, but it's still there (much to my dismay). Anyway, I restart the laptop -- armed with the possibly inacurate knowlege that a restart will erase everything in the /tmp directory -- but to no improvement. I'll list all of the /tmp directory's contents; however, not recursively. Any information would be EXTREMELY helpful.
> 
ubuntu@ubuntu:~$ ls /tmp/
gconfd-ubuntu   mapping-ubuntu  raided-map
keyring-Ii4tUI  mounted-map     ssh-nyYdpI8014
libgksu-wwcLs9  orbit-ubuntu    virtual-ubuntu.Y6fvZi
ubuntu@ubuntu:~$ 

---

### Post by ray bot on 2007-12-08
Yeah, that seems perfectly normal.  Your /tmp will never be empty, because all kinds of programs store temporary data there while they're running.  If you want to see which programs are using those files, open a terminal and type ```
lsof +D /tmp
```

---

### Post by Salazar420 on 2007-12-08
> **ray bot said:**
> Yeah, that seems perfectly normal.  Your /tmp will never be empty, because all kinds of programs store temporary data there while they're running.  If you want to see which programs are using those files, open a terminal and type ```
lsof +D /tmp
```

Thanks for the feedback. Btw, the output reads:

> xenouser@XeNoToP:~$ lsof +D /tmp
COMMAND    PID     USER   FD   TYPE     DEVICE SIZE     NODE NAME
x-session 6062 xenouser   13u  unix 0xd408d200         18476 /tmp/orbit-xenouser/linc-17ae-0-15e8f8bb88adc
x-session 6062 xenouser   14u  unix 0xcfcb4e00         18708 /tmp/orbit-xenouser/linc-17ae-0-15e8f8bb88adc
x-session 6062 xenouser   15u  unix 0xcf250c00         18724 /tmp/.ICE-unix/6062
x-session 6062 xenouser   21u  unix 0xd00aca00         18870 /tmp/.ICE-unix/6062
x-session 6062 xenouser   22u  unix 0xce563400         18968 /tmp/.ICE-unix/6062
x-session 6062 xenouser   23u  unix 0xce87a000         19103 /tmp/.ICE-unix/6062
x-session 6062 xenouser   24u  unix 0xc6f3dc00         22826 /tmp/.ICE-unix/6062
x-session 6062 xenouser   25u  unix 0xcdbcf800         19352 /tmp/.ICE-unix/6062
x-session 6062 xenouser   26u  unix 0xcd8aee00         19354 /tmp/.ICE-unix/6062
x-session 6062 xenouser   27u  unix 0xccc05800         19431 /tmp/.ICE-unix/6062
x-session 6062 xenouser   28u  unix 0xcb4c1400         19705 /tmp/.ICE-unix/6062
x-session 6062 xenouser   29u  unix 0xccc5d400         21002 /tmp/.ICE-unix/6062
x-session 6062 xenouser   30u  unix 0xce25a000         53713 /tmp/.ICE-unix/6062
x-session 6062 xenouser   32u  unix 0xd1c34c00         23083 /tmp/.ICE-unix/6062
gconfd-2  6105 xenouser    6u  unix 0xd263c600         18706 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   11u  unix 0xcfcb4800         18466 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   12wW  REG        8,2  625 11830401 /tmp/gconfd-xenouser/lock/ior
gconfd-2  6105 xenouser   13u  unix 0xcb32d800         51329 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   15u  unix 0xcefdb400         18764 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   17u  unix 0xcf783c00         18873 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   19u  unix 0xd1e3f400         23077 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   21u  unix 0xce563e00         18979 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   23u  unix 0xce563200         19107 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   25u  unix 0xcd93da00         19150 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   27u  unix 0xce1b0800         19281 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   29u  unix 0xce1b0200         19359 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   31u  unix 0xce1d0a00         19365 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   33u  unix 0xccc05600         19392 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   35u  unix 0xcc804000         19434 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   37u  unix 0xcd9c8400         19716 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   39u  unix 0xcb4c1200         19889 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   41u  unix 0xccc5da00         21005 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   43u  unix 0xc9a0ae00         21040 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   45u  unix 0xc9073000         21070 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   47u  unix 0xc9304600         21096 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   49u  unix 0xc9252a00         21111 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   52u  unix 0xd0bf7c00         53716 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gconfd-2  6105 xenouser   57u  unix 0xce1b6a00         22829 /tmp/orbit-xenouser/linc-17d9-0-282f3dd474742
gnome-key 6108 xenouser    3u  unix 0xcf250400         18733 /tmp/keyring-aWRwbT/socket
gnome-set 6112 xenouser   13u  unix 0xcefdba00         18765 /tmp/orbit-xenouser/linc-17e0-0-3b8d3d442c14c
gnome-set 6112 xenouser   14u  unix 0xcfcb4a00         18768 /tmp/orbit-xenouser/linc-17e0-0-3b8d3d442c14c
sh        6117 xenouser   15u  unix 0xcf250c00         18724 /tmp/.ICE-unix/6062
esd       6118 xenouser    4u  unix 0xcf783800         18785 /tmp/.esd/socket
esd       6118 xenouser    5u  unix 0xcefdbc00         18796 /tmp/.esd/socket
esd       6118 xenouser    6u  unix 0xcab35000         20084 /tmp/.esd/socket
esd       6118 xenouser    7u  unix 0xc9e51400         21014 /tmp/.esd/socket
esd       6118 xenouser    8u  unix 0xce365e00         19118 /tmp/.esd/socket
esd       6118 xenouser    9u  unix 0xcd57f400         19415 /tmp/.esd/socket
esd       6118 xenouser   10u  unix 0xcd9c8200         19563 /tmp/.esd/socket
esd       6118 xenouser   11u  unix 0xcbc9ce00         19585 /tmp/.esd/socket
esd       6118 xenouser   12u  unix 0xcbc9ca00         19641 /tmp/.esd/socket
esd       6118 xenouser   13u  unix 0xc9316200         21133 /tmp/.esd/socket
esd       6118 xenouser   14u  unix 0xc892f000         21208 /tmp/.esd/socket
esd       6118 xenouser   15u  unix 0xc892fa00         21229 /tmp/.esd/socket
esd       6118 xenouser   16u  unix 0xc92cee00         50546 /tmp/.esd/socket
esd       6118 xenouser   17u  unix 0xd7a7aa00         53745 /tmp/.esd/socket
esd       6118 xenouser   18u  unix 0xc9f0e400         22836 /tmp/.esd/socket
gnome-pan 6123 xenouser   12u  unix 0xce1d0000         18980 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   13u  unix 0xce1d0400         18983 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   15u  unix 0xce1d0e00         19548 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   20u  unix 0xce4de000         20079 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   25u  unix 0xc9a0a000         21131 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   27u  unix 0xc9316e00         21148 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   28u  unix 0xc92ce800         21227 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
gnome-pan 6123 xenouser   33u  unix 0xce25a800         27887 /tmp/orbit-xenouser/linc-17eb-0-2d482efaabc45
nautilus  6125 xenouser   12u  unix 0xce365000         19108 /tmp/orbit-xenouser/linc-17ed-0-1f8bc5459526c
nautilus  6125 xenouser   13u  unix 0xce1b6e00         19111 /tmp/orbit-xenouser/linc-17ed-0-1f8bc5459526c
nautilus  6125 xenouser   18u  unix 0xccc5dc00         19550 /tmp/orbit-xenouser/linc-17ed-0-1f8bc5459526c
gnome-vol 6129 xenouser   12u  unix 0xcf783400         18874 /tmp/orbit-xenouser/linc-17ee-0-2d482efa63c1b
gnome-vol 6129 xenouser   13u  unix 0xce87ae00         18877 /tmp/orbit-xenouser/linc-17ee-0-2d482efa63c1b
bonobo-ac 6143 xenouser    3u  unix 0xce1d0c00         19545 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   14u  unix 0xcd9c8600         19540 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   15u  unix 0xcd9c8e00         19546 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   18u  unix 0xcb26c000         20054 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   19u  unix 0xca9fb000         19895 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   21u  unix 0xccc5de00         53722 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   23u  unix 0xc9e51800         21023 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   24u  unix 0xc8d0a000         21117 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   28u  unix 0xc9ab4e00         21107 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   30u  unix 0xc8d0a400         21154 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
bonobo-ac 6143 xenouser   34u  unix 0xc9073a00         21076 /tmp/orbit-xenouser/linc-17ff-0-29e844d1663d
gnome-vfs 6172 xenouser   13u  unix 0xcd93de00         19151 /tmp/orbit-xenouser/linc-181c-0-6dc2fd9b7e34
gnome-vfs 6172 xenouser   14u  unix 0xce594c00         19154 /tmp/orbit-xenouser/linc-181c-0-6dc2fd9b7e34
vino-sess 6175 xenouser   12u  unix 0xccc5d200         19360 /tmp/orbit-xenouser/linc-181f-0-41ef5483890f6
vino-sess 6175 xenouser   13u  unix 0xcd57f600         19363 /tmp/orbit-xenouser/linc-181f-0-41ef5483890f6
update-no 6179 xenouser   12u  unix 0xce92f000         19366 /tmp/orbit-xenouser/linc-1823-0-41ef54838aa30
update-no 6179 xenouser   13u  unix 0xce87a400         19369 /tmp/orbit-xenouser/linc-1823-0-41ef54838aa30
evolution 6188 xenouser   12u  unix 0xcb4bba00         19718 /tmp/orbit-xenouser/linc-182c-0-1efced0454bbc
evolution 6188 xenouser   13u  unix 0xcbc84200         19736 /tmp/orbit-xenouser/linc-182c-0-1efced0454bbc
evolution 6188 xenouser   21u  unix 0xcab35c00         20056 /tmp/orbit-xenouser/linc-182c-0-1efced0454bbc
evolution 6188 xenouser   25u  unix 0xc9316a00         21162 /tmp/orbit-xenouser/linc-182c-0-1efced0454bbc
nm-applet 6194 xenouser   11u  unix 0xccc05400         19393 /tmp/orbit-xenouser/linc-1832-0-731f305ca7047
nm-applet 6194 xenouser   12u  unix 0xce594600         19396 /tmp/orbit-xenouser/linc-1832-0-731f305ca7047
gnome-scr 6195 xenouser   11u  unix 0xcd93d000         19282 /tmp/orbit-xenouser/linc-1828-0-530068ffab37b
gnome-scr 6195 xenouser   12u  unix 0xcd57f000         19285 /tmp/orbit-xenouser/linc-1828-0-530068ffab37b
gnome-pow 6201 xenouser   12u  unix 0xcc804800         19435 /tmp/orbit-xenouser/linc-182d-0-2541ecc817e3b
gnome-pow 6201 xenouser   13u  unix 0xcd973400         19438 /tmp/orbit-xenouser/linc-182d-0-2541ecc817e3b
trashappl 6213 xenouser   11u  unix 0xcb32d400         19890 /tmp/orbit-xenouser/linc-1845-0-321e830e3c237
trashappl 6213 xenouser   12u  unix 0xcafdc800         19893 /tmp/orbit-xenouser/linc-1845-0-321e830e3c237
trashappl 6213 xenouser   13u  unix 0xca9fb800         19897 /tmp/orbit-xenouser/linc-1845-0-321e830e3c237
trashappl 6213 xenouser   18u  unix 0xca05ae00         20077 /tmp/orbit-xenouser/linc-1845-0-321e830e3c237
evolution 6230 xenouser   12u  unix 0xce4de200         21006 /tmp/orbit-xenouser/linc-1856-0-39d1bc3066f74
evolution 6230 xenouser   13u  unix 0xcb32d600         21009 /tmp/orbit-xenouser/linc-1856-0-39d1bc3066f74
evolution 6230 xenouser   14u  unix 0xc9e51600         21025 /tmp/orbit-xenouser/linc-1856-0-39d1bc3066f74
evolution 6230 xenouser   20u  unix 0xc92ce200         21158 /tmp/orbit-xenouser/linc-1856-0-39d1bc3066f74
evolution 6230 xenouser   21u  unix 0xc914bc00         27883 /tmp/orbit-xenouser/linc-1856-0-39d1bc3066f74
mapping-d 6232 xenouser    3u  unix 0xca05a400         20066 /tmp/mapping-xenouser
mapping-d 6232 xenouser    4u  unix 0xca05a600         20070 /tmp/mapping-xenouser
evolution 6249 xenouser   10u  unix 0xc9a0a600         21041 /tmp/orbit-xenouser/linc-1869-0-39d1bc30e3983
evolution 6249 xenouser   11u  unix 0xce4de600         21044 /tmp/orbit-xenouser/linc-1869-0-39d1bc30e3983
evolution 6249 xenouser   16u  unix 0xc9316400         21156 /tmp/orbit-xenouser/linc-1869-0-39d1bc30e3983
evolution 6249 xenouser   18u  unix 0xcb32dc00         21160 /tmp/orbit-xenouser/linc-1869-0-39d1bc30e3983
evolution 6249 xenouser   22u  unix 0xdaa66c00         27885 /tmp/orbit-xenouser/linc-1869-0-39d1bc30e3983
mixer_app 6254 xenouser   11u  unix 0xc914b000         21097 /tmp/orbit-xenouser/linc-186e-0-6a5602bd53879
mixer_app 6254 xenouser   12u  unix 0xcab35800         21100 /tmp/orbit-xenouser/linc-186e-0-6a5602bd53879
mixer_app 6254 xenouser   13u  unix 0xc9ab4a00         21109 /tmp/orbit-xenouser/linc-186e-0-6a5602bd53879
mixer_app 6254 xenouser   15u  unix 0xcafdc000         21225 /tmp/orbit-xenouser/linc-186e-0-6a5602bd53879
gnome-net 6256 xenouser   11u  unix 0xc9073200         21071 /tmp/orbit-xenouser/linc-1870-0-6a5602bd3df2a
gnome-net 6256 xenouser   12u  unix 0xc914ba00         21074 /tmp/orbit-xenouser/linc-1870-0-6a5602bd3df2a
gnome-net 6256 xenouser   13u  unix 0xc9ab4000         21078 /tmp/orbit-xenouser/linc-1870-0-6a5602bd3df2a
gnome-net 6256 xenouser   16u  unix 0xcbc84a00         21145 /tmp/orbit-xenouser/linc-1870-0-6a5602bd3df2a
multiload 6258 xenouser   11u  unix 0xc9252e00         21112 /tmp/orbit-xenouser/linc-1872-0-6a5602bd5747e
multiload 6258 xenouser   12u  unix 0xcbc84000         21115 /tmp/orbit-xenouser/linc-1872-0-6a5602bd5747e
multiload 6258 xenouser   13u  unix 0xc8d0a800         21119 /tmp/orbit-xenouser/linc-1872-0-6a5602bd5747e
multiload 6258 xenouser   15u  unix 0xcbc84600         21129 /tmp/orbit-xenouser/linc-1872-0-6a5602bd5747e
/usr/bin/ 6516 xenouser    8u  unix 0xc9f0ea00         22830 /tmp/orbit-xenouser/linc-1974-0-1c9279ed5d05f
/usr/bin/ 6516 xenouser   15u  unix 0xce25aa00         22833 /tmp/orbit-xenouser/linc-1974-0-1c9279ed5d05f
metacity  6518 xenouser   11u  unix 0xd1c34400         23078 /tmp/orbit-xenouser/linc-1976-0-6ab04d2ef2b5f
metacity  6518 xenouser   12u  unix 0xd1c34600         23081 /tmp/orbit-xenouser/linc-1976-0-6ab04d2ef2b5f
firefox-b 7037 xenouser   17u  unix 0xcb32d200         51330 /tmp/orbit-xenouser/linc-1b7d-0-4e11a1be163c4
firefox-b 7037 xenouser   18u  unix 0xd7a7a200         51333 /tmp/orbit-xenouser/linc-1b7d-0-4e11a1be163c4
gnome-ter 7288 xenouser   12u  unix 0xce25a200         53717 /tmp/orbit-xenouser/linc-1c78-0-497680443230
gnome-ter 7288 xenouser   13u  unix 0xc52a5400         53720 /tmp/orbit-xenouser/linc-1c78-0-497680443230
gnome-ter 7288 xenouser   14u  unix 0xc52a5c00         53724 /tmp/orbit-xenouser/linc-1c78-0-497680443230

I know: that probably should have been an attachment in its own. Anyway, there's that command's feedback. This is all mundane? Do you think you could make a comparison? So, I hope I didn't exploit any of my own vulnerabilities by posting that (probably a typical newb-muse). lolz

---

### Post by ray bot on 2007-12-08
Yeah, that all looks pretty normal.  I don't think there's any cause for concern here.

---

### Post by Salazar420 on 2007-12-11
Right on. Thanks again.

---

### Post by Salazar420 on 2007-12-30
See, what concerns me is the stuff that's running. I recognize SSH (newb perspective) as a means of accessing my computer remotely, and mapping-xenouser is a bit scary, to be honest. Also, Having ran etherape on other systems, I don't seem to get all that many visuals without certain programs operating, but look at this: [[IMG]http://img256.imageshack.us/img256/3601/screenshot19xg1.th.png[/IMG]](http://img256.imageshack.us/my.php?image=screenshot19xg1.png)

...and that's with my wireless disabled via (Fn + F2).

---

