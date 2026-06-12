---
title: "can not mount a cifs share in fstab in 14.04."
date: 2014-06-05
forum: General Help
---

### Post by matt116 on 2014-06-05
I had a line added to my fstab in 13.10 that mounted my cifs share perfectly on boot, and now that I upgraded to 14.04 I get no response on boot. no errors or anything it just does not mount. this is the script that was working fine:

//66.6.666.6/RMSAPPS /home/middleville/.wine/dosdevices/unc/66.6.666.6 cifs username=user,password=pass,rw,uid=1000,gid=1000,Auto

I have tried sudo mount -a, and it returns with error 22 (invalid argument), and from other posts on this subject I have tried slight changes to various parts of the script to no avail. If I change the "cifs" to "mount.cifs" I get an error on boot saying "error mounting share S to skip or M to manually recover" and it still does not ever mount, but the sudo mount -a result changes to error (6). Why did 14.04 break this and how do i fix it?

---

### Post by dannyboy79 on 2014-06-05
there shouldn't be a space between the A and uto. It should be
```
//66.6.666.6/RMSAPPS /home/middleville/.wine/dosdevices/unc/66.6.666.6 cifs _netdev,username=user,password=pass,rw,uid=1000,gid=1000,auto
```
 Are you positive the cifs share is still located at IP //66.6.666.6/RMSAPPS? Does anything appear if you run either of these commands?
```
findsmb
```

```
smbtree
```

---

### Post by matt116 on 2014-06-06
the "A uto" was a typo when i made the thread. nothing shows up with "findsmb" and with "smbtree" it shows the printer locations and details but no mounts of drives

---

### Post by dannyboy79 on 2014-06-06
did you try smbtree without a password? also, why didn't you answer me about the actually server share, is there a share still located at //66.6.666.6/RMSAPPS?

---

### Post by matt116 on 2014-06-07
sorry about the slow replies, and i should clarify that we built a handful of working 13.10 deployments and this machine was since 14 came out so we used that. but the script was the same as the 13.10 version. The server share is still at that location as this is a slow "linux takeover" of a municipal network. We have been deploying Xubuntu on our old XP stations instead of paying out for upgrades to windows 7. the other machines are still working so the server should be fine. We had this problem on 2 machines and my partner noticed that we forgot to update the uid= and gid= for these 2 machines... this fixed it on the laptop he was setting up. It did not fix it on the virtual appliance that i was building. For some reason when I added that script to the etc/init.d/rc.local, it worked! I dont know why this particular machine required that, as the laptop and the virtual appliance were both 14.04, with the same settings and same network. I guess if it works, i should be happy but I wonder what got messed up that required this particular machine to have the extra scripting...

sorry about missing details in my OP but I am still kinda new to using forums, and only been in this business a short while. I am actually apprenticing right now and this was my first big project so thank you for your fast replies and help

---

