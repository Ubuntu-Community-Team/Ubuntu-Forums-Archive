---
title: "System Compromized need forensics help."
date: 2013-05-09
forum: General Help
---

### Post by ant2ne on 2013-05-09
My CPU fan was running pretty high. I did a top and saw that pscan2 was using 100% cpu. After a very audible "WTF!" I did a ps -A which showed a whole bunch of ssh sessions. These sessions were being used by a limited user account I named xbox. I use xbmc and connect to a samba file share with this user xbox. xbox only has read access to the media share, and no access to any other data/share. This limited user did have a weak password so I guess it is plausible it got brute forced, and then there was an attempt to elivate preivledges. I immediatly brought the system down. Disconnected all other drives. (All of my data is stored on a seperate drives other than the one used to boot the system.) I logged in at grub recovery and then tarred my / to a USB drive. With the NICs unplugged. I brought the system back up and it hung at a plymouth error. I rebooted again and it came up to a login prompt. Changed all passwords. Changed the ssh config so only my account can ssh. 

I'm not real skilled on forensics. So this is a great opportunity to learn some. I do know enough to do 
```
ant2ne@vmhost:/var/log$ cat auth.log | grep xbox
May  5 13:55:42 vmhost sshd[20413]: Accepted password for xbox from 173.10.42.97 port 57655 ssh2
May  5 13:55:42 vmhost sshd[20413]: pam_unix(sshd:session): session opened for user xbox by (uid=0)
May  5 13:56:30 vmhost passwd[20658]: pam_unix(passwd:chauthtok): password changed for xbox
May  5 13:56:30 vmhost passwd[20658]: pam_smbpass(passwd:chauthtok): password for (xbox/1002) changed by (xbox/1002)
May  5 21:10:40 vmhost sshd[20413]: pam_unix(sshd:session): session closed for user xbox
May  7 03:54:06 vmhost sshd[22385]: Accepted password for xbox from 173.10.42.97 port 42356 ssh2
May  7 03:54:06 vmhost sshd[22385]: pam_unix(sshd:session): session opened for user xbox by (uid=0)
May  7 04:22:30 vmhost sshd[22385]: pam_unix(sshd:session): session closed for user xbox
May  8 21:04:13 vmhost passwd[5150]: pam_unix(passwd:chauthtok): password changed for xbox
May  8 21:04:13 vmhost passwd[5150]: pam_smbpass(passwd:chauthtok): password for (xbox/1002) changed by (root/0)

``` Notice the IP address? Not my IP. Notice the password changes? I did have an issue where I couldn't access my media share from xbmc. I troubleshooted the problem and ended up using a script I wrote to help automate creating and resetting samba passwords. In that script is both the smbpasswd command as well as the passwd command. It worked. I chalked it up to a fluke or smbpasswd bug and went on. Now I know someone got in. And change the password on me. And like a dummy I just changed it back to the same insecure password. 
 
Anyway, I'd like advice on how to find out exactly what xbox was doing while logged in. What all did xbox get access to? was it ever able to elivate?  I tried to log in as xbox and do a history but it didn't have anything in it.

Was the plymouth issue a fluke?

Should I contact comcast (owner of that IP) and give them that log?

---

### Post by TheFu on 2013-05-09
Start here: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
Also be sure you don't use password for ssh access anymore (only ssh-keys) and run **fail2ban** or **denyhosts** ALWAYS.  Passwords are to be avoided. They are the weakest part, even for long-time security people, using ssh-keys is actually easier too.  If a password is under 20, random, characters, then it is too weak. 

When something related to passwords seems wrong, you should research immediately. Resettng the samba passwords over and over was an administrative failure.

If you use any web-gui system admin tools - stop. Learn to secure those before re-enabling those - or better, just stop using them.

From a forensics standpoint you've already failed.  The rule is never touch the disk that has been compromised.  Shut it down and only mount it read-only. With that, you can can use dd or **ddrescue** to clone the entire partition to another disk where you can start looking around, compare the current files to backups, etc.  I hope you have versioned backups so you can see which files changed when. 

I hope you have versioned backups.

---

