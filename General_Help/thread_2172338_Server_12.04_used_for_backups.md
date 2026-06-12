---
title: "Server 12.04 used for backups"
date: 2013-09-04
forum: General Help
---

### Post by Gannas on 2013-09-04
Hi all. Well after an absence from working on learning about Ubuntu, I'm finally back. I'm working on having my server be available on my home network to be used as a file server for those everyday thing like photo's, music, video's, etc. But I first wanted to set it up for backing up my computers. I have a desktop running Windows 7 (64 bit ) and two laptops. One using Vista and the other running Win 7 Home Premium, each are 32 bit systems. Now I found a previous question along these lines for setting up Samba to do this. But in this case two of the computers will be for one user ( the desktop and the vista laptop ) and the other laptop for a different user. Now here is the post I found from about a year ago.....


  [TABLE]
[TR]
[TD="class: votecell"]     4     down vote          [favorite]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer#")          [/TD]
[TD="class: postcell"]                I took my old computer (AMD 5600+, 2GB RAM, 880gt, 250GB  SATA, etc) and decided to jump and try Ubuntu for the first time.  I  have *very very*  little knowledge (Red Hat when I was younger) with Linux in general.
  My main desktop is Windows 7 and my plan is to use the Ubuntu  computer as a file server sort of speak.  I want to be able to setup  back up schedules from my Windows PC to the Ubuntu PC (plan on leaving  this on 24/7 to double as a Seedbox)
  How do I go on to doing this?
      
              [server]("http://askubuntu.com/questions/tagged/server") [file-sharing]("http://askubuntu.com/questions/tagged/file-sharing")      
     [TABLE="class: fw"]
[TR]
[TD="class: vt"]            [share]("http://askubuntu.com/q/185369")[improve this question]("http://askubuntu.com/posts/185369/edit")[/TD]
[TD="class: post-signature, align: right"]                                           [edited Sep 9 '12 at 2:38]("http://askubuntu.com/posts/185369/revisions")          
                      [URL="http://askubuntu.com/users/74307/peachy"][IMG]https://www.gravatar.com/avatar/ad4e4bb767d4678eccef790dc993e168?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [Peachy]("http://askubuntu.com/users/74307/peachy")
            2,80441830         
     [/TD]
[TD="class: post-signature owner"]                                                           asked Sep 8 '12 at 6:49         
                      [URL="http://askubuntu.com/users/88263/derek"][IMG]https://www.gravatar.com/avatar/8d3bb883f3feda1e6a60ed16bf34e50c?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [derek]("http://askubuntu.com/users/88263/derek")
            212         
     [/TD]
[/TR]
[/TABLE]
 [/TD]
[/TR]
[TR]
[TD="class: votecell"][/TD]
[TD]              [TABLE]
[TR="class: comment"]
[TD][/TD]
[TD="class: comment-text"]which version of ubuntu? – [VendettaDroid]("http://askubuntu.com/users/87576/vendettadroid") [Sep 8 '12 at 6:56]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer#comment230917_185369")[/TD]
[/TR]
[TR="class: comment"]
[TD][/TD]
[TD="class: comment-text"]the latest desktop version – [derek]("http://askubuntu.com/users/88263/derek") [Sep 9 '12 at 20:37]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer#comment231687_185369")[/TD]
[/TR]
[TR="class: comment"]
[TD][/TD]
[TD="class: comment-text"]There is a 300 pages book dedicated for this. "Beginning Ubuntu server administration" – [Suhaib]("http://askubuntu.com/users/24621/suhaib") [Sep 15 '12 at 1:23]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer#comment234271_185369")[/TD]
[/TR]
[/TABLE]
     [/TD]
[/TR]
[/TABLE]
                                                                                                     **2 Answers**

                                                               [             active         ]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer?answertab=active#tab-top")         [             oldest         ]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer?answertab=oldest#tab-top")         [             votes         ]("http://askubuntu.com/questions/185369/how-to-setup-ubuntu-as-a-backup-server-for-my-windows-computer?answertab=votes#tab-top") 
                          
                     
                 
              [TABLE]
[TR]
[TD="class: votecell"]                             up vote     2     down vote        [/TD]
[TD="class: answercell"]     You want to install and configure Samba. I  will assume you are using Ubuntu Server 12.04. If you have a desktop  installed there may be all kinds of GUI configuration tools you can use  but let's keep this simple.
  This should install Samba if you don't already have it:
  sudo apt-get install samba
  Now you should have the file /etc/samba/smb.conf so edit this and add these lines to the end:
  [backup]
path = /home/username/backup
browsable =yes
writable = yes
guest ok = yes
read only = no
  Now read the new configuration by running this command:
  sudo service smbd reload
  Finally, make sure /home/username/backup exists and is readable and writeable by everyone:
  mkdir /home/username/backup
chmod a+rwx /home/username/backup
  You should now have a working share. If the IP address of your server is 192.168.0.2 you could visit \\192.168.0.2\backup from Explorer and see the directory and read and write files.
  Note that there is no security here. Anyone on your LAN can access your files. But this should get you started.
 [/TD]
[/TR]
[/TABLE]


My concern is the fact their would be no security. I've already set up one user with the permissions of 0755 and I would like to use the ufw too. Also should I be worried since there would be two users with a total of three computers.

---

### Post by rai_shu2 on 2013-09-04
If you don't trust the others on your LAN, then you are right to be worried. If that's the case, then I would suggest looking into using encryption for security (or perhaps something stronger than that). The number of users is not really relevant.

The thing that should worry you is whether you can trust the other people on your network, which is why you need security for the WAN (you cannot reasonably trust everyone connected to the internet). UFW will only help if you have a plan to simplify security. For example, UFW can be configured to disallow incoming connections that aren't from the LAN and thus restrict access to anyone on the LAN. That does assume that everyone on the LAN is trustworthy, however.

---

### Post by TheFu on 2013-09-04
Don't let guests write to samba shares ... ever.  User logins are needed.  I don't remember the exact setting, but Allowed Users  = %s seems like it. Sorry I don't remember exactly.  Initialize the user passwords with the smbpasswd command.

Either you backup the system or you backup the user directories. Your security will be based on which you choose. If you choose both, then you'll have different backup methods for OS and user data. That can be smart, since backing up system might be wanted weekly and user data nightly.

The software you choose for backups will lead you to the solution for remote disk access. Samba can be used, if you like, but it really isn't very secure. The network traffic is not encrypted.  If you choose a Windows-based backup tool, then samba is probably the only real solution. On a LAN, the lack of encrypted transport doesn't usually matter. I don't worry about it myself.

Check out Duplicity and Duplicati for Windows backups that are encrypted before sending them to remote storage - remote can be LAN or WAN.

For user data backups, I'd drop them under the $HOME for each user on the Ubuntu box. Samba will let you mount a specific HOME based on the login. By setting the backup directory for each user to 700 permissions, only the logged in user can see those file areas ... besides root.

---

