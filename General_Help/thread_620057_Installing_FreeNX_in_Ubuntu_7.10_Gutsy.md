---
title: "Installing FreeNX in Ubuntu 7.10 Gutsy"
date: 2007-11-22
forum: General Help
---

### Post by daflame on 2007-11-22
I have read so many posts on users having troubles installing the Seveas packages on AMD64 with Gnome or KDE.  Or having to chase down some outdated client that is only available on remote sites and isn't 64bit ready.  Also, I have become tired of Linux being consistently behind the ball game on the latest and greatest technology.  Namely NX 3.2.0 protocol compression which is now 64bit ready, so in frustration I modded the FreeNX Debian packages to arrive on a solution that works on Gutsy and Hardy extremely well using FreeNX 0.7.2.  All other mods I've heard of need either an outdated client and server or require someone with sysadmin level knowhow to install and setup.  The following is a guide to install and setup the Gutsy packages that I have compiled for everyone's convenience.

[b]NOTICE: NX 3.2.0 is released!  After much toil I have concluded that I cannot get native Hardy packages to compile in 64bit, so I am releasing Gutsy built packages in the Hardy repos for now since they work fine on Hardy.  I will continue to try to find the problem, but it is a vague linker error that tells me to use -fPIC (which I am), so it is hard to track down the true cause.

**ATTENTION:** These are Gutsy and Hardy packages and I DO NOT GUARANTEE any usability especially on any other distribution prior to Gutsy.  If someone would like to debuild packages for other debian versions I have also posted the source repos here that I have used to make these packages as well as compilation instructions.  My only request is that you make them available to me so that I may make them available to the community.  One note:  You cannot build the Hardy sources on Hardy 64bit just yet.  I built them on Gutsy 64 bit instead.

**WARNING:** All packages and files below are open-source and free according to the GPL license EXCEPT the nxclient-3.2.0 ones.  This is the commercial nxclient, but it is still free to download and use according to the licensing on their site at [www.nomachine.com]("http://www.nomachine.com/").  I have chosen the version below because it has been tested to work with these packages, you may use a newer one, but your mileage may vary.  Do not bother to post about a newer version failing, as it has not been tested, it may not work so please use the version supplied.  However, this new release should function with newer packages should you desire to use them.  You may alternatively use the new qtnx client in Hardy repos, but only for the client side I believe.

For those desiring to use nxclient 3.2.0 for Windows, here is a link to a compatible nxclient 3.2.0-10:
[nxclient-3.2.0-10.exe]("http://www.datakeylive.com/ubuntu/dists/gutsy/main/source/nxclient-3.2.0-10.exe")
This is the recommended nxclient for Windows.  I have tested this version and it definitely works well.

First add the following lines to your sources.list for Gutsy:
deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

Or add the following lines to your sources.list for Hardy:
deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) hardy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) hardy main

Then add my keys for authentication and update your package list
(both Gutsy and Hardy):
```
wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key -O - | sudo apt-key add -
sudo apt-get update
```

Then install necessary packages:
```
sudo apt-get install expect openssh-server tcl8.4 dbus-x11 libxcomp3 libxcompext3 libxcompshad nxlibs nxagent nxproxy nxclient freenx-server
```

(I'm not sure what other libs are necessary as I have them all installed already, but you MUST have a desktop (X minimal, KDE, or Gnome) installed,
please let me know if I'm missing anything since the dependencies have changed.)

Please verify the above operation was successful by executing:
```
sudo apt-get -f install
sudo apt-cache show expect openssh-server tcl8.4 dbus-x11 libxcomp3 libxcompext3 libxcompshad nxlibs nxagent nxproxy nxclient freenx-server | grep "Unable"
```
If the previous command says unable to find .... (with a package name) you need to install that package first.
Otherwise it should just drop you back to the command prompt.
**If you installed the files above you can skip this next section for compiling from source...**

**For those brave souls willing to compile from source first I will present the quick and dirty method (for Debian based ONLY):**
Make sure you added the above package repository, then execute:
```
sudo apt-get install expect openssh-server tcl8.4 dbus-x11 build-essential devscripts fakeroot cdbs autotools-dev debhelper patchutils autoconf automake1.9 bzip2 libjpeg-dev libpng12-dev libssl-dev libx11-dev libxaw7-dev xutils zlib1g-dev apt-build nxclient
```
If you also want to build freenx-client you will need to execute:

Then execute:
```
sudo apt-build install libxcomp3 libxcomp-dev libxcompext3 libxcompext-dev libxcompshad libxcompshad-dev nxlibs nxlibs-dev nxagent nxagent-dev nxproxy freenx-server
```

Alternatively download these and try to build them yourself (I do not provide non-debian support):
[nx_3.2.0.orig.tar.gz]("http://www.datakeylive.com/ubuntu/pool/main/n/nx/nx_3.2.0.orig.tar.gz")
[nx_3.2.0-1gutsy1.diff.gz]("http://www.datakeylive.com/ubuntu/pool/main/n/nx/nx_3.2.0-1gutsy1.diff.gz")
[freenx-server_0.7.2.orig.tar.gz]("http://www.datakeylive.com/ubuntu/pool/main/f/freenx-server/freenx-server_0.7.2.orig.tar.gz")
[freenx-server_0.7.2-1gutsy1.diff.gz]("http://www.datakeylive.com/ubuntu/pool/main/f/freenx-server/freenx-server_0.7.2-1gutsy1.diff.gz")

verify that all of the above packages are installed correctly by first executing:
```
sudo apt-get -f install
sudo apt-cache show libxcomp3 libxcompext3 libxcompshad nxagent nxlibs nxproxy nxclient freenx-server | grep "Unable"
```
If the previous command says unable to find .... (with a package name) you need to reinstall that package again or restart the build process since something didn't work.
Otherwise it should just drop you back to the command prompt.

**(CONTINUING FROM PACKAGE CHOICE)**

Open /etc/X11/xorg.conf and make sure the font paths are in there.  My section looks like:
```
Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```
If you are missing this section from your xorg.conf configuration file I recommend adding it as without this FreeNX will die unexpectedly because FreeNX is actually xorg version 6.9 and Gutsy and Hardy are >=7.1. Since Gutsy, these settings aren't necessary anymore for a default install, and often aren't included by default.

I don't think this is necessary anymore but here is nxcupsd-wrapper for posterity for printing in old freenx:
[nxcupsd-wrapper]("http://www.datakeylive.com/ubuntu/dists/gutsy/main/source/nxcupsd-wrapper")
Let me know if you have printing issues.

Now if you want someone to log into the server you need to make their account ready for log in.  At a console prompt execute where xxxx is the name of the user you want to log in:
```
sudo nxserver --adduser xxxx
```
This should setup the user for you automatically.

If you want to support file sharing you will need to install smbfs and I would also recommend installing Samba:
```
sudo apt-get install samba smbfs
```
You need to share the directories (on the client side) using Samba or Windows file sharing that you want to mount.  It is recommended to configure Samba, but it is beyond the scope of this FAQ, so just Google "setup Samba on Ubuntu" to get a better idea how to do this.

If you want to be able to proxy and tunnel RDP (Windows Remote Desktop/Terminal Services) you need to install rdesktop.
From a console type:
```
sudo apt-get install rdesktop
```
rdesktop is the RDP client that FreeNX uses to proxy RDP through the NX protocol.  Then at the client end choose Windows, then click the settings button to setup the server and domain to log into. Make sure you use a server name that linux can resolve an IP to. Enter your credentials here if they differ on the windows machine.
I have found proxying RDP slightly more laggy on broadband, but it scales better and is much faster over slower connections.

If you want to proxy vnc sessions you need to install xvncviewer:
```
sudo apt-get install xvncviewer
```
If you want to also mirror sessions and the local desktop via VNC you need to install x11vnc:
```
sudo apt-get install x11vnc
```
On the client side you need to choose the session type as VNC and set a host, display and password in the custom section.  Make sure to set the correct display size at the bottom or your window won't match the display size and vncviewer's scrollbar is terrible. (Right click to scroll up?)  If you want to shadow when the window list pops up choose the session to shadow and click resume.  If you want to VNC to a screen (Another machine usually) then click new instead.
When mirroring the local desktop make sure you have any builtin desktop VNC RFB server disabled. eg. KRFB

You should now be able to test this now by creating a connection to localhost using nxclient.  If you need a Windows client version it is posted above.
There are many other commands that you can execute on nxserver just use:
```
sudo nxserver --help
```
Please post with your experiences!

**TROUBLESHOOTING**

I have heard reports that sometimes you need to copy the key from /home/xxxx/.ssh/authorized_keys2 to /home/xxxx/.ssh/authorized_keys where xxxx is the user name when public key authentication fails for user nx.
**DO NOT DO THE FOLLOWING UNLESS YOU HAVE TO**
```
sudo -u xxxx -i
cd
cat .ssh/authorized_keys2 >> .ssh/authorized_keys
exit
```

If you are having problems connecting with agent startup timeout, try one of the following:
uncomment the following from /etc/nxserver/node.conf and make sure it is at least 60 and DO NOT ADD ANY SPACES:
```
#AGENT_STARTUP_TIMEOUT="60"
```
or, delete all the xauthority files:
```
cd
sudo rm .XA*
```
Make sure you don't disable encryption of all traffic in the client.  I have had problems logging in remotely with this setting turned on, local logins will still work. (There is a problem with direct unencrypted connections in FreeNX still trying to connect to localhost)
Don't forget to check the log under your username:
/home/username/.nx/F-C-(long alphanum session code)/session
if it has an error like:
/usr/lib/nx/nxnode: line 333: /usr/bin/dbus-launch: No such file or directory

You need to install the dbus-x11 package.  There should be an auto-dependency from the dbus package, but there isn't.

The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/118919](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/118919)

Also, remember to open port 22 (or whatever port you want to redirect to it) in your router and firewalls!
Another little trick, if you need to get through a firewall at work, it can be done by making port 21 or port 80 the new SSH port or tunneling via some tunneling client like hamachi, but make sure you do not have some other program using those ports first.  For those wondering about using hamachi with NX, yes it does work, but I am having troubles with Hardy though.  If you have hamachi installed in your linux box with a kernel <=2.6.23 (Not Hardy) and hamachi installed at a remote location and are a member of the network, just use the hamachi IP or a name that resolves to the hamachi IP as the server address.  Opening post 22 on your internet router/firewall isn't necessary for hamachi to work, but opening hamachi ports may be.

[Datakey Live Website Design and Development]("http://www.datakeylive.com/")

---

### Post by psypher on 2007-11-22
I just tried installing and the install went fine, but i don't have the nxserver folder and cannot even run the nxserver command. I think you are missing a package or am I missing something?

Other than that, thanks for taking the time to do this!! You rock!!

---

### Post by daflame on 2007-11-22
> **psypher said:**
> I just tried installing and the install went fine, but i don't have the nxserver folder and cannot even run the nxserver command. I think you are missing a package or am I missing something?

Other than that, thanks for taking the time to do this!! You rock!!

Oops, you are correct, I forgot to put links to the freenx packages :oops:.  You might not have a nxserver command without that package.  The files are already there, so I will update the post.  Thanks!!

---

### Post by daflame on 2007-11-23
All x86_64 and i386 packages are now uploaded and ready for download.  I apologize for any inconveniences.  I have to make a few notes however.  I have come across four known issues that I am working out.
1) VNC proxy and shadowing currently fail to work.  I am working on a resolution as this is VERY important for me to have prior to Christmas (I am visiting relatives away from the office (3000KMS away) and I need to manage my employees).
2) The shares folders do not function correctly.  It seems to create a folder that is the name of the variable %24(SHARES) instead of extracting the variable's value to know where to put the directory.
3) The nxclient dialogs failed to work for me correctly, so as a last resort I disabled them.  Now you will get the ugly xmessage dialogs as a result, but they do work at least.
4) Printing does not work currently without the nxcupsd-wrapper mentioned above.  You will need to put this on the computer that needs to log into the server in a place the user that needs to log in can access and make it executable.

I think problems 1, 2 and 3 might be related, but I have put in a request for answers from the maker of FreeNX, Fabian.  I thank you all in advance for your help in making this a great forum.

---

### Post by Brazilian Joe on 2007-11-23
I have tried your packages, and it ALMOST worked, but the connection always timed out. it's a brand new installation to set up a printer/scanner/file server. I have uninstalled the packages but I will give it another shot.
build-essential etc are installed. 

The connection always showed up a X0: vnc something  as an option to resume a session which I never started. I assume there is a vnc remote desktop connection for gnome or something. anyway, I can't terminate this connection. If I try connect to it it bails out almost instantly. If I try to set up a new connection, It goes up to 'authentication completed', then stays on that stage for some time and quits. the log says something like 'no data received from proxy for more than 30 seconds'.

I shotgun-guess that nxagent is not being able to run because of something.

---

### Post by fm1234 on 2007-11-23
I tried the installation in a fresh system. It was missing the package "expect", easily fixed with synaptic.

It would be nice to have here pointers or instructions to setting up the server.

---

### Post by AkuKalle on 2007-11-25
Does this work in my scenario:

feisty server and seveas packages for freenx -> upgrade to gutsy-> and then i install these packages. Do i have to remove seveas freenx packages?

---

### Post by fm1234 on 2007-11-25
Hi,

I've instaleed as per above, nxserver is running, I've added a user, but I get an authentication error:

```

NX> 148 Server capacity: not reached for user: user123
NX> 105 listsession --user="user123" --status="suspended,running" --geometry="1280x1024x16+render" --type="unix-gnome"
NX> 127 Sessions list of user 'user123' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        DACCC0BFC8331D4A98EBAA0A49A9CA42 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: user123
NX> 105 restoresession  --link="lan" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-gnome" --geometry="1024x768" --client="windows" --keyboard="pc102/pt" --id="DACCC0BFC8331D4A98EBAA0A49A9CA42" --resize="1" 

cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
NX> 280 Exiting on signal: 15

```

What should I look for? BTW, my win machine is 98 (I know with smaba there used to exist an issue with authentication)

I'm also confused as to why it says it is a vnc session. I thought it was other protocol?

---

### Post by djtm on 2007-11-25
Well, you can use VNC through NX as well. Maybe you chose that option.

Did you change any options from the standard in the NX Client? Can you connect with the NX Client from the Linux machine?

I don't know much about FreeNX though, I use the NX Server Free Edition...

---

### Post by daflame on 2007-11-26
> **fm1234 said:**
> I tried the installation in a fresh system. It was missing the package "expect", easily fixed with synaptic.

It would be nice to have here pointers or instructions to setting up the server.

Thank you, duly noted.  I will make appropriate notes at the top.  I apologize for the shack assembled version above.  I had to assemble this site quickly as an offer to the community since I do programming by trade and I do not have much time to spend.  This was the lease I could do to offer packages for a community hurting for updated software since I use FreeNX so much.

---

### Post by daflame on 2007-11-26
> **Brazilian Joe said:**
> I have tried your packages, and it ALMOST worked, but the connection always timed out. it's a brand new installation to set up a printer/scanner/file server. I have uninstalled the packages but I will give it another shot.
build-essential etc are installed. 

The connection always showed up a X0: vnc something  as an option to resume a session which I never started. I assume there is a vnc remote desktop connection for gnome or something. anyway, I can't terminate this connection. If I try connect to it it bails out almost instantly. If I try to set up a new connection, It goes up to 'authentication completed', then stays on that stage for some time and quits. the log says something like 'no data received from proxy for more than 30 seconds'.

I shotgun-guess that nxagent is not being able to run because of something.

Can you post a log from /var/logs/nxserver.log?

Make sure not to include passwords of course.  Also, did you replace your /etc/nxserver/node.conf with the one supplied above?  I know that I could not get it to run with the one supplied in the packages.  The last suggestion is to check the /etc/nxserver/node.conf and find the line that has "-fp ....." with lots of font paths and compare them with what is in your /etc/X11/xorg.conf.  If either is missing or doesn't match you will have problems.  I know that Gutsy often removes all font paths from the xorg.conf file by default you will need to add them back in or nxserver crashes.

---

### Post by daflame on 2007-11-26
> **AkuKalle said:**
> Does this work in my scenario:

feisty server and seveas packages for freenx -> upgrade to gutsy-> and then i install these packages. Do i have to remove seveas freenx packages?

Yes this is actually what I did on my i386 box and my x86_64 box.  Remove all previous freenx packages before upgrading or you may kill freenx for good since this now runs on nx-3.0 and the packages are VERY different.

---

### Post by daflame on 2007-11-26
> **fm1234 said:**
> Hi,

I've instaleed as per above, nxserver is running, I've added a user, but I get an authentication error:

```

NX> 148 Server capacity: not reached for user: user123
NX> 105 listsession --user="user123" --status="suspended,running" --geometry="1280x1024x16+render" --type="unix-gnome"
NX> 127 Sessions list of user 'user123' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        DACCC0BFC8331D4A98EBAA0A49A9CA42 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: user123
NX> 105 restoresession  --link="lan" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-gnome" --geometry="1024x768" --client="windows" --keyboard="pc102/pt" --id="DACCC0BFC8331D4A98EBAA0A49A9CA42" --resize="1" 

cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{DACCC0BFC8331D4A98EBAA0A49A9CA42}: No such file or directory
NX> 280 Exiting on signal: 15

```

What should I look for? BTW, my win machine is 98 (I know with smaba there used to exist an issue with authentication)

I'm also confused as to why it says it is a vnc session. I thought it was other protocol?

FreeNX has an option to resume a session that it resemble as a X0 vnc-local session using xvncviewer.  This gives you a vnc NX proxy session to the local desktop.  DO NOT USE THIS!!!  As posted above I am still resolving problems with vnc sessions on the server. they do not work currently.

If you click the button to create a new session instead of resuming it should work just fine.  Also the error you see above comes from the fact that vnc sessions need x11vnc and xvncviewer installed on the server now as part of the Linux integration of FreeNX.  Even if you install this, it still won't work yet.  For now don't bother trying.  I will post when I fix this.

---

### Post by daflame on 2007-11-26
> **djtm said:**
> Well, you can use VNC through NX as well. Maybe you chose that option.

Did you change any options from the standard in the NX Client? Can you connect with the NX Client from the Linux machine?

I don't know much about FreeNX though, I use the NX Server Free Edition...

I also usually recommend NX Free Edition, except when the need to remain open source or the need for more than 2 simultaneous connections is present as is often the case for me.

---

### Post by rockballad on 2007-11-26
Thanks, I have a quick test on fresh Ubuntu AMD64 and it works well ;-)

Thank you a lot. Have a nice day!

---

### Post by fm1234 on 2007-11-26
Thanks for the explanations, I removed the vnc setup from xinetd. Instead of doing a resume (of vnc) I'm asking for a new session. I get stuck when nxclient is "Negotiating link parameters". It comes back with:

"NX client was not able to establish an unencrypted channel with the server. This could be due to the remote server being behind a firewall. If tis is the case, you should be able to run your session by unchecking the option "Disable SSL encryption of all traffic".

which I did, and next time I tried nxclient crashed. How can I check if Ubuntu is firewalling?

---

### Post by daflame on 2007-11-26
> **fm1234 said:**
> Thanks for the explanations, I removed the vnc setup from xinetd. Instead of doing a resume (of vnc) I'm asking for a new session. I get stuck when nxclient is "Negotiating link parameters". It comes back with:

"NX client was not able to establish an unencrypted channel with the server. This could be due to the remote server being behind a firewall. If tis is the case, you should be able to run your session by unchecking the option "Disable SSL encryption of all traffic".

which I did, and next time I tried nxclient crashed. How can I check if Ubuntu is firewalling?

Could you post your /var/log/nxserver.log?  That should tell me what is going wrong right away.

---

### Post by daflame on 2007-11-26
> **daflame said:**
> Could you post your /var/log/nxserver.log?  That should tell me what is going wrong right away.

Also, I remember there being a problem with trying to connect with Disable Encryption checked on in the client.  Even after I checked it off it failed to connect until I did a nxserver --restart and closed and reopened the client.  Finally, make sure you have nxclient-3.0 as that is the only one I could get to work.

---

### Post by daflame on 2007-11-26
> **rockballad said:**
> Thanks, I have a quick test on fresh Ubuntu AMD64 and it works well ;-)

Thank you a lot. Have a nice day!

Glad to be of assistance.  Now if I can only resolve the VNC issues I can put to rest any needs for NX Free Edition and use FreeNX exclusively with shadowing.

---

### Post by fm1234 on 2007-11-27
Hi daflame,

I tried again now, after rebooting, and it works! However it is significantly slower than my former VNC connection on Ubuntu 7.04. I perceive it easily as two times slower.

Also, is it normal that when I start the client it finds a vnc-local session available?

I've to rush out but I believe vncserver is not working anymore.

Thanks for your help,

---

### Post by Linder on 2007-11-27
Just got it to work. Is it, however, possible to connect to an already EXISTING session? That would be much more comfortable to me. For instance, is it possible to connect to the already running X session?

EDIT: 
Nvm, I just read that VNC connections currently don't work. I'll be waiting for you to post about a fix :D

---

### Post by Brazilian Joe on 2007-11-27
I stated about a few problems before, it turned out that they were NOT related to NX at all. 
I left NX aside for a moment and tried to set up my Samba Server, and was bitten by some unexplained timeouts. Turned out my CLIENT machine was wireles, so even though my SERVER was on a (vmwarehost == wired ) WIRED connection, there was some MTU bug crippling the packets causing communication problems. 
I solved all communication problems from wireless clients to the wired host by setting mtu 1400 on /etc/network/interfaces under my network card adapter section (in my case, eth0).

```

#/etc/network/interfaces
#I have put this option on my eth0:
mtu 1400

```

---

### Post by daflame on 2007-11-27
> **fm1234 said:**
> Hi daflame,

I tried again now, after rebooting, and it works! However it is significantly slower than my former VNC connection on Ubuntu 7.04. I perceive it easily as two times slower.

Also, is it normal that when I start the client it finds a vnc-local session available?

I've to rush out but I believe vncserver is not working anymore.

Thanks for your help,

Something I have noticed is that some of the options are exceptionally slow such as the kicker icon rollovers.  If you turn down a few effect options you may find the speed will improve substantially.  This is not a problem with FreeNX specifically, but with the poor response to these options with the X remote protocol.  Many of these options cause bandwidth expensive graphical animations which don't remote well even when compressed with NX.  VNC seems faster because it doesn't send every frame of that animation, just what is captured.

---

### Post by daflame on 2007-11-27
> **Linder said:**
> Just got it to work. Is it, however, possible to connect to an already EXISTING session? That would be much more comfortable to me. For instance, is it possible to connect to the already running X session?

EDIT: 
Nvm, I just read that VNC connections currently don't work. I'll be waiting for you to post about a fix :D

I am still working on this as you have noted.  I will keep you posted.  However, I have been able to run a vncviewer program instead of a whole desktop using unix custom and connect that way.  It still doesn't give me session shadowing yet, but you should be able to grab the active desktop if desktop sharing is turned on.

---

### Post by alex_dm on 2007-11-28
I tried this on my Gutsy box, and everything worked well... I am considering upgrading my Debian Etch box with the newer freenx .deb so I can use the new clients... Do you know if these debs work on etch?

Thanks

Alex

---

### Post by daflame on 2007-11-29
> **alex_dm said:**
> I tried this on my Gutsy box, and everything worked well... I am considering upgrading my Debian Etch box with the newer freenx .deb so I can use the new clients... Do you know if these debs work on etch?

Thanks

Alex

I have no idea, but if it is based on the same libraries as Gutsy or newer then most likely it will.

---

### Post by dlstyley on 2007-11-29
I just stumbled on to this thread.  I have Gutsy on AMD64 and about a week ago I installed the x86_64 DEB package from this page:

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

I realize that x86_64 is probably different that  AMD64, but that package worked fine for me.  Is that package fundamentally different than what these instructions are installing, or is basically the same thing?  

I ask because everything seems to work fine for me with one exception, and I can't figure out if that's just the way it is supposed to work or if it's just a problem I need to fix.  When I use "shadowing" mode to connect to the exisitng sessions that is the "local" desktop on the server, I can't seem to get it to change the resolution of that session like RDP allows on Windows.  Is that supposed to work?  Right now, my client only supports  a lower resolution, so I can either have the screen "scaled" down to fit my local client, or I can only see a portion of the desktop... either is not very useful.

---

### Post by daflame on 2007-11-30
> **dlstyley said:**
> I just stumbled on to this thread.  I have Gutsy on AMD64 and about a week ago I installed the x86_64 DEB package from this page:

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

I realize that x86_64 is probably different that  AMD64, but that package worked fine for me.  Is that package fundamentally different than what these instructions are installing, or is basically the same thing?  

I ask because everything seems to work fine for me with one exception, and I can't figure out if that's just the way it is supposed to work or if it's just a problem I need to fix.  When I use "shadowing" mode to connect to the exisitng sessions that is the "local" desktop on the server, I can't seem to get it to change the resolution of that session like RDP allows on Windows.  Is that supposed to work?  Right now, my client only supports  a lower resolution, so I can either have the screen "scaled" down to fit my local client, or I can only see a portion of the desktop... either is not very useful.

Actually that is NOT FreeNX those are the commercial NX Server Free Edition packages and x86_64 is actually not different than amd64 really since AMD paved the way for the 64bit standard for x86.  However, these commercial packages are limited to only 2 connections.  As for shadowing, you are accessing the local desktop, so the resolution on the desktop defines the resolution of the shadow.

---

### Post by NTolerance on 2007-11-30
This guide worked for me, but I have a few questions.  I keep hearing about shadowing and VNC.  If you want to view the local display does it use VNC and as a result give slower performance?  I have x11vnc set up on my remote Ubuntu PC and I tried to connect to the local X session via FreeNX, but I got this error in the client:

```
cat: /var/lib/nxserver/db/running/sessionId{CE7980E57B50A54BF0331E90D302C74A}: No such file or directory
NX> 280 Exiting on signal: 15
```

I was able to successfully start a new X session remotely, but some of my GNOME applets crashed on both the new X session and the local X session.  Any way to fix this?

Edit:  Almost forgot to say THANK YOU for these packages and this guide.  For all of Microsoft's misgivings, Remote Desktop is a great product and there's no reason why Linux can't leverage its technology for something similar.  Since FreeNX is superior to just about all other Linux remote programs, why can't it be in the repos and be easier to set up?

---

### Post by NTolerance on 2007-11-30
> **daflame said:**
> Actually that is NOT FreeNX those are the commercial NX Server Free Edition packages and x86_64 is actually not different than amd64 really since AMD paved the way for the 64bit standard for x86.  However, these commercial packages are limited to only 2 connections.  As for shadowing, you are accessing the local desktop, so the resolution on the desktop defines the resolution of the shadow.

I don't mind the two connection limit as I'm the sole user of my remote PCs.  Does this mean shadowing works if you use the commercial edition?

---

### Post by daflame on 2007-11-30
> **NTolerance said:**
> I don't mind the two connection limit as I'm the sole user of my remote PCs.  Does this mean shadowing works if you use the commercial edition?

Yes, the commercial one has shadowing working just fine.  This is a detail being resolved right now in FreeNX.

---

### Post by daflame on 2007-11-30
> **NTolerance said:**
> This guide worked for me, but I have a few questions.  I keep hearing about shadowing and VNC.  If you want to view the local display does it use VNC and as a result give slower performance?  I have x11vnc set up on my remote Ubuntu PC and I tried to connect to the local X session via FreeNX, but I got this error in the client:

```
cat: /var/lib/nxserver/db/running/sessionId{CE7980E57B50A54BF0331E90D302C74A}: No such file or directory
NX> 280 Exiting on signal: 15
```

I was able to successfully start a new X session remotely, but some of my GNOME applets crashed on both the new X session and the local X session.  Any way to fix this?

Edit:  Almost forgot to say THANK YOU for these packages and this guide.  For all of Microsoft's misgivings, Remote Desktop is a great product and there's no reason why Linux can't leverage its technology for something similar.  Since FreeNX is superior to just about all other Linux remote programs, why can't it be in the repos and be easier to set up?

As mentioned above, VNC and shadowing are not working currently.  The method that will eventually be used to shadow sessions (I believe) in FreeNX will be desktop mirroring via x11vnc.  I don't think NX Server Free Edition does it much differently except they use their own protocol.  I think the next release of FreeNX will fix this, which I hear is coming soon.

---

### Post by dlstyley on 2007-11-30
Thanks for clearing up the difference between FreeNX and NX Server.  I should have read the entire thread before posting.  I didn't realize they were two different things.  

I also don't mind the 2 connection limit, however I do need shadowing, and to make it useful, I really need (ok, want) it to change the resolution of the session to which I'm connecting to match the client resolution.  This seems to work well in the Remote Desktop world.  

Any chance that dynamic resolution changing will be added as a feature to FreeNX (after the issues with shadowing are worked out?)

---

### Post by daflame on 2007-12-02
> **dlstyley said:**
> Thanks for clearing up the difference between FreeNX and NX Server.  I should have read the entire thread before posting.  I didn't realize they were two different things.  

I also don't mind the 2 connection limit, however I do need shadowing, and to make it useful, I really need (ok, want) it to change the resolution of the session to which I'm connecting to match the client resolution.  This seems to work well in the Remote Desktop world.  

Any chance that dynamic resolution changing will be added as a feature to FreeNX (after the issues with shadowing are worked out?)

It's more of a limitation of the technology than a failure of FreeNX.  As far as I know the commercial version is as equally limited as is Citrix server shadowing on Windows.  I think the host resolution may be able to be changed by xrandr (krandrtray on KDE), though I've never tried it.  I have heard that some versions of shadowing/vnc desktop mirroring kick the user out when you do that though.  When you log back in the resolution is changed still.  Slightly painful way, but it is an option.

---

### Post by daflame on 2007-12-02
I have some good news!  The xdialog issues are resolved!  I have pulled the files from the FreeNX trunk and made a patch for 0.7.1.  Doenload the new version of freenx for your arch from the original post again.  It looks the same, but it is not.  Reinstall freenx like so:
```
sudo dpkg -i freenx*
```
This will restore the proper NX dialogs again!

I am still working on the vnc issues.  I have narrowed it to a fault in the vncpasswd program that is in vnc-common.  TightVNC normally has the -f switch that allows you to auto-generate a password, the Ubuntu version doesn't.  I have compiled a TightVNC version which works and am contemplating creating a script that ties the library to make the password instead.  My goal is not to have to force a non-Debian style of installation.

---

### Post by daflame on 2007-12-02
I have more good news!  For those of you who are fairly brave and run a different version of Debian, I have provided source packages for your enjoyment (I know, compiling isn't always that fun).  Check out the instructions and packages on the first page again.  If you get a successful build and install, please post packages and I will make them available for everyone to enjoy.  If you find out any missing dependencies, please let me know them and I will post them too.

---

### Post by yocec on 2007-12-03
Thanks a lot for this tuto, but I still have a problem.
After several hours to figth with Nx server of nomachine and now with freenx, I don't understand, i 'me about to give up and install VNC....

Here is my problem, I carreful read this tuto, everything seems works fine except when i try to contact freeNX from the nx client : 

NX> 203 NXSSH running with pid: 276
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.222 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

On the server the file /var/log/ nxserver.log is empty

I ve tried sudo nxserver --restart
NX> 100 NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 123 Service stopped
NX> 122 Service started
NX> 999 Bye

sudo nxserver --status
NX> 100 NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 110 NX Server is running
NX> 999 Bye

Is ther something to do with crypto key of ssh ?
>> Yes it was one problem 
> cd /var/lib/nxserver
sudo -
cd home/.ssh
cp authorized_keys2 authorized_keys
chown nx authorized_keys
exit

in the tuto the "Finally download the nxcupsd-wrapper script from Fabian to the client machine (the one that needs to connect) and save it somewhere that you can use it: nxcupsd-wrapper...." section is it also for Windows clients ?

For the command sudo nxserver --adduser xxxx, xxx must be a user defined in ubuntu ?
>> Yes

I have for the moment only one user defined (my root user) must i launch the command or create before an another user ?

Finally the RDP section is optionnal ?

After the config of the key as described above, the error is not the same, I can see the available session if i try to rsume or create a new session  have the following new error (on the client) :
NX> 148 Server capacity: not reached for user: yoann
NX> 105 restoresession  --xdm_port="-1" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-xdm" --geometry="1280x992" --client="winnt" --keyboard="pc102/fr" --id="9A71A9ECE859CB6857DBE7FC8BF54235" --resize="1" 
cat: /var/lib/nxserver/db/running/sessionId{9A71A9ECE859CB6857DBE7FC8BF54235}: Aucun fichier ou rÃ©pertoire de ce type
cat: /var/lib/nxserver/db/running/sessionId{9A71A9ECE859CB6857DBE7FC8BF54235}: Aucun fichier ou rÃ©pertoire de ce type
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15


A suivre....

My conf : 
Server Xubuntu 7.10 acceded via ssh
Client Windows XP

No Firewall, ssh on port 22



Thanks a lot for your help
Yoann

---

### Post by daflame on 2007-12-04
> **yocec said:**
> Thanks a lot for this tuto, but I still have a problem.
After several hours to figth with Nx server of nomachine and now with freenx, I don't understand, i 'me about to give up and install VNC....

Here is my problem, I carreful read this tuto, everything seems works fine except when i try to contact freeNX from the nx client : 

NX> 203 NXSSH running with pid: 276
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.222 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

On the server the file /var/log/ nxserver.log is empty

I ve tried sudo nxserver --restart
NX> 100 NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 123 Service stopped
NX> 122 Service started
NX> 999 Bye

sudo nxserver --status
NX> 100 NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 110 NX Server is running
NX> 999 Bye

Is ther something to do with crypto key of ssh ?
>> Yes it was one problem 


in the tuto the "Finally download the nxcupsd-wrapper script from Fabian to the client machine (the one that needs to connect) and save it somewhere that you can use it: nxcupsd-wrapper...." section is it also for Windows clients ?

For the command sudo nxserver --adduser xxxx, xxx must be a user defined in ubuntu ?
>> Yes

I have for the moment only one user defined (my root user) must i launch the command or create before an another user ?

Finally the RDP section is optionnal ?

After the config of the key as described above, the error is not the same, I can see the available session if i try to rsume or create a new session  have the following new error (on the client) :
NX> 148 Server capacity: not reached for user: yoann
NX> 105 restoresession  --xdm_port="-1" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-xdm" --geometry="1280x992" --client="winnt" --keyboard="pc102/fr" --id="9A71A9ECE859CB6857DBE7FC8BF54235" --resize="1" 
cat: /var/lib/nxserver/db/running/sessionId{9A71A9ECE859CB6857DBE7FC8BF54235}: Aucun fichier ou rÃ©pertoire de ce type
cat: /var/lib/nxserver/db/running/sessionId{9A71A9ECE859CB6857DBE7FC8BF54235}: Aucun fichier ou rÃ©pertoire de ce type
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15


A suivre....

My conf : 
Server Xubuntu 7.10 acceded via ssh
Client Windows XP

No Firewall, ssh on port 22



Thanks a lot for your help
Yoann

BTW you cannot log in as root with NX as it prohibits this user from logging in (for obvious security reasons).  Create another user in Ubuntu with sudo privileges if you want that.

Have you tried rebooting the machine first?
If that doesn't fix it, what happens when you execute the following:
```
/usr/lib/nx/nxsetup --install --setup-nomachine-key
```

---

### Post by yocec on 2007-12-04
Thanks for this answer.

I will try this tonight (french hour) for the moment I'me at work....

Yoann

---

### Post by c-m on 2007-12-04
I have tired this and kept getting an error.

I then clicked on new and it worked. 

The only problem is that it is dog slow. It takes around 30seconds to respond to mouse clicks. Is there anyway to optimise this to speed things up at all?

I'm accessing my home pc (2mb cable) from work (8mb ADSL)

---

### Post by BassKozz on 2007-12-04
Having the same trouble **NTolerance** was having ([http://ubuntuforums.org/showthread.php?p=3867372#post3867372](http://ubuntuforums.org/showthread.php?p=3867372#post3867372)) connecting here is the debug output ```

cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
NX> 280 Exiting on signal: 15
``` 
How can I fix this?

**EDIT**: Will the following fix my problem?
> **daflame said:**
> I have some good news!  The xdialog issues are resolved!  I have pulled the files from the FreeNX trunk and made a patch for 0.7.1.  Doenload the new version of freenx for your arch from the original post again.  It looks the same, but it is not.  Reinstall freenx like so:
```
sudo dpkg -i freenx*
```
This will restore the proper NX dialogs again!

I am still working on the vnc issues.  I have narrowed it to a fault in the vncpasswd program that is in vnc-common.  TightVNC normally has the -f switch that allows you to auto-generate a password, the Ubuntu version doesn't.  I have compiled a TightVNC version which works and am contemplating creating a script that ties the library to make the password instead.  My goal is not to have to force a non-Debian style of installation.

---

### Post by yocec on 2007-12-04
@daflame
Thanks a lot, the reboot and the creation of an another user solve the authentification problem.

I had some more problem but got answer in old thread of this forum.

It may be useful for the other, here is my problems and the solutions.

My server running Xubuntu 7.1 (gutsy) so the window manager is XFCE.

Problem :
After authentication, a window "session avaliable" appears, choose new, many message appear in the dialog box, and after "Established the display connection", a windows open with !M symbol witch disapear but no desktop (the windows still be black).

Solution : 
in the nomachine client choose Unix / custom as desktop
click settings button and enter "startxfce4" in the "run the following command" input of Application section
Choose "new virtual desktop" in options section.
Save, enter your password and loggin....

that all,it works for me, thanks a lot at all (specially daflame)

I will probably made a tuto in french ubuntu forum ([http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)), can I put link to .deb package ?

Yoann
(a really happy man) :biggrin:

---

### Post by BassKozz on 2007-12-04
After reading yocec's post above :roll:, I decided to give this a shot (since I also am using Xubuntu 7.10) with a new session (instead of trying to resume a session which only gets me the following:```
cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
NX> 280 Exiting on signal: 15
```

So like yocec said I setup Custom Unix, placed "startxfce4" in the "run the following command" section and selected the "new virtual desktop" option... and here is what I got:

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/NX1.jpg[/IMG]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/NX2.jpg[/IMG]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/NX3.jpg[/IMG]:(

Here is the output of details:```
Info: Display running with pid '5080' and handler '0x150412'.

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '5580'.
Session: Starting session at 'Tue Dec  4 16:55:05 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-desktop'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Tue Dec  4 16:55:06 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Tue Dec  4 16:55:06 2007'.
Session: Session terminated at 'Tue Dec  4 16:55:06 2007'.

```

I can't win ](*,)
I've been trying [anything](http://ubuntuforums.org/showthread.php?t=618937) and [everything](http://ubuntuforums.org/showthread.php?p=3823957#post3823957) to get any VNC/Remote Desktop solution to work, with no luck, someone PLEASE help[-o<

---

### Post by daflame on 2007-12-05
> **c-m said:**
> I have tired this and kept getting an error.

I then clicked on new and it worked. 

The only problem is that it is dog slow. It takes around 30seconds to respond to mouse clicks. Is there anyway to optimise this to speed things up at all?

I'm accessing my home pc (2mb cable) from work (8mb ADSL)

As posted earlier, you may have to turn off some glitz, such as the mouse rollovers on the menu buttons on KDE.  I'm not sure about anything else since it works very well for me with KDE.  I do know that it starts slow at first since it is sending pictures to the client and each time you login it gets better because it reuses the client images.  However, the mouse rollover effects are always very slow.

---

### Post by daflame on 2007-12-05
> **B/-\ssKozz said:**
> Having the same trouble **NTolerance** was having ([http://ubuntuforums.org/showthread.php?p=3867372#post3867372](http://ubuntuforums.org/showthread.php?p=3867372#post3867372)) connecting here is the debug output ```

cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{66FB2A34CD936682FA589CE35F31A9AC}: No such file or directory
NX> 280 Exiting on signal: 15
``` 
How can I fix this?

**EDIT**: Will the following fix my problem?

I don't think you posted enough of your log to diagnose your problem, but make sure when you get the login prompt that you choose a NEW session and NOT RESUME.  The resume session feature doesn't work currently.  This is usually to resume an already started session and that works, but the default session X0 as shows up by default is NOT a running session, but the physical desktop.

---

### Post by daflame on 2007-12-05
> **yocec said:**
> @daflame
Thanks a lot, the reboot and the creation of an another user solve the authentification problem.

I had some more problem but got answer in old thread of this forum.

It may be useful for the other, here is my problems and the solutions.

My server running Xubuntu 7.1 (gutsy) so the window manager is XFCE.

Problem :
After authentication, a window "session avaliable" appears, choose new, many message appear in the dialog box, and after "Established the display connection", a windows open with !M symbol witch disapear but no desktop (the windows still be black).

Solution : 
in the nomachine client choose Unix / custom as desktop
click settings button and enter "startxfce4" in the "run the following command" input of Application section
Choose "new virtual desktop" in options section.
Save, enter your password and loggin....

that all,it works for me, thanks a lot at all (specially daflame)

I will probably made a tuto in french ubuntu forum ([http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)), can I put link to .deb package ?

Yoann
(a really happy man) :biggrin:

Please don't link directly to the .deb packages as this is hosted on my home server and I may not keep it there.  I am looking at moving it to a free online packaging repo as soon as I can (1 or 2 months time).  Instead, if you can direct them to come to this forum until I have made this change.  Then you can link directly.

---

### Post by daflame on 2007-12-05
The problem starts here I think, but without your server log (/var/log/nxserver.log) I cannot tell more.

> **B/-\ssKozz said:**
> Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-desktop'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.


It looks to me like you may have chosen not to encrypt the transmission of all traffic and chose LAN connection type.  Please use ADSL or lower and make sure that encryption of all traffic is enabled.  I found trouble when turning this option off.  I have found that using these settings is optimal even on a local network.  In NX Client 3.0 (that should be the ONLY version that is used) click the configure button and on the advanced tab, make sure none of those options are checked on.  Playing with those options is deadly in FreeNX.

---

### Post by yocec on 2007-12-05
> **daflame said:**
> Please don't link directly to the .deb packages as this is hosted on my home server and I may not keep it there.  I am looking at moving it to a free online packaging repo as soon as I can (1 or 2 months time).  Instead, if you can direct them to come to this forum until I have made this change.  Then you can link directly.

OK, no problem

---

### Post by vladdlen on 2007-12-05
Just installed this, but can't seem to get it properly working :-/ My session fails when trying to connect with unix/gnome.

Here's the output:

```
NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '124'.
Session: Starting session at 'Thu Dec  6 01:22:05 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Thu Dec  6 01:22:05 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Dec  6 01:22:05 2007'.
Session: Session terminated at 'Thu Dec  6 01:22:05 2007'.
```

(Have not ticked any of the boxes in configure/advance in the client)

When i choose unix/custom/run the default X client script on server a get a all black screen. Can't do anything but close the client. Here's the log entry for that one:

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: henrik
NX> 102 Password: 
Info: Auth method: passdb ssh 
NX> 103 Welcome to: super user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        01401A6C6CEDBE9ED94AE1BF7C978DC0 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        D78F5EC830A14B7066485BAE25BB1A8A --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        8F26FEF94E39D805DBEC41AC29C58670 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        36DD322C603B3819FBC0E32ECFAC6E57 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 startsession  --virtualdesktop="1" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="super" --type="unix-default" --geometry="1024x768" --client="winnt" --keyboard="pc102/us" --screeninfo="1024x768x32+render" 

&virtualdesktop=1&link=lan&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=super&type=unix-default&geometry=1024x768&client=winnt&keyboard=pc102/us&screeninfo=1024x768x32+render&clientproto=2.1.0&user=henrik&userip=192.168.0.109&uniqueid=3D1F94CCF71FCBB41BF6D3986BE28A27&display=1001&host=127.0.0.1 
henrik@127.0.0.1's password: 
NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
server_nxnode_echo: NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: super-1001-3D1F94CCF71FCBB41BF6D3986BE28A27
NX> 705 Session display: 1001
NX> 703 Session type: unix-default
NX> 701 Proxy cookie: 8f96107495ad0424294dd709841f6777
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 8f96107495ad0424294dd709841f6777
NX> 704 Session cache: unix-default
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: super-1001-3D1F94CCF71FCBB41BF6D3986BE28A27
server_nxnode_echo: NX> 705 Session display: 1001
server_nxnode_echo: NX> 703 Session type: unix-default
server_nxnode_echo: NX> 701 Proxy cookie: 8f96107495ad0424294dd709841f6777
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: 8f96107495ad0424294dd709841f6777
server_nxnode_echo: NX> 704 Session cache: unix-default
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status 3D1F94CCF71FCBB41BF6D3986BE28A27 Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye

```

Any solution?

---

### Post by daflame on 2007-12-06
> **vladdlen said:**
> Just installed this, but can't seem to get it properly working :-/ My session fails when trying to connect with unix/gnome.

Here's the output:

```
NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '124'.
Session: Starting session at 'Thu Dec  6 01:22:05 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Thu Dec  6 01:22:05 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Dec  6 01:22:05 2007'.
Session: Session terminated at 'Thu Dec  6 01:22:05 2007'.
```

(Have not ticked any of the boxes in configure/advance in the client)

When i choose unix/custom/run the default X client script on server a get a all black screen. Can't do anything but close the client. Here's the log entry for that one:

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: henrik
NX> 102 Password: 
Info: Auth method: passdb ssh 
NX> 103 Welcome to: super user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        01401A6C6CEDBE9ED94AE1BF7C978DC0 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        D78F5EC830A14B7066485BAE25BB1A8A --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        8F26FEF94E39D805DBEC41AC29C58670 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 listsession --user="henrik" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-default"
NX> 127 Sessions list of user 'henrik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        36DD322C603B3819FBC0E32ECFAC6E57 --------       1280x800       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: henrik
NX> 105 startsession  --virtualdesktop="1" --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="super" --type="unix-default" --geometry="1024x768" --client="winnt" --keyboard="pc102/us" --screeninfo="1024x768x32+render" 

&virtualdesktop=1&link=lan&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=super&type=unix-default&geometry=1024x768&client=winnt&keyboard=pc102/us&screeninfo=1024x768x32+render&clientproto=2.1.0&user=henrik&userip=192.168.0.109&uniqueid=3D1F94CCF71FCBB41BF6D3986BE28A27&display=1001&host=127.0.0.1 
henrik@127.0.0.1's password: 
NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
server_nxnode_echo: NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: super-1001-3D1F94CCF71FCBB41BF6D3986BE28A27
NX> 705 Session display: 1001
NX> 703 Session type: unix-default
NX> 701 Proxy cookie: 8f96107495ad0424294dd709841f6777
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 8f96107495ad0424294dd709841f6777
NX> 704 Session cache: unix-default
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: super-1001-3D1F94CCF71FCBB41BF6D3986BE28A27
server_nxnode_echo: NX> 705 Session display: 1001
server_nxnode_echo: NX> 703 Session type: unix-default
server_nxnode_echo: NX> 701 Proxy cookie: 8f96107495ad0424294dd709841f6777
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie: 8f96107495ad0424294dd709841f6777
server_nxnode_echo: NX> 704 Session cache: unix-default
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
server_nxnode_echo: NX> 710 Session status: running
server_nxnode_echo: NX> 1002 Commit
session_status 3D1F94CCF71FCBB41BF6D3986BE28A27 Running
NX> 105 server_nxnode_echo: NX> 1006 Session status: running
bye
Bye
NX> 999 Bye

```

Any solution?

Which version of Debian/Ubuntu do you have installed, what method did you use on the front page, and what desktop environment do you have installed (Gnome/KDE/Xfce/Other).

---

### Post by BassKozz on 2007-12-06
> **daflame said:**
> It looks to me like you may have chosen not to encrypt the transmission of all traffic and chose LAN connection type.  Please use ADSL or lower and make sure that encryption of all traffic is enabled.  I found trouble when turning this option off.  I have found that using these settings is optimal even on a local network.  In NX Client 3.0 (that should be the ONLY version that is used) click the configure button and on the advanced tab, make sure none of those options are checked on.  Playing with those options is deadly in FreeNX.
Did that and I still can't get it to work:```
Info: Display running with pid '6004' and handler '0x12088c'.

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '5196'.
Session: Starting session at 'Thu Dec  6 01:14:17 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-desktop'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Thu Dec  6 01:14:19 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Dec  6 01:14:20 2007'.
Session: Session terminated at 'Thu Dec  6 01:14:20 2007'.
```

---

### Post by daflame on 2007-12-06
> **B/-\ssKozz said:**
> Did that and I still can't get it to work:```
Info: Display running with pid '6004' and handler '0x12088c'.

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '5196'.
Session: Starting session at 'Thu Dec  6 01:14:17 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-desktop'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Thu Dec  6 01:14:19 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Dec  6 01:14:20 2007'.
Session: Session terminated at 'Thu Dec  6 01:14:20 2007'.
```

Could you let me know what version of Ubuntu/Debian you are using?  Which method you installed from the instructions on the firont page?
Could you please send me your /var/log/nxserver.log from your NX server?

I can't help much more without this info.

Also, when you choose a custom unix session and enter the startxfce4 in the command line you should use the FULL path to the startxfce4 script such as /usr/bin/startxfce4.  I have had many a problem solved by making sure I did this one simple thing.  I'm not sure why, but sometimes FreeNX doesn't seem to use the PATH environment on the server.  I not sure if this is an oversight or a security feature, but it can be annoying at times.

---

### Post by daflame on 2007-12-06
> **yocec said:**
> I will probably made a tuto in french ubuntu forum ([http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)), can I put link to .deb package ?

If you do make the forum, please drop a link to it here for many French speaking/writing people to benefit.

---

### Post by vladdlen on 2007-12-06
I'm on ubuntu 7.10, gutsy, running Gnome.

Not sure what you meant with "what method did you use on the frontpage", though..?

---

### Post by yocec on 2007-12-06
> **daflame said:**
> If you do make the forum, please drop a link to it here for many French speaking/writing people to benefit.

The french version of this Tuto (minus the compilation part)

[HTML]http://forum.ubuntu-fr.org/viewtopic.php?pid=1372566[/HTML]

---

### Post by mozkill on 2007-12-07
I installed NXSERVER using the FREE pre-compiled i386_64 binaries on the commercial FreeNX site for debian.

Anyway, I installed them and then also installed sshd and everything works great except that the NX client seems to pick up the desktop effects and that seems to slow it down to about the same speed as VNC.

---

### Post by diyfiesta on 2007-12-08
Hi,

Just giving this a spin but noticed I dont have *any* font paths in my xorg.conf? Is that a problem and if so where do I go to sort it out (newbie user here).

Thanks in advance,

here's my full xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "L350"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "L350"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

---

### Post by daflame on 2007-12-09
> **yocec said:**
> The french version of this Tuto (minus the compilation part)

[HTML]http://forum.ubuntu-fr.org/viewtopic.php?pid=1372566[/HTML]

Thank you for the forum posting.  I think you may have to check your dependencies though.  I have updated them on the front page.  Also, I believe it is the package named openssh-server, not ssh.  Correct me if I'm wrong, but I think that is all I noticed.  My French is not the best though, so I can't vouch for the instructions.  If someone knows French, can you verify that yocec's instructions work?  Then I will link to it on the first post.

---

### Post by daflame on 2007-12-09
> **diyfiesta said:**
> Hi,

Just giving this a spin but noticed I dont have *any* font paths in my xorg.conf? Is that a problem and if so where do I go to sort it out (newbie user here).

Thanks in advance,

here's my full xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "L350"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "L350"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

Thats actually not uncommon with a clean install of Gutsy and YES it will be a problem because NX actually uses an outdated version of Xorg in its NX X server implementation.  This means that it will likely crash as an old X server would if the font paths were missing.  You can try inserting the font path section that I have in the instructions and test it to make sure that doesn't cause trouble for your regular X windows environment.  I would verify the paths first to make sure they really are font paths on your system though.  But if you have Gutsy, those paths are likely to work.

---

### Post by daflame on 2007-12-09
> **mozkill said:**
> I installed NXSERVER using the FREE pre-compiled i386_64 binaries on the commercial FreeNX site for debian.

Anyway, I installed them and then also installed sshd and everything works great except that the NX client seems to pick up the desktop effects and that seems to slow it down to about the same speed as VNC.

What do you mean commercial FreeNX?  Do you mean NX Free Edition?  This is NOT FreeNX.  Even NoMachine's site will clarify this.  If this is the version installed I cannot support you very much since they are not the same thing at all.  However, I will do my best even so, but I recommend uninstalling them and following the guide on the first page of this forum as NX Free Edition has a 2 connection limit and I have found it to be slightly slower.

All that aside, my best suggestion is to disable desktop effects.  That can be accomplished very simply by removing it from startup if you are using KDE or turning off advanced desktop effects on Gnome.  If you still need assistance I recommend Googling "disable desktop effects (name of window environment)".  If you need finer grained control and you use Xgl, lLet me know, I have a script that can help.  If you use AIGLX for desktop effects on your computer you can either disable it or make a new Xorg config file and change your settings so that NX uses a different config than your default one.

---

### Post by daflame on 2007-12-09
> **vladdlen said:**
> I'm on ubuntu 7.10, gutsy, running Gnome.

Not sure what you meant with "what method did you use on the frontpage", though..?

What I am asking is, which of the two methods did you use in the install process posted on page 1 of this forum.  Install from packages, or compile it from source.  If I were you I'd use the packages, as I have compiled them already for Gutsy and I have thoroughly tested them too.  My employees use the one machine to log into regularly with the current version installed.  If you are having trouble try restarting the instructions and follow them word for word and line by line.  I have not written anything superfluous in those instructions and I may have updated them since you looked at them last.

Finally, make sure you choose the Gnome session, as the custom unix session is for xfce or some non-mainstream desktop environment (I am not implying that xfce is not mainsteam as I know that it is, NX just didn't include it when they built their technology), or for running rootless windows (windows that look like an app running on your computer).

---

### Post by jpgauthier on 2007-12-12
hello FreeNX gurus. Im almost there, not quite yet though. Here a sample of my nxserver.log :

```

-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: someuser
NX> 102 Password: 
Info: Auth method: passdb 
NX> 103 Welcome to: golgoth user: someuser
NX> 105 listsession --user="someuser" --status="suspended,running" --geometry="1440x900x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'someuser' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: someuser
NX> 105 startsession --session="golgoth.onsomedomain.com" --type="unix-gnome" --cache="8M" --images="32M" --link="adsl" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="1024x768+208+35" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1024x768x32+render" 

&session=golgoth.onsomedomain.com&type=unix-gnome&cache=8M&images=32M&link=adsl&nodelay=1&encryption=1&backingstore=when_requested&geometry=1024x768+208+35&media=0&agent_server=&agent_user=&agent_password=******&screeninfo=1024x768x32+render&clientproto=1.5.0&user=someuser&userip=206.1xx.xxx.xxx&uniqueid=12D46CA1ACD1B392B4EEFE4AAEA290D6&display=1000&host=127.0.0.1 
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: golgoth-1000-12D46CA1ACD1B392B4EEFE4AAEA290D6
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: cee55b53e4647e681b82000e386ed879
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: cee55b53e4647e681b82000e386ed879
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed
NX> 105 NX> 596 Session startup failed.
NX> 1001 Bye.

```

Basicaly, i can authentificate on my server but it look like there is non existant directory. Bellow is a sample of my client log :

```

NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: golgoth-1000-12D46CA1ACD1B392B4EEFE4AAEA290D6
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: cee55b53e4647e681b82000e386ed879
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: cee55b53e4647e681b82000e386ed879
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1.
/usr/lib/nx/nxserver: line 1190:  9294 Completed©              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{12D46CA1ACD1B392B4EEFE4AAEA290D6}: No such file or directory.
mv:  `/var/lib/nxserver/db/running/sessionId{12D46CA1ACD1B392B4EEFE4AAEA290D6}': No such file or directory
NX> 1006 Session status: closed
NX> 1001 Bye.
Killed by signal 15.

```

And the content of my sessionID :

sessionName=TESTBOX
display=1000
status=Failed
startTime=1197495378
foreignAddress=XXX.XXX.XX.XXX
sessionRootlessMode=0
type=unix-gnome
sessionId=8EBAEE30AE226B5C53B9495DD59DFDB1
creationTime=1197495378
userName=someuser
serverPid=
screeninfo=1024x768x32+render
geometry=1024x768+208+35
host=127.0.0.1

I know there is something about temporary directory. I went to ~/.nx and couldnt find any C-BIGNUMBER or S-BIGNUMBER directory in there. Any help will be appreciated :)

Thanks

---

### Post by mattshane on 2007-12-12
Thank you  very much for the packages! I was using the free NoMachine server, but needed
to allow three users to login, and it only allowed two.

Several posters have mentioned the confusing X0 VNC local item that always shows up 
as an existing session after logging in.

If you would like to eliminate the extra dialog when you have no active sessions, you can
turn off that feature (which doesn't currently work anyway).

In /etc/nxserver/node.conf I changed the following two settings:
ENABLE_DESKTOP_SHARING=0
ENABLE_MIRROR_VIA_VNC=0
Now it goes straight to my desktop like the NoMachine server does.

---

### Post by BassKozz on 2007-12-12
> **daflame said:**
> Could you let me know what version of Ubuntu/Debian you are using?  Which method you installed from the instructions on the firont page?
Could you please send me your /var/log/nxserver.log from your NX server?

I can't help much more without this info.

Also, when you choose a custom unix session and enter the startxfce4 in the command line you should use the FULL path to the startxfce4 script such as /usr/bin/startxfce4.  I have had many a problem solved by making sure I did this one simple thing.  I'm not sure why, but sometimes FreeNX doesn't seem to use the PATH environment on the server.  I not sure if this is an oversight or a security feature, but it can be annoying at times.
Xubuntu 7.10
Front page instruactions
See attached /var/log/nxserver.log
I tried both "startxfce4" and "/usr/bin/startxfce4", no luck :(

---

### Post by daflame on 2007-12-14
> **jpgauthier said:**
> hello FreeNX gurus. Im almost there, not quite yet though. Here a sample of my nxserver.log :

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
```

Your problem starts there...  You are getting a response of NX Server 1.5...  You should get a response of NX Server 2.1.0.  Are you sure you followed the instructions on page one of this forum?  It appears like you either have an outdated client or server, or you forgot to copy the node.conf file to the proper place.

---

### Post by daflame on 2007-12-14
> **B/-\ssKozz said:**
> Xubuntu 7.10
Front page instruactions
See attached /var/log/nxserver.log
I tried both "startxfce4" and "/usr/bin/startxfce4", no luck :(

You must have a missing library or something.  It could also be the fonts list in /etc/Xqq/xorg.conf
Make sure all the paths specified in there exist.  To make sure I installed xfce to test it.  It works, albeit a little broken in my opinion.  All I get is a desktop without anything else.  My guess is that desktop effects may be causing the troubles too.  You can disable AIGLX/XGL to see if that fixes the problem.  If it does you may need to give nxserver a custom xorg.conf file to look at.

---

### Post by daflame on 2007-12-14
So everyone the long awaited package repo may be here.  Could someone try out my new repo and let me know if it works?

deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

---

### Post by Quietlife on 2007-12-14
Hi many thanks for the repo - works nicely apart from two things :-

1) The node.conf as supplied by the repo is missing the AGENT_EXTRA_OPTIONS_X info. 
2) Standard Gutsy AMD64 installs WILL need the ¨Files¨ section adding to the xorg.conf.

Once again great stuff tyvm.

---

### Post by daflame on 2007-12-16
> **B/-\ssKozz said:**
> Xubuntu 7.10
Front page instruactions
See attached /var/log/nxserver.log
I tried both "startxfce4" and "/usr/bin/startxfce4", no luck :(

I noticed recently a posting on FreeNX.  Maybe this will help:
> Frederik schrieb:
> I have a machine running Fedora 8 with the Fedora freenx 0.7.1 and nx
> 0.2.1 packages. When I connect to the machine and try to run the
> /usr/bin/startxfce4 session, I only get a blank screen. When choosing
> GNOME, everything works fine. The blank screen does not occur if I
> leave rootless mode enabled.

I'm using /usr/bin/xfce4-session directly without the starting script.
Maybe you try that.

---

### Post by daflame on 2007-12-16
> **Quietlife said:**
> Hi many thanks for the repo - works nicely apart from two things :-

1) The node.conf as supplied by the repo is missing the AGENT_EXTRA_OPTIONS_X info. 
2) Standard Gutsy AMD64 installs WILL need the ¨Files¨ section adding to the xorg.conf.

Once again great stuff tyvm.

Yes. I am aware of  both issues.  I plan on changing the make script to include the modified node.conf and hopefully create a special script to add the missing font paths in xorg.conf.  The latter I expect will be more difficult.  Thank you for trying the repos, I will now update the front page.  For those of you that have links to the old files, I will still maintain them until February, but I will have to remove them then to save on my bandwidth as these are hosted at my home server.  This new repo is a permanently paid for site which should offer much faster downloads.

---

### Post by spottyrover on 2007-12-18
I have just tried to install nx from the instructions on the first page
All went well I thought as I could login to the other pc and all went well
( by the way a good article)
Until I rebooted the pc's and now I can not get them to talk to each other
I can ping the router from both pc's but they will not ping each other.
I installed guarddog and then opened up all of the settings but still no change.
I rebooted a number of times and still no go.
Luckily for me I have another ubuntu install and booted into that one and they could talk to each other.

the install is an amd 64x2 3800 which was updated just before I did the nx install
any help would be appreciated

Dave

---

### Post by martijntje on 2007-12-18
Thanks! I now *finally* have freenx working under Gutsy!

BTW: I was wondering, could you please make a package of nxesd?

---

### Post by valuntahr on 2007-12-19
I have recently installed FreeNX using the instructions given in the first post. However whenever I try and access my server using my Windows XP machine I get an authentication failure, does anybody have any ideas as to what might be going wrong?

---

### Post by daflame on 2007-12-19
> **spottyrover said:**
> I have just tried to install nx from the instructions on the first page
All went well I thought as I could login to the other pc and all went well
( by the way a good article)
Until I rebooted the pc's and now I can not get them to talk to each other
I can ping the router from both pc's but they will not ping each other.
I installed guarddog and then opened up all of the settings but still no change.
I rebooted a number of times and still no go.
Luckily for me I have another ubuntu install and booted into that one and they could talk to each other.

the install is an amd 64x2 3800 which was updated just before I did the nx install
any help would be appreciated

Dave

That is quite odd.  I have never seen installations of FreeNX shut down network traffic.  It sounds to me more like a kernel issue than a NX one.

I suggest viewing /var/log/messages after running ping:
```
tail -n 30 /var/log/messages
```

---

### Post by daflame on 2007-12-19
> **valuntahr said:**
> I have recently installed FreeNX using the instructions given in the first post. However whenever I try and access my server using my Windows XP machine I get an authentication failure, does anybody have any ideas as to what might be going wrong?

I'm guessing you are using the latest version of nxclient 3.0 for Windows?  I have heard there are issues with this.  I will post a working binary soon.

---

### Post by goodrench on 2007-12-19
well, I figured out what my problem was.
I was having similar issues as the ones stated here.
When I installed the nxserver package it completed with errors.
I could not connect and it said that the service was not enabled or something.
I was using dropbear instead of ssh on both machines.
once I removed dropbear and installed ssh, everything worked perfectly.
I hope this helps someone here.

---

### Post by valuntahr on 2007-12-20
> **daflame said:**
> I'm guessing you are using the latest version of nxclient 3.0 for Windows?  I have heard there are issues with this.  I will post a working binary soon.

the client version i'm using is 3.0.0-63.

---

### Post by daflame on 2007-12-20
> **valuntahr said:**
> the client version i'm using is 3.0.0-63.

I think the version I've used is 3.0.0-83.  I'm not certain about previous or later versions.  I will post a link for a compatible Windows binary.  Also for all interested, I have noticed that nx-3.1.0 has been released.  I will be working this weekend to make new packages for testing.  Anyone interested please let me know.

---

### Post by spottyrover on 2007-12-20
thanks for the reply I thought it was a bit odd too
so I reinstalled
now i get the problem of it starts up in a screen which shows the available sessions.
If i go resume i get
"
NX> 203 NXSSH running with pid: 5946
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.2.2.5 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: david
NX> 102 Password: 
NX> 103 Welcome to: asbox user: david
NX> 105 listsession --user="david" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'david' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        72BCECC8767075483AEBF0EC8DC21269 --------       1024x768       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: david
NX> 105 listsession --user="david" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'david' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        336B8DC1FE8F301781B8389BB4B549B7 --------       1024x768       Running     X0 (Local)


NX> 148 Server capacity: not reached for user: david
NX> 105 restoresession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-gnome" --geometry="1024x718" --client="linux" --keyboard="pc105/us" --id="336B8DC1FE8F301781B8389BB4B549B7" 

cat: /var/lib/nxserver/db/running/sessionId{336B8DC1FE8F301781B8389BB4B549B7}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{336B8DC1FE8F301781B8389BB4B549B7}: No such file or directory
NX> 280 Exiting on signal: 15
"

after searching this forum I found I should use start a new session when i do this i get
"NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '5900'.
Session: Starting session at 'Fri Dec 21 13:52:05 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':20.0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Fri Dec 21 13:52:05 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Session: Terminating session at 'Fri Dec 21 13:52:05 2007'.
Session: Session terminated at 'Fri Dec 21 13:52:05 2007'."

as far as I know I am using port 22 not 11000

none of the compression boxes are ticked

I installed with your packages and the instructions from the 1st page
I am using gutsy which has been updated before adding nxfree


any help would be appreciated
Thanks dave

update I found on this thread that it is better to use adsl but verry little changed .I got this
"NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '6175'.
Session: Starting session at 'Fri Dec 21 14:50:46 2007'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':20.0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Fri Dec 21 14:50:46 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Session: Terminating session at 'Fri Dec 21 14:50:46 2007'.
Session: Session terminated at 'Fri Dec 21 14:50:46 2007'.
"

---

### Post by daflame on 2007-12-24
> **spottyrover said:**
> thanks for the reply I thought it was a bit odd too
so I reinstalled
now i get the problem of it starts up in a screen which shows the available sessions.
If i go resume i get


I see.  Well, I must say I've never seen it start on DISPLAY 20 before.  The default as far as I am aware should be display 1000+ though this should not be a problem.  It does bring attention to the likelyhood of some messed up file.  Port 11000 is for font server communication and is normal.
Do you still have any traces of any commercial NX packages still installed?
Did you check for the font section of your xorg.conf file?

---

### Post by boonx on 2007-12-26
Hi I've installed freenx on my ubuntu machine.

But I get a strange error that port 5001 is already in use.

this is my log file. Can anybody help me?
NX> 203 NXSSH running with pid: 620
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 194.134.189.203 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: michiel
NX> 102 Password: 
NX> 103 Welcome to: oozo-server user: michiel
NX> 105 listsession --user="michiel" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-application"
NX> 127 Sessions list of user 'michiel' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        FB569EE4FAF59D0A7BBF7AEA976A86BB --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: michiel
NX> 105 listsession --user="michiel" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-application"
NX> 127 Sessions list of user 'michiel' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        CBDDFC4C37670C04425ABDF4D13611D4 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: michiel
NX> 105 listsession --user="michiel" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-application"
NX> 127 Sessions list of user 'michiel' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        42048BF39152DE35B0F586D82C44BC00 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: michiel
NX> 105 startsession  --rootless="1" --virtualdesktop="0" --application="startxfce4" --link="isdn" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="oozo" --type="unix-application" --client="winnt" --kbload=" --kbload=pc102/en_US" --keymap=" --keymap=en_US" --keyboard="pc102/en_US" --aux="1" --screeninfo="800x600x32+render" 

NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: oozo-server-1001-8F19CA0984CBADD7EA97CC9BDC9A1099
NX> 705 Session display: 1001
NX> 703 Session type: unix-application
NX> 701 Proxy cookie: 967761fe6b08948c68ca8fbb4a817908
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 967761fe6b08948c68ca8fbb4a817908
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/michiel/.nx/F-C-oozo-server-1001-8F19CA0984CBADD7EA97CC9BDC9A1099/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 105 /usr/lib/nx/nxserver: line 1283: 12044 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 1009 Session status: starting

NXAGENT - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '12268'.
Session: Starting session at 'Wed Dec 26 14:18:20 2007'.
Loop: WARNING! Ignoring unknown option 'kbload' with value 'pc102/en_US'.
Warning: Ignoring unknown option 'kbload' with value 'pc102/en_US'.
Loop: WARNING! Ignoring unknown option 'keymap' with value 'en_US'.
Warning: Ignoring unknown option 'keymap' with value 'en_US'.
Info: Proxy running in server mode with pid '12268'.
Error: Call to bind failed for TCP port 5001. Error is 98 'Address already in use'.
Error: Aborting session with 'Unable to open display 'nx/nx,options=/home/michiel/.nx/C-oozo-server-1001-8F19CA0984CBADD7EA97CC9BDC9A1099/options:1001''.
Session: Aborting session at 'Wed Dec 26 14:18:20 2007'.
Session: Session aborted at 'Wed Dec 26 14:18:20 2007'.
Can't open /var/lib/nxserver/db/running/sessionId{8F19CA0984CBADD7EA97CC9BDC9A1099}: No such file or directory.
mv: NX> 1006 Session status: closed
cannot stat `/var/lib/nxserver/db/running/sessionId{8F19CA0984CBADD7EA97CC9BDC9A1099}': No such file or directory
NX> 280 Exiting on signal: 15

---

### Post by spottyrover on 2007-12-26
thanks for all of your help
I finally got it going by removing and reinstalling until it worked

 my question now
1) is how do you do a private key?
2) howmany users can you have? ( i am trying a third user called f0kd7cv but i can not login to it )


thanks again Dave

---

### Post by boonx on 2007-12-28
Got it working as well.
Only thing is it is not as stable as I had hoped. 
Hopefully I get some time to fix this.

---

### Post by monstrfolk on 2007-12-28
I have been trying for 3 days to get this to work...I have reinstalled and reinstalled to no avail. 

I can connect to the server, authenticate, start a new session, and after the client says establishing display.... a window opens with the logo of what looks like an ATI logo, then the client crashes. I have an ati card installed on the server computer and an nvidia on the client...

Does this matter?   Anyone, someone, please help me.

Ohh....and when i try to log back into the freenx server...the session that had created before is still running.

---

### Post by rrolfe on 2007-12-28
Thanks for posting this i was having all sorts of trouble getting freenx to work.
followed your steps and now its working. even got the web companion working.

---

### Post by krelkor on 2007-12-30
Hi, thanks for the guide, but im having a little trouble. 

Im brand new to linux(last night) so forgive my complete noobness

Im at the point where i need to look at xorg.conf to see if its listing the fonts correctly(right after i changed to the edited node.conf). my xorg.conf is empty! i can only assume that this is not good and that i am missing some libraries?

can someone point me in the correct direction in what to do next!

thanks :)

---

### Post by monstrfolk on 2007-12-30
are you certain that you are looking at /etc/X11/xorg.conf?

---

### Post by krelkor on 2007-12-31
hmmmm, i typed in the command in terminal to edit it and it popped up empty, but when i surfed to it this morning in nautilus it is all there, stupid case sensitiveness that im not used to :p

brain fart, seems to be ok! Hopefully the rest of the setup goes smoother

---

### Post by krelkor on 2007-12-31
Another problem! i can feel im almost there though
I try to connect to my existing session(my server is locally logged in as steve, so i created a user steve for nxserver as said to do) I tried to login to resume my session so i could monitor my torrents and the windows nx client for windows spit this out at me after it connected but had an error

NX> 203 NXSSH running with pid: 3116
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.128 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: steve
NX> 102 Password: 
NX> 103 Welcome to: server user: steve
NX> 105 listsession --user="steve" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'steve' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        E7A7E1F301E58A5609D71DF85B8E83F7 --------       1680x1050      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: steve
NX> 105 listsession --user="steve" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'steve' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        415BD73127B4EB88C09D69FDA51DE5E1 --------       1680x1050      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: steve
NX> 105 listsession --user="steve" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'steve' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        39597BA25389203D4F3ACFB7E5BB5368 --------       1680x1050      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: steve
NX> 105 restoresession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X0 (Local)" --type="unix-gnome" --geometry="1680x1020" --client="winnt" --keyboard="pc102/en_US" --id="39597BA25389203D4F3ACFB7E5BB5368" --resize="1" 

cat: /var/lib/nxserver/db/running/sessionId{39597BA25389203D4F3ACFB7E5BB5368}: No such file or directory
cat: /var/lib/nxserver/db/running/sessionId{39597BA25389203D4F3ACFB7E5BB5368}: No such file or directory
NX> 280 Exiting on signal: 15


any idea how to fix it?

---

### Post by jhetrick62 on 2008-01-01
This worked well!  I do use a non-standard ssh port so you must also open the node.conf and add your port definition for your sshd server if it is not port 22 as expected.

Great tutorial.

Thanks,
Jeff

---

### Post by GSBoomer on 2008-01-01
Thanks for the thread. On a clean gutsy install this all worked very well except for the bit about editing node.conf. Prior to editing, it looked like this:

```
#AGENT_EXTRA_OPTIONS_X=""
```

The first couple of times I neglected to add -fp inside the quotes; that obviously fails. But, since it is late at night, a failed to notice (several times) that I did not remove the comment tag (#) at the beginning of the line. So, for all newbies and experienced idiots like me, and assuming you have all of these fonts installed,  this is what the line in node.conf should look like. 

```
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```

Without this line, your connection will fail. Allow me to suggest cutting and pasting.

---

### Post by DaDisbe on 2008-01-02
A big thanks GSBoomer !

Thanks to You , I have solved one problem ! :)
Now, I can see a window with No Machine symbol, but it closed immediatly :s

Nice day

---

### Post by krelkor on 2008-01-02
Ok i discovered that i get the error i posted a few posts ago when i try to resume my current session. However, i am able to connect to a new session with a new desktop. I dont like the idea of this, as i would much rather connect to the existing session. Any idea how i can make the server le tme do this?

---

### Post by monstrfolk on 2008-01-02
dadisbe....that is the exact same problem i am a having. Have you figured out anything useful to share with me?

---

### Post by atie on 2008-01-02
@daflame,
Just inform you that somehow md5sum for nx-3.0.0.diff.gz in the dsc file doesn't match with the size of the gz file actually downloaded so couldn't extract the source deb unless manipulating the value by myself.

---

### Post by DaDisbe on 2008-01-02
Yep, i solved the problem

see here :  [http://ubuntuforums.org/showthread.php?p=4041423#post4041423]("http://ubuntuforums.org/showthread.php?p=4041423#post4041423")

---

### Post by daflame on 2008-01-06
> **monstrfolk said:**
> I have been trying for 3 days to get this to work...I have reinstalled and reinstalled to no avail. 

I can connect to the server, authenticate, start a new session, and after the client says establishing display.... a window opens with the logo of what looks like an ATI logo, then the client crashes. I have an ati card installed on the server computer and an nvidia on the client...

Does this matter?   Anyone, someone, please help me.

Ohh....and when i try to log back into the freenx server...the session that had created before is still running.

I have had a similar issue with one machine when using the proprietary drivers.  I believe I resolved the problem by using  LD_PRELOAD= and referencing the correct generic video library since the proprietary drivers replace them with their modified versions.  Quite commonly this is caused by desktop effects or anything referencing 3D graphics, but I have had it happen without it.  If you do not need proprietary drivers I would recommend using the linux open source versions.  This could also happen if your fonts list is incorrect.

---

### Post by daflame on 2008-01-06
> **krelkor said:**
> Ok i discovered that i get the error i posted a few posts ago when i try to resume my current session. However, i am able to connect to a new session with a new desktop. I dont like the idea of this, as i would much rather connect to the existing session. Any idea how i can make the server le tme do this?

You CAN resume NX sessions, but you cannot access the local physical desktop session yet.  I'm still working on a solution for Ubuntu (which has a broken vncpasswd implementation).

---

### Post by daflame on 2008-01-07
> **atie said:**
> @daflame,
Just inform you that somehow md5sum for nx-3.0.0.diff.gz in the dsc file doesn't match with the size of the gz file actually downloaded so couldn't extract the source deb unless manipulating the value by myself.

That is odd.  Those are autogenerated by debuild.  I will have to rebuild and copy again.  I am moving to nx-3.1.0 on the next rebuild anyways.

---

### Post by daflame on 2008-01-10
For those of you have troubles with accessing some of the files needed for the install.  I have fixed all of paths now.  All I need to do is fix the source repos to have the correct signatures.  The links to the sources have been corrected.

---

### Post by spottyrover on 2008-01-12
trying to insatll to gutsy 64bit and get this

 sudo apt-cache show libxcomp2 libxcompext2 libxcompshad nxagent nxlibs nxproxy nxclient freenx | grep "Unable"
W: Unable to locate package nxclient


well done but the way

Dave

---

### Post by DrumNBisco on 2008-01-12
I was having connection time out issues initially after NX had been working for weeks, so i decided to remove and reinstall.  I found out that my connection timeout issues were due to recently installing firestarter and port 22 was blocked and not being forwarded correctly on the router.  I fixed this and was atleast able to tunnel through shh from my laptop now.  All in all i shouldnt have had to reinstall, just forgot to check this first.

Onto reinstalling, tried to use the repositories listed on the front page however sudo apt install would fail due to not being able to find the packages.  I browsed to the repositories and found the packages at the following link [http://www.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/](http://www.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/)

I installed the following packages
 libxcomp2_3.0.0-0_i386.deb
 libxcompext2_3.0.0-0_i386.deb
 libxcompshad_3.0.0-0_i386.deb
 nxlibs-dev_3.0.0-0_all.deb
 nxagent_3.0.0-0_i386.deb
nxproxy_3.0.0-0_i386.deb
 freenx_0.7.1-0_i386.build

as well as expect manually through synaptic

I followed all the other instructions on the main page and tried to connect from my windows xp box running NX Proxy 3.1.0

I get pretty much the same output as a few other people when the session terminates however I'm using Gnome instead of Xfce
Here's mine:

Info: Display running with pid '1728' and handler ' handler "0x470bc'

NXPROXY - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1728'
Session: Starting session at 'Sat Jan  12 16:34:05 2008'.
Warning: Connected to remote version 3.0.0 with local version 3.1.0
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding multimedia connections to port '6000'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Sat Jan 12 16:58:19 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sat Jan 12 16:58:19 2008'.
Session: Session terminated at 'Sat Jan 12 16:58:19 2008'.

Any idea what i need to do to fix this?

---

### Post by daflame on 2008-01-15
> **DrumNBisco said:**
> I was having connection time out issues initially after NX had been working for weeks, so i decided to remove and reinstall.  I found out that my connection timeout issues were due to recently installing firestarter and port 22 was blocked and not being forwarded correctly on the router.  I fixed this and was atleast able to tunnel through shh from my laptop now.  All in all i shouldnt have had to reinstall, just forgot to check this first.

Onto reinstalling, tried to use the repositories listed on the front page however sudo apt install would fail due to not being able to find the packages.  I browsed to the repositories and found the packages at the following link [http://www.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/](http://www.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/)

I installed the following packages
 libxcomp2_3.0.0-0_i386.deb
 libxcompext2_3.0.0-0_i386.deb
 libxcompshad_3.0.0-0_i386.deb
 nxlibs-dev_3.0.0-0_all.deb
 nxagent_3.0.0-0_i386.deb
nxproxy_3.0.0-0_i386.deb
 freenx_0.7.1-0_i386.build

as well as expect manually through synaptic

I followed all the other instructions on the main page and tried to connect from my windows xp box running NX Proxy 3.1.0

I get pretty much the same output as a few other people when the session terminates however I'm using Gnome instead of Xfce
Here's mine:

Info: Display running with pid '1728' and handler ' handler "0x470bc'

NXPROXY - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1728'
Session: Starting session at 'Sat Jan  12 16:34:05 2008'.
Warning: Connected to remote version 3.0.0 with local version 3.1.0
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding multimedia connections to port '6000'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Sat Jan 12 16:58:19 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sat Jan 12 16:58:19 2008'.
Session: Session terminated at 'Sat Jan 12 16:58:19 2008'.

Any idea what i need to do to fix this?

3.1.0 isn't supported yet.  I need to build new packages for NX 3.1.0.  I will post 3.0.0 Windows packages that work soon.

---

### Post by daflame on 2008-01-15
> **spottyrover said:**
> trying to insatll to gutsy 64bit and get this

 sudo apt-cache show libxcomp2 libxcompext2 libxcompshad nxagent nxlibs nxproxy nxclient freenx | grep "Unable"
W: Unable to locate package nxclient


well done but the way

Dave

Try executing:
```
sudo apt-get install nxclient
```

If that fails run:
```
sudo apt-get update
```
and pay attention to any errors there and post them.

---

### Post by daflame on 2008-01-15
I have just posted the most recently compatible version of the Windows client for FreeNX 3.0.0 on the first page.

---

### Post by daflame on 2008-01-15
> **spottyrover said:**
> trying to insatll to gutsy 64bit and get this

 sudo apt-cache show libxcomp2 libxcompext2 libxcompshad nxagent nxlibs nxproxy nxclient freenx | grep "Unable"
W: Unable to locate package nxclient


well done but the way

Dave

I apologize, I forgot the amd64 nxclient package in the repo.  I will fix this ASAP.

---

### Post by daflame on 2008-01-15
I am currently remaking the repository the right way.  The first one was more of a kludge to get one together.  I finally found all the tools I need to maintain a repo properly.  I will be uploading them tonight if all goes well.

---

### Post by jon21 on 2008-01-16
Using the instructions from this thread I tried installing Freenx on Ubuntu 7.10 Gutsy running on an Amazon EC2 server booted with a Ubuntu 7.10 image.

Everything works except for an error when starting up Gnome: "The panel encountered a problem while loading "OAFIID:Deskbar_Applet".  I click on "Don't Delete".

Then Gnome loads perfectly.  I can run apps, but they have no window Titlebar.  Trying to run System/Preferences/Windows produces an error "Window manager 'unknown' has not registered a configuration tool".

I found another thread in Ubuntu forums about OAFIID:Deskbar_Applet.  I tried removing files in the /tmp directory per the thread but that did not work.

- Jon

---

### Post by daflame on 2008-01-17
> **jon21 said:**
> Using the instructions from this thread I tried installing Freenx on Ubuntu 7.10 Gutsy running on an Amazon EC2 server booted with a Ubuntu 7.10 image.

Everything works except for an error when starting up Gnome: "The panel encountered a problem while loading "OAFIID:Deskbar_Applet".  I click on "Don't Delete".

Then Gnome loads perfectly.  I can run apps, but they have no window Titlebar.  Trying to run System/Preferences/Windows produces an error "Window manager 'unknown' has not registered a configuration tool".

I found another thread in Ubuntu forums about OAFIID:Deskbar_Applet.  I tried removing files in the /tmp directory per the thread but that did not work.

- Jon

I just read here that the deskbar applet is incompatible with NX currently:
[http://jyquentel.wordpress.com/2007/02/15/ubuntu-610-with-nomachine-nx-server/](http://jyquentel.wordpress.com/2007/02/15/ubuntu-610-with-nomachine-nx-server/)

I would venture to guess that it is because NX uses its own X libraries.

The only suggestion I can make is to log out from the local desktop and try to log in from another location.  Strangely this works for me.

---

### Post by daflame on 2008-01-17
Hello Everyone!  I still haven't had an opportunity to update to 3.1.0 yet, but I have updated the repo and uploaded a new version of FreeNX with a fixed node.conf included with it.  It also incorporates many of the bug fixes posted in this forum including:

1) X0 non-resumeable session (defaulted to off)
2) Desktop mirror sessions also non-resumeable (defaulted to off)
3) Font path defaults in extra options
4) Modified DISPLAY base to avoid port conflicts
5) Invalid spaces in config removed

The package should work almost out of the box now.  Also, all dependencies are corrected and the source is updated.  I highly recommend using the node.conf supplied in the package now since all these updates will improve quality of service.

---

### Post by daflame on 2008-01-17
> **spottyrover said:**
> trying to insatll to gutsy 64bit and get this

 sudo apt-cache show libxcomp2 libxcompext2 libxcompshad nxagent nxlibs nxproxy nxclient freenx | grep "Unable"
W: Unable to locate package nxclient


well done but the way

Dave

This is fixed now.  Just run:
```
sudo apt-get update
sudo apt-get install nxclient
```

---

### Post by emisca on 2008-01-25
I have made Etch packages from Daflame's source packages.
They are in this repository:
deb [http://download.tuxfamily.org/emiscabpo/freenx](http://download.tuxfamily.org/emiscabpo/freenx) ./
deb-src [http://download.tuxfamily.org/emiscabpo/freenx](http://download.tuxfamily.org/emiscabpo/freenx) ./

Bye,
Emilio

---

### Post by daflame on 2008-01-28
> **emisca said:**
> I have made Etch packages from Daflame's source packages.
They are in this repository:
deb [http://download.tuxfamily.org/emiscabpo/freenx](http://download.tuxfamily.org/emiscabpo/freenx) ./
deb-src [http://download.tuxfamily.org/emiscabpo/freenx](http://download.tuxfamily.org/emiscabpo/freenx) ./

Bye,
Emilio

Can I add your package lists on the front page?

---

### Post by yocec on 2008-01-28
Hello
me again, after sevral weeks i've decided to reinstall, my ubuntu computer with ubuntu server 7.10, and when I try to install freenx package i have the following error in French :

Paramétrage de freenx (0.7.1-1) ...
dpkg : erreur de traitement de freenx (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 freenx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Paramétrage de freenx (0.7.1-1) ...
dpkg : erreur de traitement de freenx (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 freenx


Can I continue the installation, how can i do ?
thanks
Yoann


EDIT : RESOLVED : 
this error seems to have no consequence after all, but every time I install a package dpkg is trying to reconfigure freenx and my config was lost, solution :
edit /var/lib/dpkg/status and change status from "ok half-configured" to "install ok installed"

Maybe this error is due to server kernel ??

---

### Post by daflame on 2008-01-31
> **yocec said:**
> Hello
me again, after sevral weeks i've decided to reinstall, my ubuntu computer with ubuntu server 7.10, and when I try to install freenx package i have the following error...


Did you install all the necessary dependency packages as described in the instructions?  I suggest removing any existing packages related to freenx/nx libs and install as described on the front page.  However, I will test this on a machine that I haven't setup yet.

BTW are you using 64bit or 32bit version?

---

### Post by daflame on 2008-01-31
I have included my GPG public key in the instructions for those who would like to authenticate their packages or are having trouble installing for this reason.

Also, I have good news.  I have succeeded in creating a replacement for nxpasswd which means that in the next release VNC proxy will work in Debian again, and no package duplication or excess dependency is necessary.  i will include it in the next freenx package release which should also include NX 3.1.0.

---

### Post by Fracture on 2008-01-31
> **daflame said:**
> 
Then add my key for authentication and update you package list:
```
wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key | sudo apt-key add -
sudo apt-get update
```


this command needs to be changed to cause wget to output to standard out

```
wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key -O - | sudo apt-key add -
sudo apt-get update
```

Also, after adding this key

```
me@host$ wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key -O - | sudo apt-key add -
--19:01:18--  http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key
           => `-'
Resolving www.datakeylive.com... 69.89.20.149
Connecting to www.datakeylive.com|69.89.20.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================================================================================================================================================================>] 1,353         --.--K/s             

19:01:18 (930.81 KB/s) - `-' saved [1353/1353]

OK

```

I get an error

```
W: GPG error: http://www.datakeylive.com gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1086D842BA41CFFC
W: You may want to run apt-get update to correct these problems

```

---

### Post by yocec on 2008-01-31
> **daflame said:**
> Did you install all the necessary dependency packages as described in the instructions?  I suggest removing any existing packages related to freenx/nx libs and install as described on the front page.  However, I will test this on a machine that I haven't setup yet.

BTW are you using 64bit or 32bit version?

Yes I've installed all the dependancy package, and for the suggestion to remove all nx package i've alredy done it : 

```
sudo aptitude purge expect openssh-server tcl8.4 libxcomp2 libxcompext2 libxcompshad nxlibs nxagent nxproxy nxclient freenx
sudo aptitude install openssh-server
sudo /etc/init.d/ssh restart

sudo aptitude install expect
(sudo aptitude install tcl8.4)     ----> see bellow
sudo aptitude install libxcomp2
sudo aptitude install libxcompext2
sudo aptitude install libxcompshad
sudo aptitude install nxlibs
sudo aptitude install nxagent
sudo aptitude install nxproxy
sudo aptitude install nxclient
sudo aptitude install freenx
```


The error came with the freenx package...

For information tcl8.4 package is installed with expect...


An my system is 32 bits


Thanks
Yoann

---

### Post by daytimer045 on 2008-01-31
Thanks for the howto.  

I can't seem to get it working, and I have been struggling to get a remote desktop working for weeks!

Followed all the steps, don't think there were any serious errors.  However, one install gave me a long list of scrollkeeper related errors.  what's this about?

Here is the error log upon connection with Unix/GNOME from Vista to my Gutsy box "birch"

I get "Session Startup failed" on NX Client.

Thanks for your help.

(Battle-scarred newbie on week 5 with Linux)

NX> 148 Server capacity: not reached for user: daytimer
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Birch" --type="unix-gnome" --geometry="1530x1020" --client="winnt" --keyboard="pc102/ca" --screeninfo="1530x1020x32+render" 

NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: birch-1001-C2E9556188463F7AD45C2E46D4F6DD64
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5ee17f0bcf4ae326399d94db86b65bbd
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5ee17f0bcf4ae326399d94db86b65bbd
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/daytimer/.nx/F-C-birch-1001-C2E9556188463F7AD45C2E46D4F6DD64/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 105 /usr/lib/nx/nxserver: line 1283: 10591 Terminated              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{C2E9556188463F7AD45C2E46D4F6DD64}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{C2E9556188463F7AD45C2E46D4F6DD64}': No such file or directoryNX> 1006 Session status: closed

NX> 280 Exiting on signal: 15

---

### Post by vertical98 on 2008-02-03
6 or so hours of checking and re-checking later - :confused:

Bear with me while I bitch for a line or two.  I know I am not the smartest kid on the block, but I'm not completely stupid either.  How ever installing FreeNX on my Ubuntu LTSP server has left me feeling like a complete moron.  I simply want to be able to connect from laptops to the ltsp machine from the outside world.  I can get VNC over SSH working no issue and my thin clients are only limited by the speed of my server, SO why oh why does this allude me?  I figured out DJBDNS so this should be a walk in the park.

Anyway, I am setting next to the ltsp machine with my trusty win2k desktop and can ssh and vnc to the ltsp machine.  I tried the NoMachine approach first and could not connect for anything.  the client said starting connection and then died with no errors on either side (client/server).  I was looking for errors like you get with X, like fatal no screens...yada yada.  That aside there was nothing that said  something failed or didn't work.    Fresh install (just in case) and tried the howto listed here and I get an: Address already in use error.

The next statement is not meant to put anyone down, but:  With the exception of the author...has anyone gotten this app to work?  Should I wait for the product to mature and just be happy with my VNC connection?

If other people have gotten it to work, then I know I can too.  

Later

Vertical

* - its only a computer, its only a computer, its only a computer, its only a computer

---

### Post by yong on 2008-02-05
hello. Does nxpasswd work for nx3.0.0? Could you fix it up in the repo package? I wonder whether I can get nxpasswd from nx2.1.0. Thanks.

> **daflame said:**
> I have included my GPG public key in the instructions for those who would like to authenticate their packages or are having trouble installing for this reason.

Also, I have good news.  I have succeeded in creating a replacement for nxpasswd which means that in the next release VNC proxy will work in Debian again, and no package duplication or excess dependency is necessary.  i will include it in the next freenx package release which should also include NX 3.1.0.

---

### Post by lobo235 on 2008-02-06
Thanks for your work in this area daflame. I was able to get freenx up and running and I can even use the latest Windows NX Client (3.1.0-6) to connect without issues.

---

### Post by johansonm on 2008-02-06
> **vertical98 said:**
> The next statement is not meant to put anyone down, but:  With the exception of the author...has anyone gotten this app to work?  Should I wait for the product to mature and just be happy with my VNC connection?

If other people have gotten it to work, then I know I can too.

No put down taken. I have gotten it to run without a issue. I followed the instructions on the main page right down the list. 

I shrank the image down since my windows desktop happens to be a bit on the large size at 19x12.

---

### Post by cfmunster on 2008-02-09
Dude you rock! I have been screwing around with VNC for days and never got past the blank gray screen. I followed your howto and got freenx working in 10 minutes. Thanks!

---

### Post by daflame on 2008-02-12
> **Fracture said:**
> this command needs to be changed to cause wget to output to standard out

```
wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key -O - | sudo apt-key add -
sudo apt-get update
```

Also, after adding this key

```
me@host$ wget http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key -O - | sudo apt-key add -
--19:01:18--  http://www.datakeylive.com/ubuntu/dists/gutsy/wjeremy.key
           => `-'
Resolving www.datakeylive.com... 69.89.20.149
Connecting to www.datakeylive.com|69.89.20.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================================================================================================================================================================>] 1,353         --.--K/s             

19:01:18 (930.81 KB/s) - `-' saved [1353/1353]

OK

```

I get an error

```
W: GPG error: http://www.datakeylive.com gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1086D842BA41CFFC
W: You may want to run apt-get update to correct these problems

```

Thank you, I have resolved the issues and updated the front page.  I have two keys for keysigning and I thought that debuild was smart enough to choose the right one, but it isn't and just chose the first available private key.  I included that key on the front page too.

---

### Post by daflame on 2008-02-12
> **yocec said:**
> Yes I've installed all the dependancy package, and for the suggestion to remove all nx package i've alredy done it : 

```
sudo aptitude purge expect openssh-server tcl8.4 libxcomp2 libxcompext2 libxcompshad nxlibs nxagent nxproxy nxclient freenx
sudo aptitude install openssh-server
sudo /etc/init.d/ssh restart

sudo aptitude install expect
(sudo aptitude install tcl8.4)     ----> see bellow
sudo aptitude install libxcomp2
sudo aptitude install libxcompext2
sudo aptitude install libxcompshad
sudo aptitude install nxlibs
sudo aptitude install nxagent
sudo aptitude install nxproxy
sudo aptitude install nxclient
sudo aptitude install freenx
```


The error came with the freenx package...

For information tcl8.4 package is installed with expect...


An my system is 32 bits


Thanks
Yoann

Try going over the instructions on the first page again.  If it still doesn't work, I may have to check out these packages again.  Does anyone else have trouble with the packages on an upgrade?

---

### Post by daflame on 2008-02-12
> **daytimer045 said:**
> Thanks for the howto.  

I can't seem to get it working, and I have been struggling to get a remote desktop working for weeks!

Followed all the steps, don't think there were any serious errors.  However, one install gave me a long list of scrollkeeper related errors.  what's this about?

Here is the error log upon connection with Unix/GNOME from Vista to my Gutsy box "birch"

I get "Session Startup failed" on NX Client.

Thanks for your help.

(Battle-scarred newbie on week 5 with Linux)

NX> 148 Server capacity: not reached for user: daytimer
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Birch" --type="unix-gnome" --geometry="1530x1020" --client="winnt" --keyboard="pc102/ca" --screeninfo="1530x1020x32+render" 

NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: birch-1001-C2E9556188463F7AD45C2E46D4F6DD64
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5ee17f0bcf4ae326399d94db86b65bbd
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5ee17f0bcf4ae326399d94db86b65bbd
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/daytimer/.nx/F-C-birch-1001-C2E9556188463F7AD45C2E46D4F6DD64/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 105 /usr/lib/nx/nxserver: line 1283: 10591 Terminated              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{C2E9556188463F7AD45C2E46D4F6DD64}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{C2E9556188463F7AD45C2E46D4F6DD64}': No such file or directoryNX> 1006 Session status: closed

NX> 280 Exiting on signal: 15

Hmmm...  SESSION_LOG_CLEAN=0 should already be set in /etc/nxserver/node.conf.  If not, you may have the wrong config file.  Which architecture are you using?  Set it to 0 in the config and try to get the session from /home/[username]/.nx and paste it here for me to review.

You could try to check your font paths again in /etc/nxserver/node.conf and /etc/X11/xorg.conf.  Sometimes the font paths are missing in stock Gutsy which is fine for Gutsy, but spells death for NX.

---

### Post by daflame on 2008-02-12
> **vertical98 said:**
> 6 or so hours of checking and re-checking later - :confused:

Bear with me while I bitch for a line or two.  I know I am not the smartest kid on the block, but I'm not completely stupid either.  How ever installing FreeNX on my Ubuntu LTSP server has left me feeling like a complete moron.  I simply want to be able to connect from laptops to the ltsp machine from the outside world.  I can get VNC over SSH working no issue and my thin clients are only limited by the speed of my server, SO why oh why does this allude me?  I figured out DJBDNS so this should be a walk in the park.

Anyway, I am setting next to the ltsp machine with my trusty win2k desktop and can ssh and vnc to the ltsp machine.  I tried the NoMachine approach first and could not connect for anything.  the client said starting connection and then died with no errors on either side (client/server).  I was looking for errors like you get with X, like fatal no screens...yada yada.  That aside there was nothing that said  something failed or didn't work.    Fresh install (just in case) and tried the howto listed here and I get an: Address already in use error.

The next statement is not meant to put anyone down, but:  With the exception of the author...has anyone gotten this app to work?  Should I wait for the product to mature and just be happy with my VNC connection?

If other people have gotten it to work, then I know I can too.  

Later

Vertical

* - its only a computer, its only a computer, its only a computer, its only a computer

There are probably hundreds of people who have it working just with these packages alone (judging by my increasing package hit rate from the same users).  But that doesn't mean your situation is the same as theirs.  What client are you using for starters?  Secondly, what else is loaded on the box and what ports do they use?

---

### Post by daflame on 2008-02-12
> **yong said:**
> hello. Does nxpasswd work for nx3.0.0? Could you fix it up in the repo package? I wonder whether I can get nxpasswd from nx2.1.0. Thanks.

There is no nxpasswd for nx 3.0.0 in reality, but I have created an expect script emulating nxpasswd by reflecting it against the vncpasswd distributed with debian/ubuntu.  However, I am preparing to release it as soon as I have a working VNC proxy attempt.  There still seems to be a problem I can't resolve.  I may wait until I have a fully working version of 3.1.0 if I continue to have trouble, since it is getting popular already.  If you want the script I have so far let me know and I will post it.

I have heard you can get it from 2.1.0, but I am against using outdated code and a duplicate code base to accomplish the same task as programs we already have.  What I have already built is more than able to do the job, since I was able to get a vncproxy session directly using the nxviewer_helper script, just not through NX yet strangely.  So my guess is that even with NX 2.1.0 nxpasswd installed it still wouldn't work yet.

---

### Post by Spitphire on 2008-02-12
.

---

### Post by ccfiel on 2008-02-12
daflame,

Hello first of all thanks for the freenx package for ubuntu. I have an issue using nxclient 3.0.0-84 that is included in your ubuntu package. I can connect to the server when i am in the same network but if not i can not connect. I have open port 22 in my router. I have   tried using windows nxclient 3.0.0.83 it works well  even if  I am not in the same network. how can i resolve this issue? hope you can help me with this. thanks in advance! :) more power

this is the error : session failled 

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '7887'.
Session: Starting session at 'Wed Feb 13 08:23:59 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-desktop'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/home/ian/.nx/cache-unix-desktop/S-31DC3BAC16F6F6F655F36B68523F8B74'.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Wed Feb 13 08:23:59 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Session: Terminating session at 'Wed Feb 13 08:25:00 2008'.



chris

---

### Post by ccfiel on 2008-02-13
ok its not the nxclient problem. i tried to other dsl connection i can connect. but my home dsl connection i can not connect. any tips?

---

### Post by satyriasis on 2008-02-14
Thanks very much for this resource.  I guess I'm sort of dense, but I can't get the client to connect.  Using the default key, I get the message:

NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Would you mind posting the steps one needs to take to actually log into the server?  I get the same message whether I'm connecting to the localhost or from a remote client.

Thanks again.

Edit:

Okay, I figured out that you need to run

$ nxserver --passwd <user>

to set the user's password in the server.  This allows me to connect via localhost, but not from the remote client. However, I thought the program was using publickey auth?  Also, I still can't get cups printing to work, even using the wrapper script.  Here's the output from the server log after it drops the remote client:

```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xxxxx
NX> 102 Password: 
NX> 103 Welcome to: satyr user: xxxxx
NX> 105 listsession --user="xxxxx" --status="suspended,running" --geometry="1024x768x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'xxxxx' for reconnect:

Display Type      Session ID     Options     Depth Screen Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------  ------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: xxxxx
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --cups="1" --media="1" --mediahelper="esd" --session="nxsession" --type="unix-gnome" --geometry="1024x718" --client="linux" --keyboard="pc105/us" --screeninfo="1024x718x24+render" 

NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: satyr-1001-5CD5F427EA755BD4787A4AFEDFD9B6E1
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 7e9f021c86bb336ebc87847b50103637
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 7e9f021c86bb336ebc87847b50103637
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.

```Thanks.

-- 
This message optimized for teletypes.

---

### Post by yocec on 2008-02-15
Thanks for your answer daflame, 

I have solved this problem : 
Paramétrage de freenx (0.7.1-1) ...
dpkg : erreur de traitement de freenx (--configure) :
le sous-processus post-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
freenx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Paramétrage de freenx (0.7.1-1) ...
dpkg : erreur de traitement de freenx (--configure) :
le sous-processus post-installation script a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
freenx

it seems it have no consequence after all, but every time I install a package dpkg is trying to reconfigure freenx and my config was lost, solution : 
edit /var/lib/dpkg/status and change status from "ok half-configured" to "install ok installed"

No more problem.


BUT for the 3rd time I re-install completely my computer, server kernel is not compatible with nvidia drivers so I reinstall ubuntu but with alternate CD to have a simple command line installation.

And for the 3rd time I have trouble with FreeNX but diferent from the 2 previous time ....


Here is the new log : 

```
...
Info: Auth method: passdb
NX> 103 Welcome to: sweetBox user: yoann
NX> 105 listsession --user="yoann" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-applicati$
NX> 127 Sessions list of user 'yoann' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- -------------------$


NX> 148 Server capacity: not reached for user: yoann
NX> 105 startsession  --virtualdesktop="1" --application="startxfce4" --link="adsl" --backingstore="1" --encryption="1"$

&virtualdesktop=1&application=startxfce4&link=adsl&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&str$
server_nxnode_echo: NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: sweetBox-1001-
NX> 705 Session display: 1001
NX> 703 Session type: unix-application
NX> 701 Proxy cookie:
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie:
NX> 704 Session cache: unix-application
NX> 707 SSL tunneling: 1
server_nxnode_echo: NX> 700 Session id: sweetBox-1001-
server_nxnode_echo: NX> 705 Session display: 1001
server_nxnode_echo: NX> 703 Session type: unix-application
server_nxnode_echo: NX> 701 Proxy cookie:
server_nxnode_echo: NX> 702 Proxy IP: 127.0.0.1
server_nxnode_echo: NX> 706 Agent cookie:
server_nxnode_echo: NX> 704 Session cache: unix-application
server_nxnode_echo: NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigat$
server_nxnode_echo: NX> 596 Session startup failed.
NX> 596 Session startup failed.
server_nxnode_echo: NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node$
NX> 105 NX> 1006 Session status: closed
session_close
server_nxnode_echo: NX> 1006 Session status: closed
NX> 1009 Session status: starting
server_nxnode_echo: NX> 1009 Session status: starting
NX> 1001 Bye.
server_nxnode_echo: NX> 1001 Bye.

```


Authentication is OK, but not session...

I don't try to resume session, I have verified my font path, I have tried to uninstall-reinstall....


Any Idea ?


By comparison with above message I noticed this :
me : 
NX> 700 Session id: sweetBox-1001-
satyriasis : 
NX> 700 Session id: satyr-1001-**5CD5F427EA755BD4787A4AFEDFD9B6E1**

Why I don't have an UID on my session id ?
idem for agent and proxie cookie 

Yoann



EDIT : RESOLVED:
It seem that openssl is required to make freenx work properly.
In this case i have installed openssl, uninstalled freenx and all dependant package : 
sudo aptitude purge expect tcl8.4 libxcomp2 libxcompext2 libxcompshad nxlibs nxagent nxproxy nxclient freenx

and re-install everything...

and it works for me....

---

### Post by daflame on 2008-02-22
> **ccfiel said:**
> ok its not the nxclient problem. i tried to other dsl connection i can connect. but my home dsl connection i can not connect. any tips?

Oftentimes this is caused by router settings and the packets are probably being blocked by your router.  The common problem is packet sizes above 1500.

---

### Post by daflame on 2008-02-22
> **satyriasis said:**
> 
Okay, I figured out that you need to run

$ nxserver --passwd <user>

to set the user's password in the server.  This allows me to connect via localhost, but not from the remote client. However, I thought the program was using publickey auth?  Also, I still can't get cups printing to work, even using the wrapper script. .....


Well, first you must make sure the wrapper script is chmod a+x [wrapper filename] where [wrapper filename] is the name of the file where you saved it.  Then you need to setup the wrapper script in the client setup on the environment page where it says system CUPS daemon.  Make sure you use the FULL PATH there.  As for remote, how remote?  Did you try within the same network first?

---

### Post by daflame on 2008-02-22
> **yocec said:**
> 
EDIT : RESOLVED:
It seem that openssl is required to make freenx work properly.
In this case i have installed openssl, uninstalled freenx and all dependant package : 
sudo aptitude purge expect tcl8.4 libxcomp2 libxcompext2 libxcompshad nxlibs nxagent nxproxy nxclient freenx

and re-install everything...

and it works for me....

Good to hear, sorry I couldn't be of any help in the matter.  I hope others can learn from your experiences though.

---

### Post by northernx on 2008-02-22
Thank for providing this.  A very useful post.  A very smooth implementation.

Client (Source):  Windows XP SP2
Server (Target): Kubuntu Desktop 'Gutsy Gibbon' 7.10

---

### Post by greavette on 2008-02-25
Hello,

A big thank you to daflame for starting this thread!  Your instructions for installing Freenx on Gusty worked very well for me.  I've only connected to my Ubuntu box from my Windows laptop within my own home network and I'm very impressed at the responsiveness of my Ubuntu box using Freenx.  

I would like to try using Freenx from outside my home network and I have some questions that I'm hoping someone can give me some direction on.

[LIST]
[*]  Before finding Freenx, I've used VNC with Hamachi on all my computers.  I like the fact that with the Hamachi ip address, I never have to ask a family member to tell me their ip address so I can connect to them.  I would like to use Hamachi with Freenx as well and I would like to know if anyone has done this before?  I have Hamachi on my Ubuntu box and Hamachi on my Window laptop.  How do I use the Hamachi address instead of SSH to connect the two PC's?  Do I change the port number from 22 (for SSH) to a Hamachi port?  If anyone has done this with Hamachi, which port did you use?  I've googled and searched and found nothing so I'm hoping someone here has some ideas.[/LIST]

[LIST]
[*]  There are times where I am using a PC that doesn't have have Hamachi installed, so using SSH to connect to my Ubuntu box would be useful.  Does my Ubuntu box need to have a static ip in order for me to use Freenx?  If SSH needs to have a static ip where I need to use companies like dyndns.com or no-ip.com, which company is the best to use?[/LIST]

[LIST]
[*]  I don't understand when to use or not use the SSH keys?  Do I need to use the SSH key to connect or is this an option to keep my connection secure?  It looks to me that using the SSH key is optional.  Would only using SSH with a password and not the key mean an unsecure connection?[/LIST]

[LIST]
[*]  I've tried to find a good tutorial on how to connect to my Ubuntu box's current session without starting a new session with Freenx.  Since my Ubuntu box is always on, I would rather just connect to the current session.  Has anyone found a good tutorial/thread/blog they can point me to on how to do this?[/LIST]

I'm really hoping someone has an answer to using Hamachi since I don't want to leave a port open on my router.  Although on the flip-side it can be said that with my router I have control and don't need the services of a third party company like Hamachi does.  If anyone would like to throw in their two cents as to which option is best, I'd love to hear it!

Thanks in advance for any help you may provide!

---

### Post by daflame on 2008-02-26
> **greavette said:**
> A big thank you to daflame for starting this thread!  ...
You are very welcome.  It has been a pleasure and a challenge thus far.
> **greavette said:**
> I would like to try using Freenx from outside my home network and I have some questions that I'm hoping someone can give me some direction on.
A worthy endeavor, since that is the main intent of NX.  Responsive desktops over low bandwidth connections.

> **greavette said:**
> I would like to use Hamachi with Freenx ... anyone has done this before?
Yes, I am sure someone has done this before.  I have installed hamachi on my linux box as well, and I believe you get an address assigend to you which should you can use the same way.  You might be able to use the same method to connect, but disable encryption and use the hamachi IP of the server to connect to it.  No port changes should be required.

> **greavette said:**
> There are times where I am using a PC that doesn't have have Hamachi installed, so using SSH to connect to my Ubuntu box would be useful.  Does my Ubuntu box need to have a static ip in order for me to use Freenx?
Yes, or a statically assigned address via DHCP MAC address static leases will work too.  This is not necessary for the hamachi solution unless you want to open specific ports for hamachi.

> **greavette said:**
> If SSH needs to have a static ip where I need to use companies like dyndns.com or no-ip.com, which company is the best to use?
These companies own domains for which they allow you to have a free subdomain.  Such as, test.no-ip.org or test.dyndns.org.  You can point those to your public address and then you only have to use the dynamic DNS name from then on.  Both have internet methods for automatically refreshing when your public IP changes. You just need to install the update software in the server.  I cannot make a recommendation personally, since I have used both I would have to say it depends on what your router supports since I would recommend using the features built into your router first (low maintenance).

> **greavette said:**
> I don't understand when to use or not use the SSH keys?  Do I need to use the SSH key to connect or is this an option to keep my connection secure?  It looks to me that using the SSH key is optional.  Would only using SSH with a password and not the key mean an unsecure connection?
As far as I know the password is ALWAYS sent securely, but the session is encrypted by the SSH tunneling.  Please let me know if this is incorrect.  As far as SSH keys are concerned, why are you concerned?  I think they are always needed, but it will only prompt you once to accept a key unless it changes.

> **greavette said:**
> I've tried to find a good tutorial on how to connect to my Ubuntu box's current session without starting a new session with Freenx.  Since my Ubuntu box is always on, I would rather just connect to the current session.  Has anyone found a good tutorial/thread/blog they can point me to on how to do this?
Currently there isn't a way except to use VNC on a new FreeNX session and connect to the local desktop.  However, if you start a FreeNX session on your home machine and work on the windowed session, you can pick it up elsewhere as long as you suspend the session. (Sometimes even if you don't)  I recommend using Linux to resume Linux sessions and Windows to resume Windows sessions.  It doesn't seem to work any other way.  Also, you should make the session to resume the same desktop dimensions.  It is more expedient that way.

> **greavette said:**
> I'm really hoping someone has an answer to using Hamachi since I don't want to leave a port open on my router.  Although on the flip-side it can be said that with my router I have control and don't need the services of a third party company like Hamachi does.  If anyone would like to throw in their two cents as to which option is best, I'd love to hear it!

Thanks in advance for any help you may provide!
Hamachi is certainly possible, but I do implore those that use such systems that whomever you allow on your hamachi network is virtually similar to them being on your LOCAL network, so if you have anything that you want protected from them I recommend you take such precautions since they have equivalent to local access to your computers.  Hamachi bypasses all the normal checking that your router does to block would be attackers/trojans/worms.  Make sure you trust the machines that share data across it.

---

### Post by kwaanens on 2008-02-26
I guess I posted this in the wrong thread: [http://ubuntuforums.org/showthread.php?t=467219&page=7](http://ubuntuforums.org/showthread.php?t=467219&page=7)

So:

2 small questions:

- If I want to access my freenx server computer from somewhere not on the local network, what host do I put in. I currently connect to the computer name, but that doesn't work on the internet, I'm assuming?

- Is there any way I can be able to copy files over freenx+ssh easily? I can currently use the clipboard across computers, but not files.

Thanks for a great howto!

I'm using Gutsy 64 bit on both server and client, and had to fiddle around with some stuff to get it working.

---

### Post by kwaanens on 2008-02-26
Also, is there any way to make the server keep having e.g. Amarok play after I terminate the session? Currently, it shuts down when I terminate the session.

---

### Post by paoletto on 2008-03-04
First of all thanks a lot for having packaged freenx for gutsy! It works very well and
since i tried NX many years ago (with pstn modem) i wished to have it on my machine
in place of vnc

> **daflame said:**
> 

Currently there isn't a way except to use VNC on a new FreeNX session and connect to the local desktop.  However, if you start a FreeNX session on your home machine and work on the windowed session, you can pick it up elsewhere as long as you suspend the session. (Sometimes even if you don't)  I recommend using Linux to resume Linux sessions and Windows to resume Windows sessions.  It doesn't seem to work any other way.  Also, you should make the session to resume the same desktop dimensions.  It is more expedient that way.


I'd like to ask you if you think that it will be possible to reattach a nx session from everywhere in the near future.
It's quite pissing that i cant attach from windows sessions i create on linux and vice versa and it binds me
to vnc for now..

---

### Post by satyriasis on 2008-03-04
Thanks, daflame, for this great resource.  I have one note and a question.

First, your installation routine puts the ssh keys in ~/.ssh/authorized_keys2, but the Ubuntu sshd default is ~/.ssh/authorized_keys.  Don't know if it should make a difference, but I had to copy your key to my existing authorized_keys.

My question is about proxying RDP through NX.  Could you outline the steps of how that's done?

Thanks again.

---

### Post by dlopez on 2008-03-06
Hello there!!

This is mi first time at forum.  I'm using Ubuntu for years ago and always I could solve the problems until now!!

I installed freenx without problems following the post of daflame, and it works perfectly with all the users of my computer except with my login.  When I log appear the main window (!m) and, inmediatly, it closes unexpectedly.

I have not found anything significant in the logs...
Has it happened to someone?

Thanks!!!
David.

PD: Sorry for my english!!

---

### Post by satyriasis on 2008-03-06
Have you run the commands "nxserver --adduser <username>" and "nxserver --passwd <username>"?

---

### Post by dlopez on 2008-03-06
> **satyriasis said:**
> Have you run the commands "nxserver --adduser <username>" and "nxserver --passwd <username>"?

Yes, I did.  I am in the "nxserver --listuser".

But I have noticed a strange behavior. I can also connect with users who are not on the list. WHY???  I don't understand...

Have somebody any idea?

Thanks,
David.

---

### Post by curiogeo on 2008-03-11
Not sure what to look for and perhaps I have conflicting installs.

I installed NX from the nomachine website and when it did not work I tried to install this version over top of it.  The install seems to have completed successfully with no errors.  The problem I am having is that when I attempt to connect with the only user I have created so far I see the session seems to start and then it fails and the following is reported back in the details:

Info: Display running with pid '5540' and handler '0x140384'.

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1376'.
Session: Starting session at 'Tue Mar 11 01:55:33 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Tue Mar 11 01:55:34 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Tue Mar 11 01:55:35 2008'.
Session: Session terminated at 'Tue Mar 11 01:55:35 2008'.


Not seeing any change or messages in the nxserver log or in messages log

I am not sure where to look for the problem and of course can't figure out what to fix.  What might I be missing here?

---

### Post by dlopez on 2008-03-11
> **curiogeo said:**
> Not sure what to look for and perhaps I have conflicting installs.

I installed NX from the nomachine website and when it did not work I tried to install this version over top of it.  The install seems to have completed successfully with no errors.  The problem I am having is that when I attempt to connect with the only user I have created so far I see the session seems to start and then it fails and the following is reported back in the details:

Info: Display running with pid '5540' and handler '0x140384'.

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1376'.
Session: Starting session at 'Tue Mar 11 01:55:33 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-gnome'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11001'.
Session: Session started at 'Tue Mar 11 01:55:34 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Tue Mar 11 01:55:35 2008'.
Session: Session terminated at 'Tue Mar 11 01:55:35 2008'.


Not seeing any change or messages in the nxserver log or in messages log

I am not sure where to look for the problem and of course can't figure out what to fix.  What might I be missing here?

This is also my problem.  When I attempt to connect with the user I have created so far the validation is ok but the graphic session fails.  And I can connect with the new users I have created perfectly!!!
I did everything especified in the post and I have reinstalled the freenx several times with the same result.

What's the problem??
David.

---

### Post by Pesho on 2008-03-12
I had problems connecting to my FreeNX server (installed according to this thread). Occasionally it would succeed, but most of the times nxclient would display different error messages and not establish connection. Finally I found the solution - it turned out that nxagent was timing out. I solved it by uncommenting the following line in /etc/nxserver/node.conf:

```
#AGENT_STARTUP_TIMEOUT="60"
```@**daflame**, I think you should uncomment it by default in node.conf. Googling showed that quite a few other users are having the same problem, and it can be hard to diagnose as the error messages are not really helpful.

P.S. I'm using Hardy, but your packages work fine =D>

---

### Post by curiogeo on 2008-03-12
I found the issue.  It was buried in the forum archives.

"I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l" and ".Xauthority-c" in your home dir. Delete them if they exist."

As soon as I erased all three .Xauthority (the quote only suggests erasing 2 of them - that failed) files the client held the connection with the nx server under my original user.

The post is: [http://ubuntuforums.org/archive/index.php/t-57592.html](http://ubuntuforums.org/archive/index.php/t-57592.html)

Hope this helps anyone in the same boat I was in.:grin::biggrin:

---

### Post by dlopez on 2008-03-14
> **curiogeo said:**
> I found the issue.  It was buried in the forum archives.

"I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l" and ".Xauthority-c" in your home dir. Delete them if they exist."

As soon as I erased all three .Xauthority (the quote only suggests erasing 2 of them - that failed) files the client held the connection with the nx server under my original user.

The post is: [http://ubuntuforums.org/archive/index.php/t-57592.html](http://ubuntuforums.org/archive/index.php/t-57592.html)

Hope this helps anyone in the same boat I was in.:grin::biggrin:

THANKS!!!!!
It worked, that was the problem.
David.

---

### Post by daflame on 2008-03-14
> **kwaanens said:**
> I guess I posted this in the wrong thread: [http://ubuntuforums.org/showthread.php?t=467219&page=7](http://ubuntuforums.org/showthread.php?t=467219&page=7)

So:

2 small questions:

- If I want to access my freenx server computer from somewhere not on the local network, what host do I put in. I currently connect to the computer name, but that doesn't work on the internet, I'm assuming?

- Is there any way I can be able to copy files over freenx+ssh easily? I can currently use the clipboard across computers, but not files.

Thanks for a great howto!

I'm using Gutsy 64 bit on both server and client, and had to fiddle around with some stuff to get it working.

I'm sorry to say that currently the file system mounting doesn't function correctly.  I'm not sure why, but it trys to create a folder $(SHARES) instead of creating the proper folder.  This folder name breaks KDE and I'm not sure where to go to fix it just yet.  I will fix this in the upcoming release though.

---

### Post by daflame on 2008-03-14
> **kwaanens said:**
> Also, is there any way to make the server keep having e.g. Amarok play after I terminate the session? Currently, it shuts down when I terminate the session.

Simply put, no.  unless you bind Amarok to the live local display :0 under a separate shell session like screen can provide. It will terminate upon logging out.  This is by design, because you do not want users creating rogue processes on the system.

---

### Post by daflame on 2008-03-14
> **paoletto said:**
> First of all thanks a lot for having packaged freenx for gutsy! It works very well and
since i tried NX many years ago (with pstn modem) i wished to have it on my machine
in place of vnc



I'd like to ask you if you think that it will be possible to reattach a nx session from everywhere in the near future.
It's quite pissing that i cant attach from windows sessions i create on linux and vice versa and it binds me
to vnc for now..

I can't say if it ever will be possible, but I sure hope so, because just like you I would like access to suspend and resume between Windows and Linux.  This is a matter of compatibility I think.  The windows sessions aren't exactly the same since you run a different X server on windows.  I still wonder if when the VNC shadowing is resolved on Debian if you could shadow a running session instead.  It may not be as fast, but it would certainly be better than nothing.

---

### Post by daflame on 2008-03-14
> **satyriasis said:**
> Thanks, daflame, for this great resource.  I have one note and a question.

First, your installation routine puts the ssh keys in ~/.ssh/authorized_keys2, but the Ubuntu sshd default is ~/.ssh/authorized_keys.  Don't know if it should make a difference, but I had to copy your key to my existing authorized_keys.

My question is about proxying RDP through NX.  Could you outline the steps of how that's done?

Thanks again.

It's simply a matter of installing rdesktop on the server:
```
sudo apt-get install rdesktop
```

Then at the client end choose Windows, then click the settings button to setup the server and domain to log into.  Make sure you use a server name that linux can resolve an IP to.  Enter your credentials here if they differ on the windows machine.

---

### Post by daflame on 2008-03-14
> **dlopez said:**
> Hello there!!

This is mi first time at forum.  I'm using Ubuntu for years ago and always I could solve the problems until now!!

I installed freenx without problems following the post of daflame, and it works perfectly with all the users of my computer except with my login.  When I log appear the main window (!m) and, inmediatly, it closes unexpectedly.

I have not found anything significant in the logs...
Has it happened to someone?

Thanks!!!
David.

PD: Sorry for my english!!

First off, make sure your client configuration is correct, and delete all the X authority files if they are present in your home directory (.XA*).

If that fails try to deleted your profile and recreate it.

---

### Post by daflame on 2008-03-14
> **Pesho said:**
> I had problems connecting to my FreeNX server (installed according to this thread). Occasionally it would succeed, but most of the times nxclient would display different error messages and not establish connection. Finally I found the solution - it turned out that nxagent was timing out. I solved it by uncommenting the following line in /etc/nxserver/node.conf:

```
#AGENT_STARTUP_TIMEOUT="60"
```@**daflame**, I think you should uncomment it by default in node.conf. Googling showed that quite a few other users are having the same problem, and it can be hard to diagnose as the error messages are not really helpful.

P.S. I'm using Hardy, but your packages work fine =D>

Duly noted...  The next release will set that by default.

---

### Post by yohansb on 2008-03-17
I was receiving a similar error. The problem in my case was due to the way I had set up ssh.

== error message I received ==

NX> 105 startsession  --link="lan" --backingstore="1"
--encryption="1" --stream="0" --cache="16M"
--images="64M"
--shmem="1" --shpix="1" --strict="0"
--composite="1"
--samba="1" --media="1" --mediahelper="esd"
--imagecompressionmethod="3" --imagecompressionlevel="-1"
--render="1" --session="xyz" --type="unix-gnome"
--geometry="1280x971" --client="winnt"
--keyboard="pc102/en_US" --screeninfo="1280x971x32+render" 

Permission denied (publickey,password).
NX> 280 Exiting on signal: 15

The NX service is not available or the NX access was
disabled on host abc.xyz

== cause of error ==
ssh is denying access to the new username


== testing ssh ==
If I run this on the server:
*	ssh -p 12345 newUserName@localhost
...the result will be: 
*	Permission denied, please try again.
and after a few more attempts:
*	Permission denied (publickey,password).

== fix ==

* edit /etc/ssh/sshd_config
	add user to "AllowUsers" option, ie:
	AllowUsers nx [etc..] newUserName

* /etc/init.d/ssh restart
* now try again with ssh
	ssh -p 12345 newUserName@localhost
.. it should work now! [well it did for me]

---

### Post by malaprohibita on 2008-03-17
Wow!  This worked fantastically.  Thanks very much for such a comprehensive guide.

---

### Post by daflame on 2008-03-23
GOOD NEWS!!!

I have finally been able to compile a new version with NX 3.1.0 support thanks to Fabian Franz the original maintainer of FreeNX releasing the new 0.7.2 version which resolves all the nagging issues that we have been dealing with.  VNC proxy now works as well as remote shares as mounted directories.  Now only one patch file is necessary to make NX work on Debian.  All customized defaults have been moved out of the node.conf.  The name has changed to freenx-server since a freenx-client is now available designed in QT.  I will release this when it becomes better, it is still beta and has issues.

All that is left is to make a build for i386, since all my testing is 64bit currently and I will release it.

---

### Post by daflame on 2008-03-24
Ok, the update is complete.  I will now update the instructions on the front page.  Most of the instructions aren't necessary now.  Make sure you update to freenx-server since the package name changed:
```
sudo apt-get install freenx-server
```
Make sure to backup your node.conf.  I recommend that you use the package supplied version since it has undergone a major version overhaul.

Then update your libraries after:
```
sudo apt-get update
```

I still have one caveat with the vnc proxy.  It doesn't automatically choose the right size for you or scale it.  You MUST choose the right width and height when you create the connection details.  The scrollbar is completely useless in vncviewer, so an alternative viewer would be appreciated.  But VNC mirroring of NX desktops and the local X0 desktops all work!  Shadowing suspended sessions is NOT recommended though.

---

### Post by dasbooter on 2008-03-24
excellent timing. I just am getting a fresh install of gutsy going after using feisty for so long, along with nomachines "free" packages. I sort of skipped a  few posts here ;) is the file sharing working properly or even improperly, I like that feature. Thanks for your hard work I will probably give these packages a try. Is the new server now incompatible with nomachines cliens ?

---

### Post by daflame on 2008-03-24
Well, I have good news regarding the file sharing.  It wasn't working logging in locally initially even though it gave me the right message on login.  However, when connecting to a remote machine it worked just fine.  Now it also works locally.  So all I can think is that I needed to update my NX client to 3.1.0 and I hadn't done that yet when testing it.  Side note: File sharing requires Samba installed and configured.  As well as smbfs.

Also, I mentioned above that it only takes one patch, but I had to add a second patch to fix X0 VNC local session shadowing.  Thats right, VNC to the physical desktop with no VNC server setup required.  This was a bug and not related to getting it to work on Debian, so I made it into a separate patch.

---

### Post by dasbooter on 2008-03-25
Can somebody set me straight in terms of desktop shadowing. My understanding is that it enables one to share a desktop with another eg you can watch somebody at a remote location move your cursor.I remember you could do this in suse with vnc but I also remember gkrellm showing my cpu was pinned right out. I wonder if what I am experiencing is a result of the implementation of shadowingI have noticed with nomachines packages that the servers desktop gets pretty screwed up after I have logged in from a remote location. The server has dual monitors but the client machine only has the single monitor so as soon as I log in with the client when I get back to the server machine I find gnome panel and the icons have moved into the one screen. Does anyone have similiar experience with this sort of thing. Does this happen with the freenx packages. I guess it is a small thing anyways.

---

### Post by daflame on 2008-03-25
> **dasbooter said:**
> Can somebody set me straight in terms of desktop shadowing. My understanding is that it enables one to share a desktop with another eg you can watch somebody at a remote location move your cursor.I remember you could do this in suse with vnc but I also remember gkrellm showing my cpu was pinned right out. I wonder if what I am experiencing is a result of the implementation of shadowingI have noticed with nomachines packages that the servers desktop gets pretty screwed up after I have logged in from a remote location. The server has dual monitors but the client machine only has the single monitor so as soon as I log in with the client when I get back to the server machine I find gnome panel and the icons have moved into the one screen. Does anyone have similiar experience with this sort of thing. Does this happen with the freenx packages. I guess it is a small thing anyways.

Unfortunately this is probably due to the fact that dual monitor support isn't enabled in NX by default and I don't think you can enable it either with NoMachine's binary version, but you don't necessarily need to log into the physical desktop to work on the machine.  I would recommend using an NX session separate from the physical desktop whenever possible.
It may also be that your display driver is getting reinitialized if you find this still happens from a normal NX session.  The only option in this case is to use a different xorg.conf file for NX that uses the basic svga driver or something that doesn't affect your normal display.  I don't think NX even uses this anyways except when initializing 3D support, and since NX uses an outdated GLX version that might not even work properly anyways.  Soon though, we will have VMGL support and remote 3D applications will also be possible in virtual machines using FreeNX.

So, I guess the best answer is that most of this is either working or being resolved in FreeNX.  I wouldn't hold my breath with NoMachine, since their focus is only for profit, they will only design what makes them more money.  On the open source initiative side, we design what makes sense to us and the users want whether it is profitable or not.

---

### Post by dasbooter on 2008-03-26
> **daflame said:**
>   I would recommend using an NX session separate from the physical desktop whenever possible.

I kind of always thought I was using a separate session from the physical machine because I am in fact logged in from 2 separate machines.I am logged into the physical desktop and logged in with the same user from a remote desktop. I know one of the powers of Linux is the ability to be logged into with the same user with 2 different sessions simultaneously but I guess that is the extent of my knowledge and there for I have issues. It would be nice if the settings for the desktop would stay separate for each session; example it is a guilty pleasure to have the screen saver enabled on the physical desktop but downright impractical to have it enabled on the remote desktop (the compression overhead is killer even for nx) but I have never been able to have the screen saver enabled for one and not the other.... boohoo me ;) I think I will live on anyways. getting packages now. It has been awhile hopefully the setup is the same :)

---

### Post by dasbooter on 2008-03-26
Installed and followed directions but 

Authentication failed for user xxxxx

This happens both from a remote location(windows client from the first page of this thread) and locally from the server. Putty works fine from the windows machine. Have tried each time restarting the server adding port 22 to firestarter ( I had initially disabled only but probably iptables rules were still active). Changed the passwd for the user. Readded the user. Restarted the whole darn system (damn u when in doubt windows habit;) ) Manually added the ssh key as per the first page. The initial connecttion asks u to accept the key which was encouraging... Need a little help here.

hmm tried setting it up again and got some interesting warnings:
```
root@fatman:/home/xxxxxx# nxsetup --clean --purge --install --setup-nomachine-key
Removing special user "nx" ...done
Removing session database ...done
Removing logfile ...done
Removing home directory of special user "nx" ...done
Removing configuration files ...done
Setting up /etc/nxserver ...done
Generating public/private dsa key pair.
Your identification has been saved in /etc/nxserver/users.id_dsa.
Your public key has been saved in /etc/nxserver/users.id_dsa.pub.
The key fingerprint is:
41:ea:79:bf:80:96:f5:d0:9d:1f:87:fd:8f:6b:7d:48 root@fatman
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...Adding system user `nx' (UID 111) ...
Adding new user `nx' (UID 111) with group `nx' ...
Creating home directory `/var/lib/nxserver/home' ...
Password changed.
done
Adding user "nx" to group "utmp" ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so:/usr/lib/libXcompshad.so:/usr/lib/libXrender-nx.so.1". /usr/lib/libXcomp.so could not be found. Users will not be able to run a single application in non-rootless mode.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is 05:c2:c0:20:d9:9b:e9:b3:ae:99:ae:a8:a0:11:79:85.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 105 quit
Quit
NX> 999 Bye
<--- done

Ok, nxserver is ready.
PAM authentication enabled:
  All users will be able to login with their normal passwords.

  PAM authentication will be done through SSH.
  Please ensure that SSHD on localhost accepts password authentication.

  You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!


```

[SIZE="5"][COLOR="Red"]got it working[/COLOR][/SIZE]

Ok checked /var/log/nxserver.log and I was getting wrong password errors
I changed the password to something simple and was able to log on. I have a space in my password to increase its strength this is probably the problem can I add it manually somewhere.

Have I broken anything by setting up things manually with nxsetup I received a bunch of warnings ?

[COLOR="Red"][SIZE="4"]Update[/SIZE][/COLOR]

Cannot get filesharing to work. I have uncommented this line in node.conf```
#SAMBA_MOUNT_SHARE_PROTOCOL="both"
``` and restarted the server but I get this.Samba and smbfs are installed and drive mapping and mounting via smb4k both work although nothing is mounted while I am attempting the remote session. This is the result :
[[IMG]http://img329.imageshack.us/img329/9074/97740736xe4.th.png[/IMG]](http://img329.imageshack.us/my.php?image=97740736xe4.png)

---

### Post by BlizzofOZ on 2008-03-27
Very new to linux/Ubuntu...

I originally put in sources.list
deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

And after doing the key stuff, I now have this:
deb [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main
deb-src [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main



When I went to update my sources, I recieved this error:
Failed to fetch [http://packages.datakeylive.com/ubuntu/dists/gutsy/Release.gpg](http://packages.datakeylive.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'packages.datakeylive.com'
Failed to fetch [http://packages.datakeylive.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://packages.datakeylive.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not resolve 'packages.datakeylive.com'
Failed to fetch [http://packages.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://packages.datakeylive.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve 'packages.datakeylive.com'
Failed to fetch [http://packages.datakeylive.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://packages.datakeylive.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve 'packages.datakeylive.com'
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Any ideas?

---

### Post by dasbooter on 2008-03-27
Sorry what did you do with key stuff... can you be more explanative. 

Enter the code from the first page in the terminal line by line to add the keys...

freenx is a little difficult for first time linuxers some times all goes well sometimes well ... be determined

Your sources list should look like this in /etc/apt/sources.list at the end your should have
deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

I do not have :
deb [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main
deb-src [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main

---

### Post by satyriasis on 2008-03-28
I'm using the recently-posted Windows client to access an nxserver running on my home machine.  It works very well, but I have to set the window size to "Available Space" in order to get the entire desktop on the screen.  I haven't  been able to figure out how to switch between my NX window and my regular Windows desktop that's running behind the client.  Is there any way to do this?

I understand that NX won't run a rootless window, but is there some escape sequence that will allow me to switch it to the background and call it back when I need it?

Thanks again for all the work you've put into making this resource available to the community!  I hope you'll have the time and energy to recompile when the LTS version is issued.  That would be great.

---

### Post by BlizzofOZ on 2008-03-28
> **dasbooter said:**
> Sorry what did you do with key stuff... can you be more explanative. 

Enter the code from the first page in the terminal line by line to add the keys...

freenx is a little difficult for first time linuxers some times all goes well sometimes well ... be determined

Your sources list should look like this in /etc/apt/sources.list at the end your should have
deb [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main
deb-src [http://www.datakeylive.com/ubuntu](http://www.datakeylive.com/ubuntu) gutsy main

I do not have :
deb [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main
deb-src [http://packages.datakeylive.com/ubuntu](http://packages.datakeylive.com/ubuntu) gutsy main

Please ignore my post... I was not paying attention.  I copied and pasted the previous line, which had "packages" and not "www"... which I missed.

I'm installing at the moment...

---

### Post by BlizzofOZ on 2008-03-28
I am now able to login using NoMachine.  I'm then presented with new window of "Available Sessions".  I double click on X0 (Local) and error is displayed:

The NX client received an error from the server.
Please check the details for more information.

Details:
NX> 203 NXSSH running with pid: 2800
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.101 on port: 21013
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xx
NX> 102 Password: 
NX> 103 Welcome to: xxxxxxxxServer.xx.xxx.net user: xx
NX> 105 listsession --user="xx" --status="suspended,running" --geometry="1280x1024x32+render" --type="vnc"
NX> 127 Sessions list of user 'xx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        A64207A35E8EFA0818688CB5B4CE374F --------       1280x1024      Running     X0 (Local)
1       vnc-local        ECCFFC8AB7F9704A557CAD0E3F39EB65 --------       1280x1024      Running     X1 (Local)


NX> 148 Server capacity: not reached for user: xx
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="0" --session="SchmeerServer Local" --type="vnc" --agent_server="192.168.1.101%3A21013" agent_password="******" --geometry="1024x768" --client="winnt" --kbload=" --kbload=pc102/en_US" --keyboard="pc102/en_US" --aux="1" --screeninfo="1024x768x32+render" 

ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 280 Exiting on signal: 15


Not sure why it is looking at port 22 as I've changed the port (in General tab and VNC settings)to some other port forward port... I have been able to connect Putty and TightVNC.

When I do change the port to 22 I get a connection refused error.

---

### Post by dasbooter on 2008-03-29
so blizz with everything set to default eg. ssh is running on port 22 and you have not changed any of the settings for nx say in node.conf does it work?

You may have to clean up some sessions I think```
sudo nxserver --cleanup
```

I am sort of comtemplating going back to nomachines packages I cant get the samba shares working :/

---

### Post by sweetsinse on 2008-04-01
these packages worked perfectly with my gutsy gnome box, i never got VNC working quite right, but that isnt crucial.

i am running xfce4/xubuntu hardy beta, and the server is the same. both running compiz/emerald.

any idea why, once i create a session my xfce panels are in SEPARATE windows from the desktop, and each has window borders.  also when i open apps/windows on the server, they are using xfwm4 instead of emerald.... AND there is an emerald window border around that?!!  double window borders (xfwm4/emerald)...

i have edited the:   /etc/xdg/xfce4-session/xfce4-session.rc   :default session file to run compiz and emerald and cleared all session files from:   ~/.cache/sessions/   :folder.

nice w3rk w/packages.

edit..forgot to mention i was using /usr/bin/startxfce4 in NX's 'custom unix mode' or whatever, this was the only way i could get it to w3rk.  is there a better way?

---

### Post by BlizzofOZ on 2008-04-02
> **dasbooter said:**
> so blizz with everything set to default eg. ssh is running on port 22 and you have not changed any of the settings for nx say in node.conf does it work?

You may have to clean up some sessions I think```
sudo nxserver --cleanup
```

I am sort of comtemplating going back to nomachines packages I cant get the samba shares working :/

Other than the port change, I have not touched any configurations.  I haven't looked at this in a couple days as I trying some stuff. 

I'll try your suggestion when I get home...

What can't you get in Samba to work?  I got Samba to work and can view shares from my Win XP Pro computer...

---

### Post by dasbooter on 2008-04-02
Samba works fine :) but I will try to explain.

The freenx client has an option underservices to mount shares. It is easier to give and example of what I am talking about....

So say I am at work using a windows based system(god help us all) and I realize that I require a file that I have left on my linux based system at home. On that linux based system I have the freenx server running with the shares option working. So @ work I start up the freenx client on the windows machine and connect. On the windows machine I have some network shared drives that would be mountable in samba. Ok the remote linux based desktop is starting up and I see a message stating that I have succesfully mounted the shares to my home folder(the windows based system with the shared drives, the system I am on). So I browse to the important document say in my home folder and drag it to the mounted windows drive and in doing so I "transparently" move the document from my system @ home to the windows based system I am on... and all I believe through and encrypted connection... hopefully that is clear as mud..

By the way I am jumping ship... I am thankfull for these packages but I am jumping ship to the nomachine packages. I will come back to this thread and see what is going on from time to time ...

[SIZE="4"][COLOR="Red"]Update...[/COLOR][/SIZE]
Well finished uninstalling these packages and installing the nomachine ones and the mounted samba shares are working with the nomachine packages so I dont know what the problem is with the daflames packages sounds like he did alot of work to get things going and fabian is/was the guy keeping the freenx scene alive ... I havent kept up on the development... hopefully daflame can offer some solution

---

### Post by DBreshears on 2008-04-05
I have gone through all of the posts here to date and have not found a situation quite like what I am seeing.
I have successfully set up freenx on the server and the 3.1.0-6 client on my laptop.
I can connect to the server and even get sound but when I suspend a session I am not able to resume it.
I am using the same client (laptop) every time only two machines are involved at the moment.

Server: Ubuntu 7.10
Client: WinXP Pro SP2 with NX Client 3.1.0-6
Desktop: Gnome

The real problem is that I am not getting any real error messages except "Connection Error" on the client.
The log on the client (After clicking "Details") is as follows...

----------------------- BEGIN CLIENT LOG  --------------------------------------
> 
NX> 203 NXSSH running with pid: 2648
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.176 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: doug
NX> 102 Password: 
NX> 103 Welcome to: gutsytest user: doug
NX> 105 listsession --user="doug" --status="suspended,running" --geometry="1280x800x32+render+fullscreen" --type="unix-gnome"
NX> 127 Sessions list of user 'doug' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
1001    unix-gnome       0DE2DF02D6CD8B966AC33AF1B806F9B6 -RD--PSA    32 1280x800       Suspended   TestGutsy


NX> 148 Server capacity: not reached for user: doug
NX> 105 NX> 280 Exiting on signal: 15

--------------------------- END CLIENT LOG  ------------------------

The log on the server is basically the same w/o the "280 Exiting on signal: 15" line.
I have enabled logging level "7" in node.conf and still the output does not get any more verbose.

I do not get a screen that pops up to select a session as it appears others in the forum are getting.
It feels like the client is the one terminating the session but I cannot say for sure.

Also it seems like I should be getting a "restoresession" command line in the log just as I have seen in other posts but this is missing as well. It is almost like the "restoresession" command is missing.
I have searched the system for a "restoresession" command and not found any. I also did a dpkg -S restoresession with no results. So I assume that it is not an actual file but a command embedded in a executable somewhere.

This functionality is important, am I missing something obvious?
Please help!

---

### Post by DBreshears on 2008-04-05
> **satyriasis said:**
> I'm using the recently-posted Windows client to access an nxserver running on my home machine.  It works very well, but I have to set the window size to "Available Space" in order to get the entire desktop on the screen.  I haven't  been able to figure out how to switch between my NX window and my regular Windows desktop that's running behind the client.  Is there any way to do this?

I understand that NX won't run a rootless window, but is there some escape sequence that will allow me to switch it to the background and call it back when I need it?

Thanks again for all the work you've put into making this resource available to the community!  I hope you'll have the time and energy to recompile when the LTS version is issued.  That would be great.

I my experience (1 day) The "Available Space" produced a full screen window with a border and the "Minimize/Maximize/Kill" buttons on the top right.  You should also have the taskbar down at the bottom you could use the switch apps. You should be able to take your pick of these to get the job done.

The "Full Screen"  option however is less obvious. The "ENABLE_PULLDOWN_MENU" option in node.conf does not seem to work for me with the windows client (It should create a dropdown menu when you hover around the top center of the screen) but the "Windows" key on the keyboard will minimize the NX Session and bring your regular desktop to the foreground. Also the "Alt-Tab" key sequence seems to do the trick as well.

Good Luck!

---

### Post by daflame on 2008-04-07
> **dasbooter said:**
> Cannot get filesharing to work. I have uncommented this line in node.conf```
#SAMBA_MOUNT_SHARE_PROTOCOL="both"
``` and restarted the server but I get this.Samba and smbfs are installed and drive mapping and mounting via smb4k both work although nothing is mounted while I am attempting the remote session. This is the result :
[[IMG]http://img329.imageshack.us/img329/9074/97740736xe4.th.png[/IMG]](http://img329.imageshack.us/my.php?image=97740736xe4.png)

Confirmed, Windows sharing doesn't work after all.  Sorry for getting your hopes up everyone.  Linux file sharing does work however.

---

### Post by daflame on 2008-04-07
> **satyriasis said:**
> I'm using the recently-posted Windows client to access an nxserver running on my home machine.  It works very well, but I have to set the window size to "Available Space" in order to get the entire desktop on the screen.  I haven't  been able to figure out how to switch between my NX window and my regular Windows desktop that's running behind the client.  Is there any way to do this?

I understand that NX won't run a rootless window, but is there some escape sequence that will allow me to switch it to the background and call it back when I need it?

Thanks again for all the work you've put into making this resource available to the community!  I hope you'll have the time and energy to recompile when the LTS version is issued.  That would be great.

Actually NX WILL run a rootless window.  Just use Unix Custom and in the setup you can select a floating window.  Then your apps are integrated as part of your screen.

---

### Post by daflame on 2008-04-08
> **BlizzofOZ said:**
> I am now able to login using NoMachine.  I'm then presented with new window of "Available Sessions".  I double click on X0 (Local) and error is displayed:

The NX client received an error from the server.
Please check the details for more information.

Details:
NX> 203 NXSSH running with pid: 2800
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.101 on port: 21013
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.1.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xx
NX> 102 Password: 
NX> 103 Welcome to: xxxxxxxxServer.xx.xxx.net user: xx
NX> 105 listsession --user="xx" --status="suspended,running" --geometry="1280x1024x32+render" --type="vnc"
NX> 127 Sessions list of user 'xx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        A64207A35E8EFA0818688CB5B4CE374F --------       1280x1024      Running     X0 (Local)
1       vnc-local        ECCFFC8AB7F9704A557CAD0E3F39EB65 --------       1280x1024      Running     X1 (Local)


NX> 148 Server capacity: not reached for user: xx
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="0" --session="SchmeerServer Local" --type="vnc" --agent_server="192.168.1.101%3A21013" agent_password="******" --geometry="1024x768" --client="winnt" --kbload=" --kbload=pc102/en_US" --keyboard="pc102/en_US" --aux="1" --screeninfo="1024x768x32+render" 

ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 280 Exiting on signal: 15


Not sure why it is looking at port 22 as I've changed the port (in General tab and VNC settings)to some other port forward port... I have been able to connect Putty and TightVNC.

When I do change the port to 22 I get a connection refused error.

Did you follow the instructions on the front page for VNC proxy?  Also, are you using Compiz with XGL or is that a dual display system?  If you have X1 showing that could mean that X1 is the display that you want to be referencing not X0.

Of course I am assuming you want to VNC to the local desktop not get a virtual NX screen?

---

### Post by daflame on 2008-04-08
> **sweetsinse said:**
> these packages worked perfectly with my gutsy gnome box, i never got VNC working quite right, but that isnt crucial.

i am running xfce4/xubuntu hardy beta, and the server is the same. both running compiz/emerald.

any idea why, once i create a session my xfce panels are in SEPARATE windows from the desktop, and each has window borders.  also when i open apps/windows on the server, they are using xfwm4 instead of emerald.... AND there is an emerald window border around that?!!  double window borders (xfwm4/emerald)...

i have edited the:   /etc/xdg/xfce4-session/xfce4-session.rc   :default session file to run compiz and emerald and cleared all session files from:   ~/.cache/sessions/   :folder.

nice w3rk w/packages.

edit..forgot to mention i was using /usr/bin/startxfce4 in NX's 'custom unix mode' or whatever, this was the only way i could get it to w3rk.  is there a better way?

That is the right way to do it.  The only solution for problems like these that I've seen is to use a custom script which prevents XGL/Compiz from loading usually by a custom xorg.conf.

---

### Post by daflame on 2008-04-08
> **dasbooter said:**
> Samba works fine :) but I will try to explain.

The freenx client has an option underservices to mount shares. It is easier to give and example of what I am talking about....

So say I am at work using a windows based system(god help us all) and I realize that I require a file that I have left on my linux based system at home. On that linux based system I have the freenx server running with the shares option working. So @ work I start up the freenx client on the windows machine and connect. On the windows machine I have some network shared drives that would be mountable in samba. Ok the remote linux based desktop is starting up and I see a message stating that I have succesfully mounted the shares to my home folder(the windows based system with the shared drives, the system I am on). So I browse to the important document say in my home folder and drag it to the mounted windows drive and in doing so I "transparently" move the document from my system @ home to the windows based system I am on... and all I believe through and encrypted connection... hopefully that is clear as mud..

By the way I am jumping ship... I am thankfull for these packages but I am jumping ship to the nomachine packages. I will come back to this thread and see what is going on from time to time ...

[SIZE="4"][COLOR="Red"]Update...[/COLOR][/SIZE]
Well finished uninstalling these packages and installing the nomachine ones and the mounted samba shares are working with the nomachine packages so I dont know what the problem is with the daflames packages sounds like he did alot of work to get things going and fabian is/was the guy keeping the freenx scene alive ... I havent kept up on the development... hopefully daflame can offer some solution

That is sad to hear, but you are right that feature doesn't work from Windows at the moment.  I'm trying to resolve it with Fabian.

---

### Post by daflame on 2008-04-08
> **sweetsinse said:**
> these packages worked perfectly with my gutsy gnome box, i never got VNC working quite right, but that isnt crucial.

i am running xfce4/xubuntu hardy beta, and the server is the same. both running compiz/emerald.

any idea why, once i create a session my xfce panels are in SEPARATE windows from the desktop, and each has window borders.  also when i open apps/windows on the server, they are using xfwm4 instead of emerald.... AND there is an emerald window border around that?!!  double window borders (xfwm4/emerald)...

i have edited the:   /etc/xdg/xfce4-session/xfce4-session.rc   :default session file to run compiz and emerald and cleared all session files from:   ~/.cache/sessions/   :folder.

nice w3rk w/packages.

edit..forgot to mention i was using /usr/bin/startxfce4 in NX's 'custom unix mode' or whatever, this was the only way i could get it to w3rk.  is there a better way?

What problems have you had with VNC if you don't mind my asking?  You need to install x11vnc and xvncviewer to get it to work and you need to disable your desktop sharing.  Also, you need to setup a password in the VNC setup at the client side and enter the VNC host as localhost:0.  It should work when you resume X0 or X1 (whichever one is the physical display).  I have had some troubles with Compiz+XGL when multiple displays are involved, but that is all.  Also make sure you are logged in as the same user that is logged in on the desktop.  X by default will not let you access another user's desktop for obvious security reasons.

---

### Post by satyriasis on 2008-04-08
I also found out that there's a "magic pixel" in the top right corner of the NX windows client that will minimize the rooted window.  Very handy.
-- 
This message optimized for teletypes.

---

### Post by kpenrose on 2008-04-10
Great instructions that worked for me.  However, I have one user (me) that cannot start an nx session.  Other users on the same box can...
I turned off all effects (translucency and shadows) thinking that might me the problem.  I use kde, but so do my other users.  They report no problems at all.  Here is the relevant portion of the log file:

---

### Post by alexey_tomsk on 2008-04-11
Hello, for those who have problems with the repo. Here is ftp server with built binaries.
Also, there are plenty of other OS to select from.
[ftp://updates.etersoft.ru/pub/Etersoft/RX@Etersoft/](ftp://updates.etersoft.ru/pub/Etersoft/RX@Etersoft/)
(sshd preinstalled required).

---

### Post by dasbooter on 2008-04-13
> **alexey_tomsk said:**
> Hello, for those who have problems with the repo. Here is ftp server with built binaries.
Also, there are plenty of other OS to select from.
[ftp://updates.etersoft.ru/pub/Etersoft/RX@Etersoft/](ftp://updates.etersoft.ru/pub/Etersoft/RX@Etersoft/)
(sshd preinstalled required).

sorry, are you mirroring daflames packages or are these your own now?

P.S. Thanks for answering my posts Daflame.

---

### Post by alexey_tomsk on 2008-04-14
> **dasbooter said:**
> sorry, are you mirroring daflames packages or are these your own now?

This server is not mine. Though, I'll request this company to make it clear and I'll post their reply here.

If they are mirroring some of daflames packages they will make a note about it (they could get dataflames packages from 3d party and did not know about origin of the packages)

---

### Post by alexey_tomsk on 2008-04-14
The company Etersoft.ru claims that these packages are their original stuff and that they did not know anything about Daflames before. Probably, they will post more comments in this thread.

---

### Post by kpenrose on 2008-04-22
> **kpenrose said:**
> Great instructions that worked for me.  However, I have one user (me) that cannot start an nx session.  Other users on the same box can...
I turned off all effects (translucency and shadows) thinking that might me the problem.  I use kde, but so do my other users.  They report no problems at all.  Here is the relevant portion of the log file:


Found the problem with this and the clue was in a posting elsewhere.  Open KDE System Settings, go to Advanced and Session Manager and select "Start with Empty Session".  After doing that one time, the NXClient connects successfully.  I can then go back to "Starting with saved session" and everything continues to work.  There must have been something "bad" in my saved session that was causing the problem.

On a different note, selecting to allow multimedia support in the client kills the sound on my server.  Only by terminating my sessions and un-selecting that option do I get sound back on my server.  It seems the client sessions are grabbing the sound system exclusively.

Haven't tried printing or samba yet....

---

### Post by daflame on 2008-04-23
> **alexey_tomsk said:**
> The company Etersoft.ru claims that these packages are their original stuff and that they did not know anything about Daflames before. Probably, they will post more comments in this thread.

Those packages are not the same ones that I have posted.  Their NX libraries I am guessing fail to comply normally with Debian rules.  If you use those packages you will be using a non-debian based architecture and it might conflict much worse with NoMachine's NX Server should you have it installed.  However, they do offer older distribution packages.

---

### Post by daflame on 2008-04-23
Good to hear.  I think I may make session clearing suggestions more often for these quirky errors.  It's too bad we don't know what caused it.
> **kpenrose said:**
> Found the problem with this and the clue was in a posting elsewhere.  Open KDE System Settings, go to Advanced and Session Manager and select "Start with Empty Session".  After doing that one time, the NXClient connects successfully.  I can then go back to "Starting with saved session" and everything continues to work.  There must have been something "bad" in my saved session that was causing the problem.

On a different note, selecting to allow multimedia support in the client kills the sound on my server.  Only by terminating my sessions and un-selecting that option do I get sound back on my server.  It seems the client sessions are grabbing the sound system exclusively.

Haven't tried printing or samba yet....

---

### Post by d3a1i0 on 2008-04-26
Okay, so I just upgraded my Ubuntu machine from Gutsy to Hardy.  I had FreeNX working on Gutsy and I have become dependant on it. :P  Now when I try to connect to the Ubuntu machine from any other computer on my network it begins to load, I get the Ubuntu boot up music, and then it crashes displaying the error:

The connedtion with the remote server was shut down.
Please check the state of your network connection.

Nothing on any of my computers or network has changed except for upgrading to Hardy.  Can anyone help?

Screenshot of error:

[IMG]http://www.mykungfuisstrong.com/test/images/NX_Error.JPG[/IMG]

---

### Post by GSBoomer on 2008-04-28
To confirm what d3a1i0 said in the previous post, I too am getting this error immediately after an upgrade, but only on one of two machines. The other works fine, but from the same client.

Anyway, it's not an isolated error.

---

### Post by billWalker on 2008-04-29
I've been able to connect to Hardy with FreeNX, but it's really slow (to the point of being unusable).

We had FreeNX working fine with a different PC running Gutsy.  The principle difference with the new one is that it's running on a VMWare ESX server. 

Is there some way to speed it up, or are we stuck using VMWare's (also slow) client? Is anyone else having the same problem?

---

### Post by daflame on 2008-04-30
> **billWalker said:**
> I've been able to connect to Hardy with FreeNX, but it's really slow (to the point of being unusable).

We had FreeNX working fine with a different PC running Gutsy.  The principle difference with the new one is that it's running on a VMWare ESX server. 

Is there some way to speed it up, or are we stuck using VMWare's (also slow) client? Is anyone else having the same problem?

The version of ESX server matters here, but I have found VMWare incompatible as both a server end and client end for Hardy as I guess there are major fundamental kernel changes that break compatibility.  As a result I found myself choosing Virtual Box over VMWare's solutions.  There is a lack of server support with Virtual Box though and I'm not sure if it is as stable.  Do you need ESX Server for a specific reason that you can't use User Mode Linux for?  Do you also run Windows guests on this server?  All these play a factor in the performance.  I once loaded Windows 2000 on a Linux Host and enabled two CPU support and the whole box came to a grinding halt.  NEVER enable more than one CPU for a guest as that is not well emulated from my experiences.  Xen and UML are much more responsive options and with a modified kernel can get less than 5% overhead versus VMWare which has much worse overhead.
However, I have also upgraded to Hardy recently and haven't noticed any difference yet.  Everything seems to work fine.

---

### Post by daflame on 2008-04-30
> **d3a1i0 said:**
> Okay, so I just upgraded my Ubuntu machine from Gutsy to Hardy.  I had FreeNX working on Gutsy and I have become dependant on it. :P  Now when I try to connect to the Ubuntu machine from any other computer on my network it begins to load, I get the Ubuntu boot up music, and then it crashes displaying the error:

The connedtion with the remote server was shut down.
Please check the state of your network connection.

Nothing on any of my computers or network has changed except for upgrading to Hardy.  Can anyone help?

Screenshot of error:

[IMG]http://www.mykungfuisstrong.com/test/images/NX_Error.JPG[/IMG]

This definitely needs more looking into.  What are the architectures of the machines that are failing everyone x86 or amd64?  I upgraded my amd64 laptop without a hitch.  The other possibility is that Hardy messed up your /etc/xorg.conf file while upgrading.  Check to make sure the font paths are still correct in there.  Does anyone have a report on what the NX server reports in the logs?

---

### Post by d3a1i0 on 2008-05-03
My server is running on a i386 architecture.  I have just went through and upgraded all the NX stuff on my server (client, node, and server) and the client on my Windows machine.  I went through and re-configured the /etc/xorg.conf file which looked to be fine.  I went and added "files" section to /etc/X11/xorg.conf as described in the first post of this guide.  Still have the same issue.  Can you tell me how to check the logs?

---

### Post by billWalker on 2008-05-03
Just to update, the problem was not with FreeNX.  We installed JeOS instead and are happy with the performance.

---

### Post by OgBad on 2008-05-05
> Okay, so I just upgraded my Ubuntu machine from Gutsy to Hardy. I had FreeNX working on Gutsy and I have become dependant on it. :P Now when I try to connect to the Ubuntu machine from any other computer on my network it begins to load, I get the Ubuntu boot up music, and then it crashes displaying the error:

The connection with the remote server was shut down.
Please check the state of your network connection.

Nothing on any of my computers or network has changed except for upgrading to Hardy. Can anyone help?

Screenshot of error:
[IMG]http://www.mykungfuisstrong.com/test/images/NX_Error.JPG[/IMG]

I was/am having the same problem.  Every time i reboot my server box remotely (maybe locally to haven't tried that) i need to delete /tmp/.X0-lock upon reboot for nx to connect.  Since nx functions nicely and i don't reboot often it works for now as a work around.  Hope this helps.

---

### Post by daflame on 2008-05-07
> **d3a1i0 said:**
> My server is running on a i386 architecture.  I have just went through and upgraded all the NX stuff on my server (client, node, and server) and the client on my Windows machine.  I went through and re-configured the /etc/xorg.conf file which looked to be fine.  I went and added "files" section to /etc/X11/xorg.conf as described in the first post of this guide.  Still have the same issue.  Can you tell me how to check the logs?

The logs are usually stored on your home directory on the server under:
/home/[username]/.nx/S-[host-session id]/
There is a session and an errors log in there as well as the options and stats on the connection.

There is also:
/var/log/nxserver.log
which contains a log of your server's activity.

If you post it, make sure there aren't any passwords in there first though.  There shouldn't be, but just to be certain.

---

### Post by daflame on 2008-05-07
> **OgBad said:**
> I was/am having the same problem.  Every time i reboot my server box remotely (maybe locally to haven't tried that) i need to delete /tmp/.X0-lock upon reboot for nx to connect.  Since nx functions nicely and i don't reboot often it works for now as a work around.  Hope this helps.

This is often a recommended solution for login problems.  It usually rears its ugly head when the X server shuts down unexpectedly (forced kill) as happens when the server is shutting down while you are still logged in.  You can avoid this by sending a time to the shutdown command instead of using the server reboot now option.

```
sudo shutdown -r +1
```

which will shutdown and reboot in 1 minute.  Then log out.  It will shut down and reboot gracefully.

---

### Post by daflame on 2008-05-07
> **billWalker said:**
> Just to update, the problem was not with FreeNX.  We installed JeOS instead and are happy with the performance.

Like I said earlier.  I suspect the kernel in Hardy has some problems with virtualization currently (or virtualization has a problem with it).  Use Gutsy's kernel or another OS as you have done.  Also, the pulseaudio that Hardy uses by default can be a major pain for virtualization too.  Switching back to ALSA/ESD can improve performance there.  My best recommendation is to install Gutsy and if by chance you want Hardy, upgrade to it instead of installing from scratch.  That's right you heard me advocate an upgrade instead of a clean install.  Gutsy's default settings are more server friendly from my experiences and upgrading to Hardy usually keeps those settings intact.

---

### Post by crazy___cow on 2008-05-07
I have used this repository for FreeNX on Hardy

deb [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main

and ALL works fine!!
I have only edited xorg.conf for fonts path...

---

### Post by daflame on 2008-05-08
> **crazy___cow said:**
> I have used this repository for FreeNX on Hardy

deb [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/marceloshima/ubuntu](http://ppa.launchpad.net/marceloshima/ubuntu) hardy main

and ALL works fine!!
I have only edited xorg.conf for fonts path...

Thank you for your post, I haven't had a chance to check Marcello's packages, but it's good to hear a positive report.

---

### Post by satyriasis on 2008-05-08
I'm trying to get your packages installed on a fresh installation of Hardy.  I'm running into the following problem using aptitude:

Errors were encountered while processing:
 /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nxclient (3.1.0-6) ...

dpkg: dependency problems prevent configuration of nxproxy:
 nxproxy depends on libxcomp3; however:
  Package libxcomp3 is not installed.
dpkg: error processing nxproxy (--configure):
 dependency problems - leaving unconfigured


Installing libxcomp3 leaves me with this:

root@satyr:~# aptitude install libxcomp3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be installed:
  libxcomp3
The following partially installed packages will be configured:
  nxproxy
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/381kB of archives. After unpacking 1081kB will be used.
Writing extended state information... Done
(Reading database ... 159447 files and directories currently installed.)
Unpacking libxcomp3 (from .../libxcomp3_3.1.0-6-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libXcomp.so.3.1.0', which is also in package libxcomp2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of nxproxy:
 nxproxy depends on libxcomp3; however:
  Package libxcomp3 is not installed.
dpkg: error processing nxproxy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxproxy


Has anyone else encountered this, and if so, how did you get around it?

Thanks again for all your work, daflame.

---

### Post by alexey_tomsk on 2008-05-08
Seems like libxcomp2 prevents installation of libxcomp3.
At least aptitude can't manage it.
Try to download libxcomp3_3.1.0-6-2_i386.deb and install it with dpkg -i procedure.

---

### Post by satyriasis on 2008-05-08
> **alexey_tomsk said:**
> Seems like libxcomp2 prevents installation of libxcomp3.
At least aptitude can't manage it.
Try to download libxcomp3_3.1.0-6-2_i386.deb and install it with dpkg -i procedure.


Thanks for the tip.  I did install libxcomp3_3.1.0-6-2_i386.deb, but it broke nxserver.  I had to back down to libxcomp2, which leaves nxproxy unconfigured, but at least it allows me to log in using nx.

---

### Post by Eladon on 2008-05-09
I am in the same boat as you satyriasis.  I have a brand new Hardy install, same error messages during install.  Sorry, haven't gotten any farther with it than you have. :(

---

### Post by daflame on 2008-05-11
> **satyriasis said:**
> I'm trying to get your packages installed on a fresh installation of Hardy.  I'm running into the following problem using aptitude:

Errors were encountered while processing:
 /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nxclient (3.1.0-6) ...

dpkg: dependency problems prevent configuration of nxproxy:
 nxproxy depends on libxcomp3; however:
  Package libxcomp3 is not installed.
dpkg: error processing nxproxy (--configure):
 dependency problems - leaving unconfigured


Installing libxcomp3 leaves me with this:

root@satyr:~# aptitude install libxcomp3
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be installed:
  libxcomp3
The following partially installed packages will be configured:
  nxproxy
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/381kB of archives. After unpacking 1081kB will be used.
Writing extended state information... Done
(Reading database ... 159447 files and directories currently installed.)
Unpacking libxcomp3 (from .../libxcomp3_3.1.0-6-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libXcomp.so.3.1.0', which is also in package libxcomp2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libxcomp3_3.1.0-6-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of nxproxy:
 nxproxy depends on libxcomp3; however:
  Package libxcomp3 is not installed.
dpkg: error processing nxproxy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxproxy


Has anyone else encountered this, and if so, how did you get around it?

Thanks again for all your work, daflame.

WHATEVER YOU DO, DO NOT ADD MARCELO's PACKAGES POSTED ABOVE if you have my repos as well.  I will post updated packages that should fix some of these issues.  If you have done this in error and want to revert, remove all NX packages and Marcelo's repos and
```
sudo apt-get update
```
Reinstall all NX packages as on the first page of this forum.  I made a mistake and packaged NX 3 libraries with the name libxcomp2 and libxcompext2 when they should have ended in 3.

If you still want to use Marcelo's packages instead remove ALL of the NX packages and libraries first.  Then remove my repos and add Marcelo's ones.

---

### Post by daflame on 2008-05-11
I am building new packages for NX 3.2.0 with support for Hardy also I found yet another patch that allows you to suspend a session from Windows and resume it on Linux and also resume a Linux session from Windows.  I tested it and it works!  This will also include improved support for nxcl which is an open source replacement for nxclient which NoMachine supplies.

---

### Post by daflame on 2008-05-13
The packages are built and uploaded now.  Make sure to remove any packages named freenx first.  Upgrade nxclient, freenx-server and all the nx libraries.

Also support for hardy has been added as:
```
deb http://www.datakeylive.com/ubuntu hardy main
deb-src http://www.datakeylive.com/ubuntu hardy main
```

Enjoy!

---

### Post by FoolsRun on 2008-05-13
Does anyone have sound working over NX?

When I check the "enable multimedia" box in the NX client gnome-settings-daemon crashes on login but for some reason my login and logout sounds work fine and no other sound works at all; Mp3s and videos have no sound.

Anyone get this to work?

---

### Post by satyriasis on 2008-05-13
I have a clean install of the new packages on Hardy.  Using the Windows client, my connection attempts just time out.  The client log shows the following:

NX> 203 NXSSH running with pid: 2912
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 71.123.100.148 on port: 22
Warning: the RSA host key for 'satyr.dnsalias.net'
differs from the key for the IP address '71.123.100.148'
Offending key for IP in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:1
Matching host key in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:2
Are you sure you want to continue connecting (yes/no)? 

There's no prompt to answer the question at the end; this is just what appears in the log.  I'm not on a Cygwin machine, by the way.  Is there any way to clear the error?

Thanks for all the time you put into this, daflame!

---

### Post by kwaanens on 2008-05-13
Have you fixed your ssh keys? It's all over blogs and the forums. Might be something to check out.

---

### Post by Dnaumm on 2008-05-14
> **daflame said:**
> The packages are built and uploaded now.  Make sure to remove any packages named freenx first.  Upgrade nxclient, freenx-server and all the nx libraries.

Also support for hardy has been added as:
```
deb http://www.datakeylive.com/ubuntu hardy main
deb-src http://www.datakeylive.com/ubuntu hardy main
```

Enjoy!
Thanks daflame for the new packages; I was hoping they'd solve my probem, but unfortunately not. I had a working installation of freenx under gutsy (with my own private key), but when my auto-upgrade to hardy crashed mid-stream and I lost network access, I had to reformat my OS partition (not the /home one) and install hardy from the CD. Now I can't get freenx back up again (with the NoMachine key, since my other key was lost in the reformat), and my error messages don't look quite the same. Here's what /var/log/nxserver.log says:

> 
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: margolis
NX> 102 Password: 
NX> 103 Welcome to: LinuxMargolis user: margolis
NX> 105 listsession --user="margolis" --status="suspended,running" --geometry="1
400x1050x16+render" --type="unix-gnome"
NX> 127 Sessions list of user 'margolis' for reconnect:

Display Type             Session ID                       Options  Depth Screen 
        Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------
------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: margolis
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="
16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --samba
="1" --media="1" --mediahelper="esd" --session="My Linux Box" --type="unix-gnome
" --geometry="1400x1020" --client="winnt" --keyboard="pc102/fr" --screeninfo="14
00x1020x16+render" 

Info: Using /usr/lib/nx/nxacl to change session parameters or deny session.
NX> 1004 Error: Session did not start.


The client side error messages look similar, but end with 
> 
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15
.
Any suggestions would be greatly appreciated.

P.S. In your first page of the tutorial, you forgot to mention the "nxsetup --install" step...

---

### Post by tk471 on 2008-05-14
Just recently got the 'random number generator' issue patched (security updates).  After regenerating ssh keys, I deleted this:

/var/lib/nxserver/home/.ssh/known_hosts

and then I was able to reconnect to FreeNX.  

And just a day after finally getting FreeNX to work :D

---

### Post by daflame on 2008-05-15
> **FoolsRun said:**
> Does anyone have sound working over NX?

When I check the "enable multimedia" box in the NX client gnome-settings-daemon crashes on login but for some reason my login and logout sounds work fine and no other sound works at all; Mp3s and videos have no sound.

Anyone get this to work?

You need to use ESD as the output sound path.  I DO NOT recommend sending multimedia over NX though.

---

### Post by daflame on 2008-05-15
> **satyriasis said:**
> I have a clean install of the new packages on Hardy.  Using the Windows client, my connection attempts just time out.  The client log shows the following:

NX> 203 NXSSH running with pid: 2912
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 71.123.100.148 on port: 22
Warning: the RSA host key for 'satyr.dnsalias.net'
differs from the key for the IP address '71.123.100.148'
Offending key for IP in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:1
Matching host key in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:2
Are you sure you want to continue connecting (yes/no)? 

There's no prompt to answer the question at the end; this is just what appears in the log.  I'm not on a Cygwin machine, by the way.  Is there any way to clear the error?

Thanks for all the time you put into this, daflame!

The latest openssh update deleted and regenerated all machine keys that were made since 2006 when a major security hole was introduced into the Debian SSH packages (no randomness) so all keys potentially have a known seed (In other words someone could regenerate a valid spoof key identity for any of those keys).  No one knows if it was ever exploited, but that was a major blunder which now causes us all great pain.

You need to empty your .ssh/known_hosts file and possibly recopy keys if you made any custom ones.

---

### Post by daflame on 2008-05-15
> **Dnaumm said:**
> Thanks daflame for the new packages; I was hoping they'd solve my probem, but unfortunately not. I had a working installation of freenx under gutsy (with my own private key), but when my auto-upgrade to hardy crashed mid-stream and I lost network access, I had to reformat my OS partition (not the /home one) and install hardy from the CD. Now I can't get freenx back up again (with the NoMachine key, since my other key was lost in the reformat), and my error messages don't look quite the same. Here's what /var/log/nxserver.log says:



The client side error messages look similar, but end with 
.
Any suggestions would be greatly appreciated.

P.S. In your first page of the tutorial, you forgot to mention the "nxsetup --install" step...

My guess would be that you have custom keys still setup in the client?  Usually stored under .nx and .ssh in your profile.  If you delete them fromo there and rerun nxclient that might help.  Alsom with the recent update of openssh it is receommended to delete .ssh/known_hosts and readd all the known hosts.

---

### Post by daflame on 2008-05-15
> **tk471 said:**
> Just recently got the 'random number generator' issue patched (security updates).  After regenerating ssh keys, I deleted this:

/var/lib/nxserver/home/.ssh/known_hosts

and then I was able to reconnect to FreeNX.  

And just a day after finally getting FreeNX to work :D

Good job!  That would have been my recommendation too.

---

### Post by daflame on 2008-05-15
Ok, here is another interesting tidbit:
If you ever have troubles logging into a Hardy machine with FreeNX.  Check the log under your username:
/home/username/.nx/F-C-(long alphanum session code)/session
if it has an error like:
/usr/lib/nx/nxnode: line 333: /usr/bin/dbus-launch: No such file or directory

You need to install the dbus-x11 package.  There should be an auto-dependency from the dbus package, but there isn't.

The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/118919](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/118919)

---

### Post by gertvdijk on 2008-05-15
I also had to change the following line to the /etc/nxserver/node.conf overcome a 'can't open display' problem.
```

# The base display number from which sessions are started.
DISPLAY_BASE=1002

```

---

### Post by merlin2100 on 2008-05-15
Hi, 
After today's upgrade freenx server stops to work.
I tried to remove and install again but without success.
Here are the error I get:

Error: Could not find 1.5.0 or 2.[01].0 or 3.[01].0 version string in nxagent. NX 1.5.0 or 2.[01].0 or 3.[01].0 backend is needed for this version of FreeNX.

BTW: the installed version are freenx-server 0.7.2-1hardy2, nxagent 3.2.0-1hardy1..

Any help ? Should I "downgrade" nxagent to 3.1.x ?






$ sudo nxsetup --install --clean --puerge
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually. 
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] 
Removing special user "nx" ...done
Removing session database ...done
Removing logfile ...done
Removing home directory of special user "nx" ...done
Removing configuration files ...done
Setting up /etc/nxserver ...done
Generating public/private dsa key pair.
Your identification has been saved in /etc/nxserver/users.id_dsa.
Your public key has been saved in /etc/nxserver/users.id_dsa.pub.
The key fingerprint is:
02:f5:20:6c:fa:17:e2:87:06:b3:e3:56:06:7e:43:f9 root@hrom
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...Adding system user `nx' (UID 113) ...
Adding new user `nx' (UID 113) with group `nx' ...
Creating home directory `/var/lib/nxserver/home' ...
Password changed.
done
Adding user "nx" to group "utmp" ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so:/usr/lib/libXcompshad.so:/usr/lib/libXrender-nx.so.1". /usr/lib/libXcomp.so could not be found. Users will not be able to run a single application in non-rootless mode.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA. 
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
Error: Could not find 1.5.0 or 2.[01].0 or 3.[01].0 version string in nxagent. NX 1.5.0 or 2.[01].0 or 3.[01].0 backend is needed for this version of FreeNX.

  Errors occured during config check.
  Please correct the configuration file.

---

### Post by Dnaumm on 2008-05-15
> **daflame said:**
> My guess would be that you have custom keys still setup in the client?  Usually stored under .nx and .ssh in your profile.  If you delete them fromo there and rerun nxclient that might help.  Alsom with the recent update of openssh it is receommended to delete .ssh/known_hosts and readd all the known hosts.
Thanks for the suggestion (and thanks for all of your help, by the way), but as far as I can understand, that doesn't seem to do it. I am kind of new to ubuntu, so I'm not sure how to readd known hosts. But I also discovered a strange thing; I appear to be missing /etc/nxserver/node.conf. I tried using "apt-get install --reinstall" for all of the packages on the first page, but it doesn't appear. All I have in the directory is
> 
margolis@LinuxMargolis:/etc/nxserver$ ls -alt
total 15
drwxr-xr-x   2 nx   root  176 2008-05-15 16:29 .
drwxr-xr-x 145 root root 7128 2008-05-15 16:29 ..
-rw-------   1 nx   root    0 2008-05-15 16:29 passwords
-rw-------   1 nx   root    0 2008-05-15 16:29 passwords.orig
-rw-------   1 nx   root  668 2008-05-15 16:29 users.id_dsa
-rw-r--r--   1 nx   root  608 2008-05-15 16:29 users.id_dsa.pub

I imagine this might be the source of the problem, but I have no idea how to get it back. Is there any place I can download a new version of node.conf?

---

### Post by dlopez on 2008-05-15
> **merlin2100 said:**
> Hi, 
After today's upgrade freenx server stops to work.
I tried to remove and install again but without success.


The same here.  Any suggestion?
David.

---

### Post by Dnaumm on 2008-05-16
Just an update. I tried the suggestions of yocec in post number 118 (remember, I'm new to all of this), plus the full package list from the first page, and now my errors are different again; node.conf still hasn't appeared, but the behavior has changed. For one account, I see the following:
> 
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: margolis
NX> 102 Password: 
NX> 103 Welcome to: LinuxMargolis user: margolis
NX> 105 listsession --user="margolis" --status="suspended,running" --geometry="1
280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'margolis' for reconnect:

Display Type             Session ID                       Options  Depth Screen 
        Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------
------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: margolis
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="
16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --samba
="1" --media="1" --mediahelper="esd" --session="My Linux Box" --type="unix-gnome
" --geometry="1280x994" --client="winnt" --keyboard="pc102/us" --screeninfo="128
0x994x32+render" 

Info: Using /usr/lib/nx/nxacl to change session parameters or deny session.
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: LinuxMargolis-1001-B947D2B9B1B72F9FC3C0482BEA96CA27
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: ec02f66b900dd56ce3865b9270450df9
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: ec02f66b900dd56ce3865b9270450df9
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 709 File-sharing port: 445
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 addprinter  --type="smb" --port="4001" --username="David%20N.%20MARGOLIS
" password="******" --share="HP6%20Bureau%20416" --computername="PC416-1" --sess
ion_id="B947D2B9B1B72F9FC3C0482BEA96CA27" --model="NULL" --defaultPrinter="1" 
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 1001 Bye.
NX> 719 CUPS printer: running
NX> 105 addmount  --port="4001" --username="David%20N.%20MARGOLIS" password="***
***" --share="Installation%20Disks" --computername="PC416-1" --session_id="B947D
2B9B1B72F9FC3C0482BEA96CA27" --dir="%24(SHARES)/Installation%20Disks" 
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 1001 Bye.
NX> 719 SMB filesystem: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.

I get past the nxacl stage, but then there's a "Bye" that appears from nowhere and the session terminates. On the clent side a window opens and closes immediately, and the client side log has
> 
Session: Terminating session at 'Fri May 16 12:13:37 2008'
Session: Session terminated session at 'Fri May 16 12:13:37 2008'
.

Strangely, for another user it works fine. In the server log I get
> 
NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: terracol
NX> 102 Password: 
NX> 103 Welcome to: LinuxMargolis user: terracol
NX> 105 listsession --user="terracol" --status="suspended,running" --geometry="1
280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'terracol' for reconnect:

Display Type             Session ID                       Options  Depth Screen 
        Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------
------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: terracol
NX> 105 startsession --session="David2" --type="unix-gnome" --cache="8M" --image
s="32M" --link="lan" --kbtype="pc102/fr" --nodelay="1" --encryption="1" --backin
gstore="never" --geometry="1280x770" --media="0" --agent_server="" --agent_user=
"" agent_password="******""  --screeninfo="1280x770x32+render" 

Info: Using /usr/lib/nx/nxacl to change session parameters or deny session.
NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: LinuxMargolis-1001-25E4110707DA0BEC6E5D229E5E622B86
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 3f91fff84ad81fc24007236effadc35b
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 3f91fff84ad81fc24007236effadc35b
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye

Here I get the same "Bye", but the session doesn't terminate. 

Does anyone have any ideas? Since I tried both logins from the same client machine it's clearly related to the account (the first one has superuser rights and the second doesn't) on the server side, but I'm not sure where the problem is.

OK: Post modified, problem solved. For information, the user was not the owner of the .Xauthority in his home directory (the owner was "root"). "sudo chown" fixed the problem. 

Thanks for your patience, and I hope this helps anyone else who might have similar issues.

---

### Post by d3a1i0 on 2008-05-17
> **d3a1i0 said:**
> Okay, so I just upgraded my Ubuntu machine from Gutsy to Hardy.  I had FreeNX working on Gutsy and I have become dependant on it. :P  Now when I try to connect to the Ubuntu machine from any other computer on my network it begins to load, I get the Ubuntu boot up music, and then it crashes displaying the error:

The connedtion with the remote server was shut down.
Please check the state of your network connection.

Nothing on any of my computers or network has changed except for upgrading to Hardy.  Can anyone help?

Screenshot of error:

[IMG]http://www.mykungfuisstrong.com/test/images/NX_Error.JPG[/IMG]

Okay, I hooked a monitor and inputs up to my Ubuntu machine and found out that the upgrade did not complete corretly.  I formated and did a clean install of the OS.  I went through the install from the first page using the new repositories listed (thanks, btw).  I am still not able to conect via NX, but now it's a totally different issue I am not able to figure out.  Here is what it is saying:

SH running with pid: 4004
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.102 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: neil
NX> 102 Password: 
NX> 103 Welcome to: zomfg user: neil
NX> 105 listsession --user="neil" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'neil' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: neil
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="32M" --images="128M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Server" --type="unix-gnome" --geometry="1680x1050" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1680x1050x32+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: zomfg-1001-AEC4E75C7D88449A7C2498CD37D40C1A
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 2c95e43c095228bf211f96067054195d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 2c95e43c095228bf211f96067054195d
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 1370:  8792 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/neil/.nx/F-C-zomfg-1001-AEC4E75C7D88449A7C2498CD37D40C1A/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 280 Exiting on signal: 15

---

### Post by gertvdijk on 2008-05-19
> **gertvdijk said:**
> I also had to change the following line to the /etc/nxserver/node.conf overcome a 'can't open display' problem.
```

# The base display number from which sessions are started.
DISPLAY_BASE=1002

```
And yet again I got the same error "Check the state of your network connection". Now was a simple DISPLAY_BASE=1003 the (temprorarily) solution. Do I need to increase this number every time it just suddenly stops working? ](*,)

BTW: I get the following error in de /home/user/.nx/FC...
> 
xrdb: No such file or directory
xrdb: Can't open display ':1002'

(gnome-session:9030): Gtk-WARNING **: cannot open display: :1002


---

### Post by tarotoast on 2008-05-21
I just wanted to personally thank you for the time you've put into maintaining this thread and keeping this wonderful project up to date. Before knowing what FreeNX is, I used to think gdm over VNC does the job I want pretty good. Now? There's no turning back from FreeNX!

Thank you :)

---

### Post by drapsag on 2008-05-23
I have some problem with the web companion plugin. I placed my session files in the right directory and adjust the settings in the html file. But I'm  getting as screen with "there's no session file available on the server"

Someone know a solution?

---

### Post by iresprite on 2008-06-01
Hey, all. This is a really amazing app-- thanks to daflame for putting together the packages! I think I've got this mostly hammered out, but I'm running into an issue where libX11-nx.so.6 isn't being built. I'm running an AMD 64 architecture, so I'm wondering if that's the problem.

If that's the case, how do I go about resolving the issue? Thanks!

---

### Post by dasbooter on 2008-06-03
I was wondering if the newest packages have better support for the samba sharing options(mount the local drives for access) that has been a sticking point for me switching over to the free packages. I saw something posted about multimedia in this thread and I have to agree that it doesnt work very well but I thought I read that nomachine was trying to support some of the new sound servers besides ESD does anybody know anything about that? Do you think it will filter down into the free packages...

---

### Post by dannymac64 on 2008-06-04
I used the instructions in this forum and had great success for a week or two on Hardy.  But today I needed to reboot the server machine and now I can no longer connect to it from home.  I tried various combinations of uninstalling/reinstalling/upgrading the FreeNX server apps and now I keep getting the following error in my /home/<username>/.nx/<sessionID>/session file:

====
/usr/lib/nx/nxagent: error while loading shared libraries: libX11-nx.so.6: cannot open shared object file: No such file or directory

(gnome-session:2648): Gtk-WARNING **: cannot open display: :1001
====

I have tried changing the display base to 1002, but obviously that won't help when it can't find a shared library.

Any ideas?

---

### Post by dannymac64 on 2008-06-04
> **dannymac64 said:**
> I used the instructions in this forum and had great success for a week or two on Hardy.  But today I needed to reboot the server machine and now I can no longer connect to it from home.  I tried various combinations of uninstalling/reinstalling/upgrading the FreeNX server apps and now I keep getting the following error in my /home/<username>/.nx/<sessionID>/session file:

====
/usr/lib/nx/nxagent: error while loading shared libraries: libX11-nx.so.6: cannot open shared object file: No such file or directory

(gnome-session:2648): Gtk-WARNING **: cannot open display: :1001
====

I have tried changing the display base to 1002, but obviously that won't help when it can't find a shared library.

Any ideas?

OK, so I figured out the library issues and they appear to be resolved.  However, I still get the "(gnome-session:2648): Gtk-WARNING **: cannot open display: :1001" error.  Changing the display base again does not help.

Any ideas?

---

### Post by dannymac64 on 2008-06-04
> **dannymac64 said:**
> OK, so I figured out the library issues and they appear to be resolved.  However, I still get the "(gnome-session:2648): Gtk-WARNING **: cannot open display: :1001" error.  Changing the display base again does not help.

Any ideas?

OK all is resolved now.  There were still remnants of another version of FreeNX floating around on my machine.  After removing them and reinstalling from the steps on page 1 of this thread, it works again.

---

### Post by daflame on 2008-06-17
> **iresprite said:**
> Hey, all. This is a really amazing app-- thanks to daflame for putting together the packages! I think I've got this mostly hammered out, but I'm running into an issue where libX11-nx.so.6 isn't being built. I'm running an AMD 64 architecture, so I'm wondering if that's the problem.

If that's the case, how do I go about resolving the issue? Thanks!

You haven't mentioned your architecture, but I could not get the source to build on Hardy64 either.  I had to use the Gutsy environment to build them.

---

### Post by daflame on 2008-06-17
> **dasbooter said:**
> I was wondering if the newest packages have better support for the samba sharing options(mount the local drives for access) that has been a sticking point for me switching over to the free packages. I saw something posted about multimedia in this thread and I have to agree that it doesnt work very well but I thought I read that nomachine was trying to support some of the new sound servers besides ESD does anybody know anything about that? Do you think it will filter down into the free packages...

I imagine that this will filter down through and there is better file sharing support in this version, but the audio issues won't go away until the new system is setup and with Hardy moving to pulse it may be even worse for a while.

---

### Post by daflame on 2008-06-17
> **drapsag said:**
> I have some problem with the web companion plugin. I placed my session files in the right directory and adjust the settings in the html file. But I'm  getting as screen with "there's no session file available on the server"

Someone know a solution?

I can't remember the solution, but I believe you have to pay attention to file permissions and setup the config to read the files.  I can't remember exactly, but I did do this once.  Maybe I'll setup a web login to remind myself and let you know.

---

### Post by daflame on 2008-06-17
> **tarotoast said:**
> I just wanted to personally thank you for the time you've put into maintaining this thread and keeping this wonderful project up to date. Before knowing what FreeNX is, I used to think gdm over VNC does the job I want pretty good. Now? There's no turning back from FreeNX!

Thank you :)

You're welcome!  I am happy to see yet another FreeNX convert.  I think the web will be a better place once dangerously insecure and slow methods are updated or replaced.

---

### Post by daflame on 2008-06-17
> **gertvdijk said:**
> And yet again I got the same error "Check the state of your network connection". Now was a simple DISPLAY_BASE=1003 the (temprorarily) solution. Do I need to increase this number every time it just suddenly stops working? ](*,)

BTW: I get the following error in de /home/user/.nx/FC...

Have you tried to remove FreeNX and clean out ALL NX components and follow page 1 again?  I know that there can be conflicts with pre-existing components.

---

### Post by daflame on 2008-06-17
> **FoolsRun said:**
> Does anyone have sound working over NX?

When I check the "enable multimedia" box in the NX client gnome-settings-daemon crashes on login but for some reason my login and logout sounds work fine and no other sound works at all; Mp3s and videos have no sound.

Anyone get this to work?

In order to get sound to work, all applications need to use ESD, which Gnome does by default, but more apps don't and I hope this will change in NX because ESD is old.

---

### Post by daflame on 2008-06-17
> **satyriasis said:**
> I have a clean install of the new packages on Hardy.  Using the Windows client, my connection attempts just time out.  The client log shows the following:

NX> 203 NXSSH running with pid: 2912
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 71.123.100.148 on port: 22
Warning: the RSA host key for 'satyr.dnsalias.net'
differs from the key for the IP address '71.123.100.148'
Offending key for IP in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:1
Matching host key in /cygdrive/c/DOCUME~1/jlg/.ssh/known_hosts:2
Are you sure you want to continue connecting (yes/no)? 

There's no prompt to answer the question at the end; this is just what appears in the log.  I'm not on a Cygwin machine, by the way.  Is there any way to clear the error?

Thanks for all the time you put into this, daflame!

On the client machine under "c:\Documents and Settings\jlg\.ssh" delete the known_hosts file.  My guess is that you are accessing this remotely and your IP or host key must have changed on the server.

---

### Post by daflame on 2008-06-17
> **Dnaumm said:**
> Thanks daflame for the new packages; I was hoping they'd solve my probem, but unfortunately not. I had a working installation of freenx under gutsy (with my own private key), but when my auto-upgrade to hardy crashed mid-stream and I lost network access, I had to reformat my OS partition (not the /home one) and install hardy from the CD. Now I can't get freenx back up again (with the NoMachine key, since my other key was lost in the reformat), and my error messages don't look quite the same. Here's what /var/log/nxserver.log says:



The client side error messages look similar, but end with 
.
Any suggestions would be greatly appreciated.

P.S. In your first page of the tutorial, you forgot to mention the "nxsetup --install" step...

My suggestion is to delete the .ssh/known_hosts and .ssh/authorized_keys .ssh/authorized_keys2 in your home directory and in C:\Documents and Settings\[username]\.ssh (or it might be .nx) on your windows clients and reinstall NX Client.
On the server run:
```
sudo nxserver --deluser [username]
sudo nxserver --adduser [username]
```

This should clean out your settings.  If not, let me know.

BTW nxsetup --install should not be necessary with these packages.

---

### Post by daflame on 2008-06-18
> **merlin2100 said:**
> Hi, 
After today's upgrade freenx server stops to work.
I tried to remove and install again but without success.
Here are the error I get:

Error: Could not find 1.5.0 or 2.[01].0 or 3.[01].0 version string in nxagent. NX 1.5.0 or 2.[01].0 or 3.[01].0 backend is needed for this version of FreeNX.

BTW: the installed version are freenx-server 0.7.2-1hardy2, nxagent 3.2.0-1hardy1..

Any help ? Should I "downgrade" nxagent to 3.1.x ?






$ sudo nxsetup --install --clean --puerge
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually. 
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] 
Removing special user "nx" ...done
Removing session database ...done
Removing logfile ...done
Removing home directory of special user "nx" ...done
Removing configuration files ...done
Setting up /etc/nxserver ...done
Generating public/private dsa key pair.
Your identification has been saved in /etc/nxserver/users.id_dsa.
Your public key has been saved in /etc/nxserver/users.id_dsa.pub.
The key fingerprint is:
02:f5:20:6c:fa:17:e2:87:06:b3:e3:56:06:7e:43:f9 root@hrom
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...Adding system user `nx' (UID 113) ...
Adding new user `nx' (UID 113) with group `nx' ...
Creating home directory `/var/lib/nxserver/home' ...
Password changed.
done
Adding user "nx" to group "utmp" ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so:/usr/lib/libXcompshad.so:/usr/lib/libXrender-nx.so.1". /usr/lib/libXcomp.so could not be found. Users will not be able to run a single application in non-rootless mode.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA. 
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
Error: Could not find 1.5.0 or 2.[01].0 or 3.[01].0 version string in nxagent. NX 1.5.0 or 2.[01].0 or 3.[01].0 backend is needed for this version of FreeNX.

  Errors occured during config check.
  Please correct the configuration file.

You need to uninstall ALL versions of freenx and purge all NX directories.  It looks like you have an outdated version of nxserver and nxsetup hanging around either in /usr/NX/bin or /usr/lib/nx, /usr/bin, /usr/local/bin or somewhere else in your path.  If you uninstall and search for nxserver and nxsetup you should not find it.  If you do delete it or remove the package that installed it.

Also, you should use the NoMachine keys, so answer no to the first question.  You really shouldn't have to run nxsetup at all if you use my packages and the NoMachine keys, just nxserver since the paths are already setup.

---

### Post by daflame on 2008-06-18
> **Dnaumm said:**
> Thanks for the suggestion (and thanks for all of your help, by the way), but as far as I can understand, that doesn't seem to do it. I am kind of new to ubuntu, so I'm not sure how to readd known hosts. But I also discovered a strange thing; I appear to be missing /etc/nxserver/node.conf. I tried using "apt-get install --reinstall" for all of the packages on the first page, but it doesn't appear. All I have in the directory is

I imagine this might be the source of the problem, but I have no idea how to get it back. Is there any place I can download a new version of node.conf?

I had a look at the packages and the node.conf file is present in /etc/nxserver

You can manually extract from the archive if you still have trouble using dpkg -x [package name] [destination dir]

---

### Post by daflame on 2008-06-18
> **d3a1i0 said:**
> Okay, I hooked a monitor and inputs up to my Ubuntu machine and found out that the upgrade did not complete corretly.  I formated and did a clean install of the OS.  I went through the install from the first page using the new repositories listed (thanks, btw).  I am still not able to conect via NX, but now it's a totally different issue I am not able to figure out.  Here is what it is saying:

SH running with pid: 4004
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.102 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: neil
NX> 102 Password: 
NX> 103 Welcome to: zomfg user: neil
NX> 105 listsession --user="neil" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'neil' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: neil
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="32M" --images="128M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Server" --type="unix-gnome" --geometry="1680x1050" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1680x1050x32+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: zomfg-1001-AEC4E75C7D88449A7C2498CD37D40C1A
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 2c95e43c095228bf211f96067054195d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 2c95e43c095228bf211f96067054195d
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 1370:  8792 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/neil/.nx/F-C-zomfg-1001-AEC4E75C7D88449A7C2498CD37D40C1A/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 280 Exiting on signal: 15

This is one of two classic errors.  A clean install of Gutsy, Hardy and Intrepid all start with a nearly blank /etc/X11/xorg.conf since X.Org 7.2 and above have no problem with this.  Since NX uses the same config, but the 6.9.0 version of X this is not acceptable.  Check the instructions on the first page to fix it.

The other one is that I have heard a report that NX has a problem with resolutions over 1600 pixels, but I haven't had time to see if this is the case.

---

### Post by daflame on 2008-06-18
> **gertvdijk said:**
> And yet again I got the same error "Check the state of your network connection". Now was a simple DISPLAY_BASE=1003 the (temprorarily) solution. Do I need to increase this number every time it just suddenly stops working? ](*,)

BTW: I get the following error in de /home/user/.nx/FC...

I will need more logs to properly diagnose it.

---

### Post by Dnaumm on 2008-06-19
> **daflame said:**
> Have you tried to remove FreeNX and clean out ALL NX components and follow page 1 again?  I know that there can be conflicts with pre-existing components.
Thanks daflame for the suggestions, I managed to get things to work after all. And this error (or at least the changing the DISPLAY BASE solution) looks similar to one I had. I don't know if it helps, but I discovered that NX wasn't cleaning up old sessions (regardless of what was checked when I set up the client) and that caused me to have to change the DISPLAY BASE with each reboot of the server. Is this a known problem (or even a problem) with the NX client, perhaps?

---

### Post by satyriasis on 2008-07-01
> **daflame said:**
> On the client machine under "c:\Documents and Settings\jlg\.ssh" delete the known_hosts file.  My guess is that you are accessing this remotely and your IP or host key must have changed on the server.

That was it exactly.  Thanks again for this great service to the community, daflame!

---

### Post by gertvdijk on 2008-07-08
> **daflame said:**
> I will need more logs to properly diagnose it.
Okay, well, it seems that my issue can also be worked around with by trying to connect 5+ times, just keep trying until it works, basically. After the successful connection it will just keep working normally till some random moment. (I think random because, since the last successful attempt: no updates installed in the meantime, no reboot, not anything that could be related to it, afaik)

For now, I won't be using FreeNX a lot (holidays) and just working directly on my pc, so I won't be able to diagnose/post logs, but I could give some more clues:
- Only when using the Windows client (both the version in the start post and the latest on NoMachine's website). No problems when running the same client on Debian etch.
- All error logs point to the problem that it can't find the session it just has created.
- Since the Hardy upgrade things got worse.

---

### Post by Robor on 2008-07-09
> **curiogeo said:**
> I found the issue.  It was buried in the forum archives.

"I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l" and ".Xauthority-c" in your home dir. Delete them if they exist."

As soon as I erased all three .Xauthority (the quote only suggests erasing 2 of them - that failed) files the client held the connection with the nx server under my original user.

The post is: [http://ubuntuforums.org/archive/index.php/t-57592.html](http://ubuntuforums.org/archive/index.php/t-57592.html)

Hope this helps anyone in the same boat I was in.:grin::biggrin:

This solved my issue as well.  Thanks!!!

---

### Post by daflame on 2008-07-13
> **Dnaumm said:**
> Thanks daflame for the suggestions, I managed to get things to work after all. And this error (or at least the changing the DISPLAY BASE solution) looks similar to one I had. I don't know if it helps, but I discovered that NX wasn't cleaning up old sessions (regardless of what was checked when I set up the client) and that caused me to have to change the DISPLAY BASE with each reboot of the server. Is this a known problem (or even a problem) with the NX client, perhaps?

Yes, this is a known problem apparently and the vanilla sources include a patch, but unfortunately I haven't figured out how to package this fix properly yet.  There is an /etc/init.d file that cleans the session files on reboot, but they aren't packaged.  I will try to get it out in the next version to resolve this.

---

### Post by paoletto on 2008-07-15
Hi daflame!

I want to tank you again for your work!
Now with the hardy version of freenx it's even possible to connect to the same session either from windows or from linux client!

Moreover it seems it's possible to resize the desktop simply resizing the windoW! that's great! and it works perfectly!

I really wish you could bring your great packages into official ubuntu repository!

One last question: you think it will be possible in future to have the same session connected to more than one client? (just like vnc, for example)

Cheers
Paolo

---

### Post by NTolerance on 2008-07-15
Is there any chance that shadowing Compiz sessions will be possible?  I had to stop using NX due to the fact that I run Compiz and the client locks up if you try to shadow a session.  I wonder if this can be overcome or if it's a limitation with the technology.

---

### Post by daflame on 2008-07-20
> **paoletto said:**
> Hi daflame!

I want to tank you again for your work!
Now with the hardy version of freenx it's even possible to connect to the same session either from windows or from linux client!

Moreover it seems it's possible to resize the desktop simply resizing the windoW! that's great! and it works perfectly!

I really wish you could bring your great packages into official ubuntu repository!

One last question: you think it will be possible in future to have the same session connected to more than one client? (just like vnc, for example)

Cheers
Paolo

Yes in a sense.  With the next release which includes fixes to improve VNC shadowing you can shadow the desktop of another user whether on the desktop or in NX and both be sharing the same screen.  Unfortunately it isn't a native NX solution, so it is slower (for the person shadowing) but it will work.  At least one side will be fast.

---

### Post by daflame on 2008-07-20
> **NTolerance said:**
> Is there any chance that shadowing Compiz sessions will be possible?  I had to stop using NX due to the fact that I run Compiz and the client locks up if you try to shadow a session.  I wonder if this can be overcome or if it's a limitation with the technology.

As mentioned above.  FreeNX doesn't use the native NX shadowing technology which did (I'm not sure if it still does) have a problem with shadowing desktops with Compiz enabled.

FreeNX uses VNC with x11vnc to shadow, so if VNC through x11vnc works for your display to share the desktop then it should work through the new shadowing as well.

---

