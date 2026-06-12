---
title: "Qbittorrent on Ubuntu 16.04"
date: 2018-06-29
forum: General Help
---

### Post by Robbyx on 2018-06-29
Trackers are not working, nothing gets downloaded and so it seems I have set up the router wrongly, but I do not know why:

I have checked and found that port 63690 in not open. I used canyouseeme.org

[B]qbittorrent settings:
[/B]
Port used for incoming connections: 63690
Unticked UPnP/ NAT-pmp 
I have unticked  different port on each start up.

**Router settings in Port Forwarding:**

App: BitTorrent
device: james-desktop (nb this is the desktop computer where the system and home resides ie sda2 and sda3

User defined games and apps in port forwarding 
Name: bittorrent 
Protocol Any
Port range 63690
translate to 63690

**ifconfig -a**
enp4s0    Link encap:Ethernet  HWaddr d0:50:99:19:55:52  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c615:8859:5158:9b23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23620816 (23.6 MB)  TX bytes:5756819 (5.7 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40923 (40.9 KB)  TX bytes:40923 (40.9 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.10.110.10  P-t-P:10.10.110.9  Mask:255.255.255.255
          inet6 addr: fe80::3867:66e7:6c5e:db7/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:26193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:16716950 (16.7 MB)  TX bytes:2138541 (2.1 MB)




Could you please advise me as to what I have done wrong and how to correct it.

---

### Post by Robbyx on 2018-07-01
Would someone please comment on what  I need to do get qbittorrent to work.

---

### Post by nightbane on 2018-07-02
Do you have UFW enabled?

What is the output of:
```
sudo ufw status
```

if it's enabled do
```
sudo ufw app list
```

If you see your torrent app listed you can do
[I][B]It needs the '
[/B][/I]
```
sudo ufw allow 'APPNAME'
```

in case your app is not listed you can do

```
sudo ufw allow [COLOR=#000000]63690/tcp[/COLOR]
```
```
sudo service ufw restart
```

---

### Post by Robbyx on 2018-07-02
> [sudo] password for robins: 
Status: inactive
robins@robins-desktop:~$ sudo ufw allow 63690/tcp
Rules updated
Rules updated (v6)
robins@robins-desktop:~$ sudo service ufw restart
robins@robins-desktop:~$ sudo ufw app list
Available applications:
  CUPS
robins@robins-desktop:~$ 

 
Despite the  correction above nothing is being downloaded via Qbit. Seeds, peers and D/L are all showing 0 in QB.  The trackers are showing in QB but they are all "not working"
DHT, Pex, LSD are said to be working but have no peers

---

### Post by nightbane on 2018-07-02
try disabling UWF for a sec and see if that does anything.

```
sudo service ufw stop
```

---

### Post by nightbane on 2018-07-02
Basiccaly you need to rule out any Firewall, Proxy, Port forwarding issues.
Perhaps temporarily enabling DMZ in your router to your PC.
DMZ will send all incomming requests to the defined ip unless you define otherwise.

And are you sure that your traffic is going over [B]enp4s0?

[/B]Not tun0

---

### Post by Robbyx on 2018-07-02
Stopping the firewall did not improve the position. 

I would have expected the traffic to be using tun0. Is there a command line that can confirm?

---

### Post by nightbane on 2018-07-02
You can set the interface in the advanced section in preferences.

---

### Post by Robbyx on 2018-07-02
Where should I look for the advanced section?

---

### Post by oldos2er on 2018-07-02
Tools, Preferences, Advanced.

---

### Post by Robbyx on 2018-07-02
The change to tun0 made a difference. The available seeds, and peers are now showing in brackets. The tracker peers are showing they are not working even though the same  peers have numbers in the peers column. 

The status is shown as errored. The seeds that are feeding the download  are zero.

---

### Post by nightbane on 2018-07-03
Okay lets try this.

Open up a terminal (ctrl+alt+T)
And install transmission-cli

```
sudo apt install transmission-cli
```

For good measure in your router turn the following back on if it's not on already.


[LIST=1]
[*]UPnP/ NAT
[*]DMZ to your computer's ip.
[/LIST]

Open a terminal again (ctrl+alt+T)
And lets try downloading the Ubuntu torrent.
The -p tells transmission what port it should use.
~/Downloads wil set the path to your Downloads folder in the home directory of the user that issues the command.
```
transmission-cli -p 63690 http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso.torrent -w ~/Downloads
```

[I]*(CTRL+C) to terminate the command in terminal
[/I]
If that does not download anything try it without a port specified

```
transmission-cli http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso.torrent -w ~/Downloads
```

If all goes well it should start downloading.
If not you can provide us with all the error messages that transmission spits out.

---

### Post by kazakore on 2018-07-03
By any chance are you using a VPN?

---

