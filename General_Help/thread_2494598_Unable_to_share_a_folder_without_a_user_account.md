---
title: "Unable to share a folder without a user account"
date: 2024-01-21
forum: General Help
---

### Post by corradoventu on 2024-01-21
Ubuntu 24.04 after installing nautilus-share I select folder sharing selecting 'Guest access ... without a user account' but I'm unable to access the folder without a user account, I'm forced to define an smbpasswd for my user.
Not selecting 'Guest access..' does not change the problem.
Note in Ubuntu 22.04 I don't need to install nautilus-share because automatically installed when I click on Folder sharing but the problem is the same.
Please help, thanks.

---

### Post by Morbius1 on 2024-01-21
Are you sharing a folder in your home folder or under /media/your-user-name?

If yes the problem is the Linux permissions set on those parent folders. One way around this is to edit [COLOR="#B22222"]/etc/samba/smb.conf[/COLOR] and add the following line under [COLOR="#B22222"]workgroup = WORKGROUP[/COLOR]:
```
force user = morbius
```

*[COLOR="#0000FF"]Change morbius to your Linux login user name.[/COLOR]*

Then restart samba:
```
sudo service smbd restart
```

If you are sharing a folder someplace else post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by corradoventu on 2024-01-21
I'm sharing the folder 'Public' in my Home
BEFORE adding 'force user = morbius' I have:
corrado@corrado-n8-nn-0118:~$ net usershare info --long
[Pub-n8]
path=/home/corrado/Public
comment=
usershare_acl=Everyone:R,CORRADO-N8-NN-0118\corrado:F,
guest_ok=y

After adding 'force user = morbius'
corrado@corrado-n8-nn-0118:~$ net usershare info --long
[Pub-n8]
path=/home/corrado/Public
comment=
usershare_acl=S-1-1-0:R,S-1-5-21-1712845677-2382965628-2916264264-1000:F,
guest_ok=y

and trying share:

---

### Post by Morbius1 on 2024-01-21
Did you literally add "force user = morbius" or did you add "**[COLOR="#B22222"]force user = corrado[/COLOR]**". You need to add your own user name not mine.

---

### Post by corradoventu on 2024-01-22
Thanks, I didn't realize that "morbius" is your nickname, I thought it was a keyword, I'll try again.
... it works... Thank you very much

---

