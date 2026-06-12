---
title: "Ideas on a FTP prog."
date: 2005-09-19
forum: General Help
---

### Post by waynejkruse10 on 2005-09-19
You know how there are programs like cuteftp, ftpexplorer and FlashFXP for Windows so you can upload files to your webserver. Well, i have set up a webserver on a home computer. Running Linux (Ubuntu), Apache, Php, Mysql and everything i need to run a forum. This computer will be plugged into school to be used for a local school forum for students and teachers to discuss things and get news and all sorts of stuff. This computer will be placed in the server room and the server room isnt always accessable so we want this computer to be able to be controlled (file wise) from any computer around the school rather than bugging the Admin (who is very busy switching from Novell to Windows Server 2003*) to get into the room.

So my question is, what software do i need to install so i can access my /var/www folder (my webserver folder) remotely via. FTP.


*The admin sadly changing the server from Linux based server to a Windows based server . The only reason he is doing this is because when the admin retires, the next admin can actually use and manage the server even though Novell is superiour the damn education department doesnt support it because they have a deal with microsoft. So tecnically we are not allowed to run Ubuntu on this student project server, but this may be supprising but i tried getting it running on Ubuntu, and it was much easier than getting it running on Windows 2000.

---

### Post by shakin on 2005-09-19
[QUOTE=waynejkruse10]So my question is, what software do i need to install so i can access my /var/www folder (my webserver folder) remotely via. FTP.[/QUOTE]

If you've installed openssh-server you already can. From nearly any FTP client you can connect with SFTP. You can also use WinSCP or a network folder in Gnome and KDE.

If you do a search in Synaptic for 'ftpd' you'll find a lot of ftp servers. Proftpd and pure-ftpd are good choices.

---

### Post by waynejkruse10 on 2005-09-19
Ok....

I got proftpd, and did the ./configure and it checked for gcc, cc, cc, cl and it couldnt find any of them so it cant find a suitible c compiler.

So i went to Synaptic and i looked for GCC and i found that GCC-3.3-Base was installed but GCC-3.3 wasnt, so i marked GCC-3.3 for installation but it told me that these packages needed to be removed before GCC is installed"

Language Pack En
Language Pack Base
Libapache-Mod-PHP4
Libc6-dev
Libc6-i686
Locales
lsb
Php4
Php4-cgi
Php4-cli
Php4-Mysql
ubuntu-base
ubuntu-desktop

Now i know several of them are very important especially the last 2 and any of the ones mentioning PHP or Apache because i need them for the server.

How do i install GCC without uninstalling all this other stuff?

---

### Post by kvn864 on 2005-09-19
Hi waynejkruse10
Ironicly I'm trying to do exactly the same thing: having Ubuntu box be in the server room and be able to ftp to Apache default ( /var/www/directory) folder with all the updates for a small local website on the LAN. I tried to set up folder sharing read/write access to that folder, just by some reason I can't configure Samba to work...
This command (sudo apt-get install samba) installs it, but
this command (sudo apt-get install smbfs) gives me error 
So not knowing what to do next I'll watch your post :)

---

### Post by waynejkruse10 on 2005-09-19
have you tried proftpd and got the same problems that i get?

---

### Post by kvn864 on 2005-09-19
is proftpd like ftp server thing on Ubuntu box?
here is what I did:
How to share home folders with read/write permissions:
&#9679;	sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
&#9679;	sudo gedit /etc/samba/smb.conf
&#9679;	Find this line 
...
;   security = user
...
&#9679;	Replace with the following lines 


   security = user
   username map = /etc/samba/smbusers
&#9679;	Find this section 
...
# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no
...
&#9679;	Replace with the following lines 

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes
&#9679;	save
&#9679;	then run
    sudo testparm
    sudo /etc/init.d/samba restart

---

### Post by waynejkruse10 on 2005-09-19
> sudo /etc/init.d/samba restart 

cant find that file

---

### Post by kvn864 on 2005-09-20
if you have samba installed that command will restart it.
are you making any progress?
how to make /var/www (read/write) so i can upload files to it?

---

