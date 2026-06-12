---
title: "samba shares - almost there but browser access problems"
date: 2014-12-30
forum: General Help
---

### Post by keith30 on 2014-12-30
I need a bit of help with samba shares. 

I look after a small network in our office of client pc's running Windows 7 and a server running Ubuntu 14.04. This was set up with the help of an acquaintance and was arranged with no security as it was solely an internal network and everyone has the right to access all files on the server. The clients are set up without any login and therefore no passwords and all works fine. I would however now like to introduce some security and have started researching the topic which has thrown up more question than answers! To this end I have set up Ubuntu server on a spare pc for practice purposes with a hostname of testsrv. All pc's have fixed IP's and our main server (192.168.1.114) provides WINS duties to the network. 

Firstly, I am trying to get this spare standalone server to behave in the same manner as our main server which will allow me to tinker without messing up our day to day operations. Whilst I can access my test folder (/rcstest) from the client pc's via network neighbourhood I cannot get to it via web browser such as for CUPS remote administration. I quote below the smb.conf file which I accept may not be perfect but seems to work fine on the main server (changed to take account of the WINS settings and avoid being a master). Is there anything else I should configure on the testsrv? I have modified cupsd.conf to 'allow all' for admin. UFW is not running. Testparm doesn't show any obvious problem other than a warning about security = share being ignored.

```

[global]

 workgroup = WORKGROUP
 netbios name = TESTSRV
 wins server = 192.168.1.114
 name resolve order = wins bcast host lmhosts
 dns proxy = no
 map to guest = bad user
 guest ok = yes
 security = share
 usershare max shares = 50
 usershare allow guests = yes
 

 [rcstest]
 comment = test folder
 path = /srv/rcstest
 browseable = yes
 guest ok = yes
 read only = no
 create mask = 0777
 directory mask = 0777
 writable = yes

```

I can ping 192.169.1.140 (IP of testsrv) from cmd and it responds fine.
I can ping testsrv from cmd and it responds fine.
It doesn't appear under net view. Only the main server does.
nbtstat -c shows both the main server and testsrv
smbtree only shows the main server
I can't access CUPS from a remote browser 192.168.1.140:631
I get no response from a browser when trying IP address or hostname.
 
What am I missing?

---

### Post by bab1 on 2014-12-30
> **keith30 said:**
> I need a bit of help with samba shares. 

I look after a small network in our office of client pc's running Windows 7 and a server running Ubuntu 14.04. This was set up with the help of an acquaintance and was arranged with no security as it was solely an internal network and everyone has the right to access all files on the server. The clients are set up without any login and therefore no passwords and all works fine. I would however now like to introduce some security and have started researching the topic which has thrown up more question than answers! To this end I have set up Ubuntu server on a spare pc for practice purposes with a hostname of testsrv. All pc's have fixed IP's and our main server (192.168.1.114) provides WINS duties to the network. 

Firstly, I am trying to get this spare standalone server to behave in the same manner as our main server which will allow me to tinker without messing up our day to day operations. Whilst I can access my test folder (/rcstest) from the client pc's via network neighbourhood I cannot get to it via web browser such as for CUPS remote administration. I quote below the smb.conf file which I accept may not be perfect but seems to work fine on the main server (changed to take account of the WINS settings and avoid being a master). Is there anything else I should configure on the testsrv? I have modified cupsd.conf to 'allow all' for admin. UFW is not running. Testparm doesn't show any obvious problem other than a warning about security = share being ignored.

```

[global]

 workgroup = WORKGROUP
 netbios name = TESTSRV
 wins server = 192.168.1.114
 name resolve order = wins bcast host lmhosts
 dns proxy = no
 map to guest = bad user
 guest ok = yes
 security = share
 usershare max shares = 50
 usershare allow guests = yes
 

 [rcstest]
 comment = test folder
 path = /srv/rcstest
 browseable = yes
 guest ok = yes
 read only = no
 create mask = 0777
 directory mask = 0777
 writable = yes

```

I can ping 192.169.1.140 (IP of testsrv) from cmd and it responds fine.
I can ping testsrv from cmd and it responds fine.
It doesn't appear under net view. Only the main server does.
nbtstat -c shows both the main server and testsrv
smbtree only shows the main server
I can't access CUPS from a remote browser 192.168.1.140:631
I get no response from a browser when trying IP address or hostname.
 
What am I missing?

It sounds like you have 3 problems.  Browsing shares, Samba user security and CUPS printer administration.  CUPS is has nothing to do with Samba browsing or user security.  

Security in general has to parts;  _Authentication_ (who are you) and *Authorization* (permission to do that).   Samba's most basic user security is  set with *security = user in the global section of the smb.conf file.  At the very minimum you need to set up user accounts on the Samba server for different users.  This means a Linux account (adduser) and a Samba user (smbpasswd -a) for each user.  The directory you are sharing shuld have the ownership and permissions set so that only the users you what to have access access the share are allowed.

Browsing problems are usually due to name services not working correctly.  There are no simple answers here.  I'd set up the name services first.  Let's start with some diagnosis.  From the host **testsrv**, post the output of these 2 commands

```
testparm -s

smbtree -d3
```

---

### Post by keith30 on 2014-12-31
Thanks for your response.

I have made some progress :) I found my  /etc/hosts file did not have 192.168.1.140 testsrv in it. After  changing that I could get to CUPS via remote browser. I still do not get  a response from entering the IP address or testsrv in the browser  address bar though.

Here is the output from testparm -s

```

WARNING: Ignoring invalid value 'share' for parameter 'security'
Processing section "[rcstest]"
Loaded services file OK
Server role: ROLE_STANDALONE

[global]

 map to guest = bad user
 name resolve order = wins bcast host lmhosts
 dns proxy = no
 wins server = 192.168.1.114
 usershare allow guests = yes
 usershare max shares = 50
 idmap config * : backend = tdb
 guest ok = yes
 

 [rcstest]
 comment = test folder
 path = /srv/rcstest
 read only = no
 create mask = 0777
 directory mask = 0777
 

```

Some security questions:
When adding security I will need all clients to have access to all files on the server. 
Therefore, do I just need one linux user and then a samba user for each client pc and 
make the samba users members of a group with required access permissions?
Or do I need a Linux user and a samba user for each client? Presumably whichever way I will need to 
set up a user name with password on each windows client pc.

I will post the output of smbtree -d3 once I work out how to capture the text from the CLI.

---

### Post by bab1 on 2014-12-31
> **keith30 said:**
> 
I still do not get  a response from entering the IP address or testsrv in the browser address bar though.

Can you be a little more specific about this?  What browser are you referring to?
> 

Some security questions:
When adding security I will need all clients to have access to all files on the server. 
Therefore, do I just need one linux user and then a samba user for each client pc and 
make the samba users members of a group with required access permissions?

Or do I need a Linux user and a samba user for each client? Presumably whichever way I will need to 
set up a user name with password on each windows client pc.

I will post the output of smbtree -d3 once I work out how to capture the text from the CLI.

Typically a Linux Systems Administrator uses terms such as: a client is an application that requests services of a Server (in this case the Samba server).  This is not a human or a host (computer).  A host is the real machine (running OS).  The user has an account on a host.

When you add users you are not adding security per se.  The configuration of the user account is what provides some of the security.  The file system configuration and Samba share definition adds more security.  In any event if you want both Linux and Samba to identify specific users (login), allow certain operations (read, write, execute) and account for these users (auth.log) then the user (human) needs to have a user account (Linux) and a listing in the Samba users database (Samba user) on the Linux machine (in your case testsrv).  Security is a mindset.  I want each user to ID themselves and be granted certain permissions.  There is no need for any security if you are not interested in securing a user from others in the first place.  I would have each user have an account on all the clients and one on the server with matching  login and password to start with.  If you want these users to have a share that is public (available to all) then you need to configure the file system for that and add the users to a common group.

What is the goal in doing what you propose?  There is no reason to have any security if you aren't going to have separate accounts and file system security.

One way to capture the data is to re-direct the output to a text file with this command.```
smbtree -d3 > tree.txt
```...you should see the file in your home directory,

---

### Post by keith30 on 2015-01-01
Happy New Year, and thanks once again for your help.

> **bab1 said:**
> Can you be a little more specific about this?  What browser are you referring to?

I am using Firefox on a client PC. If I enter 'server' or 192.168.1.114 in the address bar I get directed to a default apache success page on our main server. If I do the same with 'testsrv' or 192.168.1.140 I get a Firefox message saying 'source not available' or words to that effect. Going back to the general browsing issue, the new testsrv does not automatically appear in the Win7 network neighbourhood. However, if I enter \\testsrv in the address bar of windows explorer it will find the shared file 'rcstest' and then show the testsrv in the network neighbourhood for the remainder of that session. Similarly testsrv does not appear under net view from cmd, but it will appear and show the share with the command 'net view testsrv'. This obviously isn't a major issue, but I would like to understand why it does not appear automatically under network neighbourhood.

> **bab1 said:**
> 
What is the goal in doing what you propose?  There is no reason to have any security if you aren't going to have separate accounts and file system security.


In due course I will need to separate some shares out from general access and only permit certian client pc's to view them. I am just making early preparations and trying to learn the systems in advance.

I will post the output of smbtree when I am next back at work. However, it only lists the shares on the main server not this testsrv. Interestingly, the testsrv does not show on the network tab when using the Files GUI I have on the main Linux server. It is as if the testsrv is hiding it's presence even though browseable = yes is in the samba.conf

---

### Post by SeijiSensei on 2015-01-01
1) The older server must be running a copy of the Apache or nginx web servers.  That's why you get the default "It works!" page.  This has nothing to do with Samba or CUPS.  If you installed a copy of Apache on testsrv, you'd get the same behavior.

2) I didn't see a "workgroup" directive in your configuration above.  You should add the entry
```
workgroup = SOMEGROUP
```
replacing "SOMEGROUP" with the workgroup the Windows machines all belong to.  That should help with making testsrv appear in Network Neighborhood.

Like bab1, I'm not sure why you are going to all this trouble if all users will have full access to the exported shares.  Just make the shares public, or use the "force user" and "force group" directives to have all files owned by a single common Unix user.

---

### Post by keith30 on 2015-01-01
Thanks for your comments SeijiSensei. The older server does in fact have apache so that would explain that one.

My global stanza does have workgroup = WORKGROUP (see my OP) for some reason it doesn't show when doing testparm. I still don't understand why it doesn't show by default under network neighbourhood though.

As stated I will need to provide some secure shares in due course hence my need to get to grips with this security malarkey.

---

### Post by SeijiSensei on 2015-01-01
Are you sure the "workgroup = WORKGROUP" line is in the [global] section of smb.conf?  That's where it is in my smb.conf file, and testparm shows it along with everything else in [global].

---

### Post by bab1 on 2015-01-01
> **SeijiSensei said:**
> Are you sure the "workgroup = WORKGROUP" line is in the [global] section of smb.conf?  That's where it is in my smb.conf file, and testparm shows it along with everything else in [global].

The testparm command doesn't always show the *default parameters*.  See below from the man pages```
testparm is a very simple test program to check an smbd(8) configuration file for internal correctness. 
```

If you want to see every parameter that smbd is using then you this```
teastparm -sv
```... the workgroup will show up.

The web server is just a distraction to the issue.

---

### Post by bab1 on 2015-01-01
> **keith30 said:**
> 
In due course I will need to separate some shares out from general access and only permit certian client pc's to view them. I am just making early preparations and trying to learn the systems in advance.


PC's don't view anything.  Users via there user accounts access Samba shares.  What preparation is there?  you either institute security or forget all about it.  Maybe a basic UNIX/Linux course would be helpful for your future endeavors.  > 

I will post the output of smbtree when I am next back at work. However, it only lists the shares on the main server not this testsrv. Interestingly, the testsrv does not show on the network tab when using the Files GUI I have on the main Linux server. It is as if the testsrv is hiding it's presence even though browseable = yes is in the samba.conf
Browsing needs to be configured at the server level before you can turn it on or off at the share level.  You have a basic name service problem.  The command smbtree will show us all. 
> As stated I will need to provide some secure shares in due course hence my need to get to grips with this security malarkey
When I see this I have to think that If you think security is "malarkey" then you are doomed before you start.  Once again; why make any effort to secure the data if you don't care?

---

### Post by keith30 on 2015-01-02
SeijiSensei
Yes, i can confirm that Workgroup is in the smb.conf file. It shows up when running Testparm -sv.

BAB1
Perhaps I chose the wrong word 'malarkey'. I am serious about trying to understand this. I obviously also mis-stated myself when saying that I wanted to restrict access from certain PC's. I obviously should have said Users. In my office, each person has their own PC and I mentally connect Users synonymously with PC's. 

I have tried to run smbtree -d3 and log the output but it hangs on screen after the line where it says Processing section [global] Added interface Eth0. At this point I can hit return and it will continue but it only logs the following to the log file and not the rest of the text which comes up on screen. The next line states 'could not open file /var/cache/samba/gencache.tdb permission denied'. If I run smbtree -d3 without the > log.txt I get asked for my password at this point.

```

Enter root's password: 
WORKGROUP
    
\\SERVER                 
        
\\SERVER\Brother-HL-5150D-series    Brother HL-5150D series
        
\\SERVER\DYMO-LabelWriter-330-Turbo    DYMO LabelWriter 330 Turbo
        
\\SERVER\SHARP-MX-2600N     SHARP MX-2600N
        
\\SERVER\print$             Printer Drivers
        
\\SERVER\rcs                RCS files
        
\\SERVER\users              Users Directories
        
\\SERVER\templates          Templates
        
\\SERVER\dictation          Dictation Files
        
\\SERVER\software           Software Files
        
\\SERVER\JRVS               JRVS Files
        
\\SERVER\IPC$               IPC Service ()

```

---

### Post by bab1 on 2015-01-02
> **keith30 said:**
> SeijiSensei
Yes, i can confirm that Workgroup is in the smb.conf file. It shows up when running Testparm -sv.

Linux is case sensitive.  The term [COLOR="#0000FF"]**Testparm**[/COLOR] is not the same as [COLOR="#008000"]**testparm**[/COLOR]. 
> 

BAB1
Perhaps I chose the wrong word 'malarkey'. I am serious about trying to understand this. I obviously also mis-stated myself when saying that I wanted to restrict access from certain PC's. I obviously should have said Users. In my office, each person has their own PC and I mentally connect Users synonymously with PC's. 

You are only as you speak.  We don't know you except for how you present yourself in the printed word.
> 

I have tried to run smbtree -d3 and log the output but it hangs on screen after the line where it says Processing section [global] Added interface Eth0. At this point I can hit return and it will continue but it only logs the following to the log file and not the rest of the text which comes up on screen. The next line states 'could not open file /var/cache/samba/gencache.tdb permission denied'. If I run smbtree -d3 without the > log.txt I get asked for my password at this point.


We need the error codes; don't we?  Run* smbtree -d3 *from the terminal of  testsev and scroll backwards to get all the information.  It's not hanging.  It's waiting for the users input and that is stopping the logging of all of the output.

---

### Post by keith30 on 2015-01-05
Thanks again for your continued support.

I cannot work out what 'user input' is required to get smbtree to proceed past the 'added interface' line when logging the output to file. It works fine on screen without the > option as it asks for a password which I duly type in. 

When using the > option I get no request for a password, but if I press enter or type my password when it  'hangs' the output continues on screen but the log file only shows the  shares from the server as listed below.

```

Enter root's password: 
WORKGROUP
    
\\SERVER                 
\\SERVER\Brother-HL-5150D-series    Brother HL-5150D series
\\SERVER\DYMO-LabelWriter-330-Turbo    DYMO LabelWriter 330 Turbo
\\SERVER\SHARP-MX-2600N     SHARP MX-2600N
\\SERVER\print$             Printer Drivers
\\SERVER\rcs                RCS files
\\SERVER\users              Users Directories
\\SERVER\templates          Templates
\\SERVER\dictation          Dictation Files
\\SERVER\software           Software Files
\\SERVER\JRVS               JRVS Files
\\SERVER\IPC$               IPC Service ()

```

As a result I have had to copy the text by hand from the screen - so here it is.

```

tester@testsrv:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process( ) &#8211; Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.140 bcast=192.168.1.255 netmask=255.255.255.0
Enter tester's password:
tdb(/var/cache/samba/genache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL*_DEL EBADF for fde[0x7fd098e59930] mpx_fde[(nil)] fd[7] &#8211; disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal &#8211; Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fd098e6c2b0] mpx_fde[(nil)] fd[9] &#8211; disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal &#8211; Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
            \\SERVER
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_FRC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal &#8211; Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
            \\SERVER\Brother-HL-5150D-series                Brother HL-5150D series
            \\SERVER\DYMO-LabelWriter-330-Turbo                   DYMO LabelWriter 330 Turbo
\\SERVER\SHARP-MS-26001N                            SHARP MX-2600N
\\SERVER\print$                                                          Printer Drivers
\\SERVER\rcs                                                              RCS Files
\\SERVER\users                                                           Users Directories
\\SERVER\templates                                                    Templates
\\SERVER\dictation                                                      Dictation Files
\\SERVER\software                                                     Software Files
            \\SERVER\JRVS                                                         JRVS Files
            \\SERVER\IPC$                                                          IPC Service ( )
tester@testsrv:~$ _

```

For reference this TESTSRV is on the same network, subnet and workgroup as the SERVER with the SERVER acting as a WINS server. Both TESTSRV and SERVER are being used as file servers only. Neither are web hosts or set up as any kind of domain.

Thanks Keith

---

### Post by Holger_Gehrke on 2015-01-05
> **keith30 said:**
> 
I cannot work out what 'user input' is required to get smbtree to proceed past the 'added interface' line when logging the output to file. It works fine on screen without the > option as it asks for a password which I duly type in. 

When using the > option I get no request for a password, but if I press enter or type my password when it  'hangs' the output continues on screen but the log file only shows the  shares from the server as listed below.


The 'user input' ? That should be the password, shouldn't it ...

'>' is not an option, it's a redirection. Redirections are processed by the shell **before** the program is even started and programs must do quite a bit of extra work to find out whether or not their output has been redirected. '>' sends all output to the file named after the '>', including the request for the password.

You can either give the option ```

--user=username%password
or
 --no-pass
```
 to smbtree then it won't wait for you to enter a password.

By the way, error messages do not get sent to 'standard output', they get sent to 'standard error output'. So if you want to capture everything including error messages to a file you would do something like '> outputfile 2>&1' which first redirects standard output and then sends standard error to wherever standard out has been sent.

---

### Post by bab1 on 2015-01-05
> **keith30 said:**
> Thanks again for your continued support.

I cannot work out what 'user input' is required to get smbtree to proceed past the 'added interface' line when logging the output to file. It works fine on screen without the > option as it asks for a password which I duly type in. 

When using the > option I get no request for a password, but if I press enter or type my password when it  'hangs' the output continues on screen but the log file only shows the  shares from the server as listed below.

```

Enter root's password: 
WORKGROUP
    
\\SERVER                 
\\SERVER\Brother-HL-5150D-series    Brother HL-5150D series
\\SERVER\DYMO-LabelWriter-330-Turbo    DYMO LabelWriter 330 Turbo
\\SERVER\SHARP-MX-2600N     SHARP MX-2600N
\\SERVER\print$             Printer Drivers
\\SERVER\rcs                RCS files
\\SERVER\users              Users Directories
\\SERVER\templates          Templates
\\SERVER\dictation          Dictation Files
\\SERVER\software           Software Files
\\SERVER\JRVS               JRVS Files
\\SERVER\IPC$               IPC Service ()

```

As a result I have had to copy the text by hand from the screen - so here it is.

```

tester@testsrv:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process( ) – Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.140 bcast=192.168.1.255 netmask=255.255.255.0
Enter tester's password:
tdb(/var/cache/samba/genache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL*_DEL EBADF for fde[0x7fd098e59930] mpx_fde[(nil)] fd[7] – disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal – Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fd098e6c2b0] mpx_fde[(nil)] fd[9] – disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal – Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
            \\SERVER
resolve_wins: using WINS server 192.168.1.114 and tag '*'
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_FRC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal – Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
            \\SERVER\Brother-HL-5150D-series                Brother HL-5150D series
            \\SERVER\DYMO-LabelWriter-330-Turbo                   DYMO LabelWriter 330 Turbo
\\SERVER\SHARP-MS-26001N                            SHARP MX-2600N
\\SERVER\print$                                                          Printer Drivers
\\SERVER\rcs                                                              RCS Files
\\SERVER\users                                                           Users Directories
\\SERVER\templates                                                    Templates
\\SERVER\dictation                                                      Dictation Files
\\SERVER\software                                                     Software Files
            \\SERVER\JRVS                                                         JRVS Files
            \\SERVER\IPC$                                                          IPC Service ( )
tester@testsrv:~$ _

```

For reference this TESTSRV is on the same network, subnet and workgroup as the SERVER with the SERVER acting as a WINS server. Both TESTSRV and SERVER are being used as file servers only. Neither are web hosts or set up as any kind of domain.

Thanks Keith

It appears that TESTSRV does not have the proper Samba daemons (servers) running at all.  Post the output of these commands from the TESTSRV command line```
pgrep -l mbd

pgrep -l samba
```

You don't need to use redirect to a text file.  You can should be able to highlight the output on the screen and copy it to an open text file.

---

### Post by keith30 on 2015-01-05
> **Holger_Gehrke said:**
> 

You can either give the option ```

--user=username%password
or
 --no-pass
```
 to smbtree then it won't wait for you to enter a password.

So if you want to capture everything including error messages to a file  you would do something like '> outputfile 2>&1' which first  redirects standard output and then sends standard error to wherever  standard out has been sent.

Aha, that makes life a bit simpler and saves my fingers a little.

> **bab1 said:**
> It appears that TESTSRV does not have the proper Samba daemons (servers) running at all.  Post the output of these commands from the TESTSRV command line```
pgrep -l mbd

pgrep -l samba
```

You don't need to use redirect to a text file.  You can should be able to highlight the output on the screen and copy it to an open text file.

Will do. 

I didn't realise it was possible to highlight text from the command line and paste it into an open text editor. I will have to research that.

---

### Post by keith30 on 2015-01-06
pgrep -l mbd gives me:-

599 smbd
756 smbd
938 nmbd

pgrep -l samba gives nothing.

---

### Post by bab1 on 2015-01-06
> **keith30 said:**
> pgrep -l mbd gives me:-

599 smbd
756 smbd
938 n
pgrep -l samba gives nothing.

The pgrep of samba is correct.  That means the AD-DC samba daemon is not running and that is as it should be.

The pgrep of the smbd and nmbd is also corredt as the standalone Samba server uses smbd and nmbd to function correctly.  But you shuld also see this host in the smbtree output.  So either you have not sent all the data or something is very wrong with your configuration.

Lets see if you can get anything out of the server at all.  From the command line of the host TESTSRV, post the output of this command```
nmblookup testsrv
```

---

### Post by keith30 on 2015-01-07
nmblookup responds with 192.168.1.114 testsrv<00>

I don't know whether it is relevant, but when booting up this machine it shows the scrolling list of services that it is starting and I noticed the line 'Starting SMB/CIFS file and Active Directory Server' is in twice with [ok] against the first and [fail] against the second.

---

### Post by bab1 on 2015-01-08
> **keith30 said:**
> nmblookup responds with 192.168.1.114 testsrv<00>

This is both good and bad.  To the good, It means the server is broadcasting its presense on the network via NETBIOS.  It's bad in that the address it is announcing not it's own.  Isn't 192.168.1.114 the iP address of the host SERVER?> 

I don't know whether it is relevant, but when booting up this machine it shows the scrolling list of services that it is starting and I noticed the line 'Starting SMB/CIFS file and Active Directory Server' is in twice with [ok] against the first and [fail] against the second.
No it's not relevent to your problem.  As a stand alone server (not a ad-dc at all) the daemons that need to be running are 2 *smbd* and 1 *nmbd*.  We checked with pgrep and that is what you have rounning.

Your problem is really in the configuration of this standalone Samba server.  I'm pragmatic about these kinds of things so I don't really spend a lot of time searching for the why/where and how of a bad configuration.  I would just replace the smb.conf you are using with the original smb.conf and start over.  I would also not use WINS on a simple 1 segment (IP range) network.  WINS is not needed for your network at all.  We don't need to dump WINS just yet.  We can work with just the TESTSRV host with the no WINS for right now.

The bottom line is: We start over with the original smb.conf file.  The only change you need to make is adding the NETBIOS NAME with```
 netbios name = TESTSRV
``` .... and adding your shares at the bottom of the file.

Post the contents of the new smb.conf file using this comand```
cat /etc/samba/smb.conf
```

---

### Post by keith30 on 2015-01-09
Firstly I must apologise if I've wasted any of your time. For some reason I posted the wrong result from nmblookup. It does indeed return the correct IP address of 192.168.1.140. Quite why I typed in the SERVER IP I have no idea, although I had been comparing results from running the same tests on SERVER and must have got myself muddled.

That aside, I have replaced the smb.conf with the original and made the 2 changes you note. Nothing seems to have changed. I can still access the shared folder from my Windows workstations, but as before it does not appear automatically under network neighbourhood. I still have to type \\testsrv in the address bar at the top after which it will then remain under the network tab for the remainder of that session. I also cannot see the TESTSRV from the file manager (nautilus?) on SERVER. The only devices it shows under network are itself and the Windows workgroup.

Thanks for your ongoing help and suggestions.

```

#

# Sample configuration file for the Samba suite for Debian GNU/Linux.

#

#

# This is the main Samba configuration file. You should read the

# smb.conf(5) manual page in order to understand the options listed

# here. Samba has a huge number of configurable options most of which 

# are not shown in this example

#

# Some options that are often worth tuning have been included as

# commented-out examples in this file.

#  - When such options are commented with ";", the proposed setting

#    differs from the default Samba behaviour

#  - When commented with "#", the proposed setting is the default

#    behaviour of Samba but the option is considered important

#    enough to be mentioned here

#

# NOTE: Whenever you modify this file you should run the command

# "testparm" to check that you have not made any basic syntactic 

# errors. 



#======================= Global Settings =======================


[global]



## Browsing/Identification###



# Change this to the workgroup/NT-domain name your Samba server will part of
   
   workgroup = WORKGROUP

   
   netbios name = TESTSRV



# server string is the equivalent of the NT Description field
    
   server string = %h server (Samba, Ubuntu)



# Windows Internet Name Serving Support Section:

# WINS Support - Tells the NMBD component of Samba to enable its WINS Server

#   wins support = no



# WINS Server - Tells the NMBD components of Samba to be a WINS Client

# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both

;   wins server = w.x.y.z



# This will prevent nmbd to search for NetBIOS names through DNS.
   
   dns proxy = no



#### Networking #### 



# The specific set of interfaces / networks to bind to

# This can be either the interface name or an IP address/netmask;

# interface names are normally preferred

;   interfaces = 127.0.0.0/8 eth0



# Only bind to the named interfaces and/or networks; you must use the

# 'interfaces' option above to use this.

# It is recommended that you enable this feature if your Samba machine is

# not protected by a firewall or is a firewall itself.  However, this

# option cannot handle dynamic or non-broadcast interfaces correctly.

;   bind interfaces only = yes





#### Debugging/Accounting ####



# This tells Samba to use a separate log file for each machine

# that connects
   
   log file = /var/log/samba/log.%m



# Cap the size of the individual log files (in KiB).
   
   max log size = 1000



# If you want Samba to only log through syslog then set the following

# parameter to 'yes'.

#   syslog only = no



# We want Samba to log a minimum amount of information to syslog. Everything

# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log

# through syslog you should set the following parameter to something higher.
   
   syslog = 0



# Do something sensible when Samba crashes: mail the admin a backtrace
   
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######



# Server role. Defines in which mode Samba will operate. Possible

# values are "standalone server", "member server", "classic primary

# domain controller", "classic backup domain controller", "active

# directory domain controller". 

#

# Most people will want "standalone sever" or "member server".

# Running as "active directory domain controller" will require first

# running "samba-tool domain provision" to wipe databases and create a

# new domain.
   
   server role = standalone server



# If you are using encrypted passwords, Samba will need to know what

# password database type you are using.  
   
   passdb backend = tdbsam

 
  
   obey pam restrictions = yes



# This boolean parameter controls whether Samba attempts to sync the Unix

# password with the SMB password when the encrypted SMB password in the

# passdb is changed.
   
   unix password sync = yes



# For Unix password sync to work on a Debian GNU/Linux system, the following

# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for

# sending the correct chat script for the passwd program in Debian Sarge).
   
   passwd program = /usr/bin/passwd %u
   
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .



# This boolean controls whether PAM will be used for password changes

# when requested by an SMB client instead of the program listed in

# 'passwd program'. The default is 'no'.
   
   pam password change = yes



# This option controls how unsuccessful authentication attempts are mapped

# to anonymous connections
   map to guest = bad user



########## Domains ###########

#


# The following settings only takes effect if 'server role = primary

# classic domain controller', 'server role = backup domain controller'

# or 'domain logons' is set 

#


# It specifies the location of the user's

# profile directory from the client point of view) The following

# required a [profiles] share to be setup on the samba server (see
# below)

;   logon path = \\%N\profiles\%U


# Another common choice is storing the profile in the user's home directory

# (this is Samba's default)

#   logon path = \\%N\%U\profile



# The following setting only takes effect if 'domain logons' is set

# It specifies the location of a user's home directory (from the client
# point of view)

;   logon drive = H:

#   logon home = \\%N\%U



# The following setting only takes effect if 'domain logons' is set

# It specifies the script to run during logon. The script must be stored

# in the [netlogon] share

# NOTE: Must be store in 'DOS' file format convention

;   logon script = logon.cmd



# This allows Unix users to be created on the domain controller via the SAMR

# RPC pipe.  The example command creates a user account with a disabled Unix

# password
; please adapt to your needs

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u



# This allows machine accounts to be created on the domain controller via the 

# SAMR RPC pipe.  

# The following assumes a "machines" group exists on the system

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u



# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  

; add group script = /usr/sbin/addgroup --force-badname %g



############ Misc ############



# Using the following line enables you to customise your configuration

# on a per machine basis. The %m gets replaced with the netbios name

# of the machine that is connecting

;   include = /home/samba/etc/smb.conf.%m



# Some defaults for winbind (make sure you're not using the ranges

# for something else.)

;   idmap uid = 10000-20000

;   idmap gid = 10000-20000

;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders


# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.

;   usershare max shares = 100



# Allow users who've been granted usershare privileges to create

# public shares, not just authenticated ones
   
usershare allow guests = yes



#======================= Share Definitions =======================



# Un-comment the following (and tweak the other settings below to suit)

# to enable the default home directory shares. This will share each

# user's home directory as \\server\username

;[homes]

;   comment = Home Directories

;   browseable = no



# By default, the home directories are exported read-only. Change the

# next parameter to 'no' if you want to be able to write to them.

;   read only = yes



# File creation mask is set to 0700 for security reasons. If you want to

# create files with group=rw permissions, set next parameter to 0775.

;   create mask = 0700



# Directory creation mask is set to 0700 for security reasons. If you want to

# create dirs. with group=rw permissions, set next parameter to 0775.

;   directory mask = 0700



# By default, \\server\username shares can be connected to by anyone

# with access to the samba server.

# Un-comment the following parameter to make sure that only "username"

# can connect to \\server\username

# This might need tweaking when using external authentication schemes

;   valid users = %S



# Un-comment the following and create the netlogon directory for Domain Logons

# (you need to configure Samba to act as a domain controller too.)
;[netlogon]

;   comment = Network Logon Service

;   path = /home/samba/netlogon

;   guest ok = yes
;   read only = yes



# Un-comment the following and create the profiles directory to store

# users profiles (see the "logon path" option above)

# (you need to configure Samba to act as a domain controller too.)

# The path below should be writable by all users so that their

# profile directory may be created the first time they log on

;[profiles]

;   comment = Users profiles

;   path = /home/samba/profiles

;   guest ok = no

;   browseable = no

;   create mask = 0600

;   directory mask = 0700



[printers]
   
   comment = All Printers
   
   browseable = no
   
   path = /var/spool/samba
   
   printable = yes
   
   guest ok = no
   
   read only = yes
   
   create mask = 0700



# Windows clients look for this share name as a source of downloadable

# printer drivers
[print$]
   
   comment = Printer Drivers
   
   path = /var/lib/samba/printers
   
   browseable = yes
   
   read only = yes
   
   guest ok = no


# Uncomment to allow remote administration of Windows print drivers.

# You may need to replace 'lpadmin' with the name of the group your

# admin users are members of.

# Please note that you also need to set appropriate Unix permissions

# to the drivers directory for these users to have write rights in it

;   write list = root, @lpadmin



[rcstest share]
   
   comment = test folder
   
   path = /srv/rcstest
   
   browseable = yes
   
   guest ok = yes
   
   read only = no
   
   create mask = 0777
   
   directory mask = 0777
   
   writable = yes



```

---

### Post by bab1 on 2015-01-09
> **keith30 said:**
> Firstly I must apologise if I've wasted any of your time. For some reason I posted the wrong result from nmblookup. It does indeed return the correct IP address of 192.168.1.140. Quite why I typed in the SERVER IP I have no idea, although I had been comparing results from running the same tests on SERVER and must have got myself muddled.

It happens to all of us at one time or another.  Sometimes I write out what I expect to see and compare that to what I actually see.  If I have 2 terminal windows open I change the color on one of them.  All of this is to keep me straight as to what I'm looking at and the answer is what I expect.
> 
That aside, I have replaced the smb.conf with the original and made the 2 changes you note. Nothing seems to have changed. I can still access the shared folder from my Windows workstations, but as before it does not appear automatically under network neighbourhood. I still have to type \\testsrv in the address bar at the top after which it will then remain under the network tab for the remainder of that session. I also cannot see the TESTSRV from the file manager (nautilus?) on SERVER. The only devices it shows under network are itself and the Windows workgroup.

Thanks for your ongoing help and suggestions.

I don't ave any Windows clients running at the moment so I'm guessing a bit here.  There is a setting in Windows to allow NETBIOS over TCP (NBT).  You should make sure that you have NBT turned on.  Also you should click on the "Windows Network".  It should show you all the machines.  If you have multiple workgroups you can drill down to fne the machine you are looking for.

Let's see what TESTSRV shows when you do this command (again)```
smbtree -d3
```

---

### Post by keith30 on 2015-01-12
I've checked that my Netbios over TCP/IP is set to on; which it is. Enable LMHOSTS lookup is turned off. (My Windows clients are all set to use WINS and are pointing to the SERVER 192.168.1.114 for this).

I have run smbtree -d3 --no-pass <filename> 2>&1 on TESTSRV which gives the following


```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.140 bcast=192.168.1.255 netmask=255.255.255.0
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fcb059778f0] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fcb0598a230] mpx_fde[(nil)] fd[9] - disabling
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\SERVER                 
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER<0x20>
resolve_hosts: getaddrinfo failed for name SERVER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SERVER<0x20>
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\SERVER\Brother-HL-5150D-series    Brother HL-5150D series
        \\SERVER\DYMO-LabelWriter-330-Turbo    DYMO LabelWriter 330 Turbo
        \\SERVER\SHARP-MX-2600N     SHARP MX-2600N
        \\SERVER\print$             Printer Drivers
        \\SERVER\rcs                RCS files
        \\SERVER\users              Users Directories
        \\SERVER\templates          Templates
        \\SERVER\dictation          Dictation Files
        \\SERVER\software           Software Files
        \\SERVER\JRVS               JRVS Files
        \\SERVER\IPC$               IPC Service ()


```

TESTSRV still does not show under Windows Network (Network Map). And in Windows Explorer it does not show unless I first 'find' it using the address bar and entering \\testsrv.

---

### Post by bab1 on 2015-01-12
> **keith30 said:**
> I've checked that my Netbios over TCP/IP is set to on; which it is. Enable LMHOSTS lookup is turned off. (My Windows clients are all set to use WINS and are pointing to the SERVER 192.168.1.114 for this).

I have run smbtree -d3 --no-pass <filename> 2>&1 on TESTSRV which gives the following


```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.140 bcast=192.168.1.255 netmask=255.255.255.0
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fcb059778f0] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fcb0598a230] mpx_fde[(nil)] fd[9] - disabling
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\SERVER                 
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER<0x20>
resolve_hosts: getaddrinfo failed for name SERVER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SERVER<0x20>
Got a positive name query response from 192.168.1.114 ( 192.168.1.114 )
Connecting to 192.168.1.114 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\SERVER\Brother-HL-5150D-series    Brother HL-5150D series
        \\SERVER\DYMO-LabelWriter-330-Turbo    DYMO LabelWriter 330 Turbo
        \\SERVER\SHARP-MX-2600N     SHARP MX-2600N
        \\SERVER\print$             Printer Drivers
        \\SERVER\rcs                RCS files
        \\SERVER\users              Users Directories
        \\SERVER\templates          Templates
        \\SERVER\dictation          Dictation Files
        \\SERVER\software           Software Files
        \\SERVER\JRVS               JRVS Files
        \\SERVER\IPC$               IPC Service ()


```

TESTSRV still does not show under Windows Network (Network Map). And in Windows Explorer it does not show unless I first 'find' it using the address bar and entering \\testsrv.

Pretty perplexing.  It appears that the host TESTSRV can't even see itself. I does add the interface for TESTSRV```
added interface eth0 ip=192.168.1.140 bcast=192.168.1.255 netmask=255.255.255.0
``` No other response is added to the output.  

I think the next step is to turn off the WINS server on the host SERVER or shutting down the host itself.  Then retest the smbtree command at TESTSRV.  If this doesn't provide any useful response then I would seriously consider purging and reinstalling Samba on TESTSRV.

---

### Post by keith30 on 2015-01-14
I've managed a brief bit of testing this morning and disconnected the SERVER from the network. I then fired up just the TESTSRV and one Win7 PC (with WINS settings removed from TCP/IP settings). The TESTSRV showed up nicely on the client and when running smbclient -L testsrv it showed itself as the master browser. It would seem as thought the WINS bit is causing problems with TESTSRV. When I get a chance I will do the same again but run smbtree -d3 as you suggested.

Assuming it is WINS issues, what settings should I have in SERVER smb.conf to set it as master browser and not use WINS? The reason I originally ended up using WINS was because of problems getting the Windows clients to see the SERVER when we first set it up. 

Another quick side issue. I appear to have 4 users on the SERVER when I run pdbedit -L namely:
nobody:65534:nobody
keith:4294967295:keith
root:0:root
reynolds:1001:

My main login is as user reynolds. Presumably I could delete keith and nobody as these are not used. Is it normal to have root listed too?

I may end up changing smb.conf to user=share at which point I understand I will need map to guest= Bad User to allow unrestricted access from client pc's without the need for a password. If I do this I presume I will need to create (or keep) a user nobody with appropriate permissions.

---

### Post by bab1 on 2015-01-14
> **keith30 said:**
> I've managed a brief bit of testing this morning and disconnected the SERVER from the network. I then fired up just the TESTSRV and one Win7 PC (with WINS settings removed from TCP/IP settings). The TESTSRV showed up nicely on the client and when running smbclient -L testsrv it showed itself as the master browser. It would seem as thought the WINS bit is causing problems with TESTSRV. When I get a chance I will do the same again but run smbtree -d3 as you suggested.

Assuming it is WINS issues, what settings should I have in SERVER smb.conf to set it as master browser and not use WINS? The reason I originally ended up using WINS was because of problems getting the Windows clients to see the SERVER when we first set it up. 

YOu do not set a Master Browser (MB).  It is detirmined by election between all the SMB capable hosts.  When a host that is a MB goes off line a new MB is elected.  The MB function continues on that host until it goes off line.  The only thing you need to do is comment out the WINS lines in the host Server smb.conf file.  I define the netbios name and set the name resolution order in the global section of the smb.conf file like this```

# Use your server server name were you see <SERVER_NAME>
netbios name = <SERVER_NAME>

name resolve order = bcast

```
> 

Another quick side issue. I appear to have 4 users on the SERVER when I run pdbedit -L namely:
nobody:65534:nobody
keith:4294967295:keith
root:0:root
reynolds:1001:

My main login is as user reynolds. Presumably I could delete keith and nobody as these are not used. Is it normal to have root listed too?

I may end up changing smb.conf to user=share at which point I understand I will need map to guest= Bad User to allow unrestricted access from client pc's without the need for a password. If I do this I presume I will need to create (or keep) a user nobody with appropriate permissions.

Root never needs to be in the Samba user database.  The user keith is not using a legitamate uid so it should be deleted also.  I would leave the user nobody as it is the anonymous (guest) user  as you have pointed out.  The user nobody is a system user with no real abilties.

Somewhere along the line you will find that WINS is not functioning correctly or misconfigured or missapplied.  You don't need it in a singel segment network anyway.  It is only needed when you have multiple segments of your LAN (i.e. subnets).

---

### Post by keith30 on 2015-01-16
Thank you BAB1. Whilst my original problem hasn't been resolved I've learnt alot through the processes of testing with your input and found ways to achieve my aims. In due course I will remove the WINS server on SERVER and introduce some secure user shares where required. I very much appreciate your committed help.

---

