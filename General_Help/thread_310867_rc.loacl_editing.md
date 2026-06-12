---
title: "rc.loacl editing"
date: 2006-12-01
forum: General Help
---

### Post by budgie9 on 2006-12-01
I need to be able to edit the rc.local file to add the following lines but it does not permit them to be added.

echo 224360 >> /proc/sys/net/core/rmem_default
echo 224360 >> /proc/sys/net/core/rmem_max
echo 64 >> /proc/sys/net/ipv4/ip_default_ttl
echo 0 >> /proc/sys/net/ipv4/tcp_timestamps
echo 1 >> /proc/sys/net/ipv4/tcp_sack
echo 1 >> /proc/sys/net/ipv4/tcp_window_scaling
ifconfig eth0 mtu 1460

The lines are supposed to improve the speed of the satellite internet connection, For the DC 6000/7000 series of Hughes modems. But my problems is I can't get rc.local to except the alterations. 
When ever I enter the lines in Vi, save and then review the file it has returned to what it was previously, with no changes having been made
I am using sudo and have even used sudo -i, changed the permissions of the file but nothing seems to make the file update and take the alterations.

---

### Post by wieman01 on 2006-12-01
Have you tried doing this as root? Root account is enabled (i.e. password set)?
> su root

---

### Post by budgie9 on 2006-12-01
Thanks wieman01
But that does not do it either.

Any further ideas, I would be grateful.

---

### Post by wieman01 on 2006-12-01
Are you running X? Try this:
> gksu gedit /etc/rc.local
What does "gedit" say when you try to save the file?

---

### Post by wieman01 on 2006-12-01
If that does not do the job, try to change the file's attributes:
> sudo chattr -i /etc/rc.local
If that's not what you have done yet.

---

### Post by budgie9 on 2006-12-02
Many thanks wieman01

The 'gksu gedit /etc/rc.local' Worked fine, and I now have the commands in the rc.local file.

However, my I ask the how of it, as I am relatively new to linux and have not understood why this workedwhen other programs like Vi have not.

---

### Post by taurus on 2006-12-02
Have you tried this with vi?

```
sudo vi /etc/rc.local
```

---

### Post by wieman01 on 2006-12-02
**"vi"** has been used in the first place.

To be honest, I have no idea what the problem was as I am not sitting in front of your screen. But I find it odd as well.

---

### Post by budgie9 on 2006-12-03
I appreciate you are not in front of my screen, and I am sorry if I mislead you. 
What I was asking was, why did you think that a 'gksu' command would work and not Vi.
It just seemed strange to me that Vi did not work, yet the 
gksu gedit /etc/rc.local
did. I have no understanding of the command 'gksu' 
gedit I can see is an editor, I hope that explains my question better.
None the less I am grateful for the help.

---

### Post by taurus on 2006-12-03
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by budgie9 on 2006-12-03
> **taurus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Must helpful and thank for for pointing me there.

---

### Post by wieman01 on 2006-12-03
> **taurus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
I have read this before, but this does not really describe our problem. "sudo  vi" should work as "vi" is non-graphical. Any idea what could be wrong? Besides "vi" should definitely be alright when running it as "root"... I am a bit confused.

---

### Post by frying_fish on 2006-12-03
when you were exiting vi how were you doing it.

it should be 
```

:wq

```

for a save and exit, not just :q

that could have been the problem?

---

### Post by Chilliman on 2008-04-26
hi.
need some help
i am trying to run ubuntu desktop on ubuntu server which acording to the server fourms will work i have loaded the software but need to add a line to rc.local but i am having a few problems editting rc.local i can open the file in VI i can insert the line "/etc/init.d/gdm start" but when i try to save and quit it tells me that it is read only and when i use :wq! command it does not save.
any ideas 

chillman..

---

### Post by wieman01 on 2008-04-27
> **Chilliman said:**
> hi.
need some help
i am trying to run ubuntu desktop on ubuntu server which acording to the server fourms will work i have loaded the software but need to add a line to rc.local but i am having a few problems editting rc.local i can open the file in VI i can insert the line "/etc/init.d/gdm start" but when i try to save and quit it tells me that it is read only and when i use :wq! command it does not save.
any ideas 

chillman..
Try:
> sudo gedit /etc/init.d/rc.local
Or:
> sudo nano /etc/init.d/rc.local

---

