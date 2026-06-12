---
title: "Remote Desktop not working"
date: 2020-06-15
forum: General Help
---

### Post by optimusprime11 on 2020-06-15
Hi everyone.

I’m new to this forum and new to Linux. 

I have a fresh install of Ubuntu 20.04 desktop on a NUC that I will use to run Plex and associated programs. I need the desktop graphics as I learn CLI on my journey. This project is essentially a server that requires a Remote Desktop 

I’m failing at the first hurdle and I can’t figure this out. I’ve read lots of how to’s but nothing is working. I understand the Remote Desktop protocol is VNC and Vino is the deamon that supports the feature. Encryption is turned off (for cross platform compatibility) and the service is running and listening on port 5900. The firewall is also set to allow any network to access the port 5900.

I have been using RealVNC on windows 10 and iOS with no luck. The iOS app reports ”The port on which the computer is listening for a connection could not be contacted”. I’m not sure if that’s a clue to the problem or a red herring. 

Everything is setup logically and as expected and it should work but something is missing... Could you help point me in the right direction, please?

---

### Post by HermanAB on 2020-06-15
You need to test the system in a structured way.  First see whether the name of the device resolve (if you use DNS);  Then see whether the IP address actually reach the host; then see whether a datagram on the port reaches the service.  To do that, you may need to install a few basic utilities.

DNS test:
$ nslookup hostname

IP routing test:
$ ping ipaddress

Connect to server test:
$ telnet ipaddress 5900

In each case, look at the error messages and google them for enlightenment.

---

### Post by TheFu on 2020-06-15
There are multiple remote desktop tools. Just because one is already installed, doesn't mean you have only that choice. IMHO, there are many better options, for a number of reasons, but your needs and mine may not align.

Regardless, you should check these things:
* is the server running, whatever that is?  For any client-server connection to work, there must be a server listening on the expected port, waiting for client connections.
* does the "server" have a static IP?  Are you 100% positive that is the IP being used by the client?
* is the system firewall allowing all the ports and types of traffic that the server (or client) need to make a connection?
* is the router setup to allow connections between computers on the same LAN?  Many routers will block connections between computers on the same subnet or between wired and wifi LAN segments.

Nobody will be able to help you when you make claims but don't actually PROVE IT.  So,>  Everything is setup logically and as expected and it should work is clearly NOT the case.  You should prove these things, step by step.

BTW, plex runs a webserver that listens on 32400/tcp, so if you point a browser at that port with the correct IP, then you should see a website with "P-L-E-X" all over it when the plex server is running.

With all that said, 20.04 gnome3 desktop has some new remote desktop solution that is supposed to be point-n-click between Ubuntu 20.04 systems and later.  I doubt it works for other OSes as easily.  The "Ubuntu Desktop Guide" should have a page about setting that up. Ok, I couldn't find it.  ;)  Found this: [https://ubuntu.com/tutorials/access-remote-desktop#1-overview](https://ubuntu.com/tutorials/access-remote-desktop#1-overview) which is the client-side setup, but not the server side.

I dumped all RDP/VNC stuff years ago and switched to x2go, which uses a more efficient protocol and uses ssh tunnels so the connections are secure even over the internet when ssh-keys are used for authentication. There are x2go clients for Linux, OSX, and Windows. I know the Linux and Windows clients are very solid.  Anyways, if you are interested in x2go, ask. x2go feels about 2-3x faster than the others over the internet.  It isn't great for video, but for typical office-productivity stuff, it is excellent when just ssh isn't enough.  x2go uses an ssh connection, ssh credentials, and the ssh port just like 50 other ssh-based tools. Takes about 10 min to setup on the client and server side. I've posted steps in these forums, I'm certain.

BTW, setting up plex doesn't have any local GUI, so that won't help. ssh or a local terminal will still be needed.  Setting up the file permissions for plex is easiest using a shell too, IMHO.

---

### Post by optimusprime11 on 2020-06-18
I final figured it out after reading your posts and applying some unilateral thinking!

In terminal I used this command:
netstat -artpe
I found that port 5900 was being used BUT vino was looking on it on it's self assigned 127.0.0.0 IP address. I used 'dcongf editor' to find the network interface and deleted the 'lo' network so that it accepts on all networks.

thanks for your help.

---

### Post by TheFu on 2020-06-18
> **optimusprime11 said:**
> I final figured it out after reading your posts and applying some unilateral thinking!

In terminal I used this command:
netstat -artpe
I found that port 5900 was being used BUT vino was looking on it on it's self assigned 127.0.0.0 IP address. I used 'dcongf editor' to find the network interface and deleted the 'lo' network so that it accepts on all networks.

thanks for your help.

You are welcome, but really VNC shouldn't be available except on localhost (127.0.0.x) for security reasons. Either an ssh tunnel or full VPN should be used to make the connection to the VNC server, then access VNC through that tunnel on the localhost:5900 port.  If you google "ssh vnc tunnel", you'll find this is a very popular search.
A reputable result: [https://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](https://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

"ssh vnc tunnel putty" will locate guides for doing this from Windows. As usual, Windows makes things harder. ;)

---

### Post by optimusprime11 on 2020-06-30
Quick update.

As I have been getting further down the rabbit hole I&#8217;ve decided to stop trying to recreate the &#8216;windows experience&#8217; and run this server as a proper, headless server. I&#8217;m now learning CLI and the Ubuntu language.

Thanks for your previous advice, it was much appreciated.

---

### Post by HermanAB on 2020-07-01
You can run GUI programs remotely using SSH:
$ ssh -Y user@server "mousepad filename"

Mousepad will then pop up on your local desktop.  

With SSH, you don't need a remote desktop and your local machine already has one.

---

### Post by ActionParsnip on 2020-07-02
What are you trying to achieve? What will you do when you get connected to the system via VNC? What is the purpose of the connection?

---

### Post by optimusprime11 on 2020-07-02
In essence i'm configuring a home server for media inc FTP, Plex etc. When i thought about I don't actually need a GUI, it was just familiar to me. I am out of my comfort zone (not a bad thing) with CLI and need to learn a few things along the way.

---

### Post by TheFu on 2020-07-02
> **optimusprime11 said:**
> In essence i'm configuring a home server for media inc FTP, Plex etc. When i thought about I don't actually need a GUI, it was just familiar to me. I am out of my comfort zone (not a bad thing) with CLI and need to learn a few things along the way.

Please don't use plain FTP. Use sftp, scp, NFS, and/or ssh w/ rsync or sshfs.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a shell reference book.  No hassle download.

---

### Post by kneutron on 2020-07-03
--There's nothing wrong with using FTP for home use in your own LAN, behind a firewall/NAT. Vsftpd has been stable and secure for years, and doesn't have encryption overhead.  Not recommended to use FTP in the modern Internet environment with a publicly accessible Internet server, but I've never heard of a home FTP user getting hacked unless they allowed it out with uPNP or similar BS.

REFs:

[https://security.appspot.com/vsftpd.html#about](https://security.appspot.com/vsftpd.html#about)

[https://www.linuxquestions.org/questions/linux-security-4/how-secure-is-vsftpd-what-alternative-is-there-for-more-secure-access-713901/](https://www.linuxquestions.org/questions/linux-security-4/how-secure-is-vsftpd-what-alternative-is-there-for-more-secure-access-713901/)

---

### Post by HermanAB on 2020-07-04
Anonymous FTP is one of the two network protocols built into the MS Windows file browser.  It has many uses and is effective if used with care.

---

### Post by TheFu on 2020-07-04
[LIST=1]
[*]We all need ssh on our systems. Securing ssh on the LAN and on the WAN is well-understood.
[LIST]
[*]Use ssh-keys/ssh-certs; avoid passwords.
[*]Use a basic fail2ban install
[/LIST]
[*]sftp comes enabled with ssh.
[*]Plain FTP is similar to telnetd or rlogind.  When was the last time anyone suggested setting up either telnetd or rlogind - even if just for LAN-only use?
[*]Google Chrome-browser is removing plain FTP support: [https://www.chromestatus.com/feature/6246151319715840](https://www.chromestatus.com/feature/6246151319715840)
[*]Almost all Linux file manager programs have support for sftp built into their URL handling. Just use sftp://userid@serverIP/. Some may use ssh:// instead, but it is sftp.
[*]All ssh/sftp/scp tools on Linux honor ssh-key and settings in ~/.ssh/config which make using these secure protocols 100x easier than plain FTP.
[/LIST]

Often, folks deploying an FTP server are doing it because it was one of the core protocols for the internet over 40 yrs. Books on Unix/Linux administration still show how to use it for some reason. RHEL Certification tests still include setting up a plain FTP server for some reason.  Python and Perl both have a 1-line FTP server that can be run.  Of course, I think plain FTP should have died out in 2000.  ssh, scp, sftp have been around and stable since about 1995.  Many corporations have security policies against using plain FTP for any non-public data.  Sadly, people often connect storage to their cheap home routers and enable FTP so they can access that storage from anywhere, not considering that the world can also access that storage.  A number of router makers have had huge bugs in their FTP and other file sharing deployment code.  Buffalo, Linksys, Asus, Netgear.  Asus is a few years into their FTC mandated security monitoring over issues with the firmware on their routers: [https://arstechnica.com/information-technology/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/](https://arstechnica.com/information-technology/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/)

There are excellent sftp/scp clients for every networked OS.  Windows has WinSCP and Filezilla.  And they both work for noobs, though not as easily as the linux tools do. That's a matter of opinion, of course, but Unix systems can use sftp, scp, and ssh for almost any sort of networking between two systems we like.  With 1 command, we can have a pretty capable server. With another command, we can have keys, not passwords, used.  Security people know that using passwords along is usually a failure to secure anything.

People who don't eat, sleep, and live security need easier answers, hence my stance about plain FTP.  All the details around it are easily forgotten by non-experts. The OP specifically said, 
> new to Linux
So I really wanted to help him out and limit confusion.

Of course, the OP should feel free to setup an FTP server, if that really is desired. I wouldn't, but it isn't my system.

---

### Post by optimusprime11 on 2020-07-14
Thanks for the information. I will use SFTP when it comes to it, that&#8217;s very good advice, thank you! In the meantime I have setup samba to work with my windows laptop from my LAN. I have no desire to access my server remotely from the internet (yet).
I know it&#8217;s been a while since I replied to this thread but I have been in the depths of learning CLI and configuring this server. I have to admit, once you get the basics of Linux and read a few posts. Ubuntu&#8217;s core system is much easier to understand and work with than Windows. Don&#8217;t get me wrong, Windows has its place but for a resource light, powerful server without obscure obstructions, Ubuntu is Great!
thank you for your help on my journey!

---

### Post by ActionParsnip on 2020-07-14
Doesn't Plex have a web interface you configure it with?

---

### Post by TheFu on 2020-07-14
> **ActionParsnip said:**
> Doesn't Plex have a web interface you configure it with?

Yes, but the initial access only works from the same /24 LAN.  In a home environment that usually isn't any issue. In fact, the web interface is THE ONLY WAY to setup a Plex Server.

sudo apt install plexmediaserver  # on the "server"
Then point your browser at the same LAN at  the IP and specific port:
**http://{my-plex-server-LAN-IP}:32400/web/**

No need for any Plex account, ever. Of course, rather than using the IP address, if DNS, /etc/hosts or avahi are working, you can use the hostname instead.

But if someone sets up a Plex server on a VPS provider, then an ssh-tunnel or remote desktop to run a browser will be necessary.  Someone trying to have a minimal "server" wouldn't want all the GUI dependencies requires to run a browser or VNC/x2go desktop. The 1 line ssh-tunnel connection is pretty easy, but for people not used to thinking about tunneled connections the abstract settings are confusing.

But a remote desktop really isn't needed/desired/cannot be used for plex stuff.  For media management, ssh and sftp and rsync are the simple methods.  But the client systems on the LAN from which the media management is being performed will matter.  Media for plex needs specific permissions.

---

