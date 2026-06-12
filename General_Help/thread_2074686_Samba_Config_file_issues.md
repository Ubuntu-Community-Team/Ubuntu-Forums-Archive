---
title: "Samba Config file issues"
date: 2012-10-22
forum: General Help
---

### Post by souar on 2012-10-22
Hey 

I've installed samba on my server but run into a couple of little issues. Firstly my global section just seems a mess and overly complicated for what I want (even though this is what was provided with the installation and I haven't edited it). 

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = WORKGROUP
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

Could someone possibly help me strip this down to what I need for simply running a local network file server with about 10 users and a couple of groups? I'm completely lost when I look at most of it.

Secondly my shares seem to be having an issue.

[Data]
	
    comment = Data
    path = /data
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

[share]
    comment = Share 
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

The share titled 'share' is based off of the first HDD running the OS as well. This works fine with all the read and write permissions for guest available and functioning! However the share titled 'data' does not allow even read permissions on any of the files in there even though its set up exactly the same way. The only difference is /data is the mount point of the second HDD that we want to use for most of our storage. Can anyone help me out on how to resolve as to why I cannot get any read or write permissions on 'data'?

Thanks

---

### Post by Morbius1 on 2012-10-22
**First**, your [global] section looks like the default smb.conf to me so there's no reason to touch it. 

[COLOR=Blue][I]And remember that smb.conf only represents modifications or additions to the default samba setup not the default itself. If you want to see how samba is actually running run this command:
```
testparm -sv
```[/I][COLOR=Black]**Second**, What are the linux permissions of /data?
[/COLOR][/COLOR]```
ls -dl /data
```[COLOR=Blue][COLOR=Black]
Linux permissions and samba authorization need to be in sync. So to allow guests read / write access to the folder itself the permissions have to be something like this:
[/COLOR][/COLOR]```
drwxrwxrwx
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by souar on 2012-10-22
I ran the ls -dl /data command and this is waht came up 

drwxr-xr-x 3 root root 4096 Oct 18 11:55 /data

Evidently this is different to what you stated it needed to be, how do I go about changing this? I'm guessing the sequence is: 

r = read
w = write
x = execute 

what does the 'd' stand for?

---

### Post by Morbius1 on 2012-10-22
"d" is for directory.

This should change permissions for everyone to rwx:
```
sudo chmod 0777 /data
```

---

### Post by souar on 2012-10-22
That worked perfectly! Thank you so much! Quick question there's a folder in the data drive labelled 'lost+found' what is this and is it necessary to have? I cannot access it and it was automatically created so was wondering do I need it? 

Thanks

---

