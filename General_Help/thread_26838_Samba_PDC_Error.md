---
title: "Samba PDC Error"
date: 2005-04-14
forum: General Help
---

### Post by kenironside on 2005-04-14
I am running Samba version 3.0.10-Ubuntu under Hoary final. I have transferred my Samba setup from a RedHat 9 system wher it ran OK. I am running Samba as a PDC in a small office network (2 x Win XP, 2 x Win 2000, 1 Hoary w/s, 1 Hoary mail & file server). 

Samba works fine and I can browse the shares etc from the clients. However, when I try to create a machine account and secret password, the clients can't access the domain. Win XP/2000 asks for the account name of an acocunt authorised to change the domain name, and I don't know what that is. I've tried the Samba root password, account name/password combo's - nothing works. I actually think that, for some reason, the clients are being prevented from acessing the domain even though all the diagnostics seem to be OK.

In log.smbd, I get the following lines:
[2005/04/14 08:19:12, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected
[2005/04/14 08:35:25, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected
[2005/04/14 09:24:06, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected
[2005/04/14 09:56:34, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected

I have googled this error without any help on understanding what may be the problem.

Here is my smb.conf file:
;KRI comments below relevant lines

[global]
;basic server settings
	workgroup = homenet
	netbios name = silverdesk
	server string = Samba %v PDC on %L
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192

;PDC and master browser settings
	os level = 64
	preferred master = yes
	local master = yes
	domain master = yes
	time server = yes
	csc policy = manual

;security and logging settings
	encrypt passwords = yes
	passdb backend = tdbsam
	domain logons = yes
	security = user
	log file = /var/log/samba/log.%m
	log level = 3 
	max log size = 5000
	kernel oplocks = no
	;Inserted to try to solve "smbd/oplock_linux.c:linux_init_kernel_oplocks(287)
	;Failed to setup RT_SIGNAL_LEASE handler" error

;user profiles
	logon drive = H:
	logon home = \\%L\%U
	;Not required if roaming profiles not implemented - KRI 27/9/2003
	;logon path = \\%L\profiles\%U

	username map = /etc/samba/smbusers

	;this line needed to tell windows machines 
	;that these users have admin rights
	;KRI 18 Sept 2003
	; apparently obsolete in Samba 3.0
	;domain admin group = ken felicity gael kath ironside

#--Shares--#

[netlogon]
	path = /etc/samba/netlogon
    	writable = no
    	browsable = no

[homes]
	comment = Home Directories
	browseable = no
	writeable = yes
	;valid users = %S
	create mode = 0664
	directory mode = 0775

[profiles]
	path = /home/samba/profiles
	writeable = yes
	browseable = no
	create mask = 0600
	directory mask = 0700

[common]
	comment = Shared folder
	path = /home/all/
	browseable = yes
	writeable = yes
	#valid users = %S
	create mode = 0664
	directory mode = 0777

Does anyone have any ideas about where I should look to get the Win XP/2000 PC's back into the domain?

Thanks, Ken

---

### Post by lutefiasco on 2005-04-22
Don't know if you've solved this, but I've been banging my head against Samba issues for a week or so now.  The Win box is asking for a **local**  administrator username/password in this instance, to chain the domain the machine is joined to.  There's theen a second authentication for a user authorised to join the domain (typically root).

---

