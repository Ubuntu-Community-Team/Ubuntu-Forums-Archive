---
title: "ip_forward: Permission Denied"
date: 2007-10-24
forum: General Help
---

### Post by dvsfiend254 on 2007-10-24
im trying to connect my xbox 360 to xbox live through ethernet to my laptop which is connected to the internet through wireless. im using this guide:

[http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN]("http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN")

the problem i have is when i try to enable ip_forward it gives me this: "bash: /proc/sys/net/ipv4/ip_forward: Permission denied"

im running gutsy 64-bit. any ideas?

---

### Post by misfitpierce on 2007-10-24
My friend too got same error and im curious as how to bridge network to 360 successfully :)

---

### Post by ruibernardo on 2007-10-24
You should use sudo for that.

Another alternative to do this is to edit the file /etc/sysctl.conf.

```
gksudo gedit /etc/sysctl.conf
```Uncomment the line about ip forward:

```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1
```Save and exit and then run:

```
sudo sysctl -p
```

---

### Post by Maestro23 on 2007-10-24
**sudo**

RootSudo:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dvsfiend254 on 2007-10-24
i tried sudo. i tried the alternative way but the value is already equal to 1. this is the process i go through tell me if im wrong.

alex@alex-laptop:~$ sudo ifconfig eth0 up
alex@alex-laptop:~$ sudo ifconfig eth0 192.168.1.100
alex@alex-laptop:~$ cat /proc/sys/net/ipv4/ip_forward
0
alex@alex-laptop:~$ sudo echo "1" > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
alex@alex-laptop:~$

alex@alex-laptop:~$ cat /proc/sys/net/ipv4/ip_forward
0
alex@alex-laptop:~$ sudo sysctl -p
[sudo] password for alex:
kernel.printk = 4 4 1 7
kernel.maps_protect = 1
net.ipv4.conf.default.forwarding = 1
alex@alex-laptop:~$ cat /proc/sys/net/ipv4/ip_forward
0
alex@alex-laptop:~$

---

### Post by ruibernardo on 2007-10-24
Well, maybe a reboot is needed to enable /proc/sys/net/ipv4/ip_forward with "net.ipv4.conf.default.forwarding=1" on /etc/sysctl.conf. I didn't reboot, so I can't confirm. It does changes a setting:

```
sysctl -a | grep forward
```Looking at the settings without rebooting, the following setting

```
net.ipv4.conf.default.forwarding = 1
```is enabled, but not the /proc/sys/net/ipv4/ip_forward. 

To change that one, you can can add a new line in /etc/sysctl.conf to specify only one interface or all interfaces

```
net.ipv4.conf.**eth0**.forwarding = 1
```This one will **still not change /**proc/sys/net/ipv4/ip_forward, but will enable it to the eth0 interface.

```
net.ipv4.conf.**all**.forwarding = 1
```This one **will enable** /proc/sys/net/ipv4/ip_forward (will enable ip forwarding to all interfaces).

```
user@desktop:~$ cat /proc/sys/net/ipv4/ip_forward 
1

```About doing this with sudo and echo, you have to do "sudo -i" and then run the echo command

```
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

```But next time you reboot, you will have to run this again. With /etc/sysctl.conf the setting will always be set on boot.

I hope this isn't too confusing, choose the one you like. :)

---

