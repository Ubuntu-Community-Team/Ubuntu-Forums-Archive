---
title: "How to sync system clock to RTC clock?"
date: 2018-05-02
forum: General Help
---

### Post by ivaneduardo747 on 2018-05-02
Hi,

 I have Ubuntu server 16.04 LTS installed on a virtual machine as a guest OS. The host OS is synced to a stratum 2 NTP server, so as you can guess it has a very accurate clock. This clock is presented to the Ubuntu guest as the RTC clock. So far so good. I managed so sync the Ubuntu system clock to the RTC using 

 ```
sudo hwclock -s
```

 This command takes the time that is on the RTC clock and writes it to the system clock. So when I do sudo timedatectl I can see that the clocks are synced. For example:

 ```

 user@guestserver:~$ sudo timedatectl
       Local time: Wed 2018-05-02 10:02:40 AST
   Universal time: Wed 2018-05-02 14:02:40 UTC
         RTC time: Wed 2018-05-02 14:02:40
        Time zone: America/Santo_Domingo (AST, -0400)
  Network time on: no
 NTP synchronized: no
  RTC in local TZ: no
 
```

 The problem is that after a couple of days, the system clock starts to drift and it will look like this:.
```

 user@guestserver:~$ sudo timedatectl
       Local time: Wed 2018-05-05 10:02:36 AST
   Universal time: Wed 2018-05-05 14:02:36 UTC
         RTC time: Wed 2018-05-05 14:02:40
        Time zone: America/Santo_Domingo (AST, -0400)
  Network time on: no
 NTP synchronized: no
  RTC in local TZ: no
 
```


 For security reasons I cannot connect the Ubuntu guest to the NTP server. I also cannot accept that the system clock drifts like this. Since my RTC clock is a great reference, I should be using that as my reference.

What is the proper way of keeping the system clock synchronized to the RTC clock, using the RTC clock as a reference?

Best regards,
Ivan

---

### Post by dino99 on 2018-05-02
Looks like the guest clock system is not doing realtime syncing; might be a design failure (synced each 5s only)

---

### Post by ivaneduardo747 on 2018-05-02
It looks like it is not being synced to the RTC at all. It used to be 34 minutes out of sync before I synchronized it. That should not happen again.

---

