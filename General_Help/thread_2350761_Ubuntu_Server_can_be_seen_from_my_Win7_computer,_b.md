---
title: "Ubuntu Server can be seen from my Win7 computer, but cant access server files"
date: 2017-01-27
forum: General Help
---

### Post by rich2016 on 2017-01-27
New to Linux in general (little experience years ago), built an Ubuntu Server (16.04 LTS).  updates, upgrades, etc., all done.   Loaded Samba.  Used the following:   [https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/](https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/)  to set up as a file server (kinda).    I can see the server on my Windows network...(as in the 1st windows pic in the above link) and the share folder (which is named Guest001).  But when I double click on the folder from my windows computer, I get an error box pop up that says:   "WINDOWS CANNOT ACCESS  \ \ UBUNTUSERVERRC1 \ Guest001   (I added spaces between the slashes here to remove the link)  I placed a test.txt file in Guest001 just to have something to look for.

I have been reading many sources and I have found information from simple (like what I used) to very very in depth with ALOT more information used than what I did.   I am thinking that I may need to also set up folders or permissions within Samba itself, but this is where I get lost.  I have watched a few uTube videos also, and it seems everyone is doing this in different ways....  is there a simple way to do this?

I would also like to be able to remote in from my win10 laptop when not at home.

Thanks in advance for any help.

---

### Post by TheFu on 2017-01-27
a) Don't use samba over the internet.
b) for internet access to files, the easiest, secure, way is sftp.  Install openssh-server and fail2ban.  That is it on the server-side. Any sftp client can be used - filezilla and winscp are popular for Windows.  Any Linux file manager has this support built in. Just use sftp:// in the URL for Linux systems.
c) for remote access to your linux machine, use ssh. Putty is the normal Windows program for the client.  On Unix systems, use a shell with ssh.

The only trick I know for samba to work is that the **smbpasswd** has to be initialized before it will work.

The best knowledge I can recommend to new people is the "Ubuntu Server Guide" and the "Ubuntu Desktop Guide" - look there for stuff like this.

---

