---
title: "NoMachine NX Newbie help!"
date: 2008-01-25
forum: General Help
---

### Post by Moonwings on 2008-01-25
I managed to successfully install the NoMachine NX server software  on my laptop running Ubuntu 7.10 (Gutsy)   When i check the status, it says
NX> 110 NX Server is running

Then I went to my Windows XP machine and downloaded the NXclient software.  I am now in the connection wizard for the client on windows and have no clue what to enter.

It wants me to "insert server's name and port where you want to connect"
I have no idea what to tell it. How do I know what my laptop is called?
Also, it wants me to select my internet connection type and I'm not sure what to put there either.

Here's my configuration:
1 laptop running Ubuntu 7.10 with NoMachine NX Server
1 PC running Windows XP
1 wireless linksys router.  The PC is plugged into one of the wired ports on the router. The laptop is using the wireless connection to the router.
Cable internet (plugged into the router, obviously)
Dynamic IP addressing
The laptop is able to successfully see drives on the Windows PC so I presume the network permissions are set up ok.


The goal is to be able to remote into my linux machine from my windows machine.

So, how do i know what my host name is?  And what should I choose for the internet connection? LAN?

Sorry for the really dumb questions but this is totally new to me.  Thanks!

---

### Post by rechick on 2008-01-26
On the linux box type:
hostname
and it will display the hostname of the machine which you can use in the NX Client.
Then, set the client to Gnome or KDE depending on what you are using (Ubuntu is Gnome, Kubuntu is KDE).
The remaining defaults you can leave until you see things work properly.

---

### Post by PinkFloyd102489 on 2008-01-26
For the hostname you can enter the IP address, in fact it's encouraged to do so since I had problems with NetBIOS for a while. As for connection, it doesnt really matter. It wont throttle you down if you select ADSL on LAN and you wont lag out if you select LAN when you're halfway across the world.


Also note that you're spawning a separate session when you log in with NX. Dont expect to see any windows you left running on your laptop when you log in remotely. If you want realtime control, better go with actual VNC instead of a session based NX.

---

### Post by Moonwings on 2008-01-26
rechick:  I typed hostname on the laptop and it returned "debbie-laptop" (which is logical, since I vaguely recall giving it that name)
So that's what I entered in the client configuration.
I chose Gnome (because I'm running ubuntu)
When it reached the NOMACHINE logon window I entered my ubuntu login name and password.  And then it returned this:

NX> 203 NXSSH running with pid: 2084
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
nxssh: debbie-laptop: no address associated with name

pinkfloyd: I didn't try the ip address because I don't remember how to ask linux what its ip address is :(


Thank you both for responding and for the tips.
by the way, if I use the ip address will I have any problems with the fact that I'm set up for dynamic IP addresses?

Many thanks!

---

### Post by ingo on 2008-01-27
Number of questions to be asked...

1 - Are you doing this on a home network or across the internet? If you intend to use the latter you either need a fixed ip connection or alternatively a dyndns account...

2 - Have you installed openssh incl. ssh server?

To find out your ip simply do a > sudo ifconfig. This will list your network interfaces and your ip address is listed under inet addr: (first number of second line of relevant interface).

HTH and let us know how you get on 'cos I'm after exactly the same thing :)

---

### Post by Moonwings on 2008-01-27
thanks ingo.
I did finally manage to figure out how to find the IP address.
And then tried to start the client using the IP rather than the hostname.
This got me a bit further but not all the way there.

FYI - I am trying to do this on my home network so my IP is 192.168.1.nnn.  Both machines (windows and ubuntu) are connected to my router.  The laptop (ubuntu) is using wireless access.

The following is exactly what I get when I attempt to connect.

> NX> 203 NXSSH running with pid: 552
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.104 on port: 22
NX> 211 The authenticity of host '192.168.1.104 (192.168.1.104)' can't be established.
RSA key fingerprint is 94:73:4d:6b:0a:eb:2c:65:90:85:e6:a9:fb:8e:ad:3a.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added '192.168.1.104' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
/usr/bin/X11/xauth:  creating new authority file /usr/NX/home/nx/.Xauthority
HELLO NXSERVER - Version 3.1.0-4 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: debbie
NX> 102 Password: *******
NX> 103 Welcome to: debbie-laptop user: debbie
NX> 105 Listsession --user="debbie" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: debbie
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu-Laptop" --type="unix-gnome" --geometry="1280x990" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1280x990x32+render" 
NX> 505 ERROR: Error occurred: public key authentication failed.
NX> 505 ERROR: NX server was unable to login as user: debbie.
NX> 505 ERROR: There is no public key on node 127.0.0.1.
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 55F4E84E. To get detailed information about
NX> 595 ERROR: the error search for the string 55F4E84E in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 999 Bye.
NX> 280 Exiting on signal: 15

I did a search about the public key problem and went back into my /etc/ssh/sshd_config to ensure that I had the following line in it:
> AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2
Interestingly enough, the line was missing.  That was odd, since I had added before.  I guess something I did during the installation deleted it.  So I added it again and then restarted ssh:
> sudo /etc/init.d/ssh restart
Unfortunately this didn't solve the problem. I get the same error.
I posted this particular problem [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4216733#post4216733")
but I haven't gotten a response yet.

---

