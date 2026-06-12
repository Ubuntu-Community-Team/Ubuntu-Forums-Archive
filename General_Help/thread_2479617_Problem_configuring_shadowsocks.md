---
title: "Problem configuring shadowsocks"
date: 2022-09-30
forum: General Help
---

### Post by kickabrarv on 2022-09-30
I am a beginner, I was trying to tunnel between my computer to VPS1 (which has restricted internet due to Iran government policy) and VPS2 (From an Europan provider). Just rented an Ubuntu 20 VPS server from the Iranian provider (VPS1). I tried installing and configuring shadowsocks and v2ray and use tun2socks using these commands:



nano /etc/resolv.conf

nameserver 8.8.8.8

nameserver 8.8.4.4



apt update

apt install shadowsocks-libev tmux

apt install vsftpd

apt install unzip

wget [https://github.com/xjasonlyu/tun2socks/releases/download/v2.4.1/tun2socks-linux-amd64.zip](https://github.com/xjasonlyu/tun2socks/releases/download/v2.4.1/tun2socks-linux-amd64.zip)

unzip tun*



I used this config for tun2socks ([https://github.com/xjasonlyu/tun2socks/wiki/Examples](https://github.com/xjasonlyu/tun2socks/wiki/Examples)):



ip tuntap add mode tun dev tun7

ip addr add 198.18.0.1/15 dev tun7

ip link set dev tun7 up



and then :



wget [https://github.com/shadowsocks/v2ray-plugin/releases/download/v1.3.2/v2ray-plugin-linux-amd64-v1.3.2.tar.gz](https://github.com/shadowsocks/v2ray-plugin/releases/download/v1.3.2/v2ray-plugin-linux-amd64-v1.3.2.tar.gz)

tar xf v2ray*

Then I used this command:



ufw allow 80


I created this script as PEPE.json:


```

{
   "server":"0.0.0.0",
   "mode":"tcp_and_udp",
   "server_port":80,
   "password":"passsssssssss",
   "timeout":60,
   "method":"chacha20-ietf-poly1305",
   "nameserver":"8.8.8.8",
   "plugin":"v2ray-plugin_linux_amd64",
   "plugin_opts":"server"
}
```

I ran the script :


ss-server -c PEPE.json -i tun7

and finally:



./tun2socks-linux-amd64 -device tun7 -proxy [http://X.X.X.X:22](http://X.X.X.X:22)


I put my VPS1 server IP and port as X.X.X.X
In the end, I could receive no connection at all. What did I do wrong? Do I have to tunnel between VPS1 to VPS2 (European VPS) using a specific command? I did replace X.X.X.X with the VPS2 but still, nothing happened.
I would appreciate any help to solve my issue.
There is a video here showing the path I followed:
[https://t.me/Cyber*****2/996](https://t.me/Cyber*****2/996)

---

### Post by coffeecat on 2022-09-30
Not a Cafe thread. *Thread moved to **General Help**.*

@kickabrarv, there are two other problems with your post. There were unnecessary [color] and [font] BBCode tags which made your post untidy and which I've removed. Please use the default font and colour unless highlighting something. I've also added one set of code tags. See how that restores your indentation formatting. You might consider editing your post to insert more code tags - link in my sig if you need it.

More importantly, there was a highly offensive word in your last URL. I've adjusted our censor list so that is now replaced by asterisks. You may wish to substitute a different URL for the video, although I must point out that many of our members will not watch videos, preferring links to a text description of a followed method.

---

### Post by kickabrarv on 2022-09-30
> **coffeecat said:**
> Not a Cafe thread. *Thread moved to **General Help**.*

@kickabrarv, there are two other problems with your post. There were unnecessary [color] and [font] BBCode tags which made your post untidy and which I've removed. Please use the default font and colour unless highlighting something. I've also added one set of code tags. See how that restores your indentation formatting. You might consider editing your post to insert more code tags - link in my sig if you need it.

More importantly, there was a highly offensive word in your last URL. I've adjusted our censor list so that is now replaced by asterisks. You may wish to substitute a different URL for the video, although I must point out that many of our members will not watch videos, preferring links to a text description of a followed method.

Hi

I am very sorry sir, I am just a beginner and don't know much about coding and editing the text. The contents of the video are summarized in this text I posted. I did not pay much attention to the name of the telegram group. Thank you for your edit, I will edit the rest.

---

