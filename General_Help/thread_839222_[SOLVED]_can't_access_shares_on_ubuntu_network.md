---
title: "[SOLVED] can't access shares on ubuntu network"
date: 2008-06-24
forum: General Help
---

### Post by UbuntuNerd on 2008-06-24
hello im a little new to linux so please correct me if im wrong anyway i have an Ubuntu server and Ubuntu desktop also i have a vista machine in my home network i installed samba and firestarter and i can see all the shares from all pc's but when i try to acces them im prompted with a login screen i used the right user name and password but got access denied any ideas i also try smbtree here is the output

WORKGROUP
	\\UBUNTU         		
		\\UBUNTU\share folder   	
		\\UBUNTU\PDF            	PDF
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
		\\UBUNTU\homes          	Home Directories
	\\THEMONKEY-PC   		
		\\THEMONKEY-PC\Users          	
		\\THEMONKEY-PC\Send To OneNote 2007	Send To OneNote 2007
		\\THEMONKEY-PC\Public         	
		\\THEMONKEY-PC\print$         	Printer Drivers
		\\THEMONKEY-PC\My Pictures    	
		\\THEMONKEY-PC\IPC$           	Remote IPC
		\\THEMONKEY-PC\D$             	Default share
		\\THEMONKEY-PC\C$             	Default share
		\\THEMONKEY-PC\C              	
		\\THEMONKEY-PC\ADMIN$         	Remote Admin
	\\JAIME-DESKTOP  		
cli_start_connection: failed to connect to JAIME-DESKTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
can anyone help thanks !!!!:confused:

---

### Post by timcredible on 2008-06-24
what os is running on the client and server?

---

