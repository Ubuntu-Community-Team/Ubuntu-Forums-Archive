---
title: "x2go hangs during login but don't know why"
date: 2024-03-05
forum: General Help
---

### Post by mike-g2 on 2024-03-05
I'm trying to use x2go with my laptop as a client and desktop at work as a server. Both are running 22.04 MATE and I've installed xfce on the server.  However, my x2go session hangs while trying to connect.

Here's the output from `$ x2goclient --debug`

```

$ x2goclient --debug
x2go-INFO-1> "Starting X2Go Client 4.1.2.2..."
x2go-WARNING-1> English language requested, not loading translator.
x2go-WARNING-1> English language requested, not loading translator.
x2go-INFO-3> "Started X2Go Client."
x2go-DEBUG-../src/onmainwindow.cpp:575> "$HOME=/home/user"
x2go-DEBUG-../src/onmainwindow.cpp:2266> Reading 1 sessions from config file.
x2go-DEBUG-../src/sessionbutton.cpp:361> Creating QPixmap with session icon: ":/img/icons/128x128/x2gosession.png".
x2go-DEBUG-../src/onmainwindow.cpp:13290> libssh not initialized yet. Initializing.
^[[Bx2go-DEBUG-../src/sessionbutton.cpp:361> Creating QPixmap with session icon: ":/img/icons/128x128/x2gosession.png".
x2go-DEBUG-../src/onmainwindow.cpp:2752> Creating QPixmap with session icon: '":/img/icons/128x128/x2gosession.png"'.
x2go-DEBUG-../src/onmainwindow.cpp:2819> Starting session via Smart Card, SSH Agent or Kerberos token.
x2go-INFO-8> "Starting connection to server: myserver.uni.edu:22"
x2go-DEBUG-../src/onmainwindow.cpp:2853> Starting new ssh connection to server:"myserver.uni.edu":"22" krbLogin: false
x2go-DEBUG-../src/sshmasterconnection.cpp:168> SshMasterConnection, host "myserver.uni.edu"; port 22; user "user"; useproxy false; proxyserver ""; proxyport 22
x2go-DEBUG-../src/sshmasterconnection.cpp:248> Starting SSH connection without Kerberos authentication.
x2go-DEBUG-../src/sshmasterconnection.cpp:250> SshMasterConnection, instance SshMasterConnection(0x7fdf04009650) created.
x2go-DEBUG-../src/sshmasterconnection.cpp:495> SshMasterConnection, instance SshMasterConnection(0x7fdf04009650) entering thread.
x2go-DEBUG-../src/sshmasterconnection.cpp:797> Session port before config file parse: 22
x2go-DEBUG-../src/sshmasterconnection.cpp:807> Session port after config file parse: 22
x2go-DEBUG-../src/sshmasterconnection.cpp:870> Session port before config file parse (part 2): 22
x2go-DEBUG-../src/sshmasterconnection.cpp:880> Session port after config file parse (part 2): 22
x2go-DEBUG-../src/sshmasterconnection.cpp:904> cserverAuth
x2go-DEBUG-../src/sshmasterconnection.cpp:943> state: 1

x2go-DEBUG-../src/sshmasterconnection.cpp:687> User authentication OK.
x2go-DEBUG-../src/sshmasterconnection.cpp:1708> LOGIN CHECK:"LOGIN OK\r\n"
x2go-DEBUG-../src/sshmasterconnection.cpp:1711> don't have interaction
x2go-DEBUG-../src/sshmasterconnection.cpp:1744> LOOP FINISHED
x2go-DEBUG-../src/sshmasterconnection.cpp:1748> No interaction needed, continue session
x2go-DEBUG-../src/sshmasterconnection.cpp:702> Login Check - OK
x2go-DEBUG-../src/onmainwindow.cpp:2947> SSH connection established.
x2go-DEBUG-../src/onmainwindow.cpp:3374> Continue normal X2Go session
x2go-DEBUG-../src/sshprocess.cpp:199> Executing remote command via SshProcess object 0: "x2golistsessions"
x2go-DEBUG-../src/sshprocess.cpp:213> this=SshProcess(0x55a3ba527290) Running masterCon->addChannelConnection(this, '"d262d45f-bb0b-4356-9e9a-64ff78bd2e59"', '"bash -l -c 'echo \"X2GODATABEGIN:d262d45f-bb0b-4356-9e9a-64ff78bd2e59\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:d262d45f-bb0b-4356-9e9a-64ff78"');
x2go-DEBUG-../src/sshmasterconnection.cpp:1810> Locking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1812> Passing new channel connection object to channelConnections.
x2go-DEBUG-../src/sshmasterconnection.cpp:1814> Unlocking SSH channel connection MUTEX.
x2go-DEBUG-../src/sshmasterconnection.cpp:1977> Creating new channel.

x2go-DEBUG-../src/sshmasterconnection.cpp:1990> New channel:0x7fdee41188b0

x2go-DEBUG-../src/sshmasterconnection.cpp:2065> Executing remote: "bash -l -c 'echo \"X2GODATABEGIN:d262d45f-bb0b-4356-9e9a-64ff78bd2e59\"; export PATH=\"/usr/local/bin:/usr/bin:/bin\";export TERM=\"dumb\"; x2golistsessions; echo \"X2GODATAEND:d262d45f-bb0b-4356-9e9a-64ff78bd2e59\";'"

x2go-DEBUG-../src/sshmasterconnection.cpp:2082> New exec channel created.


```

Can anyone help me figure out what's going on/wrong?

---

### Post by TheFu on 2024-03-05
Some things aren't clear from your post.

Does ssh work alone?
Disable audio, file sharing, printing and see if that works.
Is there anything in the x2go forums?
Did you use the PPAs for 22.04, not the default Ubuntu versions?

I don't have any 22.04 systems, but I don't see this on 20.04.  I did just test a 20.04 client into a 22.04-like Linux Mint x2goserver and it worked perfect.  I don't use any DE, so don't have any idea how that currently works.

---

### Post by mike-g2 on 2024-03-06
Hi,

Thanks for the response.  Sorry for not providing more detail.

Here's some more information.

[LIST]
[*]ssh: Works on its own, I can also run emacs remotely on the server and have an X11 window on the client.
[*]Packages installed using default ubuntu 22.04 ppa on both machines. Purged and reinstalled x2goserver and x2goserver-xsession on server, x2goclient on client.
[*] Have disabled audio and file sharing. Also tried X11 connection rather than XFCE, but getting the same behavior. 
[*] Did not see anything on the x2go forums (though they have very little traffic lately and few responses to queries posted there)
[/LIST]

I've tried adding my user to the /etc/group x2goclient entry, stopping and restarting the service on the server, but I get no change in behavior.

---

### Post by TheFu on 2024-03-06
The PPA should be from the x2go project, not Canonical/Ubuntu.

A few years ago, I remember having a similar issue. Since x2go is something I only use over the internet, when traveling, it wasn't a big deal to me.  Next time I tried it, it worked. I don't remember doing anything specific. It was probably a few months later.  I use fvwm as my window manager.

For running apps on the same LAN, I use **ssh -X** methods to run the apps as needed.  I've been doing this for 25 yrs - my browser and fat email client are running this way now.  

If I need a full desktop on the LAN, since most of my systems are running inside a libvirt+kvm VM, I use spice and **virt-manager** to make the full connection either over a network or if the VM is running on the same physical host I'm typing on, with a local Spice connection.  I've had my main desktop running inside a VM since around 2006. One of the best choices I ever made.  I've changed hypervisors 4 times and SPICE with KVM made it just like being there back in 2016.   That assumes you run a desktop inside a VM, which not everyone does.

---

