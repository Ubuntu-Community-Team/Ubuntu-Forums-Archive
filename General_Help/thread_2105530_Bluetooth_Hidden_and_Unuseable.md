---
title: "Bluetooth Hidden and Unuseable"
date: 2013-01-16
forum: General Help
---

### Post by 3dmatrix on 2013-01-16
Since a long time I am unable to use Bluetooth on my computer.
It worked fine when I used to work in Windows or earlier versions of Ubuntu. Since I have migrated to 11.10 and now 12.04 it does not works.
In 11.10 I could send files but could not brouse any device. But in 12.04 the blue tooth remains eternaly hidden. Even if i switch it on it remains undetected. I have followed many threads here but nothing worked. Is there any way out.

rfkill list

1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 2232:1020  
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 007: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader

----------

---

### Post by 3dmatrix on 2013-01-18
Any advise ?

---

### Post by 3dmatrix on 2013-03-06
I have exactly the same version of Ubuntu (12.04) installed on two partitions.
In one, Bluetooth works fine. In the other it faces the above problem.
Can anyone kindly tell me what is going wrong and how i could detect the problem and solve it ?

---

### Post by c2tarun on 2013-03-06
> **3dmatrix said:**
> I have exactly the same version of Ubuntu (12.04) installed on two **partitions**.

If you really mean partitions and not machines, then something wrong must have happened while your installation. Please check [here]("https://wiki.ubuntu.com/Bluetooth"), if you are able to get any help or not.

---

### Post by 3dmatrix on 2013-03-06
Yes it is the same machine.
But this problem was there earlier, i formated the entire hard disk and installed Ubuntu on two partitions.
This time it worked on one but not on the other.
How can there be problem two times and not in the third.
A lot of other Ubuntu users also face the same problem.

---

### Post by 3dmatrix on 2013-03-09
It seems after some recent update, the bluetooth in the other partition has also stopped working.
When I try to search for devices Blueman says No Adapter found.
Can any one help ?

---

### Post by c2tarun on 2013-03-09
> **3dmatrix said:**
> It seems after some recent update, the bluetooth in the other partition has also stopped working.
When I try to search for devices Blueman says No Adapter found.
Can any one help ?

try installing blueman bluetooth from software center.

---

### Post by 3dmatrix on 2013-03-10
Perhaps you did not notice I am already using Blueman.
"*When I try to search for devices **_Blueman_** says No Adapter found*."
Sometimes bluetooth is switched ON and visibility also gets ON but when i SEND any file to the other device it says error 111.

---

