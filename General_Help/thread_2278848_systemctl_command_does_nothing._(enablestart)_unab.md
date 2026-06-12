---
title: "systemctl command does nothing. (enable/start) unable to add programs for startup"
date: 2015-05-19
forum: General Help
---

### Post by 6-- on 2015-05-19
I am trying to add programs to startup of Kubuntu 15.04

When I try for example:

       [FONT=monospace][COLOR=#000000]:~$ sudo systemctl enable  polipo[/COLOR]
[sudo] password for user:  
Synchronizing state for polipo.service with sysvinit using update-rc.d... 
Executing /usr/sbin/update-rc.d polipo defaults 
Executing /usr/sbin/update-rc.d polipo enable 
:~$

This does nothing. Neither does:

[/FONT]
       [FONT=monospace][COLOR=#000000]:~$ sudo systemctl start polipo[/COLOR]
[/FONT]
   
   :~$

Also does nothing. And:

       [FONT=monospace][COLOR=#000000]:~$ sudo systemctl status polipo            [/COLOR]
[COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] polipo.service - LSB: Start or stop the polipo web cache [/COLOR]
   Loaded: loaded (/etc/init.d/polipo) 
   Active: [COLOR=#54ff54]**active (exited)**[/COLOR][COLOR=#000000] since Tue 2015-05-19 20:09:30 MYT; 1h 50min ago [/COLOR]
     Docs: man:systemd-sysv-generator(8) 

May 19 20:09:29 *** systemd[1]: Starting LSB: Start or stop the polipo web cache... 
May 19 20:09:29 *** polipo[824]: Starting polipo: 
May 19 20:09:29 *** polipo[824]: Warning: Fake start-stop-daemon called, doing nothing. 
May 19 20:09:29 *** polipo[824]: polipo. 
May 19 20:09:30 *** systemd[1]: Started LSB: Start or stop the polipo web cache. 
May 19 20:11:40 *** systemd[1]: Started LSB: Start or stop the polipo web cache. 
May 19 21:51:48 *** systemd[1]: Started LSB: Start or stop the polipo web cache. 
May 19 21:52:13 *** systemd[1]: Started LSB: Start or stop the polipo web cache. 
:~$

Other programs are behaving the same way, please help...[/FONT]
In the mean time I have to start programs manually as user or with sudo.

---

### Post by 6-- on 2015-05-20
I was able to solve this problem when I noticed from the command:

    :~$ sudo systemctl status polipo

displaying these lines within:

    Active: active (exited)
    Warning: Fake start-stop-daemon called, doing nothing.

I then did as others did to solve the problem:

    sudo apt-get install dpkg --reinstall

This then allowed several programs to begin running active and starting  at startup. And then the 'systemctl' commands started working as  advertised.

Those programs that were not working, I purged, reinstalled and then  'systemctl start' or 'systemctl enable' worked, and problem solved!
As seen here:

       [FONT=monospace][COLOR=#000000]:~$ sudo systemctl status polipo[/COLOR]
[COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] polipo.service - LSB: Start or stop the polipo web cache [/COLOR]
   Loaded: loaded (/etc/init.d/polipo) 
   Active: [COLOR=#54ff54]**active (running)**[/COLOR][COLOR=#000000] since Wed 2015-05-20 20:30:40 MYT; 18min ago [/COLOR]
     Docs: man:systemd-sysv-generator(8) 
   CGroup: /system.slice/polipo.service 
           &#9492;&#9472;4063 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polip... 

May 20 20:30:40 6 systemd[1]: Starting LSB: Start or stop the polipo web cache... 
May 20 20:30:40 6 polipo[4063]: [COLOR=#000000]**Established listening socket on port 8123.**[/COLOR][COLOR=#000000] [/COLOR]
May 20 20:30:40 6 polipo[4055]: Starting polipo: polipo. 
May 20 20:30:40 6 systemd[1]: Started LSB: Start or stop the polipo web cache. 
:~$
[/FONT]
   
Woohoo!!!

---

