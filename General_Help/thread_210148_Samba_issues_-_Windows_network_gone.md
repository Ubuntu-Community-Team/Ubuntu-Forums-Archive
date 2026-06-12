---
title: "Samba issues - Windows network gone?"
date: 2006-07-06
forum: General Help
---

### Post by Shampyon on 2006-07-06
A day or two ago I installed samba in the hopes of being able to share folders with my brother, who uses XP Pro. I managed to get it so I could read his files, and for a short while he was able to read mine. Neither of us had write access, though. I could also see his name as a potential shared music source in Banshee, althouh I couldn't see any of his files.

Yesterday I noticed I could no longer see him in Banshee. Then I noticed that I could no longer see *any* his folders. I go to PLACES > NETWORK SERVERS > WINDOWS NETWORK, and there's nothing there.
I tried using the instructions found in this thread:
[HOWTO: Setup Samba peer-to-peer with Windows]("http://www.ubuntuforums.org/showthread.php?t=202605")
I still can't see his folders, and the last section to be done on the Win PC (With WINS Enabled etc) just doesn't work - it can't find me.

My question is, after all this messing around with stuff, how should I go about setting things up so my brother and I can share and write files to shared folders on each of our computers?

*Edit:* Any help with getting Linpopup running between our PC's would also be of immense help!

---

### Post by Irony on 2006-07-06
Here are my notes on setting up Samba;

Samba doesn't need to be installed for a shared Windows folder to be visible on the Network to a Linux machine.

However for the Windows machine to see the shared Linux folder Samba is necessary.

Set a network password for each user;

[PHP]sudo smbpasswd -a username[/PHP]
[I]
System > Administration > Shared Folders[/I]

This adds entries to;

[PHP]gksudo gedit /etc/samba/smb.conf[/PHP]

Which can also be manually configured – once configured do;

[PHP]sudo /etc/init.d/samba restart[/PHP]

Then check the editing with;

[PHP]testparm[/PHP]

*Places > Network Servers*

To take the network/internet down and up;

[PHP]sudo ifup eth0
sudo ifdown eth0[/PHP]

The following checks the connection;
[PHP]
nmblookup MSHOME[/PHP]

The following checks the configuration;

[PHP]smbclient -L ubuntu[/PHP]

You ***must*** configure your windows firewall to allow networking, for example in Norton go to firewall and auto configure network.

Here's a sample smb.conf;

[PHP]log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

encrypt passwords = true
passdb backend = tdbsam guest
obey pam restrictions = yes
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

socket options = TCP_NODELAY

wins support = no

[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0700
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[storage]
   path = /mnt/exchange/fatshare
   comment = fat32_partition
   available = yes
   browseable = yes
   public = yes
   writable = yes[/PHP]

---

### Post by Shampyon on 2006-07-07
Results of testparmb:
[PHP]my-username@GORT:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[Videos]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = HOME
        server string = GORT
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[MyFiles]
        path = /home/samba
        force user = Mike
        force group = HOME
        read only = No
        create mask = 0644
        guest ok = Yes

[Videos]
        path = /media/sda5/Videos
        read only = No
        guest ok = Yes
[/PHP]

Results of nmblookup:
[PHP]my-username@GORT:~$ nmblookup HOME
querying HOME on 10.255.255.255
name_query failed to find name HOME
 [/PHP]

Results of smbclient -L ubuntu
[PHP]my-username@GORT:~$ smbclient -L ubuntu
Connection to ubuntu failed
[/PHP]

Still can't see MIKE (my brother's computer) through PLACES >> NETWORK SERVERS >> WINDOWS NETWORK. I have no idea what's going on...

---

### Post by Irony on 2006-07-07
Have you configured the firewall (in Norton for example) on the Windows machine to accept networking or else you won't see much - I got intermittent viewing until did this.

---

### Post by Shampyon on 2006-07-07
It was already set up on a home network when I was using XP. 
My Linux box is on the same IP (I set it to static).
I'll have my brother look and see if there's anything in his firewall that may be blocking me, though.

*Edit:* We checked. His firewall isn't blocking me. Poop, I was hoping it's be that easy :(

---

### Post by Shampyon on 2006-07-09
I didn't know how to properly restore fstab and smb.conf, so I opened the backup versions I had and copy/pasted the contents through sudo nautilus.
No luck. I still can't see my brother on the network. It's odd, when I first installed Dapper it worked okay - I could see all of his files, even if he couldn't see me. No, we've got nothing.
Whu...:confused:

---

### Post by Irony on 2006-07-09
You might want to look at a recent HOW TO, as my knowledge is limited on the subject; [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

As I indicated in my first post, you don't need samba to see your brother's computer (his shared folder should appear in Network Servers in Ubuntu). So it doesn't sound like anything to do with samba.

Samba is so your brother can see your shared folders.

So if you can't see your brother's folders but you can both ping the router then perhaps the router is blocking the exchange.

---

### Post by Shampyon on 2006-07-09
I pinged the router, no problem. I can't ping my brother, though.

Also, oddly enough, I can't get access to the router from my browser anymore.

"[B][I]Unable to connect

Firefox can't establish a connection to the server at 10.1.1.1.[/I][/B]"

It wouldn't have anything to do with my installing Firestarter, would it? I wouldn't think it'd make a difference unless it's running (I only turn it on when torrenting), but then I know nothing of the possible differences between w32 and linux firewalls.

*Edit:* I just accessed the router from my brother's computer. I can't find any settings that are different from when I first installed Ubuntu. This is a little bit frustrating...
[I]
Edit 2:[/I] I've read that Firestarter can be used to reconfigure your ports. In the hopes that this was what was causing the problem, I used firestarter to give full access to my router, plus put in the bittorrent ports I'd previously configured on the router. No dice. Still can't connect to the router, and I can't use bittorrent either.

---

