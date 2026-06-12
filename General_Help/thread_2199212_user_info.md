---
title: "user info"
date: 2014-01-12
forum: General Help
---

### Post by sajil2 on 2014-01-12
hi
i need to find out user info.that starts daemon while i reboot please.i am running ubuntu 12.04

---

### Post by Bashing-om on 2014-01-12
sajil2; Hi !

That is real vague ! .. What is your situation and what are you attempting to do ?

shots in tha dark
[INDENT][INDENT]are not to effective
[/INDENT][/INDENT]

---

### Post by sajil2 on 2014-01-12
i changed limits.conf for root user.but i have to stop the and login as a root and start the sevice.so i want to know what user starts daemon so i can add that in limits.conf.
thanks

---

### Post by Iowan on 2014-01-12
Perhaps a few more details...
*limits.conf* where?
What process/service? 
Could you provide a full path to the file.
This is still for a 12.04 machine?

You seem to have another thread or two that went without reply - let's try to change that. :)

---

### Post by whitesmith on 2014-01-12
> **sajil2 said:**
> i changed limits.conf for root user.but i have to stop the and login as a root and start the sevice.so i want to know what user starts daemon so i can add that in limits.conf.
thanksI read this as meaning that you changed ownership on a file called limits.conf from you:you to root:root. If that assumption is correct there is no need to do anything but chown back to you:you, which you must do as root```
sudo chown ...
```If I have this wrong, you need to be very specific to get the help you need. Cheers!

---

### Post by Bashing-om on 2014-01-12
Never mind, this post- better minds on the case.
EDIT:@sajil2 Responding to your Private Message here and I see iowan and whitesmith have responded.
I will continue to monitor the activity. Awaiting your response to the above posts.

we are here to help.
cheers

---

### Post by ian-weisser on 2014-01-12
> **sajil2 said:**
> i changed limits.conf for root user.but i have to stop the and login as a root and start the sevice.so i want to know what user starts daemon so i can add that in limits.conf.

The .conf suffix indicates that it's an Upstart job, not a sysvinit job.

If your daemon needs to run as root, then
1) The .conf file needs to be located in /etc/init/ , and
2) The .conf file needs to be owned by root.

If your daemon does not need to run as root because it has a separate system user (example: usernames *daemon *or *nobody* or *myserver*), then #1 and #2 still apply, PLUS
3) The .conf file needs to include a **setuid <username>** stanza

If your daemon does not need to run as root because it only runs when a user is logged in, then NONE of #1, #2, or #3 above apply. Instead,
1) The .conf file should be located in ~/.config/upstart or /usr/share/upstart/sessions/
2) The .conf file should be owned by the user (if in ~ ) or root (if in /usr)


Did you use the **init-checkconf** command to check the .conf file syntax? 
Did you use **upstart-monitor** to see if your start/stop criteria are occuring when you expect? 
If your service is still not starting, then show us the .conf file.

---

### Post by sajil2 on 2014-01-12
i have to add these too lines to limit conf

root soft nofile 65536
root hard nofile 65536
# End of file


thats why  need to log in as a root and start a dameon?

---

### Post by Bashing-om on 2014-01-12
sajil2; Hold on !

I am not going to get into why you want/need to edit that file.
As you are seeking to edit a file, then you want to open a file editor to edit that file,
IF it is a "system" file, then yes elevated privileges are required:
Make a backup prior to editing any file ,, standard operating procedure - 
```

gksudo gedit <path_to_file><file_name>

```
Now as you do not know to use a text editor, I question that you should be attempting to edit a system file .

Nor is there a need to start the daemon. Make the edits to the file, and reboot for the change to take effect.

But, please, be sure and careful of what you are doing.

Mistakes and errors at the system level can really make for 
[INDENT][INDENT]a real bad night
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-01-13
> **sajil2 said:**
> 
root soft nofile 65536
root hard nofile 65536
# End of file


The *limit *syntax seems incorrect.
Try:
```
limit nofile 65536
```

See [http://manpages.ubuntu.com/manpages/trusty/en/man2/getrlimit.2.html](http://manpages.ubuntu.com/manpages/trusty/en/man2/getrlimit.2.html) for what can be limited.
Limit stanzas only work on system-level Upstart jobs.

Er, if your process needs to spawn that many files, you may consider redesidgning it.
Are you trying to protect from a forkbomb?

---

### Post by sajil2 on 2014-01-13
everything else is fine.but when i reboot my server the daemon doesnt start as a user root.i have to login as a root and restart to work.is there any way to start daemon as a root while i reboot

---

### Post by ian-weisser on 2014-01-13
Yes.
You're doing it with an Upstart .config file already.

If it's not working, then you either have a syntax error in your .config file, or your "start on" stanza does not include valid criteria.
Use the command **init-checkconf**** <your_file>.conf** to find syntax errors.

---

### Post by sajil2 on 2014-01-13
0000000:~# init-checkconf limits.conf
ERROR: cannot run as root

---

### Post by sajil2 on 2014-01-13
here is a complete file.

```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#


#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
root soft nofile 65536
root hard nofile 65536
# End of file
```

---

### Post by ian-weisser on 2014-01-13
Ah, so it's NOT an Upstart config file.

You can start a job at boot using Upstart, Sysvinit, or Cron
Which method are you trying to use?

---

### Post by efflandt on 2014-01-13
```
efflandt@xps8100-1204:~$ locate limits.conf
/etc/security/limits.conf
/usr/share/man/man5/limits.conf.5.gz
```If you "cat /etc/security/limits.conf" by default everything is commented out (leading #). So read that and "man limits.conf", then you can edit it if necessary like Bashing-om says, or I would typically use: **sudo nano /etc/security/limits.conf** in a terminal, if I needed to do that (then reboot). If you mess up that file you can mount that partition from live/install iso on CD/DVD or bootable USB and edit it in the mounted path.

PS: What daemon are you trying to run and who is it running as?

---

### Post by sajil2 on 2014-01-23
hi sorry for replying late been sick.i am trying to increase fd for more open files.i followed info below

[h=2]Tweak Your FD[/h]
[INDENT]Hi 

CSP default thread is set at 1024. So many of you who are wondering why your peers & users connections are being dropped is because you are peaking. Placing max thread in CSP to 3000 or 5000 is not going to help regardless of your server hardware. So you need to increase your FD to accommodate for more threads. 


Here is a little how to blow up your FD in CSP.
My Howto are always based on Debian or Ubuntu 

Login to your shell of csp

nano /etc/security/limits.conf

Add the follow lines prior to end of file sentence:

root soft nofile 65536
root hard nofile 65536

Disable CSP from Auto Startup 

reboot your server


Wait until everything is booted before starting your CSP, otherwise Java will not cope the changes.

Webinfo look at the top left you will find that your FD has become 65536 

Remember the more profiles you add & the more users the more descriptor files are needed

Hope this helps [IMG]http://cccam-exchange.com/images/smilies/icon/smile.gif[/IMG][/INDENT]

---

### Post by sajil2 on 2014-01-23
here is my problem if i auto reboot [COLOR=#000000]CSP default thread is set at 1024
if i sto and login as root and restart [/COLOR][COLOR=#000000]FD has become 65536.

but sometime program crashes and give error core dump?so i need to resart again.i want run auto script use and start as a user root,so fd can remain 65536.[/COLOR]

---

