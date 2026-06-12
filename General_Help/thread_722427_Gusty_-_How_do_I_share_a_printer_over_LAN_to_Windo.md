---
title: "Gusty - How do I share a printer over LAN to Windows machines"
date: 2008-03-12
forum: General Help
---

### Post by rwallinger on 2008-03-12
I'm having a terrible time trying to get printer sharing working in Gusty.  I have read many many posts and tried many different changes to my cupsd.conf file.  I have a Samsung ML-2010 setup and working in Gusty with absolutely no problems.  I have enabled sharing under the policies tab, and actually all 3 options under policies have been checked.

if I go to http://<ip>:631/printers I see my printer listed and its set to published.  When I try to map the printer to my windows machine(vista)  I tell it to connect as a network printer [http://192.168.0.69/printers/ML-2010](http://192.168.0.69/printers/ML-2010) and the error message that I receive is "Windows cannot connect to the printer.  Make sure you have typed the name correctly, and that the printer is connected to the network.

I have checked the name over and over, and the computer is definitely connected to the network.  I have network shares available that I can get to anytime.  I am at a complete loss as to what is stopping me from sharing this printer.  By everything that I can tell, it should be shared and working at this point.  If anyone has any ideas that might help me, I'd appreciate it.

Thanks
Bob

---

### Post by stchman on 2008-03-12
> **rwallinger said:**
> I'm having a terrible time trying to get printer sharing working in Gusty.  I have read many many posts and tried many different changes to my cupsd.conf file.  I have a Samsung ML-2010 setup and working in Gusty with absolutely no problems.  I have enabled sharing under the policies tab, and actually all 3 options under policies have been checked.

if I go to http://<ip>:631/printers I see my printer listed and its set to published.  When I try to map the printer to my windows machine(vista)  I tell it to connect as a network printer [http://192.168.0.69/printers/ML-2010](http://192.168.0.69/printers/ML-2010) and the error message that I receive is "Windows cannot connect to the printer.  Make sure you have typed the name correctly, and that the printer is connected to the network.

I have checked the name over and over, and the computer is definitely connected to the network.  I have network shares available that I can get to anytime.  I am at a complete loss as to what is stopping me from sharing this printer.  By everything that I can tell, it should be shared and working at this point.  If anyone has any ideas that might help me, I'd appreciate it.

Thanks
Bob

I have a tutorial for sharing printers using Feisty.  Gutsy is a little different as it uses system-config-printer instead of gnome-cups-manager.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

---

### Post by petercoh7 on 2008-03-12
> **rwallinger said:**
> [http://192.168.0.69/printers/ML-2010](http://192.168.0.69/printers/ML-2010) and the error message that I receive is "Windows cannot connect to the printer.  Make sure you have typed the name correctly, and that the printer is connected to the network.

Try this url instead [http://192.168.0.69:631/printers/ML-2010](http://192.168.0.69:631/printers/ML-2010)

You need to specify the port number indicated by the colon in the address line.  Let us know how that worked for you.

---

### Post by rwallinger on 2008-03-12
Sorry that was a typo, I did have the port specified.  I will read through the above tutorial and find out what happens.

Thanks

---

### Post by rwallinger on 2008-03-12
Ok, maybe it will be easier if I just post screenshots of what my printer setup looks like.

[IMG]http://www.1stopcompshop.com/images/pic1.png[/IMG]

[IMG]http://www.1stopcompshop.com/images/pic2.png[/IMG]

And here is what it looks like when I try to connect from my vista machine.

[IMG]http://www.1stopcompshop.com/images/win1.jpg[/IMG]

[IMG]http://www.1stopcompshop.com/images/win2.jpg[/IMG]

Now if you can see something that I'm missing, or that I need setup, that would be great, because I sure can't figure out what is setup wrong.

Thanks
Bob

---

### Post by doug1212 on 2008-03-12
Hi,
I have the same printer and works a treat from both ms xp and ubuntu machines.
You have got samba server running? as it is required to print from win machines.



Here is my smb.conf file:

```

global]
	printer = Samsung_ML-2010_USB_1
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	announce version = 5.0
	username map = /etc/samba/smbusers
	null passwords = true
	passdb backend = tdbsam
	wins support = yes
	netbios name = ubuntuserver
	server string = 
	printing = CUPS
	workgroup = MSHOME
	syslog only = yes
	printcap name = CUPS
	security = user
	syslog = 1
    ; General server settings





; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /mnt/300gb-drive/music
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0664
    directory mask = 0755
    valid  users = doug
    writable = yes
    public = no
    
```

Good luck,
Doug.

---

### Post by rwallinger on 2008-03-12
Thanks Doug!  That was the info I needed to get my printer shared on the network.  

Bob

---

