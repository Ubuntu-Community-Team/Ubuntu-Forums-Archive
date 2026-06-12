---
title: "Samba problem; cannot share folder in Lubuntu system with smart phone"
date: 2015-11-20
forum: General Help
---

### Post by KayeNg on 2015-11-20
[FONT=arial]Hey guys, I reinstalled my Lubuntu 14.04.  Everything's working except samba.  I used to be able to share a folder in my Lubuntu system with my android phone.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I installed cifs-utils thru Synaptic.  I got these two folders:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]/etc/samba[/FONT]
[FONT=arial]/usr/share/samba
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Both folders contain the file smb.conf[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Is this normal? If I'm going to edit smb.conf, do I edit both of them? Because that's what I did.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I created a folder in desktop called 'temp', then I added the following in the two smb.conf files:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][temp]
	comment = temp
	path = /home/user/Desktop/temp
	browseable = yes
	guest ok = yes
	writeable = yes
	create mask = 0755
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I used to be able to see the contents of "temp" in my Android phone, provided both my Lubuntu computer and my Android phone are connected to the same wifi network.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now I can't anymore.  I also don't remember having to edit two smb.conf files.  It was just one.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Your help is highly appreciated. Thank you.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kaye[/FONT]

---

### Post by bab1 on 2015-11-20
> **KayeNg said:**
> [FONT=arial]Hey guys, I reinstalled my Lubuntu 14.04.  Everything's working except samba.  I used to be able to share a folder in my Lubuntu system with my android phone.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I installed cifs-utils thru Synaptic.  I got these two folders:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]/etc/samba[/FONT]
[FONT=arial]/usr/share/samba
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Both folders contain the file smb.conf[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Is this normal? If I'm going to edit smb.conf, do I edit both of them? Because that's what I did.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I created a folder in desktop called 'temp', then I added the following in the two smb.conf files:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][temp]
	comment = temp
	path = /home/user/Desktop/temp
	browseable = yes
	guest ok = yes
	writeable = yes
	create mask = 0755
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I used to be able to see the contents of "temp" in my Android phone, provided both my Lubuntu computer and my Android phone are connected to the same wifi network.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now I can't anymore.  I also don't remember having to edit two smb.conf files.  It was just one.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Your help is highly appreciated. Thank you.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kaye[/FONT]
Is the Samba server installed and running?  The cif-utils are by themselves will not be enough to share files.  You can check to see if you have a running Samba server with this command from the terminal ```
pgrep -l mbd
```...post the output back here.

The /etc/samba/smb.conf file is the file you use to configure Samba.  The other one is not used.  It is just a copy.

---

### Post by KayeNg on 2015-11-21
Hey bab1, here it is:

580 smbd
755 smbd
1760 nmbd

Using this Lubuntu system desktop computer, I can access files of another desktop computer running Windows 7.  But I just can't seem to access a shared folder in the said Lubuntu computer using my Android phone.  I used to be able to.

---

### Post by bab1 on 2015-11-21
> **KayeNg said:**
> Hey bab1, here it is:

580 smbd
755 smbd
1760 nmbd

Using this Lubuntu system desktop computer, I can access files of another desktop computer running Windows 7.  But I just can't seem to access a shared folder in the said Lubuntu computer using my Android phone.  I used to be able to.
Are you saying that you can see the shares on the Lubuntu machine from a computer running Windows 7?

---

### Post by KayeNg on 2015-11-21
> [COLOR=#000000]Are you saying that you can see the shares on the Lubuntu machine from a computer running Windows 7?

[/COLOR]

I'm saying the opposite, that is, I can see the shares of the computer running Windows 7; I haven't tried vice versa but I'm pretty sure it works too.  

What I'm saying in my previous post is this:  When I'm using my Android phone, I CANNOT see the shares in my Lubuntu desktop computer; I used to be able to.  (I reinstalled Lubuntu, then I wasn't able to do so like before.)

---

### Post by bab1 on 2015-11-21
> **KayeNg said:**
> I'm saying the opposite, that is, I can see the shares of the computer running Windows 7; I haven't tried vice versa but I'm pretty sure it works too.  

What I'm saying in my previous post is this:  When I'm using my Android phone, I CANNOT see the shares in my Lubuntu desktop computer; I used to be able to.  (I reinstalled Lubuntu, then I wasn't able to do so like before.)
Pretty sure is not worth anything at all.  See if you can see the share from Lubuntu with the Windows machine.

Let's also see if the share is available to the Lubuntu machine from itself.  Post the output of this command from the Lubuntu command line```
smbtree
```

When you post text output from the terminal you should use the [noparse]```
 
``` [/noparse] blocks to preserve the formatting.  The easiest way to do this is to click on the **[SIZE=5]# [/SIZE]** icon at the top of the advanced reply editor and place the code in between the blocks.

---

### Post by KayeNg on 2015-11-23
When I typed "smbtree", I got this:

> The program 'smbtree' is currently not installed. You can install it by typing:
sudo apt-get install smbclient

So I installed it.  Then typed it again.

WORKGROUP
	\\HOMET-01       		homet-01 server (Samba, Ubuntu)
		\\HOMET-01\homes          	Home Directories
		\\HOMET-01\temp           	
		\\HOMET-01\IPC$           	IPC Service (homet-01 server (Samba, Ubuntu))

The one I'm trying to access thru my Android phone is the "temp" folder.  Right now I'm unable to do so.

Maybe I should just reinstall the OS...........

---

### Post by KayeNg on 2015-11-23
sorry, forgot the code blocks...

---

### Post by bab1 on 2015-11-23
> **KayeNg said:**
> When I typed "smbtree", I got this:


So I installed it.  Then typed it again.

```
WORKGROUP
	\\HOMET-01       		homet-01 server (Samba, Ubuntu)
		\\HOMET-01\homes          	Home Directories
		\\HOMET-01\temp           	
		\\HOMET-01\IPC$           	IPC Service (homet-01 server (Samba, Ubuntu))

```
The one I'm trying to access thru my Android phone is the "temp" folder.  Right now I'm unable to do so.

Maybe I should just reinstall the OS...........
So far we can see that the smbd daemon that is the Samba file server is working```

580 smbd
755 smbd
1760 nmbd

```...and the server responds to a client ```
WORKGROUP
	\\HOMET-01       		homet-01 server (Samba, Ubuntu)
		\\HOMET-01\homes          	Home Directories
		\\HOMET-01\temp           	
		\\HOMET-01\IPC$           	IPC Service (homet-01 server (Samba, Ubuntu))
```

What I can't see is whether the other client sees the server advertisement>  See if you can see the share from Lubuntu with the Windows machine.

I don't see how reinstalling the OS or Samba will help.  The Samba server is working.  The problem appears to be access permissions and/or ownership.

What are the permissions on the **complete path** to */home/user/Desktop/temp*  it should be at least 755 all the way to */home/user/Desktop/* and 777 on the temp folder.

---

### Post by KayeNg on 2015-11-24
> [COLOR=#000000]What are the permissions on the [/COLOR]**complete path to */home/user/Desktop/temp it should be at least 755 all the way to [I]/home/user/Desktop/ and 777 on the temp folder.*[/I]**

I'm afraid I don't know how to do that.  All I know is right clicking on the temp folder and click Properties, then Permissions tab.

---

### Post by KayeNg on 2015-11-24
I've manually deleted the "temp" share in smb.conf , then I opened the Samba graphical front end which I downloaded from software center, then thru that Samba app I added again the temp share.  When I opened the smb.conf in Leafpad, I get this:

> [temp]
	path = /home/homet/Desktop/temp
	writeable = yes
;	browseable = yes
	guest ok = yes


Why is there a ; in front of "browseable = yes" even if I had ticked Writable and Visible in the samba graphical front end, as well as ticked "Allow access to everyone" ?

---

### Post by bab1 on 2015-11-24
> **KayeNg said:**
> I'm afraid I don't know how to do that.  All I know is right clicking on the temp folder and click Properties, then Permissions tab.
```
ls -l /home

ls -l /home/<usermame>

ls -l /home/<username>/Desktop
```

Each one of these commands shows the permissions along the path from /home to /home/<username>/Desktop/temp

---

### Post by bab1 on 2015-11-24
> **KayeNg said:**
> I've manually deleted the "temp" share in smb.conf , then I opened the Samba graphical front end which I downloaded from software center, then thru that Samba app I added again the temp share.  When I opened the smb.conf in Leafpad, I get this:
```
[temp]
path = /home/homet/Desktop/temp
writeable = yes
; browseable = yes
guest ok = yes 
```
Why is there a ; in front of "browseable = yes" even if I had ticked Writable and Visible in the samba graphical front end, as well as ticked "Allow access to everyone" ?
Because the GUI is not doing the work you think it is supposed to do...???  The script that is run with the app may not work correctly...???

If you want to be able to browse to the share you need to uncomment (**remove the semicolon**) in front of [I]browseable = yes
[/I]

Editing the smb.conf file directly is the quickest way to fix the browsing problem.

---

### Post by KayeNg on 2015-11-24
> [COLOR=#000000]If you want to be able to browse to the share you need to uncomment ([/COLOR]**remove the semicolon) in front of *browseable = yes***

Tried that, still could not access the folder thru my android phone.

Anyway, I changed the name "temp" to "share"

```
homet@homet-01:~$ ls -l /home
total 4
drwxr-xr-x 21 homet homet 4096 Nov 24 14:50 homet
homet@homet-01:~$

```

```
homet@homet-01:~$ ls -l /home/homet
total 36
drwxr-xr-x 10 homet homet 4096 Jun 19  2013 bluegriffon
drwxr-xr-x  5 homet homet 4096 Nov 24 15:49 Desktop
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Documents
drwxr-xr-x  2 homet homet 4096 Nov 20 15:12 Downloads
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Music
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Pictures
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Public
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Templates
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Videos
homet@homet-01:~$

```

```
homet@homet-01:~$ ls -l /home/homet/Desktop
total 12
drwxrwxr-x 4 homet homet 4096 Nov 21 16:32 homet-02-win7
drwxrwxr-x 3 homet homet 4096 Nov 21 16:35 homet-03-win8
drwxrwxr-x 2 homet homet 4096 Nov 24 15:49 share
homet@homet-01:~$

```

---

### Post by bab1 on 2015-11-24
> **KayeNg said:**
> Tried that, still could not access the folder thru my android phone.
I never said that it would cure your problem.  It is needed for any client to browse for SMB resources.  Can you see the shares if you run smbtree from the Samba server? > 

Anyway, I changed the name "temp" to "share"
Changed the name of what?  The share name?  I see the directory is named *share* now.  FYI:  The share name does not need to be the same as the directory name.  The share name is what you see when browsing Samba shares.  The format is:   //SERVER-NAME/share-name

```
homet@homet-01:~$ ls -l /home
total 4
drwxr-xr-x 21 homet homet 4096 Nov 24 14:50 homet
homet@homet-01:~$

```

```
homet@homet-01:~$ ls -l /home/homet
total 36
drwxr-xr-x 10 homet homet 4096 Jun 19  2013 bluegriffon
drwxr-xr-x  5 homet homet 4096 Nov 24 15:49 Desktop
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Documents
drwxr-xr-x  2 homet homet 4096 Nov 20 15:12 Downloads
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Music
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Pictures
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Public
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Templates
drwxr-xr-x  2 homet homet 4096 Nov 14 15:26 Videos
homet@homet-01:~$

```

```
homet@homet-01:~$ ls -l /home/homet/Desktop
total 12
drwxrwxr-x 4 homet homet 4096 Nov 21 16:32 homet-02-win7
drwxrwxr-x 3 homet homet 4096 Nov 21 16:35 homet-03-win8
[COLOR="#FF0000"]drwxrwxr-x 2 homet homet 4096 Nov 24 15:49 share[/COLOR]
homet@homet-01:~$

```
The permissions allow for any user to view the subdirectories down to the directory share (see red above).  However the permissions only allow read only for the users that will be accessing the share.

I still haven't heard whether the Windows machine can access the share.  Is there a reason for this?

My guess is that the problem is with the Android phone or its access, not the Linux server.

---

### Post by KayeNg on 2015-11-24
Hey, I got it. The android phone was getting the computers' host names mixed up.  I had to delete and re-scan them.  It was that simple.  Really sorry to have wasted your time.  But I was prompted to check the phone after your last post, so thanks! 

Anyway, to anyone who might encounter this in the future, using a file explorer like ES File explorer (free from google playstore), try deleting the computer or host names in the network, then re-scan.

This is thread is solved and closed.

Thanks again!

---

### Post by bab1 on 2015-11-24
> **KayeNg said:**
> Hey, I got it. The android phone was getting the computers' host names mixed up.  I had to delete and re-scan them.  It was that simple.  Really sorry to have wasted your time.  But I was prompted to check the phone after your last post, so thanks! 

Anyway, to anyone who might encounter this in the future, using a file explorer like ES File explorer (free from google playstore), try deleting the computer or host names in the network, then re-scan.

This is thread is solved and closed.

Thanks again!
As a post script to this; the COMPUTER NAME for SMB (Windows Sharing or Samba) is not a hostname.  It is a NetBIOS name.  It might not be important to this solution, but it can be important at other times.  You can't ping a NetBIOS name and the /etc/hosts file is not necessarily relevant.

---

### Post by timotheus3 on 2016-01-14
from my experience (or lack thereof) samba is a giant headache, i had it working one minute then nothing... surely there is an easier way?

---

