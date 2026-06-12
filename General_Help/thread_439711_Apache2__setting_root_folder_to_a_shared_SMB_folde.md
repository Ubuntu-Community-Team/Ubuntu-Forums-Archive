---
title: "Apache2 : setting root folder to a shared SMB folder"
date: 2007-05-10
forum: General Help
---

### Post by alingham on 2007-05-10
Hi

I am running Ubuntu Edgy through VMWare server 1.01
The reason this is important is because I have built most of my websites in Windows using Dreamweaver, in PHP.
So I am running ubuntu through vmware on XP, and I am wanting to develop my websites in Ubuntu.

But I don't want to create duplicate copies of the websites - because then I'll be forever copying them back and forward between ubuntu and xp folders as I edit them in either Linux of Windows.
I have managed to configure vmware so that I can share my "websites" folder, and I can view that in Ubuntu through Samba (smb://computer_name/websites/)

What I want to do is set my Apache2 server in Ubuntu to point to this shared folder as its document root.

Is there any way to do this?

(As I am only using this server as a local host, I am not worried about any security issues using a shared folder might raise!)

Please Help!:confused:

---

### Post by dfreer on 2007-05-11
try looking in ubuntu guide (a link is in my sig) for a way to mount samba shares permantly in ubuntu (you may need to check the edgy guide for it as the feisty guide isn't quite complete yet). You can mount it directly to /var/www/, OR mount it to /mnt/www/ and then edit your /etc/apache2/sites-enabled/000-default and change the default root directory to /mnt/www/ (recommended).

EDIT: Yep, feisty should work fine. This is a direct link to one of the how-tos, you may check out another one depending on your situation (there is like 6 there):
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

