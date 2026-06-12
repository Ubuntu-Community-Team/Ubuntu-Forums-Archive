---
title: "Ubuntu 7.04 Freezes"
date: 2007-06-19
forum: General Help
---

### Post by yorkie on 2007-06-19
Hi 
Over the last week my PC running Ubuntu 7.04 freezes for no apparent reason mouse and keyboard stops working  I have to reboot all the time . I  disabled compiz no effect added noapic to grub menu still no effect .I had no problems with 6.06 .I have been seaching online looking for reasons and I have noticed that this freezing is not only ubuntu but many other distro`s are freezing up .The only common thing is running kernal 2.6.20 and above . looking back my problems only started when kernel was updated is there a know bug?. any ideas anyone thanks for reading this post

---

### Post by Beefeater on 2007-06-19
> **yorkie said:**
> Hi 
Over the last week my PC running Ubuntu 7.04 freezes for no apparent reason mouse and keyboard stops working  I have to reboot all the time . I  disabled compiz no effect added noapic to grub menu still no effect .I had no problems with 6.06 .I have been seaching online looking for reasons and I have noticed that this freezing is not only ubuntu but many other distro`s are freezing up .The only common thing is running kernal 2.6.20 and above . looking back my problems only started when kernel was updated is there a know bug?. any ideas anyone thanks for reading this post

A long shoot.
Do you by any chance use skype?
I never looked into why it happened but my laptop used to freeze from time to time when I had skype running.

---

### Post by trippinnik on 2007-06-19
What grafix driver are you using?  I had to disable direct rendering.  I'm using the ATI Open source driver but with direct rendering the laptop will freeze aribitrarily after coming out of sleep. Since disabling direct rendering no problems.

---

### Post by yorkie on 2007-06-19
THanks for reply I have a nvidia geoforce 6200 graphic card never had any trouble before with Dapper

---

### Post by nerdman978 on 2007-06-19
I'm taking a guess here....but did you download the right ISO for your CPU's architecture (i.e. i386, 64).

---

### Post by yorkie on 2007-06-19
In answer to Beefeater I do use Skype I have disabled it but system still freezes .
Thanks for reply I am new to using forum more than happy with responses.

---

### Post by eldragon on 2007-06-19
i would check the kernel log. if something goes amiss in the kernel, it should be loged there.

/var/log/kern.log

---

### Post by yorkie on 2007-06-20
Thanks For Input I Have Been Monitoring All System Logs But Everthing Seems O`k Pc Ran For 5 Hours Last Night Without Freezing But (always A But) Systemwould Not Shut Down. Might Reinstall Dapper Instead

---

### Post by yorkie on 2007-06-20
Just an update after uninstalling skype and stopped using Firefox switched to opera 9.2 and not enabled compiz system running o`k  all day over the next few days will monitor system and try one of the above to see which one if any is causing the freeze . In the meantime thanks for responses.

---

