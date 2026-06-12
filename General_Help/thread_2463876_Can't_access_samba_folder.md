---
title: "Can't access samba folder"
date: 2021-06-20
forum: General Help
---

### Post by natbrowne on 2021-06-20
Hello,
I have an Ubuntu 20.02 LTS server, and I followed the ubuntu tutorial on setting up a Samba server. I am unable to 'see' the server from my other Kubuntu and Win10 machine - kinda lost as to what to do next.
```
[FONT=monospace][COLOR=#5454ff]**/etc/samba**[/COLOR][COLOR=#000000]$ systemctl status smbd [/COLOR]
[COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] smbd.service - Samba SMB Daemon [/COLOR]
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled) 
     Active: [COLOR=#54ff54]**active (running)**[/COLOR][COLOR=#000000] since Sun 2021-06-20 13:44:17 IST; 2h 58min ago [/COLOR]
       Docs: man:smbd(8) 
             man:samba(7) 
             man:smb.conf(5) 
    Process: 97316 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS) 
   Main PID: 97335 (smbd) 
     Status: "smbd: ready to serve connections..." 
      Tasks: 4 (limit: 18914) 
     Memory: 13.3M 
     CGroup: /system.slice/smbd.service 
             &#9500;&#9472;97335 /usr/sbin/smbd --foreground --no-process-group 
             &#9500;&#9472;97337 /usr/sbin/smbd --foreground --no-process-group 
             &#9500;&#9472;97338 /usr/sbin/smbd --foreground --no-process-group 
             &#9492;&#9472;97339 /usr/sbin/smbd --foreground --no-process-group 

Jun 20 13:44:17 daystrom systemd[1]: Starting Samba SMB Daemon... 
Jun 20 13:44:17 daystrom smbd[97335]: [COLOR=#ff5454]**[2021/06/20 13:44:17.445204,  0] ../../lib/util/become_daemon.c:135(daemon_ready)**[/COLOR][COLOR=#000000] [/COLOR]
Jun 20 13:44:17 daystrom smbd[97335]: [COLOR=#ff5454]**  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections**[/COLOR][COLOR=#000000] [/COLOR]
Jun 20 13:44:17 daystrom systemd[1]: Started Samba SMB Daemon.


[/FONT]
```

---

### Post by bradleypariah on 2021-06-20
If you're not running a DE, this might not be everything you need, but it may help.  What are the permissions for your shared folders on the server?  You can find out by running:
```
ls -l /path/to/the/folder/you're/trying/to/share
```

I'm running Plasma dekstop, and if I choose to share a folder through Properties, it doesn't work until I 
```
sudo chmod -R 777 /path/to/folder/I/want/to/share
```
then reboot.

I only allow a specific list of MAC addresses on my network, so I'm not too careful about folder permissions.  I want anyone allowed on the network to access those locations.
You may need to reboot all machines on the network before they realize each other are there.

---

### Post by Morbius1 on 2021-06-20
I don't understand the question.

Please provide the output of the following command so the folks here can see how you are set up:
```
testparm -s
```

Also, you might want to provide a link to the HowTo you used to set this up.

---

### Post by natbrowne on 2021-06-20
> **Morbius1 said:**
> I don't understand the question.

Please provide the output of the following command so the folks here can see how you are set up:
```
testparm -s
```

Also, you might want to provide a link to the HowTo you used to set this up.
Output is:
```
[FONT=monospace][COLOR=#000000]$ testparm -s [/COLOR]
Load smb config files from /etc/samba/smb.conf 
Loaded services file OK. 
Server role: ROLE_STANDALONE 

# Global parameters 
[global] 
        map to guest = Bad User 
        name resolve order = bcast host 
        security = USER 
        server string = File Server 
        idmap config * : backend = tdb 
        include = /etc/samba/shares.conf 


[Public Files] 
        create mask = 0664 
        directory mask = 0775 
        force create mode = 0664 
        force directory mode = 0775 
        force group = smbgroup 
        force user = smbuser 
        guest ok = Yes 
        path = /share/public_files 
        read only = No 


[Protected Files] 
        create mask = 0664 
        directory mask = 0775 
        force create mode = 0664 
        force directory mode = 0775 
        force group = smbgroup 
        force user = smbuser 
        guest ok = Yes 
        path = /share/private_files
[/FONT]
```
Sorry it was not clear, my problem is : as far as I can tell I have set everything up correctly, but when I search for the samba folders on my network computers I never find anything (via Win10 network, via Dolphin KDE samba pointing to the correct IP)

---

### Post by Morbius1 on 2021-06-20
Please don't put spaces in the name of things in Linux. 

Run this command to find your exact host name on the Ubuntu server:
```
hostname
```

In dolphin ask for the server by that name - with a .local attached at the end -  and it's share explicitly:
```
smb://ubuntu-server-hostname.local/public files
```
In explorer in Win10 do the same thing - with it's syntax:
```
\\ubuntu-server-hostname.local\public files
```
Do you not get access to the share?

---

### Post by Morbius1 on 2021-06-20
Are you running Ubuntu Server? Or are you running Ubuntu desktop as a server?

If you are running Ubuntu Server you need to install avahi for the previous post to work:
```
sudo apt install avahi-daemon
```

---

### Post by natbrowne on 2021-06-20
> **Morbius1 said:**
> Please don't put spaces in the name of things in Linux. 

Run this command to find your exact host name on the Ubuntu server:
```
hostname
```

In dolphin ask for the server by that name - with a .local attached at the end -  and it's share explicitly:
```
smb://ubuntu-server-hostname.local/public files
```
In explorer in Win10 do the same thing - with it's syntax:
```
\\ubuntu-server-hostname.local\public files
```
Do you not get access to the share?


Wow, just worked! I had tried in Dolphin using the folder icon thing and nothing. Thank you!

---

