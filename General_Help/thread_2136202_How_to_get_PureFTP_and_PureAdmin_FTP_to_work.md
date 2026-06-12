---
title: "How to get PureFTP and PureAdmin FTP to work?"
date: 2013-04-16
forum: General Help
---

### Post by n0c0d3 on 2013-04-16
I'm trying to set up an FTP server with PureFTP and PureAdmin, but I just don't get it to work. I've been searching all over the web for a solution, this helped to some extend, but I'm not there yet. I'm on Xubuntu 12.10-64.

I want someone to be able to log int onto a fake root on an external hard drive and upload/download, create and delete files and folders. Actually, everything I could do myslef, except for navigating below the fake-root,  see the real path of the folder he's in and of course is not able to delete the root folder he's in or change it's permissions. I've set up both the Home Directory and the fake root settings in PureAdmin to "/media/n0c03/ExtDrive/public" directory. The user has a User ID "ftpuser (114)" and Group ID of "ftpgroup (124) assigned to it. The username, password and Real Name are set as well.

At first I had the problem that the password was not correct and it gave a 530 error, which could be solved by changing the entry in the /etc/pure-ftpd/conf/MinUID file from 1000 to 100. This enabled a login, but the user still can't see anything of the contents of the folder, upload anything to it or anything else.

When I want to upload a file (file098abc.txt) I get all kinds of permission denied errors:

```

Status:    Connected
Status:    Starting upload of /home/n0c0d3/Desktop/NewFolder/file098abc.txt
Command:    CWD /
Response:    550 Can't change directory to /: Permission denied
Command:    MKD /
Response:    550 Can't create directory: File exists
Command:    CWD /
Response:    550 Can't change directory to /: Permission denied
Command:    SIZE /file098abc.txt
Response:    550 Can't check for file existence
Command:    TYPE A
Response:    200 TYPE is now ASCII
Command:    PASV
Response:    227 Entering Passive Mode (xx,xxx,xxx,xx,60,235)
Command:    STOR /file098abc.txt
Response:    553 Can't open that file: Permission denied

```

This is what I've tried more:

In the /media/n0c03/ExtDrive/public directory, in the terminal I entered : 
```
ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure
```
What it's good for I have no idea, but it seems to crteate some necessary symlink or whatever.

I also changed the value in /etc/pure-ftpd/conf/PAMAuthentication from 'yes' to 'no' and did the same in /etc/pure-ftpd/conf/UnixAuthentication. One of them had already a 'no' in it btw.

All this to now avail and I keep getting the same errors as I got before.

Then I found something on the web that was supposed to resolve this issue. I had to change the permissions for the directory this way:
```
sudo usermod -u 1021 -p -U ftpuser
```
and
```
sudo groupmod -g 1022 ftpgroup
```

and I did it from the 'public' directory on the external drive.

But when I tried this I couldn't enter the User Manager in PureAdmin anymore. I got an screen which told me the user and group permissions had to be set to 124 and 124 and it asked me if I wanted to let PureAdmin do that for me. As I didn't know what else to do I thoght that might be not such a bad idea and accepted the offer, but than the screen doesn't go away. I click cancel and when I want to enter the User Manager again I get the same error as before and nothing seems to have changed. So I've manually changed the permissions back again to 114 and 124 with the usermod- and usergroup-command I mentioned above (replacing the 1021 and 1022 to 114 and 124)

Every time I make changes I restart the server and PureAdmnin.

So now this is where I'm stuck. The user still can't see or create/upload anything.

I've been using FileZilla from my own computer, which is the same computer as on which the server is installed, to get into the server so far, so no real outside connections have been made yet. I do not have a network or router and the firewall has been switched off. I've only tested the server with a remote ftp-server test website that seems to be able to enter into the account with the credentials I enter there and shows no errors. But the interface of that site doesn't offer any possibilities to up- or download any files, it just tests the login.

I hope someone can help me out with this.

---

### Post by jim_deadlock on 2013-04-16
EDIT: oops sorry you already did that

---

### Post by n0c0d3 on 2013-04-16
> **jim_deadlock said:**
> EDIT: oops sorry you already did that

Thanks for your empathy anyway Jim ;-)

---

