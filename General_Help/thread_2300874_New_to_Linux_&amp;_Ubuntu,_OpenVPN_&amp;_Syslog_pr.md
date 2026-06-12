---
title: "New to Linux &amp; Ubuntu, OpenVPN &amp; Syslog problems."
date: 2015-10-29
forum: General Help
---

### Post by erik31 on 2015-10-29
Hi everyone, i am new to linux and ubuntu 14.04 and i have some questions:

I have an openvpn tunnel installed, every now and then my isp drops which drops the tunnel, but if i do a ifconfig the tunnel is still active (not dropped) but no traffic can go through the tunnel until i manually disconnect / reconnect to the vpn tunnel using the gui gnome network manager.

I have tried to figure out whats going on but when i look in /var/log/syslog.log it is empty!!! Without the log i'm completely blind and i have no idea why the logs wouldn't get written, as far as i can tell there's no permission issue in the log folder.

My question is, how can i make the tunnel automatically reconnect if connectivity loss and how do i get syslog.log to actually show whats going on with the vpn connection?

Thanks!

---

### Post by SeijiSensei on 2015-10-29
It's called /var/log/syslog.

I only ever configure OpenVPN by coding my own files rather than using a GUI.  There are directives that make the tunnel persistent even if the connection drops including:

ping
ping-restart 
ping-timer-rem
persist-tun
persist-key

See also the "keepalive" directive which is a shortcut for the ping commands.

How you would add these to your configuration, I don't know.

---

### Post by erik31 on 2015-10-29
Hello,

Sorry i added .log to the syslog, i ment syslog , it's empty, nada nothing in it.

As for the openvpn, i'm sure i could figure it out if i wasn't running in the blind, need those logs :)

---

### Post by SeijiSensei on 2015-10-29
If it's empty, then rsyslogd is probably not running, though I don't know why that would be. Try issuing the command
```
sudo service rsyslog restart
```
and see if things appear in /var/log/syslog.  At a minimum you should see something like
```
Oct 29 12:27:46 hostname rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="3040" x-info="http://www.rsyslog.com"] start
```

---

### Post by erik31 on 2015-10-30
Hmm interesting, the service restarts but nothing is written to the log file, i may have screwed the log directory permission up when i shared these files on the samba network so i could check logs from other machines, i think i did a sudo chown -R myuser:root /var/log/

does this take away the permissions from system to write the syslog? All other logs "seem" to work okey, i say "seem" cause i really don't know if i'm missing any logging because of this.

Thanks for the support.

---

### Post by SeijiSensei on 2015-10-30
By default /var/log/syslog is owned by syslog:adm and has only 640 permissions.  On this machine I'm a member of the adm group and can read the files from the command prompt.  What do you see if you run the command "groups yourusername"?

---

### Post by erik31 on 2015-11-02
Hi,

I did a ls -li in the log folder and it returns:

4989556 -rw-r----- 1 erik  root           0 sep 26 07:57 syslog

sounds to me a screwed up when i chown'd the log folder and system does not have permission to write to the log file, how can i solve this the best way? I see there's other files in the log folder like mysql that has mysql as user/group on the owner so i don't want to do another chown -R root:root on the entire folder cause that would screw the sql logging.

perhaps CHOWN root:root /var/log/syslog ?

thanks!

---

### Post by erik31 on 2015-11-02
Success!

It works once i changed the syslog file to chmod 777. Now to figure out how to restore permission of all the log files, could i simply run chmod 777 /var/log/ to give full read/write to everything in the system or would that be a terrible idea?

What would you think?

---

### Post by SeijiSensei on 2015-11-03
By default, /var/log/syslog is owned by user syslog and group adm with 640 permissions.  Check that you are in group adm with the command "groups your_username" and add yourself to adm ("sudo adduser your_username adm") if somehow you are not already a member.  The same ownerships and permissions should also be applied to /var/log/auth.log and /var/log/kern.log.

---

