---
title: "Shares Don't Work"
date: 2008-05-31
forum: General Help
---

### Post by Naatan on 2008-05-31
Hi,

I have 2 laptops with Ubuntu installed, a Dell Latitude D830 which had the 8.04 RC and upgraded later on, and a HP Pavilion DV6700 which I installed the release version on 2 days ago.

On the Dell shares are working fine, I use the share settings in Nautilus and voila, share created.

When I do the same on the HP it initially gave me the error that I didn't have permissions on "/var/lib/samba/usershares", so I chmodded the directory to 777 and tried again, this time it created the share but it would by no chance appear on a remote computer (not even when I typed it manually).

Does anyone have a clue as to how I can solve this?

Also, while I'm at it (and this is not nearly as important) does anyone have the problem that when you connect through SMB with a windows pc it does not show the shares but they do work when you type them manually? This always worked automatically for me in previous versions of Ubuntu.

---

### Post by Naatan on 2008-06-01
bump

---

### Post by mike2357 on 2008-06-01
Regarding your last question (Windows shares), I've had the same problem.  A work around is Places -> Connect to Server, and then select Windows Share.  Type the server and share name.  This is how I have to connect with 8.04.

Regarding your HP problem, I don't have a solution except to double check settings you're probably already checked, such as firewall settings, and to make sure you've run smbpasswd -a on the HP so users can connect from the other PCs.

---

### Post by gkestrel on 2008-06-01
First i would re check all the settings in /etc/samba/smb.conf being careful to look for any misspelled entries, if you find any change them and restart samba afterwards. Also do you have nautilus share installed on the hp if so it probably need to be configured before it will work correctly. 

To Setup and configure nautilus share
(must be done as root):
copy and paste the following lines in the terminal

export USERSHARES_DIR="/var/lib/samba/usershare"
export USERSHARES_GROUP="samba"

mkdir -p ${USERSHARES_DIR}
groupadd ${USERSHARES_GROUP}
chown root:${USERSHARES_GROUP} ${USERSHARES_DIR}
chmod 01770 ${USERSHARES_DIR}

* next edit /etc/samba/smb.conf:

;/etc/samba/smb.conf

[global]
workgroup = WORKGROUP ; you can change to your own workgroup
security = share

usershare path = /var/lib/samba/usershare
usershare max shares = 100
usershare allow guests = yes
usershare owner only = yes

* Add the samba group to your user (replace your_username by your login):

usermod -a -G ${USERSHARES_GROUP} your_username

* Logout and login again and nautilus share will then work

hope this helps.

---

