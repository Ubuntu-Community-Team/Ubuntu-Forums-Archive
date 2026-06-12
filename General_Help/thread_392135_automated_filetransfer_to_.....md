---
title: "automated filetransfer to ...."
date: 2007-03-24
forum: General Help
---

### Post by Kari_Juhani on 2007-03-24
here is my problem :

i need to copy/update my ftp-inbox to a network-drive..  cant get it work with rsync, unison or automated expect-script.

i can make this work inside my linux machine, but how to make it work to network-drive... for example, basic thing is just to .. cp /home/ftp/*.wav /home/Desktop/myusername/tesfolder  and they go there, of course ... but i cant copy them to that network-drive with this syntax. 

if i try, in terminal :

cp /home/ftp //network.address.fi/transfers/my_ftp_store

reply is =  cp: target ..........  is not a directory

and when i add / after my_ftp_store

reply is = cp: target ........... is not a directory: no such file or directory

:confused: 

setup is like this :

Ubuntu Linux has a /home/ftp - folder where i upload files from outside ..
files are 1.wav, 2.wav ...  and so on. Proftpd - server is running "standalone" and /home/ftp - folder is chmodded so that i can write/read. 

these files i would like to copy/update to smb://network.address.fi/transfers/my_ftp_store

i can copy files manually just by opening this remote folder ( in my desktop ) and dropping them there...  but i cant make it automated. 

Network driver has username and passwd, and when i reboot i need to type them again to access this drive. ( they are in keyring of nautilus, so it opens .. )

what i'm missing ??? ( one more linux-machine, instead that win-machine where to upload these files ...  :) ? )

thank you for your help .. in advance.

Kari

---

### Post by jakev383 on 2007-03-24
You'll need to install the smbclient tools so that you can mount the network drive as a folder on your FTP machine:
sudo smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
(taken from: [http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)  which has much more info on mounting SMB shares)
Then you will be able to cp the files from your FTP dir to the network drive.

---

### Post by Kari_Juhani on 2007-03-24
thanks .. ill try that too ...  lets see if can make it work.

Kari

---

