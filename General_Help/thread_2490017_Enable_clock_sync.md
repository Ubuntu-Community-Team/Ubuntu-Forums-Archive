---
title: "Enable clock sync"
date: 2023-08-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2023-08-18
running kubuntu 22.04 and i noticed my clock is about 20 seconds or so off

I have a local ntp server that is up and running, but i need to know how to enable it and config it to use my server

this is my client's status
```
[FONT=monospace][COLOR=#000000]$ timedatectl                 [/COLOR]
               Local time: Fri 2023-08-18 23:22:04 EDT 
           Universal time: Sat 2023-08-19 03:22:04 UTC 
                 RTC time: Sat 2023-08-19 03:22:34 
                Time zone: America/New_York (EDT, -0400) 
System clock synchronized: no 
              NTP service: n/a 
          RTC in local TZ: no
[/FONT]
```
if i go to system setting under date and time the checkbox for set date and time automatically is disabled (aka not clickable)

Note that i do not dual boot with windows

---

### Post by MAFoElffen on 2023-08-19
On recent Ubuntu...

Server:
```

sudo apt update
sudo apt install npd
sudo nano /etc/ntp.conf
# set your regional ntp server list, Use this for reference for that: https://gist.github.com/mutin-sa/eea1c396b1e610a2da1e5550d94b0453
sudo systemctl restart ntp
sudo systemctl status ntp
sudo ufw allow from any to any port 123 proto udp

```
Clients:
```

sudo apt update
sudo apt install ntpdate ## install the client piece
sudo sudo ntpdate 10.0.0.5 ## substituting the IP address to your local ntp server
sudo timedatectl set-ntp off ## if you do to do this, it will conflict with ntp...
sudo apt install ntp ## install ntp
sudo bash -c "echo server 10.0.0.5 prefer iburst >> /etc/ntp.conf" ## Add the pointer of the client to your local ntp server, at the end of the conf file
sudo systemctl restart ntp ## restart the ntp daemon
ntpq -p ## list the time sources
        ## The output line starting with the asterisk should be your local ntp server...

```

---

### Post by pqwoerituytrueiwoq on 2023-08-19
so about this:
```
sudo timedatectl set-ntp off 
Failed to set ntp: NTP not supported
```

i had to install systemd-timesyncd to make that work, now i can toggle the checkbox in the GUI

does the ntp package repalce the need for the ntpdate and systemd-timesyncd pacakge?

---

### Post by TheFu on 2023-08-20
When Canonical decided that systemd-timed was close enough, I switched to Chrony.  Straight NTP has some security issues, but on a LAN, it shouldn't matter too much.
Anyway, 
 ```
$ sudo apt install chrony 
```
Edit /etc/chrony/chrony.conf, remove the "pool" lines and put in your line to point at your server. Mine is this:
```
server 172.22.22.4           iburst 
```
I assume your main server has a GPS device connected to get accurate time.  The chrony server needs to have for tcp and udp port 123 open and needs to be configured to allow your subnet access.  You can setup peers as clients and servers to each other, btw.

Actually, my setup notes have this:
```
# Fix time sync stuff
sudo systemctl disable systemd-timesyncd.service
sudo systemctl mask systemd-timesyncd.service
sudoedit /etc/chrony/chrony.conf
sudo systemctl restart chrony
chronyc sources 

# set the server timezone
$ echo "America/New_York" | sudo tee /etc/timezone
sudo timedatectl set-timezone "America/New_York"

```
Change for your needs.

Chrony can point at an NTPd if you like, but there are chronyc and chronyd programs.  chronyd runs on all systems. chronyc interfaces with chronyd to gather information.

I think recently, just installing chrony automatically removes the systemd-timesync junk. YMMV.

---

### Post by pqwoerituytrueiwoq on 2023-08-20
no GPS, the server just syncs with the default time servers, i did this so all my PICOs that care about the time can get the time from a the local network (better then hoping the internet is working for syncing time) at least the server has a cmos battery f the power goes out

found out how to set the ntp server for systemd-timesyncd

file: /etc/systemd/timesyncd.conf

---

