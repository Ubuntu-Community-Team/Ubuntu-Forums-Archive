---
title: "trying to delete a .swp file"
date: 2008-04-28
forum: General Help
---

### Post by qphone on 2008-04-28
Hi all,

Just installed 8.04 and loving it. I am new to linux but am willing to go through the hoops and hurdles. Anyways...all installed perfectly inluding my wireless notebook card without a hitch (it has Atheros chipset which is fully supported)

My only question is after succesfully logging onto my secure WPA2 network, it keeps asking for "unlock keyring". I've placed my password many, many times but the damn thing keeps popping up so for now I just denied it.

After searching the endless google links i came across one link which allows me to manipulate my user password to be the same as my network password. Apparently by doing this...I won't get bothered again. BUT...after doing some command lines (still new to the game after being a gui double click windows icon zombie) I now get this:



[B]E325: ATTENTION
Found a swap file by the name "/etc/pam.d/.gdm.swp"          
owned by: compaq   dated: Sun Apr 27 20:59:03 2008         
file name: /etc/pam.d/gdm          
modified: YES         
user name: root   
host name: compaq-laptop        
process ID: 11556
While opening file "/etc/pam.d/gdm"             
dated: Mon Apr 21 08:47:43 2008

(1) Another program may be editing the same file.  

If this is the case, be careful not to end up with two    
different instances of the same file when making changes.    
Quit, or continue with caution.

(2) An edit session for this file crashed.    
If this is the case, use ":recover" or "vim -r /etc/pam.d/gdm"    
to recover the changes (see ":help recovery").    
If you did this already, delete the swap file "/etc/pam.d/.gdm.swp"    
to avoid this message.
"/etc/pam.d/gdm" 11L, 
400C
Press ENTER or type command to continue
[/B]

I'm trying to delete my erroneous swap file but to no avail. Can someone please point me in the right directions as what to type in my Terminal?

Thanks!

---

### Post by juan@forum on 2008-04-28
sudo rm -rf /etc/pam.d/.gdm.swp

---

### Post by qphone on 2008-04-28
> **juan@forum said:**
> sudo rm -rf /etc/pam.d/.gdm.swp

Thanks for the quick reply. After doing that line...it did the obvious by asking for my password which I've entered and is now at the root of username@username - laptop: -$ 

does this mean its done?

---

### Post by qphone on 2008-04-28
since I'm on this topic the main reason for me screwing up my swap file was to stop the annoying "UNLOCK KEYRING".

Can anyone point to a link (I've done the search "UNLOCK KEYRING" but no answers on this forum) to a successful approach in getting rid of this annoying feature?

Thanks again.

---

### Post by adult swim on 2008-04-28
are you using an automatic login at boot? ie no request for username or password?  the only time ive ever gotten keyring queries was when there was an autologin on boot.

---

