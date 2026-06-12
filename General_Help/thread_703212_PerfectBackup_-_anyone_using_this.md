---
title: "PerfectBackup - anyone using this?"
date: 2008-02-21
forum: General Help
---

### Post by SumnerBoy on 2008-02-21
I have signed up for the free 1GB account with PerfectBackup.co.uk. I have downloaded the tar ball and have installed it successfully. 

I then run Configurator.sh and it asks for my user name and password, and then the backup server URL. I can't find any instructions as to what the server URL is. Am I missing something here?

I really want to setup some online backup of my personal docs/files and these free services are ideal...if they work!

I have also tried SpiderOak but this only comes as a deb and I am unsure how to ensure the necessary dependencies are installed (I am new to Linux).

Any one else know of any other online backup services with a free 1GB service?

---

### Post by GuDoN on 2008-02-21
well why not install the deb?  if you're unsure of how to install it:

# sudo dpkg install <deb file>

Otherwise, there aren't any bad things to say about PerfectBackup, I checked some reviews for you, there are no bad comments! :)

10/10
[A Link For You To The Review]("http://www.reviewcentre.com/review268513.html")

---

### Post by SumnerBoy on 2008-02-21
Thanks - I had already read that review - hence the reason I was keen to try this. I ended up contacting their support team and they were EXTREMELY helpful and prompt. Managed to get me up and running in about half an hour with the correct backup server URL (which I couldn't find anywhere) and a few other bits and pieces. 

Can't speak highly enough of them - highly recommend!!

---

### Post by mozza3107 on 2008-02-21
I love [online backup ]("http://www.perfectbackup.co.uk")services from PerfectBackup, been using them for over a year, never let me down once, their support would always get you up and running quickly.

Just for the record, here is what you do.

Download the software from [www.perfectbackup.co.uk/login]("http://www.perfectbackup.co.uk/login")

Staging
1. Place the install tar.gz on the linux machine

Extract Install Files 
1. #mkdir /usr/local/obm
2. #cd /usr/local/obmgunzip obm-nix.tar.gz
3. #tar -xf obm-nix.tar

Install
1. #./bin/install.sh >install.log
2. Look for any install issues #cat install.log
3. Ensure obm is now running. Should be output from: # ps -ef grep obm

Start Configurator to Associate Backup Account with Linux Machine 
1. #sh /usr/local/obm/bin/Configurator.sh

NOTE: If you receive any java heap errors, the application is trying to use more physical memory than you have available.

HEAP Workaround: #cd /usr/local/obm/bin Use vi or whatever you like to replace Xmx512m or Xmx256m in both Configurator.sh and RunBackupSet.sh (only one entry in each). We've used Xmx32m in both files and it works fine.

2)
Login Name: username (account name that you created in the console)
Password: ******************* (password of account name)
Backup Server URL: backupserver.perfect.co.uk
Which Protocol ? (1) Http (2) Https : 2 Use proxy ? (Y)es or (N)o : N NOTE: if you enter N, the following will not show
Proxy Type ? (1) Http/Https Proxy (2) SOCKS : 1
Enter proxy server : aaa.bbb.comEnter proxy port : xxx
Enter proxy username (optional) : administrator
Enter proxy password (optional) : *******************

Encryption and Running on Computer 

Found new backup set 'xxx' where xxx is the name of your backup set
Please enter the following values for this backup set:

Encrypting Algorithm ?(1) Twofish (2) AES (3) Triple DES (4) No encryption : 2 (personal preference)
Encrypting Key: *******************
Re-Enter Encrypting Key: ******************* NOTE: Never forget this password! Encrypting Mode ? (1) ECB (2) CBC : 1 (personal preference)
Run scheduled backup on this computer ? (Y)es or (N)o : Y NOTE: If you select N, the backup set will not run on a schedule on this computer.

Optional Running Backup Set

You don't have to run this now; however, it'll get your data protected now, and it'll prove all above worked.

# sh /usr/local/obm/bin/RunBackupSet.sh [BACKUP_SET]
where [BACKUP_SET] is the name of backup set to be run. IE, if you created BackupSet-0:

#sh /usr/local/obm/bin/RunBackupSet.sh BackupSet-0

Stopping and Starting Processes

If you need to manually stop / start process, create an executable file name.

Stop

#cat stop.sh
sh "/etc/init.d/obmscheduler" stop
sh "/etc/init.d/obmaua" stop

Start
#cat start.sh
sh "/etc/init.d/obmscheduler" start &
sh "/etc/init.d/obmaua" start &

------------------------------------------

If you don't want to use resources with leaving the scheduler running, use native cron in linux:

#crontab -e
0 0 * * * /usr/local/obm/bin/RunBackupSet.sh BackupSet-0

where first five entries are
minute
hour
day
month
week of year

and BackupSet-0 is the name of your backup set.

---

### Post by SumnerBoy on 2008-02-21
Thanks for that - I have successfully got it all up and running now - thanks to some prompt assistance from the support staff. Very impressed so far.

And thanks for your tip re-shutting down the scheduler and using cron. Have done this and think I prefer it running this way.

---

