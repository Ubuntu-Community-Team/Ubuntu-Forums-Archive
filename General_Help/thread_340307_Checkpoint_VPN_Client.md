---
title: "Checkpoint VPN Client"
date: 2007-01-17
forum: General Help
---

### Post by prince_niceguy on 2007-01-17
Hi,

Is anyone able to connect to check point VPN gateway. this is the last thing which is creating bottle neck in me moving entirely to linux. Please let me know if some one has done that.

I believe strongswan is able to connect to check point gateway. If some one can help in this it would be really helpful!!!

thanks in advance....

---

### Post by paduana on 2007-01-26
Same situation as you, just need my checkpoint to complete my windows farewell. Case you happen to get to any solution, plz let me know. I will try swan and .....

---

### Post by Wolvescan on 2007-01-30
I am trying to do the same.  So far no simple directions are out there.  Any clues anyone?

---

### Post by lukew on 2007-03-12
> **Wolvescan said:**
> I am trying to do the same.  So far no simple directions are out there.  Any clues anyone?

There is an rpm available on the website.
[HTML]

http://www.checkpoint.com/downloads/quicklinks/downloads_sr.html[/HTML]

Not that I need to tell you guys but ;)

```
alien foo.rpm
```

I am going to try this this week. VPN + Linux version of PCAnywhere. 

Let us know how you get on and I will do likewise.

Luke

---

### Post by lukew on 2007-03-14
Ok here is how far I got.


There was an install script which basically installed the rpm, and a command which copied user.C into the install directory.

I converted the rpm to a deb and installed. This installed into  /opt/CPsrsc-50/

Installed csh as all the scripts were developed for this shell.

Went run a number of times and realised I needed to

Copy /opt/CPsrsc-50/SecureClientService (Can not rememeber exactly) into /boot

All Copy /opt/CPsrsc-50/*_24 files should be renamed to *_26 files.

Started with sudo csh 

sudo csh /opt/CPsrsc-50/SCStart

It said it started; there was not SecureClient service but i did have a ssh-agent which is not normally there.

Then read the F&*^&"£% manual about how to add a site and realised you need an epf file? 

I hope this helps someone but today I realised I needed to install C# Visual Studio at home. I dont have a windows machine at home and so need to install vmware. Think I will try with that.

I hope this helps someone.

Luke

---

### Post by drader on 2007-04-10
Hello everyone:
Sorry this is a bit late but I found info which may help someone.  I am in the process of following the guides now and will post my results later.

[LIST=1]
[*]Primary Guide: [http://lists.openswan.org/pipermail/users/2006-December/011397.html](http://lists.openswan.org/pipermail/users/2006-December/011397.html)
[*]Supporting Guide, patch, and a lot of good info you will need: [http://emsi.it.pl/auto/opensclienthowto](http://emsi.it.pl/auto/opensclienthowto)
[/LIST]

dave

---

### Post by prince_niceguy on 2007-04-16
any luck dave.... sorry am currently busy trying out the method you have pointed... if you get a break through please update.

---

### Post by drader on 2007-04-16
No luck again. It appears to be another 'close but no cigar' solution. I've tried several others since (including wine) to no avail.  If anyone has any info, leads, or other useful tips please let me know.
If I find anything I will update this forum first.

thanks,
dave

---

### Post by drader on 2007-04-16
To all who interested:
I need a fix to this ASAP, and as such, have opened a bounty on getting a solution.  To add to the bounty details, provide a fix (and claim the money) or to contribute, go to: 

[https://launchpad.net/bounties/secureremote-vpn-client](https://launchpad.net/bounties/secureremote-vpn-client)

I have listed this thread as a place where the person(s) creating the fix should look for info.  If you already have a fix, respond to the bounty and get yourself a little cash for helping the linux community.

To those seeking a solution as I am, I'd encourage you to go to the bounty and consider contributing a few dollars - every dollar helps and is well deserved imo if we can get a resolution to this perplexing issue.

---

### Post by marianom on 2007-05-23
Hi drader, correct me if I'm wrong but [this other bounty]("https://launchpad.net/bounties/rverrips") looks a lot like yours (I'm after the same thing too).

Just in case I will add a note on the bounty too just to be sure you guys know about it.

---

### Post by hasimir44 on 2007-06-23
I've installed vmware w/ windows just to run this vpn - talk about overhead. I'd be happy to contribute to the bounty, but marianom is right - they should be joined as they are both after the same solution.  Any update on this?

---

### Post by marianom on 2007-06-23
In my case, I can say it was 50% success.
Using QEMU, I installed Red Hat 7.3 (keep it to its minimum 700mb not installing any desktop environment), added sharutils-4.2.1-9 (required by SC), patched it with a 2.4.18-5 linux kernel version (lower version comes with segmentation fault errors when I tried to run SecureClient), installed SecureClient for Linux and successfully established a communication with a checkpoint firewall just providing IP address, user and password. So far so good...
But I have another client with a p12 certificate and when I try to connect it gives me some kind of "token error" (looks like the p12 certificate is corrupted or something). However I know this same certificate works ok in the window's counterpart.
After all of that, I decide to take a break and come back to the fight 

I wish I have knowledge enough to build my own Damn Small Linux with kernel version 2.4 to try this thing a little bit more. Maybe some day, who knows.

---

### Post by Ozeuss on 2007-07-01
> **marianom said:**
> In my case, I can say it was 50% success.
Using QEMU, I installed Red Hat 7.3 (keep it to its minimum 700mb not installing any desktop environment), added sharutils-4.2.1-9 (required by SC), patched it with a 2.4.18-5 linux kernel version (lower version comes with segmentation fault errors when I tried to run SecureClient), installed SecureClient for Linux and successfully established a communication with a checkpoint firewall just providing IP address, user and password. So far so good...
.
hey marianom,
i was looking for the same solution...
how did you set up the connection of qemu to work with vpn, using TAP?
and will it work on fedora by any chance (not really experienced with them)?
thanks.

---

### Post by Ozeuss on 2007-07-07
i ended up using a windows VM for that issue. i tried to install redhat but it gave me problems so i decided to leave it at that, and use my already installed (though almost unused) windows VM. i suspect that with the proper kernel, fedora and maybe opensuse will play nice with SC. i might try them another time because i'd rather not use winblows entirely.
marianom's idea about using DSL is really interesting, because i would want the minimum VM. there's a package called "kern2deb" that debianizes rpm-kernels, and it would be interesting to see if it's possible to patch the appropriate kernel. or maybe use an rpm equivalent of DSL.
well, enough blabber for now.

---

### Post by ControlZ on 2007-07-20
Hi Guys, 

any success? I really need the checkpoint stuff also.

---

### Post by marianom on 2007-07-20
As I told you, I could get an instance of SC up and running (using qemu, valhalla and the SC linux client). I could connect using user/passsword but failed with a p12 certificate (got a token error). I successfully ping the server behind the firewall and all.
In my particular case I needed to connect with an Oracle's database so I tried tcpforwarding in the hope I could get the connection between my ubuntu and the database in the other side, using the valhalla as a gateway. The thing is that SC transmits all the data through udp and this cannot be forwarded easily (I searched the web and I saw some guys doing it with pipes, others using a wormhole program and stuff). 
However I needed some work done before a deadline and I couldn't afford losing time so I ended working in a colleague's XP (who was staring at me all the time with that "I told you" look)... It's a hard life. 

As soon as I have some extra time I will keep experimenting with other ideas I have in mind (I'm really a stubborn guy). I will post any good/bad news,

By the way, there's a SecureClient official forum. I think we all should join it and let them hear  our needs. They think nobody's using SC with Linux. I can't find the url right now but I'll post it as soon as I get it.

Cheers

---

### Post by Ozeuss on 2007-07-23
> **marianom said:**
> 
By the way, there's a SecureClient official forum. I think we all should join it and let them hear  our needs. They think nobody's using SC with Linux. I can't find the url right now but I'll post it as soon as I get it.


I've googled it and came up with [this]("http://www.cpug.org/forums/secureclient-securemote/"). I don't seem to find any official forum though. I think that's a good idea. a few weeks ago i looked around the checkpoint site to see if I can find somewhere to post requests or send support issues, but it's really complex, requires that you register, etc. I  really think that is our best chance- customer pressure.

---

### Post by Ozeuss on 2007-07-23
after doing some serches today-
I just came across a blog-[connecting to checkpoint vpn]("http://www.x-tend.be/~fred/blog/index.php?2007/07/19/58-check-point-ssl-vpn-and-fedora-7&cos=1"). There's a comment there about making it connect to debian etch.
i installed the matching package in the repositories, but when i try to run the mentioned install binary script (snx_install.sh) it returns:
trap: 43: SIGINT: bad trap.
So, no success yet, but this is the closest i've got to a real solution...
If anyone knows how to solve this, please let me know.

---

### Post by Ozeuss on 2007-07-24
It appears that i have got 'ssl network extender' working. I dunno if it solves the problem of those that require a client. 'snx' is a clientless option for connecting to checkpoint VPNs.

anyways, i found somewhere instructions in italian or something for editing the snx_install.sh file. you'll have to open it in vim or emacs, cause gedit won't be able to open it.
 I added -x at the end of the /bin/sh line 
and commented out  the 4 "trap cleanup" lines.
 and it installed ok, and i'm connected now to my university through the VPN.
arrgghh. that was truly my holy grail. I really hope this solves everyone's  problem too.

---

### Post by prince_niceguy on 2007-07-24
> **Ozeuss said:**
> It appears that i have got 'ssl network extender' working. I dunno if it solves the problem of those that require a client. 'snx' is a clientless option for connecting to checkpoint VPNs.

anyways, i found somewhere instructions in italian or something for editing the snx_install.sh file. you'll have to open it in vim or emacs, cause gedit won't be able to open it.
 I added -x at the end of the /bin/sh line 
and commented out  the 4 "trap cleanup" lines.
 and it installed ok, and i'm connected now to my university through the VPN.
arrgghh. that was truly my holy grail. I really hope this solves everyone's  problem too.

It would be great if you can list down the steps which you did for connection. Also, does your university vpn use soft token or passcode generated using hardware. I am having a hardware token so just wanted to check.

---

### Post by Ozeuss on 2007-07-24
this seems to work for me
1.Iinstall the "libstdc++2.10-glibc2.2" library available in universe. that should take care of the segmentation fault.
2. make sure i have java
3. i specifically got the snx_install.sh file from my university, but i think i ended up using the one [here]("http://arenahome.dyndns.org/dir/N%20Linux/snx/"), it's at the bottom of the page.
4. edit the snx file with an editor (gedit won't open it for me, i did it with emacs, nano and vim are good too) and add an -x at the first line so it now
```
#!/bin/sh -x
```
and comment out the 4 line with the trap cleanup. when i didn't it gave me a "bad trap" error.
5. run the install file
```
sudo ./snx_install.sh
```
I didn't try it with regular user permissions, I don't think its possible but if it is, probably advised.

 I then was able to connect to my university checkpoint vpn gateway, I'm using a RSA SeucrID key, so no hardware token.

I hope this works for others too, tell me if you encounter anything. maybe we can solve the secureclient issue also and post a nice howto. this seems to be an issue for many people.

---

### Post by prince_niceguy on 2007-07-25
well. I got the install done. when i run the install it asks for password and when I give password it just gives the follwoing error 
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>

---

### Post by Ozeuss on 2007-07-25
I'm sorry, but i didn't run into that problem. could you specify what you've done up until you got to the point of the install asking you for a password. it didn't go through one for me.
maybe you should uninstall snx, if you have it partly installed already. If you'll give more details, mayvbe we can work it out.

---

### Post by prince_niceguy on 2007-07-25
I followed the instruction you have given. I commented the four lines containing trap cleanup. then i ran snx with the command given. May be my vpn server has some problem as my company is not so enthu about using/giving linux support. :-(

---

### Post by tyreck on 2007-08-03
> **Ozeuss said:**
> this seems to work for 
1.Iinstall the "libstdc++2.10-glibc2.2" library available in universe. that should take care of the segmentation fault.
2. make sure i have java
3. i specifically got the snx_install.sh file from my university, but i think i ended up using the one [here]("http://arenahome.dyndns.org/dir/N%20Linux/snx/"), it's at the bottom of the page.
4. edit the snx file with an editor (gedit won't open it for me, i did it with emacs, nano and vim are good too) and at an -x at the first line so it now
```
#!/bin/sh -x
```
and comment out the 4 line with the trap cleanup. when i didn't it gave me a "bad trap" error.
5. run the install file
```
sudo ./snx_install.sh
```
I didn't try it with regular user permissions, I don't think its possible but if it is, probably advised.

 I then was able to connect to my university checkpoint vpn gateway, I'm using a RSA SeucrID key, so no hardware token.

I hope this works for others too, tell me if you encounter anything. maybe we can solve the secureclient issue also and post a nice howto. this seems to be an issue for many people.

Is this using the Redhat version of SecureClient available on the Checkpoint website?

---

### Post by prince_niceguy on 2007-08-03
I tried vpnc and it seems to connect to my server for authentication but nothing more than that.. seems my vpn server is configured to have cookie and what not ... not sure how can these can be tackled. :(

---

### Post by john_navarro on 2007-08-03
Here's a VPNC walk though is someone else wants to give it a try. I'll see if it work for me later today.

[http://nic.phys.ethz.ch/readme/96](http://nic.phys.ethz.ch/readme/96)

---

### Post by marianom on 2007-08-03
> **tyreck said:**
> Is this using the Redhat version of SecureClient available on the Checkpoint website?

No, Ozeuss make it work with the bash script you can find [here]("http://arenahome.dyndns.org/dir/N%20Linux/snx/").

John, Prince, do you guys really think it will work with vpnc?

---

### Post by marianom on 2007-08-03
> **marianom said:**
> I wish I have knowledge enough to build my own Damn Small Linux with kernel version 2.4 to try this thing a little bit more. Maybe some day, who knows.

It seems I was a fool: I was checking DSL's page and it still uses a 2.4 kernel. Cool news, I can now virtualize a 50mb footprint modern distro and try the SC with it. And try Ozeuss' option too :)

---

### Post by Ptero-4 on 2007-08-03
Sorry if it got solved already, but if it isn´t I got a downloadable package that a friend of mine pointed me at some months ago when he had to connect to a checkpoint VPN at college (this solved the problem for him and he told me that it work on NIX systems), I totally forgot the link until I saw this thread, the link is at: [http://www.checkpoint.com/techsupport/downloads/bin/securemote/r56/macosx/10.4/SecureClient_B612003002_1.pkg.zip](http://www.checkpoint.com/techsupport/downloads/bin/securemote/r56/macosx/10.4/SecureClient_B612003002_1.pkg.zip)

---

### Post by marianom on 2007-08-03
Hi Ptero-4 (I think we already met in the argentinean forum) and thanks for this suggestion. 
It seems there's plenty of options right now, one of them should work.

It's time for a good google session to learn how to install mac os apps in linux. :)

---

### Post by grahams on 2007-08-04
It looks like there has been some success connecting to a Checkpoint VPN, I see a few different methods as to how. Is there a recommended way to get this working?

---

### Post by Ptero-4 on 2007-08-05
> **marianom said:**
> Hi Ptero-4 (I think we already met in the argentinean forum) and thanks for this suggestion. 
It seems there's plenty of options right now, one of them should work.

It's time for a good google session to learn how to install mac os apps in linux. :)

Oops. didn´t saw it was for ´that´ NIX variant, lol.

---

### Post by Ozeuss on 2007-08-06
> **grahams said:**
> It looks like there has been some success connecting to a Checkpoint VPN, I see a few different methods as to how. Is there a recommended way to get this working?

There isn't really one way, because it depends on the checkpoint vpn. If your office/university or whatever uses the 'clientless' method (a vpn gateway) then you can use the method i showed, although it seems not to work for prince_niceguy, who uses different authentication.
 If you need to use a vpn client, then it seems the best working option is marianom's- using a virtualized redhat and SC for linux (using DSL might prove even more effective as marianom suggested, no confirmation yet).
The third option in this thread, with no confirmation yet, is to do it with vpnc. I think checkpoint is IPSEC compatible, meaning that you should be able to connect with vpnc. but this one appears to be a long and dark road...

---

### Post by ricardoarguello on 2007-09-23
Check this thread:

[http://ubuntuforums.org/showthread.php?p=3406306#post3406306]("http://ubuntuforums.org/showthread.php?p=3406306#post3406306")

---

### Post by cider101 on 2008-01-13
I have some good news! 
A friend of mine patched Racoon to work with the hybrid-mode of the checkpoint firewall (login, passwd needed only). He did the work initially for OsX. We already compiled the code on Ubuntu and could successfuly establish a connection with the checkpoint firewall. In a week or so, he is going to release/publish the code somewhere (still trying to figure out what the best option will be). I'll post any news/results here. 

have fun

---

### Post by deloptes on 2008-01-22
Our company just switched to a gateway version of CheckPoint with SNX for linux.

I found a way to make it run. (see below) I am just concerened about the security, because I have to run the stuff as root, because snx needs root access to create and modify ethernet devices etc.

Do you have a suggestion how the thing could be tight up?

The problem in details I have to run firefox as root, then a java applet is using snx to build the connection and from inside this java applet I can lounch programs on my linux system that are executed in the VPN environment AS ROOT .... exactly what I don't like

Thank you in advance

[LIST]
Prepare:
[/LIST]

Find compatible libstdc++-2-libc6. On debian I had a problem with this, because this package is not in the official distro (I needed this before for testing ViaVoice, so thats why it is in this place). You should be able to find it i.e. as RPM package or tar.gz or similar nad install or unpack it somewher. Also the minor version numbers could be different ... don't worry. Important is that it works on your system.

       > 
        locate libstdc++-2-libc6.1
        /opt/custom/ViaVoice/lib/usr-lib/libstdc++-2-libc6.1-1-2.9.0.so
       

[LIST]
Edit:
[/LIST]

Move the snx binary to snx-bin and create a script as shown below
Replace the library path to the library that is installed on your system i.e. th output of the locate program (see above)

       > 
        sudo mv /usr/bin/snx /usr/bin/snx-bin
        sudo 
echo 'LD_PRELOAD=/opt/custom/ViaVoice/lib/usr-lib/libstdc++-2-libc6.1-1-2.9.0.so /usr/bin/snx-bin "$@" ' 
> /usr/bin/snx

        sudo chmod u+rsx  /usr/bin/snx
        sudo chmod go+x  /usr/bin/snx
       


[LIST]
Run firefox as root login and run applications:
[/LIST]


       > 
        xhost +local:0
       
       > 
        kdesudo firefox
       
or
       > 
        kdesu firefox  
       
or
       > 
        gksu firefox  
       

---

### Post by ekravche on 2008-01-30
We use VPN at work, but it requires a hardware token. Does anyone know which VPN software I can use for that?

---

### Post by jnooley on 2008-01-31
Hello All,
   I just bought a brand new Dell and I'd like to make the leap to Ubuntu Linux. However, I'm concerned about not getting Checkpoint VPN to work as I've seen many posts saying is is difficult at least. Does anyone have an update on this? I'd prefer not to spend a week getting Linux VPN set up as it would kinda defeat the purpose of going to Linux. Any help would be appreciated!

---

### Post by ekravche on 2008-02-03
> **jnooley said:**
> Hello All,
   I just bought a brand new Dell and I'd like to make the leap to Ubuntu Linux. However, I'm concerned about not getting Checkpoint VPN to work as I've seen many posts saying is is difficult at least. Does anyone have an update on this? I'd prefer not to spend a week getting Linux VPN set up as it would kinda defeat the purpose of going to Linux. Any help would be appreciated!

As far as I can tell it's really difficult to get it working. I installed vnpc and openvpn and was unable to get either to work for me. I ended up installing a vpn client on my windows partition and running vpn off of there.

---

### Post by orduek on 2008-02-06
> **Ozeuss said:**
> this seems to work for me
1.Iinstall the "libstdc++2.10-glibc2.2" library available in universe. that should take care of the segmentation fault.
2. make sure i have java
3. i specifically got the snx_install.sh file from my university, but i think i ended up using the one [here]("http://arenahome.dyndns.org/dir/N%20Linux/snx/"), it's at the bottom of the page.
4. edit the snx file with an editor (gedit won't open it for me, i did it with emacs, nano and vim are good too) and add an -x at the first line so it now
```
#!/bin/sh -x
```
and comment out the 4 line with the trap cleanup. when i didn't it gave me a "bad trap" error.
5. run the install file
```
sudo ./snx_install.sh
```
I didn't try it with regular user permissions, I don't think its possible but if it is, probably advised.

 I then was able to connect to my university checkpoint vpn gateway, I'm using a RSA SeucrID key, so no hardware token.

I hope this works for others too, tell me if you encounter anything. maybe we can solve the secureclient issue also and post a nice howto. this seems to be an issue for many people.

WOW.
I can't thank you enough!!!
Thank you.
I just paid some good money for this feature and then realized i have a problem. 
I called the university support and guess what? no Linux support :(
I was going to return this thing but WOW - you maid it so simple for me.
again, 
Thank you.

---

### Post by jnooley on 2008-02-10
Thank you all for your help. I am now able to connect with SNX to my Checkpoint gateway. Now, the challenge begins to get some of those proprietary Windows apps working on Linux via Wine or some other. Thanks again!

---

### Post by ekravche on 2008-02-10
> **prince_niceguy said:**
> well. I got the install done. when i run the install it asks for password and when I give password it just gives the follwoing error 
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>

I get the same error

---

### Post by deloptes on 2008-02-13
I still don't understand something.

On my business notebook I have SUSE 10.2. The SNX client works great (with firefox/mozilla).

On my private notebook I have debian testing. I have to run mozilla/firefox as root (kdesudo/kdesu or alike) so that it may trigger the SNX client with root permissions.

I remember that there is an option in SUSE to set some administrative rights to some user account, but don't remember where this was and I don't know how I can configure this on debian.

can somebody help?

---

### Post by marianom on 2008-02-13
You can grant an action/program the posibility of not asking a root password when it's executed with sudo (although right now I'm not 100% sure if it only works with commands that required a root pass or it can be done with any program executed with sudo). 

This can be done with visudo (check the man page for more data on this).

Although, IMHO, I would give it a second thought before granting adminitrative rights to firefox session.

---

### Post by deloptes on 2008-02-15
Hello,
thank you for the response.

Unfortunately I have the same settings for both notebooks both users and sudo.

Also I am not talking about permissions for firefox, because under SUSE I run firefox as the normal user and it runs fine without asking for a password. May be this has to do something with the way snx installes itself or some other reason.

The question is where SUSE writes this information and how it works. I was thinking of the superuser bit (as far as Iremember how it is called) -r-s--x--x

SUSE also asks for user password and not root when I have to use administrative configuration. May be setting ksudo as default command may be using some administrative group. This is also very useful, as a user can change settings without knowing the root password - i.e. in sudoers I give permission to run yast and it works.

but the question is how exactly it works, and how to achieve this same behaviour on debian.

may be both are related may be not.

there is also another difference.

On debian testing the libc compat library is missing and i am using a script that preloads the library prior to executing snx .... else I have a segmentation fault on snx.
This is though not an issue, because if I run firefox as root everything works fine.

If you have a useful suggestion it would be great. I've been using linux for many years and mostly using the server power of it so I know a lot of basic stuff, but not kde and how this interacts with the system.


Thanks in advance

---

### Post by dubcat on 2008-02-17
> **ekravche said:**
> I get the same error

yup im getting the same error too.  Does anyone have a clue as to what is going wrong? I am typing my password and hitting enter.  Note - when i type my password in I do not see any characters at all - not even ****'s.  Is this normal?

> [QUOTE]
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.[/QUOTE]

---

### Post by orduek on 2008-03-01
I have a new and wierd problem.
after I write my username and password it says initialising applet and then gives me some error message that says : "please confirm the use of this java applet and then refrsh or reopen the window".

What happend? everything was OK. I tried disabeling the ad-block plus but it didn't help.

---

### Post by ekravche on 2008-03-08
>  Originally Posted by prince_niceguy  View Post
well. I got the install done. when i run the install it asks for password and when I give password it just gives the follwoing error
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>

Anyone know what this is all about? Would be nice to get vpn working under linux.

---

### Post by orduek on 2008-03-10
> **orduek said:**
> I have a new and wierd problem.
after I write my username and password it says initialising applet and then gives me some error message that says : "please confirm the use of this java applet and then refrsh or reopen the window".

What happend? everything was OK. I tried disabeling the ad-block plus but it didn't help.

any ideas?

---

### Post by deloptes on 2008-03-13
---Quote---
 Originally Posted by prince_niceguy  View Post
well. I got the install done. when i run the install it asks for
 password and when I give password it just gives the follwoing error
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>
---End Quote---
Anyone know what this is all about? Would be nice to get vpn working
 under linux.

Did you run this as root?

For me the snx works fine as I wrote before. The checkpoint uses an "extender" applet (I think it is triggering the snx binary.
However it works under a normal user only in SuSE. On debian/ubuntu I have to run firefox as root, so that the underlaying applicationis be also triggered as root.

Untill now nobody can tell how it is possible.

When I start snx from the shell with preconfigured ~/.snxrc file it works also fine, but no connection is set up.

regards

---

### Post by ekravche on 2008-03-15
> **deloptes said:**
> ---Quote---
 Originally Posted by prince_niceguy  View Post
well. I got the install done. when i run the install it asks for
 password and when I give password it just gives the follwoing error
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>
---End Quote---
Anyone know what this is all about? Would be nice to get vpn working
 under linux.

Did you run this as root?

For me the snx works fine as I wrote before. The checkpoint uses an "extender" applet (I think it is triggering the snx binary.
However it works under a normal user only in SuSE. On debian/ubuntu I have to run firefox as root, so that the underlaying applicationis be also triggered as root.

Untill now nobody can tell how it is possible.

When I start snx from the shell with preconfigured ~/.snxrc file it works also fine, but no connection is set up.

regards

What does your ~/.snxrc look like?

Thanx in advance

---

### Post by orduek on 2008-03-16
> **orduek said:**
> I have a new and wierd problem.
after I write my username and password it says initialising applet and then gives me some error message that says : "please confirm the use of this java applet and then refrsh or reopen the window".

What happend? everything was OK. I tried disabeling the ad-block plus but it didn't help.

Sadly the problem is related to the Java fork icedtea7.
After uninstalling its components (including some gcj libraries, i think) everyhting was OK. except Miro.

---

### Post by ekravche on 2008-04-13
> **deloptes said:**
> ---Quote---
 Originally Posted by prince_niceguy  View Post
well. I got the install done. when i run the install it asks for
 password and when I give password it just gives the follwoing error
<code>nx -s ##### -u XXXXXX -g -e RC4
Check Point's Linux SNX
build 600000013
Please enter your password:

SNX: Connection aborted.
</code>
---End Quote---
Anyone know what this is all about? Would be nice to get vpn working
 under linux.

Did you run this as root?

For me the snx works fine as I wrote before. The checkpoint uses an "extender" applet (I think it 
is triggering the snx binary.
However it works under a normal user only in SuSE. On debian/ubuntu I have to run firefox as root, so that the underlaying applicationis be also triggered as root.

Untill now nobody can tell how it is possible.

When I start snx from the shell with preconfigured ~/.snxrc file it works also fine, but no connection is set up.

regards

extender applet? Where can I get that

---

### Post by deloptes on 2008-04-21
> **ekravche said:**
> extender applet? Where can I get that+

As   far as I know there are few flavours of snx, so you should identify what kind of VPN service are you trying to connect.

The version my company uses provides a web address where I am logging in. After a successful login the applet is started and I see it triggers the snx binary to setup the network.

Applets are provided by the server and executed on your machine, so you can not download them - they are designed to work in web environment, as far as I know.

May be you should contact the system support of the site you are trying to connect and find out which flavour of VPN they are using and then find the proper way to connect

regards

---

### Post by orduek on 2008-05-29
Since moving to Hardy, i can't connect to the VPN.
looks like I'm missing the libstdc++ ....
which can't be found on hardy.

I get an error message : failed to initialize.

---

### Post by deloptes on 2008-06-02
> **orduek said:**
> Since moving to Hardy, i can't connect to the VPN.
looks like I'm missing the libstdc++ ....
which can't be found on hardy.

I get an error message : failed to initialize.

You can find the library still in the net. I htink there are security issues or patents not quite sure that lead to removing it. So after you find a version that works with your system, do following.

[LIST=1]
[*]Unpack somewhere to <PATH_TO_DIR>
[*]move snx to snx-bin
[*]put the lines in the script snx
[*]set permissions like snx-bin
[/LIST]

```
#!/bin/sh
LD_PRELOAD=<PATH_TO_DIR>/libstdc++-2-libc6.1-1-2.9.0.so /usr/bin/snx-bin "$@"
```

As I wrote before the only problem for me is that under debian I have to run firefox like root, so that the snx is triggered with root priv and is able to setup the network stuff.

regards

---

