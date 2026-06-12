---
title: "network share problem in smb.conf.."
date: 2008-02-22
forum: General Help
---

### Post by Mia_tech on 2008-02-22
I have setup different shares on my kununtu box, but I want to  make one of the shares available to everyone, without the need for entering username and password when accessing the share, I know is provably something I'm missing on the smb.conf file, if someone can point me to the right direction...

thanks

---

### Post by alan34 on 2008-02-23
Try something like this

[share]
	path = /home/samba/share
	force group = share
	write list = +share
	read only = Yes
	create mask = 0770
	directory mask = 0770
	guest ok = Yes


Think its the guest ok = Yes that will do the job

---

### Post by Mia_tech on 2008-02-23
> **alan34 said:**
> Try something like this

[share]
	path = /home/samba/share
	force group = share
	write list = +share
	read only = Yes
	create mask = 0770
	directory mask = 0770
	guest ok = Yes


Think its the guest ok = Yes that will do the job

I have guest ok = yes in my conf file and still is asking me for username and password,

---

### Post by alan34 on 2008-02-23
Are the people who are "guest" users on the machine you are trying to communicate
with? You can make them users without giving them a shell to log into so

TO ADD USER


adduser --shell /bin/false 'name'

passwd 'name' 'new password'

edit /etc/group    -  if new group

smbpasswd -a 'name'

edit /etc/samba/smb.conf    - add new 'group'


/etc/init.d/samba restart

of course the users [COLOR="Blue"]must[/COLOR] have the same username and same
password on all machines or you will end up with all sorts of trouble.

Hope this helps

---

### Post by Mia_tech on 2008-02-23
no this is just a simple share where I want guest with no account on the system to be able to store and share files, security is not an issue here...I don't want the users to have to remember username and or password for this...I'm probably missing some setting, just in case I gave everyone rwx permission on the share and still no go..
hope I explain myself

---

### Post by alan34 on 2008-02-23
Your "guests" must be users on the system as my last post with adduser --shell /bin/false they can do nothing on your system because they have nothing to log into. This is how my system is set up at work and I have had no problems.

I would create a test user on all your PCs and try it out, you can always remove after if it is not what you want. Remember you have to add the users to /etc/group if you want them to have more than read permissions.

---

