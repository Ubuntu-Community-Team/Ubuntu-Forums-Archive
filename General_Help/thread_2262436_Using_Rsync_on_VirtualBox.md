---
title: "Using Rsync on VirtualBox"
date: 2015-01-24
forum: General Help
---

### Post by Lappert on 2015-01-24
I hope this is the right place to post this.

One of the reasons I switched to Kubuntu was so I could rsycnc my workstation with my remote server in both directions (I own the server). Can't do that with Windows.

But some pesky Windows applications will not run, even with Wine, so I have them on an instance of Win7 using VirtualBox. I'm OK with that.

But here's the rub. When I rsync my kubuntu box to our server, it comes across the VirtualBox file at /home/user/VirtualBox VMs/Win7-32/Win7-32.vdi.

The Win7-32.vdi file is around 32 GB and so it takes at least 30 minutes to copy the file locally and even longer to rsync the file with the remote server. On average very little changes on the VM file, but the data is important.

Is anyone familiar with a strategy to rsync a VM file in a reasonable amount of time? I can't invoke rsync from inside the Windows VM. Last I checked the so-called rsync solutions on Windows just didn't work.

ANy help is appreciated. Thanks.

---

### Post by TheFu on 2015-01-24
a) exclude the vdi file from the sync.  There is a --exclude option. **man rsync** explains the multiple ways to use that and there are lots of examples at [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html) - the tool author's site.
b) rsync does work in windows, just don't use it for large files without ensuring large-file-support has been compiled into the version you run.  There are native ports or the cygwin versions.  

I've extensively tested rsync on virtual machine files.  Somewhere around 4G it stops being useful and usually fails.  In my environment, we decided to perform backups for VMs from inside each and treat it like a physical machine. Doing this made backups for a VM drop from 15-30 min down to 1-3 min. We use rdiff-backup, if you care.

BTW, rsync for backups really isn't enough. Extra steps are needed to get versioned backups, which is absolutely critical in a backup solution. There are easier backup tools, based on librsync, that handle this stuff already.

OTOH, if you just want to mirror a website or webapp code (scripting) to a webhost, rsync is fine. Backups would be necessary for the versioned backups, of course.

---

### Post by Lappert on 2015-01-24
TheFu, thanks for your reply.

I am familiar with --exclude and until I get a better solution, I am using that flag, but of course that excludes a backup of the VDI, or more in particular, the specific files in the windows VM that I wish to backup. At the moment I do rsync the 32GB VM to a local disk for a mirror. That works fine (takes at least 25 minutes). But when I rsync to my remote server, I use the --exclude.

As you describe it, I want to "p[COLOR=#000000]erform backups for VMs from inside each and treat it like a physical machine.[/COLOR]" If I could do that, I could get it down to less than 1 minute.

I did look at the rsync options for Windows. I couldn't get any of them working (of course I was on a Vista box then; I have not tried it with W7 or W8).

I understand that rsync is not the same as versioned backups. One step at a time :). What can you recommend for that?

In the meantime I'm trying to get they rsync to work in cron (or anacron). The problem there is that I use ssh and it needs a passphrase. So I'm trying to get it to work without the passphrase.

Thanks again.

---

### Post by afoin on 2015-01-25
If you can put the files that you want to rsync in a shared folder in your /home directory, that would be easier.

---

### Post by Lappert on 2015-01-25
Afoin, thanks for your reply.

How would that be easier? For sake of discussion, I have two 'sections' of files that get rsynced. They are physically on two different drives. One is around 89 GB and the other around 95 GB. But one of those contains the .vdi VM file that is around 36 GB. Other than that particular file, updating the two sections daily might take all of 2-3 minutes. The .vdi file alone takes about 25 minutes.

The problem is how to "get inside" the VM and just backup the files from the Windows applications I am still using. If I could do that, then there would be no need to rsync the entire VM file.

Thank you.

---

### Post by TheFu on 2015-01-25
> **Lappert said:**
> I understand that rsync is not the same as versioned backups. One step at a time :). What can you recommend for that?
rdiff-backup - the command looks much like rsync, but does much more. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)  There are other backup tools too.

> **Lappert said:**
> 
In the meantime I'm trying to get they rsync to work in cron (or anacron). The problem there is that I use ssh and it needs a passphrase. So I'm trying to get it to work without the passphrase.

I have a "backup" account that doesn't need a passphrase to unlock ssh keys. It is root-equiv to get all the files regardless of ownership.  I currently push backups, but need to switch over to pulling them for better security of the backup server. Of course, the ssh access must be locked down to allow remote root access, and only from the specific server.

---

### Post by Lappert on 2015-01-25
Thank you. I'll look into the rdiff-backup.

Curious, how does one make a root-equiv account?

I can push or pull from the desktop to the server, but not the other way. All commands must come from the desktop as it has a dynamic IP. How would pulling make better security for your server than pushing?

---

### Post by SeijiSensei on 2015-01-25
If you give the root user a password on the remote server, you can follow this method:

1) Log in as yourself, and issue the command "ssh-keygen".  Accept the defaults when prompted.

2) Now run "ssh-copy-id root@remote_server".  Enter the password you gave root when prompted.

3) Now try logging into the remote using "ssh root@remote_server".  You should be logged in to the root account and see the "#" prompt instead of "$".

4) You can now remove the password for root if you like.

For rsync transfers, I find things work best if you create an SSH ID for the root user and copy that to root's account on the remote.  Then you can create a backup job in /etc/crontab or /var/spool/cron/root that will run with root's privileges on both ends of the connection.

---

### Post by TheFu on 2015-01-26
No need to provide any root account password for this stuff.  Just use **sudo -s** to get a root session (with your personal settings and HOME) - or use **sudo -i** to get a real root shell with root's HOME set and none of your personal environment.  Then you can manually copy the public ssh-key from whatever account you'll be using for the remote connection.

A root-equiv account is just another account added with a HOME, then change the uid to zero (0). Be certain NOT to put it above the root entry in /etc/passwd.  It can have a password, but I consider it a security failure.

Also - just because you have a dynamic IP address, that doesn't mean it cannot be maintained with a DNS name - dyndns.org used to have free dynamicDNS accounts (they don't anymore), but there must be 10 other providers. Most home routers have a dyndns setting - check for the providers in that drop-down list and check them out.  Sorry I don't know more.  I've been using dyndns for over a decade and have grandfathered access - plus I have static IPs now.  The dynamicDNS stuff works well, IME.  OTOH, my residential ISP only changed the dynamic IP 4 times in 8 yrs.  I've heard about ISPs forcing a change every 4 hrs, so the dyndns just needs to be setup to monitor every 5 minutes.

Why is pulling more secure than pushing?  In my environment, some of the servers are internet facing and under constant attack. Should any of them be breached, then any access that machine may have to other systems would provide another attack vector for the "bad guys" to use.  If I pull the backups, the remote machine doesn't get that access.  Pulling means that prior backup versions can't be modified by the attacker. Pulling means only that machine is likely to be harmed. Pulling means I only have one public key to place on all the remote machines, not 1 for each machine to place on the backup server.  Those are the reasons just off the top of my head.  I had about 10 others when it was decided I needed to switch.  KISS.

---

