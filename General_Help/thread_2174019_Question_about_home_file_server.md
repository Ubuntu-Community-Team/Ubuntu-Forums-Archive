---
title: "Question about home file server"
date: 2013-09-12
forum: General Help
---

### Post by theonlywalks on 2013-09-12
Hi everyone,

What I want is to have a home fileserver that is encrypted and also that I can connect to with SFTP. I am under the impression that this would give pretty good security on all ends.

What I did was create a user and have ubuntu encrypt my home folder. Then I put all my files in this home folder that I want to access from outside my house, so it is encrypted in case someone stole the harddrive.

Then I login, and then lock screen, and so when I leave the house I can access my files securely from anywhere, my harddrive is encrypted, and no one can touch the computer because the screen is locked.

The problem is that the other day there was a power failure, and so once the power came back on my computer rebooted and stayed at the ubuntu login screen. However I was not able to access my files all day, so I guess the file server only works if you login.

I dont want it to auto login in though because then that defeats the purpose of my security. I looked into autologin and then having the screensaver/lockscreen start right away, but that does not seem that secure to me because it may be possible for someone to interrupt the sequence before the lockscreen command is given. which would compromise my security.

Can anyone suggest me a generally better way to accomplish what I am doing, or point me in the right direction? Or if there is a way to start the fileserver automatically in the background at the login screen?

Thanks.

Shawn

---

### Post by lukeiamyourfather on 2013-09-12
What SFTP server are you using?

---

### Post by theonlywalks on 2013-09-12
Sorry I guess thats an important piece of information I left out, I am using vsftpd.

---

### Post by lukeiamyourfather on 2013-09-16
By default the FTP server should run when the system is booted regardless of whether a user is logged in or not. So unless you went out of your way to disable the service it's running if the machine is on. My guess is the files are inaccessible on disk because they are encrypted and the owner isn't logged in (otherwise what would be the point of encryption?).

---

### Post by theonlywalks on 2013-09-16
I discovered that the "background service" has to be set to "YES" in the vsftpd configuration file (I had to add the line manually). I set it to YES and now the FTP server is running in the background without logging in.

Even though the disk is encrypted I am able to access my files from a remote machine without the user being logged in. From your last post, I agree this is kind of weird.

Somehow my home folder is being decrypted in the background, or perhaps it is only decrypted because I am logging in as that user from my remote machine?

When I am logged in from my remote machine my server must be decrypting the home folder (or else how would I access, download, and upload files...). I wonder if the decrypted home folder would be visible to someone scanning my harddrive/memory locally?

---

