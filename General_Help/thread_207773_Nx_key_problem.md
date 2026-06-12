---
title: "Nx key problem?"
date: 2006-07-02
forum: General Help
---

### Post by matrooswolf on 2006-07-02
Hi, I have been messing around with Nxserver for some days now and can't get it to work.

I can get it to work with one user, but not for my regular account.

I have created a new user 'test', and he can connect (I have tried it out on my laptop, on windows on vmware, and everything works fine ...)

But I cannot get my regular account to work ... :cry: 

I tried a lot of things, I deleted my regular account with:
```
sudo /usr/NX/bin/nxserver --userdel USER --system --nohome
```
added it again with:
```
sudo /usr/NX/bin/nxserver --useradd USER
```
but this gives me this error:
> NX> 801 User: USER uses SSHD authentication.
NX> 900 Adding public key for user: USER to the authorized keys file.
NX> 910 WARNING: The SSH key to be used for user authentication could
NX> 910 WARNING: not be added to the private authorized keys file of user.
NX> 910 WARNING: Please note that, with these settings, the user won't be
NX> 910 WARNING: able to successfully run any sessions.
NX> 910 WARNING: Run the following command to get some hints on the possible
NX> 910 WARNING: reasons of the problem:
NX> 910 WARNING:
NX> 910 WARNING: nxserver --usercheck USER
NX> 910 WARNING:
NX> 301 User: USER enabled in the NX user DB.
NX> 999 Bye.

But when doing (as suggested):
 > sudo  /usr/NX/bin/nxserver --usercheck USER
I get this error:
> NX> 900 Verifying public key authentication for NX user: USER.
NX> 900 Adding public key for user: USER to the authorized keys file.
NX> 596 ERROR: NXNODE Ver. 2.0.0-93  (Error id e88B064)
NX> 596 ERROR: Sun Jul  2 18:02:09 2006 running as user: 'USER' (uid: 1000) on ''
NX> 596 ERROR: in node ssh keys manager: add server ssh public keys to user
NX> 596 ERROR: Cannot create file: /home/USER/.ssh/authorized_keys2: Toegang geweigerd. *(this means access refused) *
NX> 900 ERROR: Failed to add public key.
NX> 999 Bye.

So, why does one user work, and the other not?

When I do:
 > sudo  /usr/NX/bin/nxserver --usercheck test
I get no errors:
> NX> 900 Verifying public key authentication for NX user: test.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

It has to do something with keys, but I am afraid I know nothing of ssh, keys, etc ... (a lot of what I have been doing so far is trial and error I am afraid, and a tiny weeny bit of logic ;))

Any help mucho appreciado!!

---

### Post by Fac51 on 2006-07-02
i'm not familiar with nxserver, but see what happens if you remove the ssh info from USER's home dir

```
rm -rf ~/.ssh
```

it's a shot in the dark, but it's something

---

### Post by matrooswolf on 2006-07-02
Thank you for your reply, but no, it makes no difference

I have no clue at the moment ...](*,) ](*,)

Is it a nxserver problem?  A ssh problem? 

Can I create that key in another way?

---

### Post by matrooswolf on 2006-07-02
Maybe it can be solved simply by changing ownership (ownership of .ssh on USER was set to Root, I do not know why ...)

I just changed ownership to USER (changing the permissions only gave me some more errors ...)

This gives me no errors on 
```
 sudo  /usr/NX/bin/nxserver --usercheck matroosje
```

I'm going to try everything out tommorow ... hope I'm lucky!

But first I need some sleep (past 2:00 am here)

---

### Post by matrooswolf on 2006-07-03
Well, I managed to make a key ...
I changed the ./ssh ownership to USER
did 
 sudo  /usr/NX/bin/nxserver --usercheck USER

but still no connection to the nxserver ...
When trying to connect I get this error message
> NX> 203 NXSSH running with pid: 168
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 179.29.3.2 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Warning: No xauth data; using fake authentication data for X11 forwarding.
HELLO NXSERVER - Version 2.0.0-69 - LDS
NX> 105 Hello NXCLIENT - Version 2.0.0
NX> 134 Accepted protocol: 2.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login
NX> 101 User: USER
NX> 102 Password: ********
NX> 103 Welcome to: matroosje user: USER
NX> 105 Listsession --user="USER" --status="suspended\054running" --geometry="1024x768x32+render" --type="unix-gnome"
NX> 127 Available sessions:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: USER
NX> 105 Start session with: --link="adsl" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="32M" --images="128M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="thuis" --type="unix-gnome" --geometry="1024x738" --client="winnt" --keyboard="pc102\057nl-be" --screeninfo="1024x738x32+render"
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: ADBCB67C. To get detailed information about
NX> 595 ERROR: the error search for the string ADBCB67C in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
Killed by signal 15.

more info in /var/log/messages??? I don't find that one ...)

So for now, I have one user without any problems and my main user that generates a fatal error in the NX server.

Could it have to do something with my main user having administration priviliges,  ???

Anybody any ideas where I could continue my search?

In fact I have no clue ...
](*,) some more

---

### Post by matrooswolf on 2006-07-04
Hi, 
so I did a complete remove purge for openshh, nxclient, nxnode, and nxserver.
Installed everything again, and just the same situation:
One user works fine.
The other user gives a nxserver failure ...

I have searched for differences for the two users.
One difference is that the GOOD user was added by sudo /usr/NX/bin/nxserver --useradd
The BAD user is just my regular account and was added by system

Another difference:
GOOD user:
home/user/.ssh is owned by user, group=users
BAD user:
home/user/.ssh is owned by root, group=root
(I changed that to user, group=users to add the key with sudo  /usr/NX/bin/nxserver --usercheck USER.  The key was added, tried it, tried it again with ownership back to root, group=root, but still the same error ...)
```
> 203 NXSSH running with pid: 1892
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 172.19.3.2 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Warning: No xauth data; using fake authentication data for X11 forwarding.
HELLO NXSERVER - Version 2.0.0-69 - LDS
NX> 105 Hello NXCLIENT - Version 2.0.0
NX> 134 Accepted protocol: 2.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: USER
NX> 102 Password: ********
NX> 103 Welcome to: matroosje user: USER
NX> 105 Listsession --user="USER" --status="suspended\054running" --geometry="1024x768x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: USER
NX> 105 Start session with: --link="adsl" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="32M" --images="128M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="thuis" --type="unix-gnome" --geometry="1024x738" --client="winnt" --keyboard="pc102\057nl-be" --screeninfo="1024x738x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 30F09BE9. To get detailed information about
NX> 595 ERROR: the error search for the string 30F09BE9 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
Killed by signal 15.
```


(BTW: I was looking for /var/log/messages but the only messages I have are from 4th februari??  System logging is off it seems ...)

---

### Post by mannheim on 2006-07-04
Are you in a situation where you **need** to use the --useradd stuff in nx? Unless your server machine has users whom you wan't to prohibit from using nx, then you don't need it.

If you don't need nxserver's own user db stuff, the what I would do is: uninstall everything again, and wipe out the directories ~/.nx in the home directories. Then reinstall the .deb packages and change **nothing**. (Don't generate new keys, no --useradd etc.) You should now be able to connect, as any user, using the default key in nxclient.

Next, if you want nx on the server to have its own keypair, rather than the one supplied by nomachine, generate a new keypair on the server with:

```
sudo /usr/NX/scripts/setup/nxserver --server-keygen
```

After that, to connect to the server, users will have to paste in the new private key contained in the server's directory at /usr/NX/share/keys/default.id_dsa.key

---

### Post by matrooswolf on 2006-07-04
To Mannheim,
thank you for your reply, I am going to try this when I'm home (I am away at the moment).
(But I think I did a complete whipeout of .nx last time, did I ?).

No I don't need useradd, I just added a new user, just to test if I could connect with a new user (and I could, but still not with my regular account.)

More news soon ...

---

### Post by kb2wdi on 2006-07-04
> Cannot create file: /home/USER/.ssh/authorized_keys2:
> Failed to add public key.

try;
sudo chown -R USER:USER ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys2
chmod 644 ~/.ssh/authorized_keys2

It looks like a ssh file permission problem.

---

### Post by matrooswolf on 2006-07-05
[QUOTE=mannheim]Are you in a situation where you **need** to use the --useradd stuff in nx? Unless your server machine has users whom you wan't to prohibit from using nx, then you don't need it.

If you don't need nxserver's own user db stuff, the what I would do is: uninstall everything again, and wipe out the directories ~/.nx in the home directories. Then reinstall the .deb packages and change **nothing**. (Don't generate new keys, no --useradd etc.) You should now be able to connect, as any user, using the default key in nxclient.[/quote]

Hi mannheim, 
I tried reinstalling everything but no luck 
(I post the commands here in case I did something wrong) (still learning about linux)

completely removed openssh with synaptics (marked for complete removal with configuration files)
then:

```
sudo dpkg --purge  nxserver
sudo dpkg --purge  nxnode
sudo dpkg --purge  nxclient
```

removed ./ssh and ./nx from home of both users
removed /usr/NX/
(with gksudo nautilus)

then reinstalled everything

```
sudo apt-get install openssh-server
sudo dpkg -i nxclient_2.0.0-90_i386.deb
sudo dpkg -i nxnode_2.0.0-93_i386.deb
sudo dpkg -i nxserver_2.0.0-69_i386.deb
```

connected to my client (didn't do anything else, no useradd, no usercheck) 
and same situation:
One user connects
My regular user doesn't ...

Still very :confused: :confused: :confused: about this.

Now a difference I found is that 
in ./ssh for the GOOD user is a file authorized_keys
in ./ssh for the BAD user is a file know_hosts

the only ip i find in known_hosts is 127.0.0.1
does that mean anything?
Shouldn't my remote ip be in there also (something like 182.21.3.2)?

and why the difference between the to ./ssh files?

I am pretty much clueless about all this, networking and shh are not my forte, so forgive me if I ask stupid questions.

---

### Post by matrooswolf on 2006-07-05
[QUOTE=kb2wdi]> Cannot create file: /home/USER/.ssh/authorized_keys2:
> Failed to add public key.

try;
sudo chown -R USER:USER ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys2
chmod 644 ~/.ssh/authorized_keys2

It looks like a ssh file permission problem.[/QUOTE]

Hi kb2wdi,
thanks for your reply

after reinstalling everything (see previous post)
I tried this as well, 
but no luck

did

```
nxserver --usercheck USER
```

(which adds the authorized_keys2 to ./ssh), and which works now 

but no luck

still can connect with one user, and not with the other one ...

---

### Post by matrooswolf on 2006-07-05
Hi to all the good souls who are reading this thread!

More news

Thanks to Ramses de Norre (in another thread) I have reenabled my systemlog, and I finally can view the errors :smile: :

This is what I get:

Long version:
[php]Jul  5 12:55:41 localhost NXSERVER 2.0.0-69[13897]: WARNING: You appear to run an unsubscribed product. Please visit the 'main::chk_license'
Jul  5 12:55:41 localhost NXSERVER 2.0.0-69[13897]: WARNING: NoMachine Web site at http://www.nomachine.com/ 'main::chk_license'
Jul  5 12:55:41 localhost NXSERVER 2.0.0-69[13897]: WARNING: to purchase a valid subscription. 'main::chk_license'
Jul  5 12:55:42 localhost NXSERVER 2.0.0-69[13897]: User 'USER' logged in from '186.19.3.2'. 'NXLogin::set'
Jul  5 12:55:42 localhost NXSERVER 2.0.0-69[13897]: Selected node host:localhost (ip: 186.19.3.2) with port:22 'main::selectNode'
Jul  5 12:55:42 localhost NXSERVER 2.0.0-69[13897]: Current selected node: 186.19.3.2 is in status: running  'main::selectNode'
Jul  5 12:55:49 localhost NXNODE 2.0.0-93[13921]: DEBUG: You appear to run an unsubscribed product. Please visit the 'main:nxnode:2513'
Jul  5 12:55:49 localhost NXNODE 2.0.0-93[13921]: DEBUG: NoMachine Web site at http://www.nomachine.com/ 'main:nxnode:2514'
Jul  5 12:55:49 localhost NXNODE 2.0.0-93[13921]: DEBUG: to purchase a valid subscription. 'main:nxnode:2515'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.0.0-93  (Error id eEEE781) [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 ERROR: Wed Jul  5 12:55:51 2006 running as user: 'USER' (uid: 1000) on '' [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 ERROR: execution of last command failed [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/USER/.nx/C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021/scripts/authority' [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 exit value: 1 [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 stdout:  [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 stderr: xauth:  /home/USER/.Xauthority not writable, changes will be ignored [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93 [13921]: ERROR: NX> 596 . [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 init: stdin arguments: user=USER,userip=172%2e19%2e3%2e2,uniqueid=F599D7A7BE78EC5F3CD688A4328CB021,display=1012,license=%28None%29,subscriptionid=None,productid=LDS,reconnect=1,balance_host=172%2e19%2e3%2e2,encryption_mode=3,images=128M,cache=32M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=thuis,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1024x738x32%2brender,nodelay=1,streaming=1,keyboard=pc102%2fnl%2dbe,geometry=1024x738,link=adsl 'main:nxnode:2662'
Jul  5 12:55:52 localhost NXNODE 2.0.0-93[13921]: INFO: getting agent pid: cannot read pid file '/home/USER/.nx/C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021/pids/agent'. Exiting. 'main:nxnode:7857'
Jul  5 12:55:52 localhost NXNODE 2.0.0-93[13921]: INFO: directory '/home/USER/.nx/C-USERe-1012-F599D7A7BE78EC5F3CD688A4328CB021' moved into '/home/USER/.nx/F-C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021' for investigation 'main:nxnode:7912'
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 ERROR: NXNODE Ver. 2.0.0-93  (Error id eEEE781)
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 ERROR: Wed Jul  5 12:55:51 2006 running as user: 'USER' (uid: 1000) on ''
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 ERROR: in node start session: create session: run commands
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 ERROR: execution of last command failed
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/USER/.nx/C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021/scripts/authority'
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 exit value: 1
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 stdout:
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NX> 596 stderr: xauth:  /home/USER/.Xauthority not writable, changes will be ignored
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69 [13897]: ERROR: (exception id 82FDEB31) NX> 596 init: stdin arguments: user=USER,userip=172%2e19%2e3%2e2,uniqueid=F599D7A7BE78EC5F3CD688A4328CB021,display=1012,license=%28None%29,subscriptionid=None,productid=LDS,reconnect=1,balance_host=172%2e19%2e3%2e2,encryption_mode=3,images=128M,cache=32M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=thuis,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1024x738x32%2brender,nodelay=1,streaming=1,keyboard=pc102%2fnl%2dbe,geometry=1024x738,link=adsl
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NXNodeExec::exec('startsession', 'user=USER&userip=172%2e19%2e3%2e2&uniqueid=F599D7A7BE78EC5F...', 186.19.3.2, 22) called at handlers/nxserver.pl line 2809
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NXShell::handler_session_start('--link="adsl" --backingstore="1" --streaming="1" --nodelay="1" -...') called at NXShell.pm line 374
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --streaming="1" --nodelay="1" -...') called at NXShell.pm line 145
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) NXShell::run() called at nxserver.pl line 4438
Jul  5 12:55:52 localhost NXSERVER 2.0.0-69[13897]: ERROR: (exception id 82FDEB31) eval {...} called at nxserver.pl line 4397
Jul  5 12:58:09 localhost NXSERVER 2.0.0-69[14075]: WARNING: You appear to run an unsubscribed product. Please visit the 'main::chk_license'
Jul  5 12:58:09 localhost NXSERVER 2.0.0-69[14075]: WARNING: NoMachine Web site at http://www.nomachine.com/ 'main::chk_license'
Jul  5 12:58:09 localhost NXSERVER 2.0.0-69[14075]: WARNING: to purchase a valid subscription. 'main::chk_license'
Jul  5 12:58:10 localhost NXSERVER 2.0.0-69[14075]: User 'USER2' logged in from '186.19.3.2'. 'NXLogin::set'
Jul  5 12:58:10 localhost NXSERVER 2.0.0-69[14075]: Selected node host:localhost (ip: 186.19.3.2) with port:22 'main::selectNode'
Jul  5 12:58:10 localhost NXSERVER 2.0.0-69[14075]: Current selected node: 186.19.3.2 is in status: running  'main::selectNode'
Jul  5 12:58:16 localhost NXNODE 2.0.0-93[14095]: DEBUG: You appear to run an unsubscribed product. Please visit the 'main:nxnode:2513'
Jul  5 12:58:16 localhost NXNODE 2.0.0-93[14095]: DEBUG: NoMachine Web site at http://www.nomachine.com/ 'main:nxnode:2514'
Jul  5 12:58:16 localhost NXNODE 2.0.0-93[14095]: DEBUG: to purchase a valid subscription. 'main:nxnode:2515'
Jul  5 12:58:19 localhost NXSERVER 2.0.0-69[14075]: Session 'ADF17ED137217C74BA3AB681B1E1DD18' started by user 'test'. 'NXShell::handler_session_start'
Jul  5 12:58:19 localhost NXSERVER 2.0.0-69[14075]: User 'USER2' from '186.19.3.2' logged out. 'NXLogin::reset'
Jul  5 12:58:24 localhost NXNODE 2.0.0-93[14095]: INFO: Using port '1013' on node 'matroosje' for session 'unix-gnome'. 'main:nxnode:5420'
Jul  5 12:58:24 localhost NXNODE 2.0.0-93[14095]: INFO: Using host from available host list: '186.19.3.2'. 'main:nxnode:5421'[/php]

first the error from the failed login,
(then the correct login from the second user.)

But I think the important part is this:
```
execution of last command failed [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 last command: **/bin/bash --login -c 'xauth -v source /home/USER/.nx/C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021/scripts/authority'** [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 exit value: 1 [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 stdout:  [eEEE781] 'main:nxnode:2662'
Jul  5 12:55:51 localhost NXNODE 2.0.0-93[13921]: ERROR: NX> 596 stderr: **xauth:  /home/USER/.Xauthority not writable, changes will be ignored **[eEEE781] 'main:nxnode:2662'
```

So, does anybody know what ```
/bin/bash --login -c 'xauth -v source /home/USER/.nx/C-USER-1012-F599D7A7BE78EC5F3CD688A4328CB021/scripts/authority
```

is for?
And why it is looking for 
```
xauth:  /home/USER/.Xauthority
```
I don't have that one, (and why is it not writable, should I create it myself?)

Mind you, I have no idea what is happening, 
what xauth does, 
why it can't create ./Xauthority 
and why it should. 
(So please be patient with me ;))

---

### Post by matrooswolf on 2006-07-06
[QUOTE=kb2wdi]> Cannot create file: /home/USER/.ssh/authorized_keys2:
> Failed to add public key.

try;
sudo chown -R USER:USER ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys2
chmod 644 ~/.ssh/authorized_keys2

It looks like a ssh file permission problem.[/QUOTE]
Hi kb2wdi,
combining the xauth error message (about not being able to create .Xauthority) and your post about file permissions,
I did 
```
sudo chown -R USER:USER /home/USER/.Xauthority
chmod 700 /home/USER/.Xauthority
```

And look you here, I can login! :D :D :D 

I just logged in from my Windows VMWare (I still get some strange effects, but that could be due to Xgl/compiz? , I will look into that later, and try it from my laptop)

So in the end:

is there something wrong with my /home/USER/?
And what are *the correct ownership filepermissions *for it?

(and what did I ever do to mess them up??)

I think I will post this question in another thread as well as this has no longer anything to do with NXserver or key problems ...  (but I will first try to look it up ;))

Thanks everybody for reading!

---

### Post by barbieric on 2006-09-19
I have a similar problem and everything is ok with my default configuration on Ubuntu working like TS server.
But with my client (Ubuntu too) I cannot connect to the server.
After checking configuration, I found a solution.

Simply add the following line to /usr/NX/etc/node.cfg

AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc:/usr/share/X11/fonts/cyrillic:/usr/share/X11/fonts/Type1:/usr/share/X11/fonts/CID:/usr/share/X11/fonts/100dpi:/usr/share/X11/fonts/75dpi:/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType:/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

For more information, look this forum:

[http://www.ubuntuforums.org/showthread.php?t=204976&page=3](http://www.ubuntuforums.org/showthread.php?t=204976&page=3)

I hope this help you.

---

