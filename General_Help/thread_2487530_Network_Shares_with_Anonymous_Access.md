---
title: "Network Shares with Anonymous Access"
date: 2023-06-07
forum: General Help
---

### Post by paulkem on 2023-06-07
Please excuse my ignorance here. I have a file and media (Plex) server  running on Ubuntu 20 that I set up a couple of years ago. I chose to  use Ubuntu so I could use NTFS volumes in case I needed to pull the  drive and put into a Windows machine.  I think I started with desktop  rather than server but am not certain. I use Webmin/desktop GUI to do most of the  configuration so I don't have to mess with command line. I am able to  add disks, create new shares, etc. and can access them via my Windows  machines. I remember I had issues with getting access to the shares but I  cannot for the life of me remember how I fixed it. 

I  am trying to create a file server for a friend using version 22 that  will be very similar in functionality. But once again, no matter what I  do in WebMin, I cannot get access to the share from Windows (I also  cannot access the share from within Ubuntu). What am I missing? I just  want anonymous access to the shares. 


Thanks.

---

### Post by MAFoElffen on 2023-06-08
More information needed...

I have a Plex Server which I have on my Workstation, which is also dual-boot between Windows 10 and Ubuntu 22.04 LTS (previously 20.04)... I have Plex Server installed both in Windows, and in Ubuntu. My Media Files are stored on one drive that is formatted as NTFS. I also have it shared on my local LAN as NTFS and SMB shares...

As how I set that up, I set it up in Windows first... Then in Ubuntu, I mount the drive partition into the filesystem in the fstab. 

After the initial mount, then I used chown to own the filesystem recursively in Linux by my username. The set ACL lists on the folders...

In Plex Server, then no matter what platform I am on, I just go into Settings > Libraries ... Then point it to where they are located in that filesystem. Even though I share media files shared within my local LAN, I don't forward ports, nor do I allow Plex to go outside of private local LAN. 

My confusion (that would be cleared up by more info...) comes from... You didn't mention where the media files are located physically and logically.

You said anonymously... I am assuming by anyone to access. For that, I set chown to 'nobody:nogroup'...

---

### Post by paulkem on 2023-06-08
Thank you for this detailed description of your setup. It sounds nearly identical to mine (except I am still on 20 and have 3 media drives), so that is super helpful. 

Now, when you say you "set it up in Windows first... Then in Ubuntu" do you mean partition and format the disk?  Or do you mean something with the shares? On my server, I have prepared the disk in Windows a couple of times, and also added bare metal drives with no problems after I remember the steps I need to follow to do it. In fact, I just added a new bare metal drive to it last week. 

On both my fully functional version 20 server, and this new version 22 server, the files are stored locally on that machine on mounted hard drives. Nothing fancy in either.  

And yes, when I say anonymous, I mean anyone can access, no credentials required. So I wonder if that chown command is what I need and why when I set settings in WebMin it is not taking care of that for me?

---

### Post by MAFoElffen on 2023-06-08
I setup Plex in Windows with Separate partitions where the media is stored as being formated as NTFS. NTFS can be read by both Windows and Linux.

Here is the line in my /etc/fstab file, where it is mounted into the filesystem:
```

UUID=828C01738C016351             /Media_H                ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0

```
chowned by me:
```

drwxrwxr-x  1 mafoelffen mafoelffen 4096 Sep 25  2022  Media
drwxrwxr-x  1 mafoelffen mafoelffen    0 Sep 25  2022 'System Volume Information'
drwxrwxr-x  1 mafoelffen mafoelffen    0 Sep 25  2022 '$RECYCLE.BIN'
drwxrwxr-x  1 mafoelffen mafoelffen 4096 May 11 14:32  .
drwxr-xr-x 20 root       root       4096 Jun  7 22:34  ..

```
And set chmod permissions and set ACL's for access, beyond that:
```

mafoelffen@opti-ubuntu:~$ getfacl --absolute-names /Media_H/*
# file: /Media_H/$RECYCLE.BIN
# owner: mafoelffen
# group: mafoelffen
user::rwx
group::rwx
other::r-x

# file: /Media_H/Media
# owner: mafoelffen
# group: mafoelffen
user::rwx
group::rwx
other::r-x

# file: /Media_H/System Volume Information
# owner: mafoelffen
# group: mafoelffen
user::rwx
group::rwx
other::r-x

```
I don't use webmin. I use ssh (command line).

---

### Post by paulkem on 2023-06-08
What command can i run that will output my configuration so we can maybe see what is not right?

---

### Post by MAFoElffen on 2023-06-08
What is your goal, and what are you not able to do?

---

### Post by paulkem on 2023-06-08
I cannot access the share I created in the 22 installation, either from Windows or within the same Ubuntu environment. I want to be able to access the shares from any device or user on my network.

---

### Post by MAFoElffen on 2023-06-08
Run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") on it... But use the '--details" option so that it shows any details about the installed filesystems, ad storage controllers.
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
After the script uploads to a patsebin, please post the URL, so we can find it to look at it.

Do you have the partition, where you have the media files stored mounted to the Linux filesystem? Show me how you have that or what you used for that...

---

### Post by paulkem on 2023-06-08
I seem to be missing the utilities curl, pastebinit,  is.  As far as media files, I actually just have a folder created on a 500gb drive for testing called "share_test".  The drive was mounted using the "Disks" utility.

[COLOR=unset]https://imgur.com/z8Gicdp[https://imgur.com/z8Gicdp](https://imgur.com/z8Gicdp)[/COLOR][https://imgur.com/z8Gicdp](https://imgur.com/z8Gicdp)
[COLOR=unset]https://imgur.com/z8Gicdp[/COLOR]

---

### Post by paulkem on 2023-06-08
OK, i got it to run, but I don't know where to look for the pastebin link.

---

### Post by Morbius1 on 2023-06-09
When you have nothing else to do why not post the output of the following commands so we can see how your samba server is set up:

```
testparm -s
```
```
net usershare info --long
```

---

### Post by paulkem on 2023-06-09
```
ofs_admin@ofs:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

```
fs_admin@ofs:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/test_share is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/share_test is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```

---

### Post by Morbius1 on 2023-06-09
You have no shares defined so there is nothing for the Windows machine to access.

Try something simple first:

[1] Create a folder to share:
```
sudo mkdir /media/Test
```
[2] Change ownership to fs_admin:
```
sudo chown fs_admin /media/Test
```
[3] Create a share definition directly in /etc/samba/smb.conf:
```
[Test]
path = /media/Test
read only = No
guest ok = Yes
force user = fs_admin
```
[4] Then restart samba:
```
sudo service smbd restart
```

I wasn't smart enough to ask you what version of Windows you are using so assuming it's >= Win10 access the share this way on Explorer:
```
\\ofs.local\Test
```
Or by ip address.

Also, if you install the wsdd package Win10/11 will be able to "discover" your samba server automatically in Explorer:
```
sudo apt install wsdd
```

The Linux client will have issues connecting to just about anything because of a number of bugs but you can use **Connect to Server** in Nautilus for example to connect to the server and it's share:
```
smb://ofs.local/Test
```

---

### Post by paulkem on 2023-06-09
Oh crap, yeah, I should have mentioned that I had remove all of my attempts to create the share (there were several attempts, all via Webmin). Sorry for the confusion.  I will give your steps a try in a bit. Yes, this would be accessed from Win 10 in my testing at least. I am pretty sure my friend is still running 10, so I guess we will have to wait and see how 11 works when the time comes.

---

### Post by TheFu on 2023-06-13
It isn't clear to me, but you want the shared media via Samba only available to systems on the same LAN, never over the internet, correct?

For access over the internet, use ssh tunnels, sftp, a VPN or Plex (if you must).

---

