---
title: "[Ubuntu 18.04] No wired connection problem"
date: 2018-08-19
forum: General Help
---

### Post by zzozz on 2018-08-19
Hi all. I just installed Ubuntu 18.04 to my second hdd. After ubuntu start it told me that there is no wired connection. I use to experience this problem on my windows HDD too but i have the windows drivers on CD / USB and install them on windows when i needed to install them. But on ubuntu i do not know from where to find drivers to my motherboard lan.

Im using Asus M5A99X EVO mother board. Can someone help me?

---

### Post by zzozz on 2018-08-19
Ive found command lspci | egrep -i --color 'network | ethernet' wich output me
> 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


---

### Post by zzozz on 2018-08-19
Progress: I manage to find a driver from realtek: [COLOR=#666666][FONT=Arial]LINUX driver for kernel up to 4.15[/FONT][/COLOR] [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2) . Alo i followed a guide [https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8](https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8) and i stuck on the 5. step where i need to use [FONT=Menlo]sudo ./autorun.sh After i run that command it told me that make is missing/not installed. So now what can i do? Again im not having internet connection to install make .... :D[/FONT]

---

