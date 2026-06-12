---
title: "Samba share in 20.04"
date: 2022-04-14
forum: General Help
---

### Post by n2te on 2022-04-14
I have 3 Ubuntu machines that are running 18.04 and I installed samba share on all 3.  I was able to easily share folders and files across all 3 of my Ubuntu machines as well with my MacOSX machine and my Sony Android smart-TV. Local network file sharing is a wonderful thing.  However recently I upgraded my Ubuntu machine #3 to 20.04 and installed samba share on it. Using Nautilus I'm able to click on a particular folder and select Sharing and the appropriate check-boxes. However I can't access that folder (or any shared folders) on the 20.04 machine. My other Ubuntu PC's display an error "Unable to access location. Failed to retrieve share list from server: Connection timed out." I've searched for a solution online but I'm confused as to what I should do to share folders on my 20.04 machine. It was quite simple in 18.04. But now it seems like there is some additional setup steps required. Can someone please assist. My experience with Linux & Ubuntu is not all that extensive. But I do know enough to get myself in trouble. (LOL) Thanks.

---

### Post by SeijiSensei on 2022-04-15
If you're using something like
```
//server_name/share_name
```
to reference the share, your computer may not know how to resolve "server_name". One easy test is to use the server's IP address instead. For instance,
```
//10.10.10.10/share_name
```

Can you open a terminal and run "ping server_name"? That will tell you right away if name resolution is properly configured.

---

### Post by n2te on 2022-04-16
(Youtube Video tutorial guide used: v=7Q0mnAT1MRg)

Steps taken:
Step 1. sudo apt install samba
Step 2. systemctl status smbd
Step 3. cd /etc/samba
Step 4. sudo sudo systemctl stop smbd
Step 5. sudo systemctl status smbd
Step 6. sudo nano smb.conf

[global]
server string = edlinux3SambaServer
workgroup = WORKGROUP
security = user
map to guest = Bad User
name resolve order = bcast host
include = /etc/samba/shares.conf

Step 7. sudo nano shares.conf

[Document Files]
path = /home/ed/Documents2
force user = smbuser
force group =smbgroup
create mask = 0664
force create mode = 0664
directory mask = 0775
force directory mode = 0775
public = yes
writable = yes

Step 8. sudo groupadd --system smbgroup

Step 9. cat /etc/group
Results:  smbgroup:x:998:smbuser

Step 10. sudo useradd --system --no-create-home --group smbgroup smbuser

Step 11. cat /etc/passwd
Results: smbuser:x:998:997::/home/smbuser:/bin/sh

Step 12. sudo chown -R smbuser:smbgroup /home/ed/Documents2
Step 13. sudo chmod -R g+w /home/ed/Documents2

Step 14. sudo systemctl start smbd
Step 15. systemsctl status smbd

Step 16. Access Documents2 folder from another linux Ubuntu 18.04 machine:
Error message received:

Unable to access location. Failed to retrieve share list from server: Connection refused.

Any suggestions?

---

### Post by n2te on 2022-04-16
when i look in  /var/lib/samba/usershares I see the FOUR folders that I designated as "shares" from Nautilus. I also do not have any folder in /home/.... named "sambashare" as part of the "path" specification. What should that line look like in the file?

---

