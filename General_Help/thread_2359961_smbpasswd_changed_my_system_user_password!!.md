---
title: "smbpasswd changed my system user password!?!"
date: 2017-04-30
forum: General Help
---

### Post by AR_Kozz on 2017-04-30
On Ubuntu 14.04 desktop, set up folder in /home to share. 

Attempted to access from ChromeOS device using "network file share" app, informed share was password-protected which I remembered doing some time ago.

To make sure I remembered the samba password, I ran smbpasswd on desktop and changed the password to itself.

Accessed the share from the ChromeOS device, tried to watch a video file, player hung without showing anything.

Back to desktop, ran a superuser command, was informed my password was incorrect. After many attempts, eventually tried the SMB passwd on a hunch and it worked.

At this point I shut down the share and disconnected the ChromeOS device, and confirmed that my sudo password was now the SMB password I had set.

rebooted to see if it was permanent. Old sudo password was still incorrect, but the SMB password only caused the screen to blank and then the login screen to pop up again.

rebooted to recovery and root prompt and reset password.

Ideas? I am 100% sure that I did not run passwd, only smbpasswd, before this happened.

---

### Post by #&amp;thj^% on 2017-04-30
> **AR_Kozz said:**
> On Ubuntu 14.04 desktop, set up folder in /home to share. 

Attempted to access from ChromeOS device using "network file share" app, informed share was password-protected which I remembered doing some time ago.

To make sure I remembered the samba password, I ran smbpasswd on desktop and changed the password to itself.

Accessed the share from the ChromeOS device, tried to watch a video file, player hung without showing anything.

Back to desktop, ran a superuser command, was informed my password was incorrect. After many attempts, eventually tried the SMB passwd on a hunch and it worked.

At this point I shut down the share and disconnected the ChromeOS device, and confirmed that my sudo password was now the SMB password I had set.

rebooted to see if it was permanent. Old sudo password was still incorrect, but the SMB password only caused the screen to blank and then the login screen to pop up again.

rebooted to recovery and root prompt and reset password.

Ideas? I am 100% sure that I did not run passwd, only smbpasswd, before this happened.


Samba is configured like that by default, here are the relevant lines in smb.conf:
```

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = user
```

...
> 
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
    unix password sync = yes


For myself... The first time you add a linux user (adduser) you need to add them to smbpasswd as well.

```
sudo smbpasswd -a <user>
```

when prompted for a password use the same password you used with adduser. After this the smb password should be updated automatically when you change the linux password with ```

sudo passwd <user>
```
EDIT: If needed more here: [https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html)
Hope this helps.

---

### Post by Morbius1 on 2017-04-30
If this is just a normal old ubuntu desktop system in a home lan I cannot reproduce your symptom - and I tried.

There is a package ( libpam-smbpass ) that will do the opposite of what you describe - forces the samba password to = the login password regardless of what you do with smbpasswd.

I suppose you could have done this yourself but I would think you'd remember doing it - it's certainly not the default behaviour using the default smb.conf: 

**You would need these is your smb.conf file - and they should be there by default:
```
unix password sync = yes
pam password change = yes
```
** But they will do nothing unless the following line is added to /etc/pam.d/samba:
```
@include common-password
```

Take a look at that file and see if it has that line in it.

---

### Post by AR_Kozz on 2017-04-30
nope, third line is absent from smb.conf.

comments state that this "sync" occurs when the SMB pass is changed, does that imply it alters the Unix pass to match? Why would that be default behavior? I don't want my system pass to match one I use over a network, that's crazy. But in any case if you're correct that wasn't the cause.

I suspect it's something tricky because the new pass didn't work when I rebooted. If it had simply changed, login shouldn't have reset itself.

---

