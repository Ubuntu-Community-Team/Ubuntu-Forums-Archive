---
title: "Help me translate Windows 10 SMBv2 credentials into to Ubuntu 18.10 equivalent"
date: 2019-03-08
forum: General Help
---

### Post by jdrch on 2019-03-08
I have an Windows 10 v1809 PC (which I'll just call Windows10PC) that has an SMBv2 folder (SMBv2Folder) shared to my home LAN (i.e. NOT a domain). From a Windows 10 v1809 client perspective, the folder location looks like //Windows10PC/SMBv2Folder, and the credentials are Windows10PC\MyMicrosoftAccountUsername + MyMicrosoftAccountPassword. Note that I'm using a Microsoft Account and not a local Windows one. These credentials work perfectly from all my Windows 10 clients. 

However, I'm having great difficulty connecting to the same folder from an Ubuntu 18.10 client; I get either "Permission denied" or "Stale file handle" error messages. Can anyone tell me what the Ubuntu equivalent of the above Windows credentials are for the following SMB fields: **Path**, **Domain** (bear in mind that the PC in question is on a home LAN, *NOT* a domain), and **Username**?

Also, AFAIK I only need to have cifs-utils installed to mount an SMBv2 share. Is this the case, or should I install something additional?

---

### Post by Morbius1 on 2019-03-08
> From a Windows 10 v1809 client perspective, the folder location looks  like //Windows10PC/SMBv2Folder, and the credentials are  Windows10PC\MyMicrosoftAccountUsername + MyMicrosoftAccountPassword.
It is not clear to me after reading your entire post how you are mounting the share - from the file manager or with a cifs mount so I'll give you both:

Let's say your MS Account is [EMAIL="xxx@yyy.com"]xxx@yyy.com[/EMAIL] with a password of ppp

From the file manager:
username = xxx
domain = yyy.com
password = ppp

From a mount.cifs mount:
You would have to include as your mount options: 
```
username=xxx,password=ppp,domain=yyy.com
```

The file manager and mount.cifs are unrelated but they both do the same thing - more or less. Both will negotiate with the server the best smb dialect to use. The file manager will go from an smb dialect in antiquity all the way up to smbv3. mount.cifs today will also negotiate the best dialect from smbv2.1 to 3.02 ( 3.11 in linux kernel 4.17 ).

---

### Post by jdrch on 2019-03-08
Hmmm thanks. I'll try this later.

---

### Post by jdrch on 2019-03-10
So that doesn't work. Is there a cifs-utils conf file where I can set the SMB version or something?

Also: Good God why is everything so hard with Samba? Literally every other client connects just fine.

---

### Post by Morbius1 on 2019-03-10
> So that doesn't work.
Of course it works. I do it every day:
> tester@xub1804:~$ sudo mount -t cifs //vwin10.local/documents /home/tester/Test -o username=xxx,domain=gmail.com,password=ppp,uid=1000
tester@xub1804:~$ ls -al /home/tester/Test
total 10
drwxr-xr-x  2 tester root  4096 Feb 28 08:24  .
drwxr-xr-x 27 tester tester 4096 Mar 10 08:04  ..
-rwxr-xr-x  1 tester root   402 Apr 10  2018  desktop.ini
-rwxr-xr-x  1 tester root     0 Nov 26  2015  FromLin.txt
-rwxr-xr-x  1 tester root     0 Sep 29 07:34  FromXub2.txt
-rwxr-xr-x  1 tester root     0 Sep 29 07:15  FromXub.txt
-rwxr-xr-x  1 tester root     1 Sep 11  2017  gedit.txt
drwxr-xr-x  2 tester root     0 Apr 10  2018 'My Music'
drwxr-xr-x  2 tester root     0 Apr 10  2018 'My Pictures'
drwxr-xr-x  2 tester root     0 Apr 10  2018 'My Videos'

> Is there a cifs-utils conf file where I can set the SMB version or something?
There should be no need to do that because cifs will negotiate with the server ( Win10 ) to determine the correct smb dialect to use from a range of 2.1 to 3.02 ( 3.11 in linux kernel 4.17 ). You can always force it to a particular dialect if you want by adding the option **vers** to the list of cifs mount options:
> sudo mount -t cifs //vwin10.local/documents /home/tester/Test -o username=xxx,domain=gmail.com,password=ppp,uid=1000,[COLOR=#0000cd]**vers=2.0**[/COLOR]

Note: the uid number above is 1000. I have no idea why the forum adds a space before the last 0.

---

### Post by jdrch on 2019-05-19
Forgot to update this. Neither myself nor Veeam tech support in a live session could get this to work, so I wound up using Veeam Backup & Replication as the backup target instead. This worked just fine until the 19.04 update, which has caused Veeam backups (veeamsnap, to be specific) to stop working entirely. *sigh* Thanks for the ideas.

---

