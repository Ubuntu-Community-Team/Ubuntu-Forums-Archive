---
title: "Restore packages list from another Ubuntu instalation"
date: 2013-12-04
forum: General Help
---

### Post by tdpham4 on 2013-12-04
Hello,

I am currently using Ubuntu 13.10 and I got a new laptop. I have installed Ubuntu 13.10 on the new desktop but it is missing all the softwares/packages that I have installed in the old laptop. I want to know if there is a way that I can get a list of all the packages from old laptop; then, using that list, I import it to the new laptop and install all the missing packages on the new laptop. Please let me know if it is possible and what command should I use.

Thank you for your help.

---

### Post by philinux on 2013-12-04
[http://kvz.io/blog/2007/08/03/restore-packages-using-dselectupgrade/](http://kvz.io/blog/2007/08/03/restore-packages-using-dselectupgrade/)

Just adapt that and copy the text file to new machine.

---

### Post by deadflowr on 2013-12-04
On the laptop, just use
```
dpkg --get-selections > package.txt
```
or whatever you want to name it.
Then the text file will be in the users home folder, instead of the tmp directory.
When you copy it over to the new machine, then use sudo to install.
dpkg -get
sudo dpkg -set

No need to run sudo more than you need.

---

### Post by philinux on 2013-12-04
> **deadflowr said:**
> On the laptop, just use
```
dpkg --get-selections > package.txt
```
or whatever you want to name it.
Then the text file will be in the users home folder, instead of the tmp directory.
When you copy it over to the new machine, then use sudo to install.
dpkg -get
sudo dpkg -set

No need to run sudo more than you need.

Yeah. Too much sudo in that link I gave. I is on smart phone so limited typing and signal.

---

### Post by tdpham4 on 2013-12-04
Cool, that is nice. Did not know that there is a quick command like that. Thank you guys a lot.

---

### Post by mörgæs on 2013-12-04
Good, please mark the thread 'solved'.

---

### Post by tdpham4 on 2013-12-04
Hmm, I just follow your guide and your direction. When I type:
dpkg --set-selections < packagelist.txt

I got this line of error for every package

dpkg: warning: package not in database at line ####: name of package

Did I miss any step? Do I have to copy the sources list also? It is highly unlikely because some of the packages are very common, such as firefox, XBMC, VLC ....
Please let me know. Thank you.

---

### Post by deadflowr on 2013-12-04
What was the output.

Run an apt-get update, to refresh the database.
Run it with sudo.

---

### Post by tdpham4 on 2013-12-04
Ok, so I transfer the package.txt file to the new laptop. Then I execute:
sudo dpkg --set-selections < package.txt

Here is the error:
dpkg: warning: package not in database at line 7: aes2501-wy
dpkg: warning: package not in database at line 8: akonadi-facebook
dpkg: warning: package not in database at line 16: android-tools-adb
dpkg: warning: package not in database at line 16: android-tools-fastboot

The error went the whole length of the text file up to line 1564. Yes, I did execute sudo apt-get update. I check the source list also. I miss some sources but the important one is still there. 

Please let me know if I did something wrong. Thank you.

---

### Post by deadflowr on 2013-12-05
See if this helps
[http://rayslinux.blogspot.com/2012/10/ubuntu-1210-dpkg-warning-package-not-in.html](http://rayslinux.blogspot.com/2012/10/ubuntu-1210-dpkg-warning-package-not-in.html)

---

### Post by tdpham4 on 2013-12-08
Hello,

I have successfully restored all my packages and settings. Using the help of this thread and other sources, here is a little guide of what I did:

1/ Install Backup in Ubuntu or type "sudo apt-get install deja-dup" in terminal.
2/ Use the program to backup everything in your Home folder
3/ Go to terminal, type in these commands:
sudo dpkg --get-selections > Package.list
sudo cp /etc/apt/sources.list sources.list
sudo apt-key exportall > Repo.keys4/ Go to "etc/apt/". Copy the folder "sources.list.d" to the new computer. Place it in "etc/apt/" in the new computer
5/ Transfer all the files to the new computer (the backup files of Home folder, and the 3 files created by the commands above)
6/ IMPORTANT: the new user account on the new computer must be the same name as the old computer
7/ Install Backup and restore everything to your Home folder.
7/ In the new computer, open terminal and type this in:

sudo apt-key add Repo.keys
sudo cp sources.list /etc/apt/sources.list 
sudo apt-get update
sudo apt-get install dselect
sudo dselect update
sudo dpkg --set-selections < Package.list && sudo apt-get -u dselect-upgrade

8/ It will take a while to download and install everything. After it is done, restart the computer.

The steps above restore 99% of everything to the new computer. A few programs require additional downloading and installation such as Dropbox, Steam, Wine....

I hope this little guide help other users who want to restore all packages and settings to a new computer.

---

