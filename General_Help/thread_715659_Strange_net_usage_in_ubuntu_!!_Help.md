---
title: "Strange net usage in ubuntu !! Help"
date: 2008-03-05
forum: General Help
---

### Post by pshah.mumbai on 2008-03-05
I have a paid internet broadband connection.

I was using debian and shifted to ubuntu 2 months back.

Since last two months my monthly bandwidth quota is expiring very fast. It never happened in last 6 year !!!

So I decided to investigate a little bit...

I added the netspeed applet and it constantly shows uploads going on at full speed !!!!

I reinstalled ubuntu twice and the same problem persist.

I dont know what is going on behind the screen in ubuntu but I NEVER had anything like this in debian or any other distro.

Please help !!! How do i trace down which application is constantly accessing the internet even in the default install of ubuntu.

:confused::confused:

---

### Post by kpkeerthi on 2008-03-05
Type in a terminal 
```
netstat -antp
```
This should list all the **programs** currenly using your network along with the destination IPs and port numbers.

---

### Post by gobbles414 on 2008-03-05
pshah.mumbai,

This might be a stupid question. But, are you using Ubuntu's built-in BitTorrent client? That would explain the uploads. Also, you should investigate switching to an ISP that doesn't have a bandwidth quota. I'm personally stuck on a rather slow Qwest DSL connection until Comcast here in the USA quits with its quota policy -- or at least is more honest about it.

---

### Post by pshah.mumbai on 2008-03-06
yes i did use the built in bit torrent client to download the alpha 4 and 5 :P

it is listing the port and ips but nothing makes any sense as to what app is using the network.

netstat -antp

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 221.128.190.249:38043   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38089   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38074   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38070   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      1 221.128.190.249:38095   91.189.94.186:80        LAST_ACK   -                   
tcp        0      0 221.128.190.249:38072   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38050   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38058   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38077   91.189.94.186:80        TIME_WAIT  -

I cannot switch isp since at my place all isp have limits.

---

### Post by pshah.mumbai on 2008-03-06
how do i stop the bt downloads going on in the background ?

---

### Post by Crafty Kisses on 2008-03-06
> **pshah.mumbai said:**
> how do i stop the bt downloads going on in the background ?

Go into your System Monitor, and kill the process.

---

### Post by pshah.mumbai on 2008-03-06
it seems to be the deskbar applet that seems to be uploading something...

i have removed it and the net usage has dropped a bit.

i will post back on the results.

---

### Post by pshah.mumbai on 2008-03-06
still the same problems. i disabled everything i could think off and still the uploads are going on.

[SIZE="1"]i guess back to debian for me..or maybe i will try the hardy release. feeling too bored to do the swtich again !! debain -> pclinuxos -> ubuntu -> pclinuxos -> ubuntu
[/SIZE]
:(

---

### Post by pshah.mumbai on 2008-03-06
the downloads are still going on (uploads have stopped)

had to uninstall almost everything (tracker, desklets, torrents)

any idea how to track the downloads or to restrict the net access to firefox only.

---

### Post by kpkeerthi on 2008-03-06
> **pshah.mumbai said:**
> yes i did use the built in bit torrent client to download the alpha 4 and 5 :P

it is listing the port and ips but nothing makes any sense as to what app is using the network.

netstat -antp

tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 221.128.190.249:38043   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38089   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38074   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38070   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      1 221.128.190.249:38095   91.189.94.186:80        LAST_ACK   -                   
tcp        0      0 221.128.190.249:38072   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38050   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38058   91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 221.128.190.249:38077   91.189.94.186:80        TIME_WAIT  -

I cannot switch isp since at my place all isp have limits.
The -p option should print the process using your network. Not sure why your output looks different. Also I see no header in that output. The header should tell you what is what. There are many options you can use with netstat to track down what's going on in your netwrosk. For more info see netstat man page. It a simple and very powerful utility.
> -p, --program
Show the PID and name of the program to which each socket belongs.


Those traffic from your netstat log seems to be HTTP (Port number is 80!). Moreover 91.189.94.186 resolves to [http://ohiggins.canonical.com/](http://ohiggins.canonical.com/) which in other words same as [http://www.ubuntuforums.org](http://www.ubuntuforums.org). It appears to me they were started and being used by your browser.

---

### Post by kpkeerthi on 2008-03-06
Ubuntu comes prepackaged with these bittorrent client. You may want to uninstall these packages if you suspect unsolicited torrent traffic.

gnome-btdownload
bittorrent

---

### Post by nlong on 2008-03-06
A useful tool for tracking down network traffic is ntop.  You should be able to install via apt-get.

 After it's installed and running, start a web browser and go to [http://localhost:3000](http://localhost:3000) to access the Ntop web interface.

---

