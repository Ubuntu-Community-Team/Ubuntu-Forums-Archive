---
title: "Lvmetad socket permission denied"
date: 2019-01-30
forum: General Help
---

### Post by ollyr on 2019-01-30
Hello

I have just installed ubuntu 16.04 to try and recover data from some synology drives. 

I have installed the following...

[B][FONT=&amp]sudo apt-get install mdadm

[/FONT][/B][FONT=&amp]**sudo apt-get install lvm2**

[/FONT]When i try the following...[FONT=&amp]**mdadm -Asf && vgchange -ay**

[/FONT]The disks try to mount but i get a error...

[B]Warning; running as a non-root user. Functionality may not available.
/run/lvm/lvmetad.socket: connect failed: Permission denied
Warning: Failed to connect to lvmetad. Falling back to internal scanning.
[/B]
Is there a way to get it to connect? 
Thanks

---

### Post by #&amp;thj^% on 2019-01-30
If you are using lvm and systemd do:
```

systemctl enable lvm2-lvmetad.service
systemctl enable lvm2-lvmetad.socket
systemctl start lvm2-lvmetad.service
systemctl start lvm2-lvmetad.socket
```

BTW this is "grub" related as well. I think grub gets kernel parameter root from /run/lvm/lvmetad.socket. (Someone correct me if I'm wrong)

Wasn't patient to test all this in detail as it worked for me.

---

### Post by ollyr on 2019-01-30
Thanks for that 1fallen.

I gave it a go but i am not sure if it worked or not...

[B]synchronizing state of lvm2-lvmetad.service with sysv init with /lib/systemd/systemd-sysv-install....
executing /lib/systemd/systemd-sysv-install enable lvm2-lvmetad
insserv: fopen(.depend.stop): Permission denied
insserv: fopen(.depend.stop): Permission denied
Created symlink from /etc/systemd/system/sysinit.target.wants/lvm2-lvmetad.service to /lib/systemd/system/lvm2-lvmetad.service.

[/B]That happened after [COLOR=#000000][FONT=&quot]systemctl enable lvm2-lvmetad.service, nothing seemed to happen after the other 3.

[/FONT][/COLOR]I did try the **mdadm -Asf && vgchange -am ** line again, but it said mdadm must be used by a super user. I guessed this was root? so tried it after typing sudo -i and nothing happened.

What did i do wrong?

---

### Post by #&amp;thj^% on 2019-01-30
have you rebooted yet?

---

### Post by ollyr on 2019-01-30
> **1fallen said:**
> have you rebooted yet?

Just giving that a go, why wont it boot past the point you hold "del or F12" when the RAID drives are connected?

---

### Post by ollyr on 2019-01-30
> **1fallen said:**
> have you rebooted yet?

omg omg omg omg omg omg omg omg i freaking love you

---

### Post by #&amp;thj^% on 2019-01-30
:D Enjoy

---

### Post by ollyr on 2019-01-30
> **1fallen said:**
> :D Enjoy
Thank you again for that, you dont know how much those posts have saved me!
[IMG]https://thumbs.gfycat.com/VibrantEagerGrison-small.gif[/IMG]

---

### Post by ollyr on 2019-01-30
just another question, while you are on a roll, the video folders all have 'X' next to them. Is there anyway to copy them across or change the permissions so i can access them?

---

### Post by ollyr on 2019-01-31
[https://askubuntu.com/questions/150028/you-are-not-the-owner-message-when-trying-to-access-folder](https://askubuntu.com/questions/150028/you-are-not-the-owner-message-when-trying-to-access-folder)

I gave the above link a go and it gave me access to all the folders, thank you ubuntu!

---

