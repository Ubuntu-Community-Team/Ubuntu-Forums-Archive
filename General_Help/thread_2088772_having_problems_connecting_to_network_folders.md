---
title: "having problems connecting to network folders"
date: 2012-11-27
forum: General Help
---

### Post by RD2112 on 2012-11-27
hi all, having problems signing in to network folders from windows 7 and from this machine itself, i have been playing with smb.conf and am pretty sure my troubles lie in there, i am running 12.10 ubuntu and have included a pastebin of my smb.conf.

thanks for any help RD 

[http://pastebin.com/VGR30RaU](http://pastebin.com/VGR30RaU)

---

### Post by JonArcher on 2012-11-27
So I notice that you have security = user
have you setup any samba users?

A quick and dirty test would be to set that option to security = share and restart the service...

---

### Post by RD2112 on 2012-11-27
just tried with user = share still no luck accessing the shares with anything but my account.

not sure what you mean by setup samba users, i installed the samba gui to change settings and added a user from there, but still cant access anything under that account.

---

### Post by JonArcher on 2012-11-27
Ahh ok, so the gui should have created users for you.

The users in Samba are seperate to the users which you login to Linux with.

So you can browse the share if you enter your username but not your other users?

---

### Post by Morbius1 on 2012-11-27
> **JonArcher said:**
> So I notice that you have security = user
have you setup any samba users?

A quick and dirty test would be to set that option to security = share and restart the service...
That's just not true. 

security = user is the default for a reason please don't change it. "map to guest = Bad User" will convert anonymous remote users to the default user ( nobody ) automatically.

@RD2112, I'm confused by your post. Are you trying to access a share on your Linux box from Windows or the other way around?

If you are trying to access a Linux share what are the permissions of the shared entity:
```
ls -dl "/media/rd/nptmtls/Newport Metals"
```

---

### Post by Morbius1 on 2012-11-27
Missed something from your original post if you are trying to access a Linux share from Windows:
> i am running 12.10 ubuntu You shared a folder on **/media/rd/nptmtls/Newport Metals** and unless this is just a coincidence it's a partition that you are mounting when you need it as opposed to having it automount.

12.10 changed how this is done as it mount it to /media/$USER with access allowed only to $USER. THe remote users are not rd ( at least not all of them ) so in your case kelly has no access. The easiest way out of this is to modify your share definition in my opinion.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Change this:
> [Newport Metals]
        comment = newport documents
        path = /media/rd/nptmtls/Newport Metals
        writeable = yes
        browseable = yes
        valid users = kelly, rd
To this:
> [Newport Metals]
        comment = newport documents
        path = /media/rd/nptmtls/Newport Metals
        writeable = yes
        browseable = yes
        valid users = kelly, rd
[COLOR=Blue]**       force user = rd**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```The "valid users" line will restrict access to kelly and rd and the "force user" will convert them both to rd after samba allows access.

---

### Post by JonArcher on 2012-11-27
> **Morbius1 said:**
> That's just not true. 

security = user is the default for a reason please don't change it.

Yes but changing to share will allow a connection test without authentication and can rule out any initial connection problems, and it can easily be changed back afterwards!

---

### Post by RD2112 on 2012-11-27
changing the smb.conf file to add this made it work.

To this:
 	Quote:
 	 	 		 			 				[Newport Metals]
        comment = newport documents
        path = /media/rd/nptmtls/Newport Metals
        writeable = yes
        browseable = yes
        valid users = kelly, rd
[COLOR=Blue][B]       force user = rd

[/B][/COLOR]thank you  Morbius1 for your help [COLOR=Blue][/COLOR]was going to ask how to change mount points, but after changing that spot inthe config file it worked, then after i found that changing sharing options outsde of the samba gui adds a second entry to the server so i had duplicat entries. so have spent the last hour on clean up..  

thanks to everyone who jumped to help, you guys are what makes Ubuntu as awesome as it is : )
[COLOR=Blue][/COLOR]

---

