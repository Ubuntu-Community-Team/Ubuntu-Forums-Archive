---
title: "Backup want fully complete"
date: 2019-10-29
forum: General Help
---

### Post by telcar on 2019-10-29
Hello my core system is ubuntu and i already had an account here, So i  figured this is were i would start. I just recently started playing with  linux desktop again ive used it on my servers. One of the first things i  worry about after setting up a system is being able to back up and  restore with out much effort. So just in case im not doing a bunch of  work for nothing. I was going to use timeshift but it didnt support saving to a network location, So i went with deje dup. Everything was going fine till it finished the backup. It seas "Backup Finished - Couldnt not back up the following files. Please make sure you are able to open them, and it gives a whole list of files. Ive google this is issued and everything i come up with this happening is always one or two files that isnt relevant. Theres no way this whole list of files is irrelevant, but im assuming they belong to root is why im having this problem but how do i run the program directly as root instead of sudo or what should i do. 

```

/boot/System.map-4.15.0-36-generic
/boot/System.map-4.15.0-66-generic
/boot/lost+found
/boot/vmlinuz-4.15.0-66-generic
/etc/.pwd.lock
/etc/NetworkManager/system-connections/DG-Customer
/etc/NetworkManager/system-connections/stratosphere-001
/etc/NetworkManager/system-connections/stratosphere-001 1
/etc/apparmor.d/cache/lightdm-guest-session
/etc/apparmor.d/cache/sbin.dhclient
/etc/apparmor.d/cache/usr.bin.evince
/etc/apparmor.d/cache/usr.bin.freshclam
/etc/apparmor.d/cache/usr.bin.man
/etc/apparmor.d/cache/usr.lib.snapd.snap-confine.real
/etc/apparmor.d/cache/usr.sbin.cups-browsed
/etc/apparmor.d/cache/usr.sbin.cupsd
/etc/apparmor.d/cache/usr.sbin.tcpdump
/etc/brlapi.key
/etc/cups/ssl
/etc/cups/subscriptions.conf
/etc/cups/subscriptions.conf.O
/etc/gshadow
/etc/gshadow-
/etc/lvm/archive
/etc/lvm/backup
/etc/polkit-1/localauthority
/etc/ppp/chap-secrets
/etc/ppp/pap-secrets
/etc/security/opasswd
/etc/shadow
/etc/shadow-
/etc/ssl/private
/etc/sudoers
/etc/sudoers.d/README
/etc/sudoers.d/pwfeedback
/etc/ufw/after.init
/etc/ufw/after.rules
/etc/ufw/after6.rules
/etc/ufw/before.init
/etc/ufw/before.rules
/etc/ufw/before6.rules
/etc/ufw/user.rules
/etc/ufw/user6.rules
/lost+found
/root
/usr/lib/cups/backend/cups-brf
/usr/local/cyberghost/openvpn
/var/backups/group.bak
/var/backups/gshadow.bak
/var/backups/passwd.bak
/var/backups/shadow.bak
/var/cache/apt/archives/lock
/var/cache/apt/archives/partial
/var/cache/cups
/var/cache/debconf/passwords.dat
/var/cache/ldconfig
/var/cache/lightdm/dmrc
/var/lib/NetworkManager/secret_key
/var/lib/apt/lists/lock
/var/lib/apt/lists/partial
/var/lib/bluetooth/74:DE:2B:9B:18:0E
/var/lib/clamav/mirrors.dat
/var/lib/colord/.cache
/var/lib/dpkg/lock
/var/lib/dpkg/lock-frontend
/var/lib/dpkg/triggers/Lock
/var/lib/geoclue/.cache
/var/lib/lightdm
/var/lib/lightdm-data/lightdm
/var/lib/mlocate/mlocate.db
/var/lib/polkit-1
/var/lib/private
/var/lib/snapd/cookie
/var/lib/snapd/state.json
/var/lib/snapd/void
/var/lib/systemd/random-seed
/var/lib/udisks2
/var/lib/ureadahead/boot.pack
/var/lib/ureadahead/pack
/var/log/boot.log
/var/log/btmp
/var/log/installer/casper.log
/var/log/installer/debug
/var/log/installer/partman
/var/log/installer/syslog
/var/log/installer/version
/var/log/lightdm/lightdm.log
/var/log/lightdm/lightdm.log.1.gz
/var/log/lightdm/lightdm.log.2.gz
/var/log/lightdm/lightdm.log.3.gz
/var/log/lightdm/lightdm.log.4.gz
/var/log/lightdm/seat0-greeter.log
/var/log/lightdm/seat0-greeter.log.1.gz
/var/log/lightdm/seat0-greeter.log.2.gz
/var/log/lightdm/seat0-greeter.log.3.gz
/var/log/lightdm/seat0-greeter.log.4.gz
/var/log/lightdm/x-0.log
/var/log/lightdm/x-0.log.1.gz
/var/log/lightdm/x-0.log.2.gz
/var/log/lightdm/x-0.log.3.gz
/var/log/lightdm/x-0.log.4.gz
/var/log/lightdm/x-1.log
/var/log/lightdm/x-1.log.1.gz
/var/log/speech-dispatcher
/var/log/tallylog
/var/spool/anacron/cron.daily
/var/spool/anacron/cron.monthly
/var/spool/anacron/cron.weekly
/var/spool/cron/crontabs
/var/spool/cups
/var/spool/rsyslog
 
```

---

### Post by Tadaen_Sylvermane on 2019-10-29
Deja dup needs a running system to restore to. So backing up all of root is pointless. It is for backing up home directories, nothing more.

Just backup user homes. Its usually quicker to reinstall than reloading a full system backupl anyway unless of course you do a bunch of customizing outside of your home directory.

---

### Post by telcar on 2019-10-29
> Deja dup needs a running system to restore to 

Yes exactly thats what i want since there doesn't seem to be any other way to do it with linux. Back up the system and if it messes up or what ever, you can reinstall like normal then run deje dup and restore and its suppose to restore it back they way you had it. Unless you or somebody knows a better way. With windows i can command backup to a .wim file and with a restart and one click can restore the entire system with a blink of an eye. I could carless about the home dir. Hell i can back that up in 5m with copy and paste

---

### Post by telcar on 2019-10-29
All my important files stay on my drive array on my server and is accessed by my os via a network share. nothing important is never kept on any os. Everything important is directly transferred to the server. The only thing i care about is the os. I want to be able to say have a perfect running system just they way i want it and reformat the drive and reinstall a backup and have everything just they way it was be four the formate.

---

### Post by TheFu on 2019-10-29
> **telcar said:**
> Yes exactly thats what i want since there doesn't seem to be any other way to do it with linux. Back up the system and if it messes up or what ever, you can reinstall like normal then run deje dup and restore and its suppose to restore it back they way you had it. Unless you or somebody knows a better way. With windows i can command backup to a .wim file and with a restart and one click can restore the entire system with a blink of an eye. I could carless about the home dir. Hell i can back that up in 5m with copy and paste

Unix isn't Windows.  They will never be.  Backups is one of the times where the subtle differences between the OSes really matters.  The different capabilities of the storage systems used on Unix really matter for the most seamless backups.

Comparing a proper backup with a copy/paste operation does backups a disservice, IMHO.  Unix Backups aren't just about the data.  The owner, group, permissions and ACLs have to be captured at that point in time as well.  If all you get is the data, you won't be able to successfully restore the system.  

There are hundreds of threads here about system backups.  Check those out, try some of those solutions, ask questions.

You can use the "Try Ubuntu" environment from a flash boot to restore a backup too, BTW.

---

### Post by telcar on 2019-10-29
i know windows is not unix but neither is ubuntu its its copy cat linux 2 totally different things. Just because it uses the same file structure and principals doesnt mean its the same. im talking aboiut linux not unix. II didnt just willy nilly run to some forum and run my mouth to ask stupid questions ive done the research. Everything linux back programs is either based off of Rsync or duplicate and they all work they same way, basically its just the gui thats different. The backend is all the same. and what is this that your talking about...

>  You can use the "Try Ubuntu" environment from a flash boot to restore a backup too, BTW. 				

---

### Post by telcar on 2019-10-29
here is a tutorial using deje dup to backup and restore your entire systems that i read the other day [https://dev.to/nathanabland/creating-a-usable-backup-setup-for-linux-elementaryos-5-5b75](https://dev.to/nathanabland/creating-a-usable-backup-setup-for-linux-elementaryos-5-5b75)

---

### Post by Skaperen on 2019-10-29
i suggest [COLOR=#0000cd][FONT=courier new]**rclone**[/FONT][/COLOR] for incremental backups.  it can backup to hosts you have SSH access to using a key pair.  i do not know if the remote user needs to literally be [COLOR=#800080]**root@remote-host**[/COLOR] or if a user with sudo access is sufficient ... if you need to backup the system like [COLOR=#0000cd][FONT=courier new]**/etc**[/FONT][/COLOR].

---

### Post by telcar on 2019-10-29
i dont want incremental backups and i dont need ssh since im setting right at the machine. i just want one backup that can identically restored. So yall are telling me that if you decided to reinstall your os you set there and tediously reinstall every signal program and redo every setting and every signal thing over and over again by hand because i call bull. it could take you a damn week just to get the system back to a usable working order.

---

### Post by rbmorse on 2019-10-29
If you're just looking to preserve the system state once you get it installed and configured to your liking, Clonezilla will do that.  

Also might take a look at fsarchiver.  It has some limitations, but may do what you are looking to have done.

---

### Post by telcar on 2019-10-29
yes clonezilla does work and i have used it but i hate it because its a lie. It seas it backs up everything but empty space but thats not true it backs up everything so if you have a 2tb drive you better have a 2.5tb drive to back up to.

---

### Post by rbmorse on 2019-10-29
Look at fsarchiver

---

### Post by telcar on 2019-10-29
Yes thank You "rbmorse" my page didnt update after your edit and i just got that fsarchiver looks interesting at first glance going to check it out and if looks like it works with other FS like NTFS and such.

edited fsarchiver sounds very similar to how i backup my windows systems

---

### Post by HermanAB on 2019-10-29
The things to bear in mind are:
a. Linux is saved on thousands of internet servers around the planet, it changes all the time and is very quick and easy to install, so there is not much point in backing up the 'old and tired' system files - better to install the latest version.
b. The most important files are the user data files - everything else you can get again from the internet.
c. There are special Linux file systems that enable the creation of 'snapshots' - ZFS for example.  To use ZFS, you need to re-install your system since Ubuntu doesn't offer it by default.

If you only backup user data, then you can roll your own 'time machine' very easily:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by kevdog on 2019-10-29
I'd agree with the backup philosophy of backing up only user data and maybe some config files if you've heavily modified them. I think apt can backup a list of all the installed modules which you could import to a new system to quickly reinstall all the packages.  

In terms of backup you need to determine if you want to do this on a block or file level.  Different solutions depending on scenario.  You also need to consider where you are putting the backups, how you are going to transport the backups, how many copies of backups do you need, do you need encryption of the backups and/or encrypted transport of the backups, do you want it automated etc.  A lot to consider.  Nothing is perfect.

---

### Post by telcar on 2019-10-29
im not as proficient with linux as i am windows and it takes me for ever to get a system just the way i want, i save commands and everything i can as i go but i dont want to have to start from scratch if something happens. i just want to be able to do a back every now and then so i can restore the system back the way i had with out heaving to do anything extra. my hard drive could faile on my windows systems and as long as i have an empty formatted drive in 30 minutes i can have an identical system of the failed one with nothing but a oem install usb from ms.

---

### Post by Skaperen on 2019-10-29
> **telcar said:**
> i dont want incremental backups and i dont need ssh since im setting right at the machine. i just want one backup that can identically restored. So yall are telling me that if you decided to reinstall your os you set there and tediously reinstall every signal program and redo every setting and every signal thing over and over again by hand because i call bull. it could take you a damn week just to get the system back to a usable working order.

so you just want a snapshot of the whole system after a complete fresh install so that if you need/want to come back to that, it's easy to do?  i use [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] for that.  when i installed my Xubuntu 18.04 LTS back in July, i made snapshots like that at each phase of installing and customizing.  i still have those 5 snapshots.  i used [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR].  i did it to my 3rd HD (which had a replica of my /home partition which has plenty of space for everything w/o [COLOR=#800080][FONT=courier new]**/home**[/FONT][/COLOR] a few times), but [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] can do it over a network via [COLOR=#0000cd][FONT=courier new]**ssh**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**sudo**[/FONT][/COLOR] (i did that back in 14.04) if you don't have spare USB 3.0 hard drives, at least (a worthwhile investment ... i have 3 2TB ones).

i built a script to run the package installs of my customization step.  a grand total of 317 new packages were added.  it runs one huge [COLOR=#0000cd][FONT=courier new]**apt-get**[/FONT][/COLOR] command and saves the output.

i need to do a cross-link of those 5 snapshots because there is a lot of duplication in there.

---

### Post by telcar on 2019-10-29
rsync was what i was going to originally use, useing the timshift gui but it didnt support saving vie network location and was just testing around and didnt have a usb anything that was empty handy

---

### Post by telcar on 2019-10-29
> **Skaperen said:**
> so you just want a snapshot of the whole system after a complete fresh install so that if you need/want to come back to that, it's easy to do?  i use [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] for that.  when i installed my Xubuntu 18.04 LTS back in July, i made snapshots like that at each phase of installing and customizing.  i still have those 5 snapshots.  i used [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR].  i did it to my 3rd HD (which had a replica of my /home partition which has plenty of space for everything w/o [COLOR=#800080][FONT=courier new]**/home**[/FONT][/COLOR] a few times), but [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] can do it over a network via [COLOR=#0000cd][FONT=courier new]**ssh**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**sudo**[/FONT][/COLOR] (i did that back in 14.04) if you don't have spare USB 3.0 hard drives, at least (a worthwhile investment ... i have 3 2TB ones).

i built a script to run the package installs of my customization step.  a grand total of 317 new packages were added.  it runs one huge [COLOR=#0000cd][FONT=courier new]**apt-get**[/FONT][/COLOR] command and saves the output.

i need to do a cross-link of those 5 snapshots because there is a lot of duplication in there.

yes basically

---

### Post by telcar on 2019-10-30
I do everything on windows, thats were my important stuff is and i worry about things like encryption. Right now linux desktop is just something im testing out. Ill play with rsync and duplicate apps some more and look at this fsarchiver for backing up at the file level i. Theres aslo the logical volume managers snapshots, that can be used to restor a system at the block level im looking at but like ive said im not that proficient with a terminal. S useing the lvm or the more advanced features of rsync may be extremely difficult to figure out.

---

### Post by Skaperen on 2019-10-30
[COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] certainly can save to a network location.  lots of people do it all the the time.  that's what the [COLOR=#0000cd][FONT=courier new]**r**[/FONT][/COLOR] means (remote).  same for [COLOR=#0000cd][FONT=courier new]**rclone**[/FONT][/COLOR].

on a fresh install, you won't have your list of host names or your [COLOR=#0000cd][FONT=courier new]**ssh**[/FONT][/COLOR] id keys, so you'll need to type in the IP address and reply to the password prompts (be sure the remote host is temporarily configured to allow password access and cannot be reached from the internet that way).

---

### Post by TheFu on 2019-10-30
> **telcar said:**
> i dont want incremental backups and i dont need ssh since im setting right at the machine. i just want one backup that can identically restored. So yall are telling me that if you decided to reinstall your os you set there and tediously reinstall every signal program and redo every setting and every signal thing over and over again by hand because i call bull. it could take you a damn week just to get the system back to a usable working order.

It takes me 30-45 minutes to restore or migrate a system to a new computer using my backup techniques.  I use versioned, "pulled", daily, automatic, backups over an ssh tunnel.  If you have any concerns about malware, "pulled" backups are absolutely critical. rdiff-backup is my tool of choice.  
Some pre-backup data is gathered and placed into a specific location so it is included in the backup data. I grab crontabs, manually installed packages, storage layouts, stuff like that. Very simple scripting.  With that data, even if it isn't needed at restore time, it is handy to have if anything bad happens.  People here have sometimes wiped their partition tables, somehow.  Having a copy of **parted -lm** included with every backup set means that data is always available.  Same for LVM data (pvs, vgs, lvs).  Really handy, if we need it.  Want the manually installed package list?
```
# apt-mark showmanual > ~root/backup/aptmark.showmanual
```
Trivial to save, terrible to need, but not have.  I keep this sensitive data in /root/ which isn't available to normal users.

I don't install each program individually.  Unix systems easily work with text file lists to be installed.
I don't worry about settings, because system settings are in /etc/ and personal settings are in HOME. These aren't manually point-n-click-reinstalled like people do on Windows. Just place the config files where they were (as in where they are expected) and each program *finds* what it needs.

30-45 minutes and my system is *my system* again.

Versioned backups are extremely important, especially if we are running servers.  In another thread here, someone seems to have a hacked wordpress system. If they have 90 days of versioned backups, then they can go back in the backup sets to see when the attacker got in, what they changed on that date and anything more they changed since.  Without versioned backups, they have to guess how their server was breached.  Versioned backups are handy when an admin breaks things too.

bit-for-bit backups are just too wasteful and too inefficient for use. People do use them, however. I suppose they are better than nothing.  I just find that method missing so much flexibility that is easily provided by other backup methods.  Restoring to completely different hardware with completely different storage sub-system can't be done without manually handling those changes, for example.

---

### Post by uRock on 2019-10-30
> **telcar said:**
> i dont want incremental backups and i dont need ssh since im setting right at the machine. i just want one backup that can identically restored. So yall are telling me that if you decided to reinstall your os you set there and tediously reinstall every signal program and redo every setting and every signal thing over and over again by hand because i call bull. it could take you a damn week just to get the system back to a usable working order.

I do that several times a year on my laptop. That said, I keep a note in Google Keep with one command to install all of my favorite programs. I keep copies of all of the important conf files, as well. After installing a new Xubuntu, it takes about ten minutes to run updates, reboot, then install all of the applications and drop the conf files where they belong.

I use my file manager to drag and drop important files onto an external drive for backups.

---

### Post by HermanAB on 2019-10-30
"it could take you a damn week just to get the system back to a usable working order" - Only if you are doing it wrong.  Google for 'Debian preseed' and see this: [https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html](https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html)

It is also trivial to make a list of all the installed packages with apt in order to re-install them with one command, if you don't want to learn about preseed.

In addition to to my data files, I also keep a tar ball of /etc, in case I need to look up something special from the old install, but I haven't needed to do that in years.

---

### Post by uRock on 2019-10-31
> **HermanAB said:**
> "it could take you a damn week just to get the system back to a usable working order" - Only if you are doing it wrong.  Google for 'Debian preseed' and see this: [https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html](https://www.aeronetworks.ca/2016/03/debian-installation-for-control-freaks.html)

It is also trivial to make a list of all the installed packages with apt in order to re-install them with one command, if you don't want to learn about preseed.

In addition to to my data files, I also keep a tar ball of /etc, in case I need to look up something special from the old install, but I haven't needed to do that in years.

That looks like good stuff, but my only system, aside from my desktop, that is running as a server doesn't have the drive space, nor the WiFi throughput, to handle that. It's a Netbook running Debian 10 as a Motion server. I will keep this in mind for when I get something better to run as a server.

---

