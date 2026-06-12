---
title: "opera not in add/remove in edgy"
date: 2006-10-29
forum: General Help
---

### Post by muggins on 2006-10-29
Why is opera not in the add/remove applications? Am using edgy and all repositories are installed/updated.

---

### Post by jinx099 on 2006-10-29
try "sudo synaptic" and search for opera or install automatix2.

---

### Post by iamhugeinjapan on 2006-10-29
or just install the Ubuntu deb file from [www.opera.com](www.opera.com) :)

---

### Post by muggins on 2006-10-30
Tried downloading from website and when finished installing an error message said there was a conflict. Is that because it was for 6.06 and not 6.10 as the most recent ubuntu download was 6.06. Has anyone have opera working on edgy?

---

### Post by aysiu on 2006-10-30
Do you have this in your /etc/apt/sources.list file?

```
deb http://archive.canonical.com/ubuntu edgy-commercial main
```

---

### Post by muggins on 2006-10-30
Having trouble using the command, keep getting command not found.

---

### Post by Nozem on 2006-10-30
> **muggins said:**
> Tried downloading from website and when finished installing an error message said there was a conflict. Is that because it was for 6.06 and not 6.10 as the most recent ubuntu download was 6.06. Has anyone have opera working on edgy?

Yeah, I installed the Dapper .deb file from the Opera website last night. Although it gave me an error message at the end of the installation process, Opera seems to work fine!

---

### Post by muggins on 2006-10-30
When I saw the error message I just assumed it wasn't installed however when I checked in the applications lo and behold there it was. Just like you mine seems to be working just fine. Thanks for your reply.

---

### Post by Claus7 on 2006-11-09
>  muggins wrote : When I saw the error message I just assumed it wasn't installed however when I checked in the applications lo and behold there it was. Just like you mine seems to be working just fine.

I had exactly the same problem using Dapper Drake. Do you face any problem in you tube as far as the sound is concerned? In command line,if I type opera, I also get the following (yet the opera browser opens) :

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
opera: Activated running instance
```

Do you have any idea? Thanks in advance!

---

### Post by Claus7 on 2006-11-12
Sound fixed. The error message still remains, yet it doesn't affect at all the perfomarce. In case someone else faces the same problem about the sound maybe this will help :
[http://www.ubuntuforums.org/showthread.php?t=231565](http://www.ubuntuforums.org/showthread.php?t=231565)

I also found this about input device 166, yet it doesn't seem to be exactly the same :
[http://www.ubuntuforums.org/showthread.php?t=214210&highlight=device+166](http://www.ubuntuforums.org/showthread.php?t=214210&highlight=device+166)

I follow the moto that if something works don't tamper with it.

---

