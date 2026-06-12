---
title: "Mounting a network drive on ubuntu 20.04 LTS"
date: 2020-05-28
forum: General Help
---

### Post by dellboy on 2020-05-28
hi there i am starting to use ubutnu as my daily os again but i have one thing i cant seem to work out i have an nas device that i put a lot off my files on but for some reason i cant seem to mount it on ubuntu i can see the devices on my network in the ubuntu file manger 

see this link below to see what i mean 
[IMG]https://i.imgur.com/TEkv31k.png[/IMG]

i am guessing its because its not asking me for an login it could off been using windows smb share would i need to install something on ubuntu to get this working 

hope this has given you enough information to help me if you need more please be nice and ill try and explain more

---

### Post by Morbius1 on 2020-05-28
Just a guess as I don't own your nas but according to [this page]("https://tompai.pro/computers/d-link-dns-323-requires-smb1-protocol-cant-connect-from-windows-10/") it's because d-link doesn't enable any smb dialect greater than smb1 so you will have to do exactly the same thing in Ubuntu 20.04 as you would in Windows 10 and turn on smb1 on the client side.

You can either install samba itself ( sudo apt install samba ) if you also want to create shares on your ubuntu machine for others to access or you can install smbclient ( sudo apt install smbclient ) then edit [highlight]/etc/samba/smb.conf[/highlight] and right under the workgroup = WORKGROUP line add this one:
```
client min protocol = NT1
```
Then restart smbd:
```
sudo service smbd restart
```
Or better yet just reboot Ubuntu.

---

### Post by dellboy on 2020-05-28
i have installed samba but still no luck i get the following message 

I do plan to get a new nas in the near future but for now, its one-off the places I have all my files 
[IMG]https://i.imgur.com/e8lJ5x6.png[/IMG]

---

### Post by dino99 on 2020-05-28
Seems several users have met such issue  [https://askubuntu.com/questions/1229929/cant-acces-nas-anymore-after-upgrading-to-20-04](https://askubuntu.com/questions/1229929/cant-acces-nas-anymore-after-upgrading-to-20-04)

---

### Post by Morbius1 on 2020-05-28
Using Connect to Server in your file manager access the nas and one of it's shares explicitly.

From your original screeshot it looks like one of them is NetBIOS based and the other appears to be mDNS based- use the mDNS one. So it would look something like this:
```
smb://dlink-031D27.local/Volume_1
```
[COLOR=#ff0000]*Don't forget the .local at the end of the host name.*[/COLOR]

I have no idea how your shares on the NAS are set up so replace Volume_1 with the share name you created on the NAS.

---

### Post by dellboy on 2020-05-30
for anyone that might read this in the future  the link dino99 had the answer 


sudo nano /etc/samba/smb.conf 

in the [global] section, add the following line

client min protocol = NT1
Save the file and exit the editor.

You must restart the Samba Service for this change to take effect. In a terminal, enter this command:

sudo service smbd restart


I did not need to do the following but 

You should be able to access your samba shares successfully. If you cannot connect to your samba share, you can lower even more the protocol security in smb.conf (not recommended), by using:

client min protocol = CORE

---

### Post by Morbius1 on 2020-05-30
How was that different from my post?
> **Morbius1 said:**
> Just a guess as I don't own your nas but according to [this page]("https://tompai.pro/computers/d-link-dns-323-requires-smb1-protocol-cant-connect-from-windows-10/")  it's because d-link doesn't enable any smb dialect greater than smb1 so  you will have to do exactly the same thing in Ubuntu 20.04 as you would  in Windows 10 and turn on smb1 on the client side.

You can either install samba itself ( sudo apt install samba ) if you  also want to create shares on your ubuntu machine for others to access  or you can install smbclient ( sudo apt install smbclient ) then edit  [highlight]/etc/samba/smb.conf[/highlight] and right under the workgroup  = WORKGROUP line add this one:
```
client min protocol = NT1
```
Then restart smbd:
```
sudo service smbd restart
```
Or better yet just reboot Ubuntu.

---

