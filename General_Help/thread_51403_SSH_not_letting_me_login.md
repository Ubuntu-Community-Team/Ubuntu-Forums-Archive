---
title: "SSH not letting me login"
date: 2005-07-23
forum: General Help
---

### Post by majikstreet on 2005-07-23
Hello,
I installed SSH following the instructions at UbuntuGuide.org  (which was just using APT-GET). 

I am trying to SSH in from PuTTY on my Windows computer and after I give it the _*correct*_ username and password, it says "Access Denied".

I have NO idea why this doesn't work-- I am sick of running up and down stairs to get to that computer, so that's why I want to SSH.

Thanks,
majikstreet

(Also, I'm not sure if this is in the right forum...)

---

### Post by scoon on 2005-07-23
Hey there, 

Any logging happening to help you out here ?

regards, 

scoon

---

### Post by majikstreet on 2005-07-23
[QUOTE=scoon]Hey there, 

Any logging happening to help you out here ?

regards, 

scoon[/QUOTE]
 ? What do you mean?

---

### Post by scoon on 2005-07-23
Hey there, 

Have you checked the log files ?  If you are not certain open up a shell and try man ssh and do some reading.    I don't run winblows at all and could not really help w/ putty much.

regards, 

scoon

---

### Post by ubuntp on 2005-07-23
run *tail -f /var/log/auth.log* on the ubuntu machine while you are logging in from putty, that will show you what's going on.

---

### Post by majikstreet on 2005-07-24
Ok, thanks, I will try that now.

Here part of my /var/log/auth.log which I believe to be relevant to the SSH login:
[quote]
Jul 24 07:29:22 localhost sshd: (pam_unix) authentication failure: logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.2.6 user=majikstreet

Jul 24 07:29:24 localhost sshd[4903]: error: PAM: Authencation faulure for majikstreet by LOGIN(uid=0)

Hope someone can make sense of this!

Thanks,
majikstreet

---

### Post by majikstreet on 2005-07-24
Also,
When I try to login from PuTTY it says something about keyboard-interactive.

I read in another post that that had something to do with public keys.

So here's what I think is going on: The server has the keys setup and my Windows computer doesn't. How do I get the keys to work in PuTTY?

Note: I think I may convert this Windows computer to Ubuntu later, for now I want to get the server setup. 

Since I may convert this computer to Ubuntu, how do I get the keys to work here, also?

Thanks,
majikstreet

---

### Post by majikstreet on 2005-07-24
Hello,
I tried a solution that I found: setting PasswordAuthentication in sshd_config to 'Yes', but that didn't do anything. Actually, I am glad that didin't work because I read that is insecure.

Thanks,
majikstreet

---

### Post by diffuser78 on 2005-07-24
[QUOTE=majikstreet]Hello,
I tried a solution that I found: setting PasswordAuthentication in sshd_config to 'Yes', but that didn't do anything. Actually, I am glad that didin't work because I read that is insecure.

Thanks,
majikstreet[/QUOTE]


Try this..I hope it should work
 

Check ur /home/user/.ssh directory

There must be a file names known_host

Delete the IP address of your windows machine from that file. ... I mean that particular line which contains the IP of ur windows machine.

Try logging again from windows using putty. Click on the yes options and it will ask for password. Dont worry its not insecure..its encrypted.

I think this should work.

Dan

---

### Post by majikstreet on 2005-07-24
[QUOTE=diffuser78]Try this..I hope it should work
 

Check ur /home/user/.ssh directory

There must be a file names known_host

Delete the IP address of your windows machine from that file. ... I mean that particular line which contains the IP of ur windows machine.

Try logging again from windows using putty. Click on the yes options and it will ask for password. Dont worry its not insecure..its encrypted.

I think this should work.

Dan[/QUOTE]
 I don't see any .ssh directory.
I typed ls -a and still don't see one.

majikstreet

---

### Post by ubuntp on 2005-07-24
You can only see it as root. Or from the filebrowser by pressing Ctrl+H.

---

### Post by diffuser78 on 2005-07-24
[QUOTE=majikstreet]I don't see any .ssh directory.
I typed ls -a and still don't see one.

majikstreet[/QUOTE]


Make sure that sshd is running by ps -A

If yes 

Do the following

$ ls -al

it will show u everything

it should have .ssh directory and a file "known_host"

check  that again....if u r missing on anything,

Dan

---

### Post by majikstreet on 2005-07-24
sshd is running.

The output of ls -al (After sudo su) (I only listed the names of files instead of all the permissions and everything):
.
..
.bash_history
.bash_profile
.bashrc
.viminfo




Thanks for all your help so far,
majikstreet

---

### Post by ubuntp on 2005-07-24
Well sth. is not right because there should be lots of directories starting with a dot, like .gnome2 and so and also Desktop. Maybe you are in the wrong directory?

---

### Post by majikstreet on 2005-07-24
1st thing: I installed using the "server" option since I *DON'T* need any graphical enviroment.

Maybe that's why.

majikstreet

---

### Post by ubuntp on 2005-07-24
Ah yes that explains it, but still doesn't explain why .ssh is missing. Maybe you should reinstall ssh (apt-get install --reinstall ssh).

---

### Post by majikstreet on 2005-07-24
[QUOTE=ubuntp]Ah yes that explains it, but still doesn't explain why .ssh is missing. Maybe you should reinstall ssh (apt-get install --reinstall ssh).[/QUOTE]
 Trying that now, will update when it's done and I try again.

majikstreet

---

### Post by majikstreet on 2005-07-24
I reinstalled ssh following your instructions (then rebooted for other reasons) and I still get Access Denied.

Maybe this has something to do with PuTTY?

Thanks for being so patient,
majikstreet

---

### Post by ubuntp on 2005-07-25
It might be Putty. Have you tried switching between SSH1 and SSH2? You might also want to try and set Use PAM in sshd_config to NO, and check the log if a different error comes up.

---

### Post by majikstreet on 2005-07-25
[QUOTE=ubuntp]It might be Putty. Have you tried switching between SSH1 and SSH2? You might also want to try and set Use PAM in sshd_config to NO, and check the log if a different error comes up.[/QUOTE]
 I will try this when I get home this afternoon.

---

### Post by jason_dc on 2005-07-25
Just looking at your log file 

Jul 24 07:29:24 localhost sshd[4903]: error: PAM: Authencation faulure for majikstreet by LOGIN(uid=0)


isnt uid 0 root, so do you not need to allow logins via ssh to root

sudo vi /etc/ssh/sshd_config

PermitRootLogin yes

see if this is enabled, if not enable it and restart sshd and retry...

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]Just looking at your log file 

Jul 24 07:29:24 localhost sshd[4903]: error: PAM: Authencation faulure for majikstreet by LOGIN(uid=0)


isnt uid 0 root, so do you not need to allow logins via ssh to root

sudo vi /etc/ssh/sshd_config

PermitRootLogin yes

see if this is enabled, if not enable it and restart sshd and retry...[/QUOTE]
 I am not logging in as root, so I don't see why I should enable it.

---

### Post by jason_dc on 2005-07-25
well in a way your are, ubuntu does not have a root user, your the root user 

your uid = 0 which is the root account on all other nix's

take a look here for a full explaination

[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

I am wondering if sshd is denying access to uid 0

Your on a local network so you can try without much fear, if it still does not work switch back and restart sshd, if you really dont want to do that create a new user and try to log on with that account instead, as this will not be uid 0

---

### Post by majikstreet on 2005-07-25
Here's my question: I am forwarding port 22 to that machine so I can access it from another computer outside the network-- Should I change ssh to listen on another port? I have read that changing ssh to another port fools script-kiddies and crackers.

I will try when I get home.

majikstreet

---

### Post by jason_dc on 2005-07-25
Well these days a tool like nmap would hunt down any open ports anyway, but may tale longer if you put it above the standard server ports > 1024 some people dont scan above 1024 for time purposes but not all

If your using a router / firewall in front of your Ubuntu server which easily allows port forwarding so you can change your default port from 22 on the public side then why not....

you can always add another user like I said previously, log in via ssh and su to your username once in

---

### Post by majikstreet on 2005-07-25
My router allows port forwarding (If it works!)-- but I can't make it go like this:
Port 1659(eg) ----> router ------> Port 22

My router doesn't support that.

I could just change it on my server and my router.

---

### Post by jason_dc on 2005-07-25
Well first thing would be to sort out the ssh login problem

otherwise you may start adding other issues in to the mix, ssh is secure, make sure you only using version 2

all the script kiddies will try username root anyway which will not be available

Once you can log in you can look at further ways to secure your connection, you could use a firewall on ubuntu and only allow from certain IP addresses for example

---

### Post by majikstreet on 2005-07-25
I am going to setup a firewall on that computer because it will be connected to the internet in many ways soon. SSH came first so I could administer the computer from my computer on another level. I want to use firestarter, but I want to use a gui (I don't have xorg or any wm installed- it's a server)... Not sure how to use firestarter in the command line though.

Thanks, I'll be home around 2 pm EDT (or 18:00 GMT).

---

### Post by jason_dc on 2005-07-25
You can stick with iptables as there are plenty of examples and documents out there from the command line


This is useful as I didnt see a start script for iptables and some one has posted one

[http://ubuntuforums.org/archive/index.php/t-19106.html](http://ubuntuforums.org/archive/index.php/t-19106.html)

I spose were going a bit off topic now though

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]You can stick with iptables as there are plenty of examples and documents out there from the command line


This is useful as I didnt see a start script for iptables and some one has posted one

[http://ubuntuforums.org/archive/index.php/t-19106.html](http://ubuntuforums.org/archive/index.php/t-19106.html)

I spose were going a bit off topic now though[/QUOTE]
 Yes, I guess we are.

Anyway, I'll update when I get home, thanks for everything so far.

---

### Post by majikstreet on 2005-07-25
I already had "Permitrootlogin yes" in the file.

For some reason now, when I go to PuTTY it just hangs.....

I am going to install Ubuntu instead of windows soon.......... Maybe with Ubuntu to Ubuntu the problem will be solved?

---

### Post by jason_dc on 2005-07-25
Have you tried connecting on the same LAN, not through a firewall?

Does it connect at all or just a blank screen in putty?

---

### Post by majikstreet on 2005-07-25
It just hangs--- blank screen... see attached.


I know winblows sucks... i promise, i am going to put ubuntu on this computer-- maybe once i get ssh working i'll change this computer to ubuntu.

thanks,
majikstreet

---

### Post by jason_dc on 2005-07-25
I have to use putty a lot at work to connect to Linux servers..

It looks like you are hitting a firewall or sshd is not started properly or something is going on

on the server whats the output of  

netstat -an | grep sshd

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]I have to use putty a lot at work to connect to Linux servers..

It looks like you are hitting a firewall or sshd is not started properly or something is going on

on the server whats the output of  

netstat -an | grep sshd[/QUOTE]
 question for you: if I run netstat -an | grep sshd > /mnt/usbstick/outputnags.txt  will it put the output in that file? instead of copying it by hand I'd like to put it in a file on my usb drive.

---

### Post by jason_dc on 2005-07-25
yep should work

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]yep should work[/QUOTE]
 no output.

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]yep should work[/QUOTE]
 no output.

---

### Post by jason_dc on 2005-07-25
sorry I am used to Redhat, I just installed openssh-server on my laptop

try netstat -al | grep ssh

should get someting like this

:/etc/init.d$ netstat -al | grep ssh
tcp6       0      0 *:ssh                   *:*                     LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     11650    /tmp/ssh-VuWplU7597/agent.7597

you can see if the port is open from your server with telent

telnet locahost 22

should get something like this

Connected to localhost.localdomain.
Escape character is '^]'.
SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2


If this works try the same telnet command from you XP machine, you should still see the ssh banner

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]sorry I am used to Redhat, I just installed openssh-server on my laptop

try netstat -al | grep ssh

should get someting like this

:/etc/init.d$ netstat -al | grep ssh
tcp6       0      0 *:ssh                   *:*                     LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     11650    /tmp/ssh-VuWplU7597/agent.7597

you can see if the port is open from your server with telent

telnet locahost 22

should get something like this

Connected to localhost.localdomain.
Escape character is '^]'.
SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2


If this works try the same telnet command from you XP machine, you should still see the ssh banner[/QUOTE]
 no output on the netstat command--

when i try to telnet from winxp it just hangs again......

I think I found the problem:
I tried to reinstall ssh and the last line said that libkrb53 needed to be installed and it couldn't. I tried apt-get install libkrb53 and it says it can't install it.

majikstreet

---

### Post by jason_dc on 2005-07-25
Maybe the problem, although I would have thought it would still work withought kerberos

it certainly sounds like the daemon is not running if you get no output from netstat or telnet on port 22

I just installed openssh-server on my laptop I am working on, just to see the differences between RedHat and ubuntu to see if I could help you out, it installed fine and I was able to connect from an XP box with putty

It installed openssh-server from the CD I installed Ubuntu from not a remote repository

---

### Post by jason_dc on 2005-07-25
I seem to be having problems posting back to the forum..

"Maybe the problem, although I would have thought it would still work withought kerberos

it certainly sounds like the daemon is not running if you get no output from netstat or telnet on port 22

I just installed openssh-server on my laptop I am working on, just to see the differences between RedHat and ubuntu to see if I could help you out, it installed fine and I was able to connect from an XP box with putty

It installed openssh-server from the CD I installed Ubuntu from not a remote repository"

This may already have been posted but I dont see it...

---

### Post by majikstreet on 2005-07-25
did you reply? it says you did but i can't see it!!!

yeah, i know i had that problem too...........

so should i just remove the current ssh and change sources.list to only use cd and install ssh from there?

I've been using apt-get install ssh btw.

majikstreet

---

### Post by jason_dc on 2005-07-25
seems like my post have arrived... :)

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]seems like my post have arrived... :)[/QUOTE]
 see my above post.

---

### Post by jason_dc on 2005-07-25
Do you get any other errors when trying to install krb53?

I have all these repo's set in my sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]Do you get any other errors when trying to install krb53?

I have all these repo's set in my sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./[/QUOTE]
 i do too.

No that's the only error.

---

### Post by jason_dc on 2005-07-25
I gota say, I am a bit stuck then...  I dont see why it would not install for you if it installed ok for me.. :???:

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]I gota say, I am a bit stuck then...  I dont see why it would not install for you if it installed ok for me.. :???:[/QUOTE]
 what commands are you using to install it. this is exactly what I am doing:
```

apt-get install ssh

```
Maybe you are installing a different package that's just a different version of sshd?

---

### Post by jason_dc on 2005-07-25
ahh

try  

apt-get install openssh-server

I think your just installing the client  ;-)

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]ahh

try  

apt-get install openssh-server

I think your just installing the client  ;-)[/QUOTE]
 Ok i did and it said:
openssh-server is already the newest version"

I checked ps -aux and the line with sshd on it says:
root 4854 0.0 1.1 3472 1508 ? Ss 16:50 0:00 /usr/sbin/sshd

Hope you know what it means!

---

### Post by jason_dc on 2005-07-25
Ok I just ran

apt-cache search ssh 

the ssh is a transitional package with both server and client, try removing this and installing

openssh-client
 and
openssh-server

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]Ok I just ran

apt-cache search ssh 

the ssh is a transitional package with both server and client, try removing this and installing

openssh-client
 and
openssh-server[/QUOTE]
 Do this rite:
```

apt-get remove ssh
apt-get install openssh-client
apt-get install openssh-server

```

---

### Post by jason_dc on 2005-07-25
yes, try this and see if it solves your problem

These are the packages I installed and I was up and running straight away

---

### Post by majikstreet on 2005-07-25
[QUOTE=jason_dc]yes, try this and see if it solves your problem

These are the packages I installed and I was up and running straight away[/QUOTE]
 Output of apt-get install ssh:
```

Reading package lists...
Building dependency tree...
Note, selecting ssh-krb5 instead of ssh
Package ssh-krb5 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```

---

### Post by jason_dc on 2005-07-25
[QUOTE=majikstreet]Output of apt-get install ssh:
```

Reading package lists...
Building dependency tree...
Note, selecting ssh-krb5 instead of ssh
Package ssh-krb5 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```[/QUOTE]

Are you installing ssh?

Remove ssh

apt-get remove ssh

apt-get install openssh-client

apt-get install openssh-server


netstat - al | grep ssh

this should show its running, if not reboot just to make sure

---

### Post by majikstreet on 2005-07-25
Nononon....

I was running apt-get remove ssh and it gave me that!

I'll try netstat -al | grep ssh again.

majikstreet

---

### Post by majikstreet on 2005-07-25
output of netstat -al | grep ssh:
```

tcp6 0 0*:ssh  *:* LISTEN

```

---

### Post by jason_dc on 2005-07-26
Ok looks like its up and running

from your server do you get a ssh banner when you telnet to port 22?

telnet localhost 22


if you do get a banner try telnet from your XP machine

telnet <ip of server> 22

---

### Post by majikstreet on 2005-07-26
[QUOTE=jason_dc]Ok looks like its up and running

from your server do you get a ssh banner when you telnet to port 22?

telnet localhost 22


if you do get a banner try telnet from your XP machine

telnet <ip of server> 22[/QUOTE]
 Can't do anything right now, but I have to let you know something:
I installed Ubuntu on another computer and installed openssh-server and I was able to connect to it. There must be something wrong with the package ssh.

When I get home I'll try to telnet, but right now all I can think of is 'REINSTALL!!!'

---

### Post by jason_dc on 2005-07-26
Ok well good luck, hopefully you wont need to re install... :razz:

---

### Post by majikstreet on 2005-07-26
[QUOTE=jason_dc]Ok well good luck, hopefully you wont need to re install... :razz:[/QUOTE]
 Thanks,
Only thing I can do now is wait until I get home.... :(

---

### Post by majikstreet on 2005-07-26
[QUOTE=majikstreet]Thanks,
Only thing I can do now is wait until I get home.... :([/QUOTE]
 I am soo sorry......
I realized why this happened.
Ubuntu makes capital Es and Cs lowercase, so my password that I was entering from windows was WRONG! At least in the command line.

This is the cause of my despair.

How do I fix this?

---

### Post by jason_dc on 2005-07-26
Your kidding ? :smile: 

I never heard of this, so when you enter a captial it stays lower case in passwords or only for E and C?  :| 

At least its solved though   :)

---

### Post by majikstreet on 2005-07-26
[QUOTE=jason_dc]Your kidding ? :smile: 

I never heard of this, so when you enter a captial it stays lower case in passwords or only for E and C?  :| 

At least its solved though   :)[/QUOTE]
 If you use capslock that is.

I don't use shift, I use capslock, that's how I've always typed. It's easier.

---

