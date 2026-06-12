---
title: "dpkg: subprocess post-installation script returned error exit status 139"
date: 2008-06-06
forum: General Help
---

### Post by jonwatson on 2008-06-06
Hi All,

I seem to have completely borked my package system and can't get out of it.

Something went wrong with a recent install of libc6. I don't know what, it just puked on me and ever since then I cannot use apt-get or dpkg. If I attempt to apt-get install anything, I am told that:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

When I attempt to run dpkg --configure -a I get this:

```
jdw@zeus:~$ sudo dpkg --configure -a
Setting up libc6 (2.7-10ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: &#65533;J&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;J&#65533; is not a known library type
/sbin/ldconfig.real: &#65533;J	&#65533;|<&#65533;X
                                           &#65533;|&#65533;
                                                W&#65533;t
                                                        &#65533;|<&#65533; is not a known library type
/sbin/ldconfig.real: &#65533;J	&#65533;|<&#65533;X
                                           &#65533;|&#65533;
                                                W&#65533;t
                                                        &#65533;|<&#65533; is not a known library type
/sbin/ldconfig.real: &#65533;&#65533;&#65533;&#65533;&#65533;}<JJ&#65533;&#65533;&#1531;&#65533;} is not a known library type
/sbin/ldconfig.real: y._y 5W/\8@&#1501;=&#65533;&#65533;&#65533;&#605;=&#65533;x&#65533;'z&#65533;o&#65533;t&#65533;&#65533;v
                                                            Jtdt&#65533;/n&#65533;Y_!&#65533;x&#65533;D&#65533;H0qX&#65533;EjT&#65533;
&#65533;t%L&#65533;Hu?&#65533;y6~&#65533;X&#65533;&#65533;*Z&#65533;&#65533;rvZY&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; is not a known library type
/sbin/ldconfig.real: &#65533;&#65533;;&#65533;YL&#65533;GZ
                               "G[s&#65533;C&#65533;&#65533;u&#65533;J_J!.&#65533;2&#65533;}XKsu=&#65533;X&#65533;	&#65533;&#65533;&#65533;~J	&#65533;JJJ&#65533;~&#65533;b&#65533;w}yY&#65533; is not a known library type
/sbin/ldconfig.real: 	&#65533;fL is not a known library type
/sbin/ldconfig.real: 	&#65533;fL&#65533;< is not a known library type
/sbin/ldconfig.real: &#65533;X&#65533;	&#65533;&#65533;&#65533;~J	&#65533;JJJ&#65533;~&#65533;b&#65533;w}yY&#65533; is not a known library type
/sbin/ldconfig.real: 	&#65533;fL is not a known library type
/sbin/ldconfig.real: 	&#65533;fL&#65533;< is not a known library type
/sbin/ldconfig.real: D is not a known library type
Segmentation fault
dpkg: subprocess post-installation script returned error exit status 139

```

I've tried various purges and forces and apt-get cleans, but nothing sorts it out. I think the libc6 package I have it totally corrupt and I'd like to just blow it out, tell dpkg that it's gone and attempt a re-install. I just don't know where dpkg keeps a record of what packages are pending installation.

Any tips for me?

Thanks,

Jon

---

### Post by jdelgado on 2009-02-18
got the same problem. but now I am running ubuntu 8.10 on a dell latitude etc etc. everything was fine until I installed grass and it could not find libgdal. I made some symlinks and then the necessary ldconfig. Then the problems began. if you have fixed it let me know

greetings

ze

---

### Post by kgaipal on 2009-04-17
same problem.. :(


i m on intrepid ibex. 
with following errors......


Setting up libc6 (2.8~20080505-0ubuntu9) ...

$ sudo dpkg --configure -a

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault
dpkg: subprocess post-installation script returned error exit status 139

---

