---
title: "How do you set-up Samba to share between Linux machines?"
date: 2014-11-23
forum: General Help
---

### Post by Mike_Walsh on 2014-11-23
Evening, everybody.

I apologise for asking yet again about something that must be like old, comfy slippers to many of you!

I have two machines, both running Linux. An elderly Compaq Presario desktop, running Ubuntu 14.04; and an even older Dell laptop (an original 1100, from 2002), which is running the current release of 'Puppy' Linux. It's the only thing that WILL run on it; every other distro I've tried disagrees violently with the video chip; a 'Brookdale'-core, Intel 'Extreme Graphics' 82845 G/GL/GE/PE/PV graphics chip. I refuse to go into saga of this piece of hardware, as I don't want to bore you all with the frustration I've endured with the thing...

Specs for both are as in my signature, below.

'Puppy' includes, amongst other things, a full suite of Samba access software. I've successfully set-up network printing between these two machines; I would LIKE to set up file transfer/sharing between the pair of them, also. Since 'Puppy' already has SAMBA access software, it seems logical to install this into Ubuntu, and, accordingly, I've already done this.

Trying to configure it, and make it work, is another matter...

I've read the official Ubuntu wiki on the subject; in the course of my research, I've read I don't know HOW many articles, blogs, postings, etc., on the subject.....and they are ALL different. I really am VERY confused; doesn't take much these days! ;)

It appears to involve a LOT of command-line work, and I'm not yet THAT comfortable with the shell. Is there a straight-forward, plain-English way of setting it up.....or am I attempting something that's beyond my current skill level?

I have set various folders that I want to access , for file-sharing in Nautilus. That is, I've changed the share permissions on these folders. I've also set the appropriate exceptions in the firewall for file transfer via Samba, using gufw. Now, then; what should my next step be? 

I'm ready to be educated like never before...! :D

Any advice would be very much appreciated.


Regards,

Mike.

---

### Post by deadflowr on 2014-11-23
You can avoid the command line,mostly, by installing from the software center: Samba.
It'll install the samba gui program.
Don't know how helpful that will be, but still...

---

### Post by Mike_Walsh on 2014-11-23
Thanks for that, deadflowr.

That's what I DID do; I've got the gui, which I've used to set the folders that I want to share. Beyond that, I'm struggling...

Basically, what I want to do is to share a single folder, which I've called 'HomeShare', into which I've placed the other folders that I wish to access. I thought it might simplify matters to put everything I want to access into one location.....although this folder IS almost 7 GB in size!

Now, I don't know if THIS will pose problems; but I have a separate /home partition.....which is being shared with my Lubuntu install. Is this liable to throw a spanner in the works? ;)

Regards,

Mike.

---

### Post by kevdog on 2014-11-23
Dont to delve off your project, however in my experience Samba is really unreliable -- I'm using mostly between linux and windows machines.  What I do really like however is ssh.  With ssh, you can mount a remote directory using sshfs.  It's really really easy to setup -- meaning its basically setting up the ssh server which is really really easy to do.  Another options other than samba or sshfs, is nfs, which I've used before between linux machines.  I personally prefer ssh.  I'm almost sure your puppy machine would have this capability.

---

### Post by Mike_Walsh on 2014-11-23
> **kevdog said:**
> Dont to delve off your project, however in my experience Samba is really unreliable -- I'm using mostly between linux and windows machines.  What I do really like however is ssh.  With ssh, you can mount a remote directory using sshfs.  It's really really easy to setup -- meaning its basically setting up the ssh server which is really really easy to do.  Another options other than samba or sshfs, is nfs, which I've used before between linux machines.  I personally prefer ssh.  I'm almost sure your puppy machine would have this capability.

Hi, kevdog.

Hm. Well; there are, of course, degrees of 'easy'. This is in no way aimed at you personally, so please don't take it that way.....it's more of a generalisation. When you've probably been using a particular implementation of something for a while, of course it's 'easy'; because you're used to it, and comfortable with its mode of operation. ;)

However, from my standpoint, as someone who's still relatively new to Linux, and not yet at all comfortable with the command line, it's all bewilderingly complex! I daresay in years to come, I shall become more comfortable with the shell (even now I'm using it far more than I did 6 months ago), but as things stand, I can't ever see me being able to set this thing up with my current skill-set.....

I really need someone to show me what needs doing, and to explain, as they go along, WHY each step needs doing.....at least on the more complex jobs, as this appears to me to be! :confused:

BTW: I've always been cursed with this terrible affliction; it's not enough for me to be told,'Do *this, *& *this,* and **this**; and that'll make whatever it is work'.....oh, no. I always have to know WHY *this *needs doing ( **and ***this, *and **this**).....Awful, isn't it? I've been like it for the last 54 years; I can't see me changing any time soon! :roll::lol:

Regards,

Mike.

---

### Post by Bashing-om on 2014-11-23
Mike_Walsh; Hello, my friend;

If it is your goal to "share files" between 2 linux boxes:
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449) <-easiest way to cp files 'tween two Lubuntus that share the same router/house (Morbius1)
Samba is a Windows thing, take the easy way out.

Not to discount the thrill of learning, but
[INDENT][INDENT]I adhere to the KISS principle
[/INDENT][/INDENT]

---

### Post by kevdog on 2014-11-23
Mr. Walsh.  

Let me see if I can ask you a few more questions, but I can easily get you up and running with an ssh server easily but I need to know more about your setup.

Between these computers, do all the computers need to push and pull (meaning each one needs to send and receive files)?  Argh, let me ask that a different way.  The problems with any client-server architecture is that the client can always connect to the server, but the server can not connect to the client.  I'm asking this because a ssh server may need to be setup on more than one computer -- this is easy -- you can almost use the exact same configuration file.    

Are you going to be sharing files outside the local LAN -- I ask this since whatever method you want to use, this brings in the topic then of hardening the installation -- possibly using utilities such as a firewall, and some utility like fail to ban.  Other security precautions could be made on the ssh server itself, and of course a port in your LANs router would need to be opened to allow communication from the outside world into the server.  This may also imply you would need to use some service like noip.com or dyndns.com whereby you could assign yourself a name to access your server remotely if the IP address of your router to your LAN changes often.  Again, if I knew your situation, we could more or less make some sense how complex the setup would need to be. 

In terms of the Ubuntu machine -- I'm going to have you install the openssh server and client as well as the sshfs (SSH file system) -- this package basically allows you to mount a remote directory located on the server remotely, and then simply copy and transfer files to the server as simple as dragging and dropping from one folder to another.  The advantage of ssh is all the communication is done over an encrypted connection -- which makes this setup possibly advantageous to you if you are connecting remotely -- for example from outside the Local LAN.

Within synaptic or the package manager choose to install openssh-client, openssh-server and sshfs.  If doing this at the command line, do the following:
```

sudo apt-get install openssh-server openssh-client sshfs

```

If you get this far, I'll help you set up the two way authentication keys -- one key stays on the server and the other goes to the client.  These act as your authentication credentials that makes the initiation of the hand-shake possible.

Just a preview to where we are going before we get you buried in the details --- Once everything is setup -- one command would mount the remote filesystem locally --- it would be like this:
sshfs kevdog@10.0.1.199:/home/kevdog ~/Ubuntu_computer -p 2223

What this command does above is says using the sshfs utility, ssh into server as username kevdog located at IP address 10.0.1.199 (this is a LAN address) logging into the home directory -- which is located at /home/kevdog, and remote this remote directly locally at ~/Ubuntu_computer.  The -p 2223 argument is there since I run my ssh server on a non-standard port -- in this example port 2223 instead of the usual port 22, and it tells the sshfs to use this port when authenticating rather than the default port.  

Once a command like this is given, its possible to use any command line tool, or any file manager tool such as nautilus, thunar, dolphin -- whatever you have to view the remote files. It's then as simple as cutting and pasting.  I believe there are some graphical utilities that would do a similar thing as mentioned above.  That's about it.  

I hope this gave you a basic understanding of what the goal is.  The actual setting up of the ssh server is very easy, since it just involves editing of the /etc/ssh/sshd_config file -- No fancy scripting and really no fancy configuation is needed.

---

### Post by Mike_Walsh on 2014-11-24
Hallo again, Kevdog.

Thanks for taking the time to get back to me again. FYI, I'm not a 'noob' when it comes to computing in general; my years of faffing about with these things date back to the late 70's/early 80's. Shades of the Commodore 64, TRS-80, Osborne and the early days of MS-DOS, I'm afraid..!

However, after years of getting lazy on Windows XP, I'm finding the learning curve with Linux to be a bit steeper than anticipated....but only in certain areas.

To answer your first question (and I hope this will simplify much of the rest of the process), no, I shall not be wanting both machines to push/pull; all I'm after, at this juncture, is for the Compaq (the main workhorse PC) to 'push', and for the Dell (the old laptop) to 'pull'. In other words, I simply want to use the laptop to access files on the desktop.

If I'm lucky enough to make this work, and to understand what's going on, then at a later date I may decide to make both machines push AND pull.....even to add MORE machines into the mix. But for now, I simply want the laptop to read/write files on the desktop. This will also be strictly 'in-house'; purely on the domestic LAN, for now. Start off small, and work your way up...

One final thing I'll probably need is a degree of security. The Desktop is permanently on Ethernet' whereas the Dell uses a wireless adapter. Whenever I look at the wireless connection info on the 'Puppy' machine (the laptop), I see there's a LOT of wireless networks that I don't recognise! It's surprising how few of them appear to be secure, too.....

So; to summarise:-

1) Desktop to 'push' (host), & laptop to 'pull' (client)
2) LAN only for now
3) Some degree of security!

Over to you, now... :)


Regards,

Mike.

---

### Post by Mike_Walsh on 2014-11-24
> **Bashing-om said:**
> Mike_Walsh; Hello, my friend;

If it is your goal to "share files" between 2 linux boxes:
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449) <-easiest way to cp files 'tween two Lubuntus that share the same router/house (Morbius1)
Samba is a Windows thing, take the easy way out.

Not to discount the thrill of learning, but[INDENT][INDENT]I adhere to the KISS principle
[/INDENT]
[/INDENT]


Hey, Bashing.

Thanks for that. At this stage, I have no intentions of discounting ANY given method of doing what I want to do; I want to try things out, and find out what will work best with my particular setup. The problem I have here is that one of the two boxes is using an OS that not many people on here are familiar with; yes, it's Linux.....but despite being BASED on 'Trusty', it works very differently to the 'buntus. And no, I can't put a different OS on the Dell; because nothing else will work (and no, I don't understand that EITHER).....as things stand, that's just the way it is, and I need to find a method that will work with what I have.

I'm just pleased to FIND an OS that WILL work on the Dell (the graphics chip is the culprit, and no, it's not one like young Alex's.....its an Intel; a 'Brookdale'-core, 82845 G/GL/GE/PE/PV 'Extreme Graphics' chip). A complete pain. Don't even go there...!

Appreciated. ;)

Regards,

Mike.

---

### Post by verymadpip on 2014-11-24
Hi there.
I use samba to share files in my place, but I do have a couple of Windows boxes.
Looking at the way I've set it up I used 5 commands*, BUT I already had a smb.conf saved from my last install & one of my commands was to change file permissions on the shared folders.*

This tutorial is pretty much the path I took:
[http://www.maketecheasier.com/install-and-configure-samba-in-ubuntu-for-file-sharing/](http://www.maketecheasier.com/install-and-configure-samba-in-ubuntu-for-file-sharing/)
I didn't create another user account & I live alone so my file permissions are pretty lax.

It took me a few attempts to get this right, I even locked myself out of all my folders on the "server" box at one point...but that's another story.

---

### Post by Mike_Walsh on 2014-11-24
Hiya, Pip.

Thanks for that. Like I said to Bashing-om  in the last post, I'm not going to discount ANY method at the moment. Because I've got rather an off-beat setup, I shall experiment until I find a method that works. I DO like the look of the method outlined in Bashing's link, for one-off transfers. I run 'Puppy' from a 'nano' flashdrive, permanently plugged into one of my USBs (I only have two), and the other is occupied by a TP-Link  wireless adapter....but that means I can use the Hard drive PURELY for storage.

I'm off down town shortly, to pick up a CardBus to 4xUSB converter; so I can finally make use of the CardBus slot under the hard drive caddy.....I've never used it since the laptop was new..! If I can plug my external Seagate HDD into it, there might not even be any need to do all this; but I'd still like to try.....it's all good experience.

Appreciated.

Regards,

Mike. ;)

---

### Post by Morbius1 on 2014-11-24
Not once in any of your posts did you define the nature of the problem.

The other machine can't see the samba server?
The other machine can see it but can't access it?
Something else?

---

### Post by Mike_Walsh on 2014-11-24
Hallo, Morbius.

You're absolutely right, of course; I haven't defined the problem, have I?

I have SAMBA installed, and up & running, on the Presario (the desktop PC). When I go to access folders on the Presario (the host), from the laptop (the client, which is running 'Puppy'), what I'm getting, all the time, is 'Can't connect to server.'

That's the crux of the problem, as it currently stands. Apologies for that! So I guess you can say that at the moment, the client not only can't access the server.....it's not even seeing it (but the way Puppy's file manager, 'Rox', works is a bit of a nightmare, after getting used to Nautilus). Rox doesn't even HAVE a 'network' folder (unlike Nautilus), so.....I'm not 100% sure how it goes about looking for other machines on the network. I'm still finding my way around it!

Regards,

Mike.

---

### Post by kevdog on 2014-11-24
Ok 

On the server make sure the openssh-server package is installed.
On the client you are going to have to install the openssh-client.  i'm not sure the type of OS the client is running.  This package may be named something similar but different in the Puppy archive.

If Ubuntu is running on the server, the server configuration files are all located within the /etc/ssh directory.  Will change the sshd_config file in a minute.  This is the file that controls configuration of the server.

Each user on the server needs an account.  I'll assume you are the only user.  User keys and and specific user files are located within ~/.ssh.  If the ~/.ssh isn't created, create it, and then change into the directory.  We are going to create keys for the user (please note that I'm being biased in this recommendation, its possible to use a ssh server without keys and login with password, but I think its bad practice.)  Within the ~/.ssh directory on the server
```

ssh-keygen -t rsa -b 4096

```
This basically generates a RSA type ssh keypair that is 4096 bytes in length -- keys can be either DSA or RSA and 1024, 2048 or 4096 bits in length.  If you want a password for your key, then use one.  If you want a blank password just hit return. Passwords can always be added later.  
Two keys will be created within this directory - id_rsa (which is the private key) and id_rsa.pub (which is the private key).  The private key needs to be moved to the client.  It should not reside on the server.  The public key resides on the server.  To allow the server to use this key you need to put in with the authorized_keys files.  This is done by:
```

cat id_rsa.pub >> authorized_keys

```

Move the id_rsa key to the client, and if on another type linux distribution, this needs to go specifically within the ~/.ssh/ directory.  

On the server, edit the /etc/ssh/sshd_config file as root -- gksu gedit /etc/ssh/sshd_config or kdesu kate /etc/sshd_config or use what program you like!!
Couple of lines that you may or may not want to change:
Port 22 
Explanation:  Port 22 is the standard port for ssh server.  You can change this to a non-standard port.  I tend to run my ssh servers on a different port using this as security by obscurity method as one method to harden the installation, however the use of this practice is controversial.
RSAAuthentication yes  (remove the #tag in front of the line)
PubKeyAuthentication yes (remove the #tag in front of the line)
PasswordAuthentication  --- either use yes or no.   With password authentication you don't need any keys and just need the name and login password on the server.  With keys you need the keys as described above.

X11Forwarding -- yes or no (If choosing yes you can tunnel X sessions such as gettign some programs to run on the server but the output to show on the client.  If choosing yes, then you must change the next line to:  )
X11DisplayOffset 10  (See explanation above)

UsePAM -- yes or no (this option is the source of major frustration for me. Sometimes PAM works and sometimes it doesn't.  Change to no here for now and later you can try with the yes option)

Once your done editing your choices, save the file.

If any modification is done with this file, the ssh server must be restarted on the server.  You do this by the following:
sudo service ssh stop
sudo service ssh start

or you can combine the following:
sudo service ssh restart

That's it with the server.  

On the client, just place the id_rsa file within ~/.ssh/ directory and make sure the openssh-client package is installed. 

Once that's done -- you can test everything.  Assuming there is no firewall on the client blocking outgoing connections or firewall on the server blocking incoming connections, all you need to know is the IP address of the server (I'll assume for example it's 192.168.1.100) and the port number its running on.   From the client within a command prompt, try to login to the server  (You only need -p flag if server is running an another port other than 22):
ssh -p <portnumber> <username>@<IP_address>

If you need to tunnel X connections, you would start this with the following:
ssh -YC -c blowfish -p <portnumber> <username>@<IP_address>

If you can successfully login, that means the ssh server is correctly setup.  To exit the remote screen, just type exit.  This means that a basic setup is up and running.  

To make use of sshfs which mounts a remote directory locally, you would do the following:
sshfs <username>@<IP_address>:<remote directory> <local directory> -p <Port_number>

To test with this command use:
<remote directory>=/home/<username>
<local directory>= This can be anything.  Create the directory -- for example mkdir ~/remote_directory  and this would then be <local directory>=~/remote_directory

Hopefully this is a good start.

---

### Post by Mike_Walsh on 2014-11-24
Hi, kevdog.

Haven't yet had a chance to run right through your post (busy, busy, busy today, I'm afraid), but I can tell you the laptop (the client) is running 'Tahrpup' 6.0. This is based on 'Trusty', is running the 3.14 kernel, and has access to the Ubuntu 'Trusty' archives.....although the package format is all in .pets and .sfs files, this being the way that Puppy has worked for years, as I understand it. Blame Barry Kauler for that, if you must.....but it's rejuvenated the old Dell, and brought it back into service.

And having said that, I'm pleased to be able to report that my new Cardbus>4xUSB adapter works perfectly; I now have 6 USBs instead of 2! In a way, this makes this thread a wee bit redundant, because I can now plug my Seagate portable HDD in, and access all my files THAT way (I've got multiple backups of all my data , all OVER the place...!) 

BUT: I'm won't say the thread's redundant, because I still want to get file transfer working; I'm a stubborn old so-and-so who doesn't give in easy! So, I'll have a look through what you've just sent a little bit later on, when I've got more time in hand...

Bear with me, please. :)

Regards,

Mike.

---

### Post by verymadpip on 2014-11-24
Hi again Mike.
I was afraid Puppy would be using a "weird" file manager. :)  I know it's not really weird, just something I'm not used to or have any experience with.

I've managed to see my shared folders with PCManFM (Lubuntu) & Thunar (Xubuntu), but I expect the way they work is kinda to take the pain out of these things.

---

### Post by Dennis N on 2014-11-24
I agree with kevdog on using SSH. He has very good explanations there.

Comments:

I have SSH set up on my local network, but connect to other machines through the file manager "Connect to server" option. So I don't use the terminal. Not all file managers have this capabilily, however. Nautilus does, and so does Caja in Ubuntu MATE. 

For distros without direct file manager support, there is a application called gigolo that can manage the connection through a GUI. I see Xubuntu 14.04 comes with gigolo by default.

I never did the key exchange thing, but connected with the password of the account on the remote computer. Mainly because I'm not a frequent user of SSH. For a couple of files, I tend to just transfer with an USB stick or portable drive. For extended work sessions across two or more machines, it's great.

I am no expert on SSH by any measure. I will defer to others on advice. Just relating here how I managed it.

---

### Post by kevdog on 2014-11-24
Yes there are a number of GUI front-ends you can use to make the ssh or sshfs connection.  I usually use these GUIs after confirming everything works on the command line -- the reason for this is just in case things don't work -- you have to put the ssh server in debug mode and then read the output generated, etc. Usually I'm not aware of any GUIs that present this message, or not routinely at least.  I appreciate other users commenting here however since I'm not totally aware of all the programs and file managers in the Linux Universe.  I currently flip flop back and forth now between a Cinnamon desktop and KDE desktop.  I've never used MATE -- I suppose for lack of time setting it up.  I migrated away from Gnome 3 at least on the frontend after Gnome 2 stopped development.  I rarely use xcfe or lxde so I can't comment on their file managers.  Always so much fun too learn and play around with.

---

### Post by Morbius1 on 2014-11-24
OK, so I downloaded the puppy iso. At least I think I did. Well, you tell me..... I downloaded something called unicorn-6.2.1.91.iso. It was the only thing on the Puppy website that had an .iso at the end so I assumed this was it.

Anywho, made a cd from it and booted it to a live session:

First thing I did was try to ping the ubuntu server via mDNS:
```
ping ubuntu1404.local
```
That didn't work so I figured avahi wasn't installed so I installed it from the Puppy Package Manager + all of it's dependencies and then tried to start it. Timed out.

Frankly I gave up trying to do this the Linux way since this is the first time I have installed a Linux in the last few years that didn't have avahi running out of the box. Instead I just accessed the share by ip address:

Menu > Network > YASSM:
[ATTACH=CONFIG]258175[/ATTACH]
And the share automatically opened up in what appears to be some sort of file manager:
[ATTACH=CONFIG]258176[/ATTACH]

Maybe if I installed it for real I could eventually figure out why avahi can't be started but the samba client on puppy seems to be operational.

---

### Post by Mike_Walsh on 2014-11-24
Hi, Morbius.

If you want to see what the version I have is like, you want this page:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

Download the 4th entry from the bottom; tahr_6.0-CE_PAE.iso. That's the one. Burn to CD, and boot from it. Gives you a live session; you can then install to a flash drive, and create your save-file at the end of the first session, when you select Shutdown. That'll let you figure out what's what. I suspected it might be the firewall giving problems, so I disabled them both, temporarily. Tried your method for a one-off transfer, using SimpleHTTPServer.....even that wouldn't work, so.....I must have something blocking me somewhere, but I'm hanged if I can work out what.

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-24
Did that. That's a lot better - much faster. Same results I'm afraid only it's doing things twice as fast as the newer ( ? ) version.

Accessing the simple http server works as well:
[ATTACH=CONFIG]258179[/ATTACH]

Don't know what to tell you.

---

### Post by Mike_Walsh on 2014-11-24
Hm. Me neither...

It's obviously not the firewalls, since I disabled both, temporarily of course, just to try these out. So my next thought is that it must be a permissions thing. Either that, or I need to change some settings on the router....but what would need changing? Network printing, from the Dell laptop to the Presario desktop (which has my Epson attached), works nicely.....albeit somewhat on the slow side; almost as though it's having to fight its way through. I printed another test document off this evening; sometimes it's printed off in 30 seconds or so.....this evening, it took nearly 10 minutes to get through to the printer. I wonder if it's anything to do with the fact that 'Puppy' uses an older version of CUPS (v1.48) as opposed to the version Ubuntu uses (v1.72)? I wouldn't have thought it would make that big a difference... :confused:

Anyway, I'm turning in for the night; it's 1 am over here.....time for some shuteye. I'll catch you tomorrow, if you're about. :)

Regards,

Mike.

---

### Post by kevdog on 2014-11-25
Let me know if you guys need help.  Seems like there are a bunch of questions and issues going on in the thread.  I looked up Puppy yesterday however have never installed it.  Very light weight.

---

### Post by Mike_Walsh on 2014-11-25
Oh, yeah; it's ALL of that. My old Presario is quite snappy with Ubuntu.....but with Puppy, its feet don't touch the ground; it FLIES. It's only about 220 MB in total; it decompresses into RAM at bootup, and just sits there.....RAM of course being much faster than a HDD, and on a par with an SSD. And despite its small size, there's over 200 apps in there...yet NO skimping on features. It might not have a particularly fancy GUI, but I'd sooner have functionality over pretty looks, any day.

To give you some idea of just how rapidly it boots, my mate has a top-of-the-range HP, running Win 8, with an i7-4770k, and a 500 GB Samsung SSD, with fast-boot turned on. I have an old single-core Athlon 64 in here, with a half-meg cache, and 'Puppy' is running from a SanDisk 16 GB flash drive.'Puppy' is up-and-running, while he's still waiting for Windoze to get its act together; it's a real eye-opener just HOW quick it is.

Feel free to 'chip-in' ANY time you like; 'many hands make light work', and all that. BTW, any ideas on why my printing is sometimes fast, and sometimes very leisurely? I have a funny feeling PART of the communication problem might be RIGHT there, in plain sight...but I don't really know quite what to look for, or to check.

Regards,

Mike.

PS: I don't have much spare time at the moment, but I've saved your post about SSH. When I get a bit more time, I'm going to sit down and have a good look at what you've suggested. Incidentally, having already got Samba installed, will it interfere with ssh, if I do install it?

---

### Post by Mike_Walsh on 2014-11-25
> **Dennis N said:**
> I agree with kevdog on using SSH. He has very good explanations there.

Comments:

I have SSH set up on my local network, but connect to other machines through the file manager "Connect to server" option. So I don't use the terminal. Not all file managers have this capabilily, however. Nautilus does, and so does Caja in Ubuntu MATE. 

For distros without direct file manager support, there is a application called gigolo that can manage the connection through a GUI. I see Xubuntu 14.04 comes with gigolo by default.

I never did the key exchange thing, but connected with the password of the account on the remote computer. Mainly because I'm not a frequent user of SSH. For a couple of files, I tend to just transfer with an USB stick or portable drive. For extended work sessions across two or more machines, it's great.

I am no expert on SSH by any measure. I will defer to others on advice. Just relating here how I managed it.

Hey there, Dennis. 

I've not got a lot of 'play-time', over the next few days, but I'll have a look at your suggestion as well, when I get a chance. I've looked at 'Connect to server' in Nautilus, but didn't know what it was for... ;)

Regards, 

Mike.

---

### Post by kevdog on 2014-11-25
SSH and Samba are different protocols -- one doesn't effect the other but they are not interchangeable.  It would be possible to use both at once, however I've found Samba to be frankly a big pain in the butt!  A lot of random disconnectes

---

### Post by Morbius1 on 2014-11-25
Can you ping the ubuntu machine from puppy by it's ip address. As in:
```
ping 192.168.0.100
```
Change that to the ip address of the Ubuntu machine.
Run the following command in Ubuntu if you don't happen to know what the ip address is:
```
nm-tool
```

---

### Post by Mike_Walsh on 2014-11-26
> **Morbius1 said:**
> Can you ping the ubuntu machine from puppy by it's ip address. As in:
```
ping 192.168.0.100
```
Change that to the ip address of the Ubuntu machine.
Run the following command in Ubuntu if you don't happen to know what the ip address is:
```
nm-tool
```

Hallo, Morbius.

Sorry to be a little while getting back to you; I'm not at home at the moment, so don't have access to my own machines..! 

I'll try pinging (I know the ip adresss), as soon as I can after I get in; that will at least let us know if the laptop is SEEING the desktop, won't it? It OUGHT to, since the network printing works.

Bear with me, please, and I WILL get back to you ASAP. It's a pain when you've not got access to your own 'puters. I want to have a look and see if gigolo is available in Puppy; since it has access to the 'Trusty' archives, it's possible it is; it MIGHT make it simpler if that can manage the connection for me. What do you think; worth a try?

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-26
The reason I ask is because if the ping is successful I want you to go to Samba-Login in the puppy menu and connect to the Ubuntu machine that way, like this:
[ATTACH=CONFIG]258221[/ATTACH]
**EDIT**: Sorry, the item is the menu is "YASSM Samba share login" - the actual utility is called "samba-login".

[COLOR=#0000cd] In the case above I created a guest accessible share of a users Public folder so I don't need a user name or password. In my case the connection is made and the puppy file manager opens up to reveal the contents of the share.[/COLOR]

If it doesn't for you the first thing I would do is disable the firewalls of both machines and try it again.

If it still doesn't work after the firewall is disabled then the problem may not be with puppy but with ubuntu. In that case you might want to post the output of these commands from ubuntu:

This one will tell us how samba itself is configured:
```
testparm -s
```
This one will tell us how your shares are configured - you stated you created the shares through Nautilus:
```
net usershare info --long
```

---

### Post by Mike_Walsh on 2014-11-26
Hallo again, Morbius.

Right then; I'm back home, and 'in the saddle'.

First of all, I've done the 'ping' test. That's successful. I expected it would be, given that the network printing works. BTW, I know why it took 10 mins to send a document through to the printer the other night; 'twas my own fault, for being in a hurry and quitting Abiword before the printer had received the document... #-o

I've tried the samba login with YASSM. No soap. Tried it again with both firewalls temporarily disabled; still the same. Tried it, too, with my own 'HomeShare' folder; no log-in, and it's not seeing the shares. Each and every time, it's coming up with 'No connection to [foldername]!'.

So; this is the output from 

```
testparm -s
```

```
[Documents]
    comment = General Docs.
    path = /home/paul/Documents
    valid users = paul
    read only = No


[Mike's Stuff]
    comment = Mike's Stuff!
    path = /home/paul/Mike's Stuff
    valid users = paul
    read only = No


[Pictures]
    comment = Piccies!
    path = /home/paul/Pictures
    valid users = paul
    read only = No


[Videos]
    comment = Vidz!
    path = /home/paul/Videos
    guest ok = Yes
paul@mic-w:~$

```


And here's the result of 

```
net usershare info --long
```

```
paul@mic-w:~$ net usershare info --long
WARNING: Ignoring invalid value 'share' for parameter 'security'
[Videos]
path=/home/paul/Videos
comment=Vidz!
usershare_acl=Everyone:R,MIC-W\paul:F,
guest_ok=n


[Mike's Stuff]
path=/home/paul/Mike's Stuff
comment=My stuff...
usershare_acl=Everyone:R,MIC-W\paul:F,
guest_ok=n


[Pictures]
path=/home/paul/Pictures
comment=Piccies!
usershare_acl=Everyone:R,MIC-W\paul:F,
guest_ok=n


[Documents]
path=/home/paul/Documents
comment=General Docs.
usershare_acl=Everyone:R,MIC-W\paul:F,
guest_ok=n


[HomeShare]
path=/home/paul/HomeShare
comment=
usershare_acl=Everyone:F,
guest_ok=n


paul@mic-w:~$

```

I hope that tells you more than it does me; I'm not at all certain what I'm supposed to be looking for here.

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
I needed the entire output of the testparm -s command not just the share definitions.

As for the share definitions ....... You can create a samba share two different ways in Ubuntu:

The classic way by adding a share definition to smb.conf itself like this one:
> [Videos]
    comment = Vidz!
    path = /home/paul/Videos
    [COLOR=#0000cd]**guest ok = Yes**[/COLOR]
And through Nautilus ( which puts the share definition in /var/lib/samba/usershares ) like this one:
> [Videos]
path=/home/paul/Videos
comment=Vidz!
usershare_acl=Everyone:R,MIC-W\paul:F,
[COLOR=#0000cd]**guest_ok=n**[/COLOR]
You have created the same share with the same name using two different methods but with two different settings. One allows guest access and the other does not. Which share definition will Samba obey? Your guess is as good as mine.

I would get rid of one or the other so that there is only one definition per share.

If you keep the shares that do not allow guests you will need to add the client user to the samba password database. So if you want to allow say ... morbius to access the share you would have to:

Add morbius as a regular user on the ubuntu machine.
Then add morbius to samba:
```
sudo smbpasswd -a morbius
```

Really need the total output of "testparm -s" though. When you ran the net usershare command it posted a warning about how you are set up:
> WARNING: Ignoring invalid value 'share' for parameter 'security'
The whole output of testparm may reveal other anomalies.

---

### Post by Mike_Walsh on 2014-11-27
Hallo, Morbius.

My mistake; was nearly asleep when I got in last night, and didn't think to scroll back up in the terminal to get everything you needed!

This, I believe, is the full output:-

```
paul@mic-w:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: Ignoring invalid value 'share' for parameter 'security'
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Mike's Stuff]"
Processing section "[Pictures]"
Processing section "[Videos]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = mic-w
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Documents]
    comment = General Docs.
    path = /home/paul/Documents
    valid users = paul
    read only = No


[Mike's Stuff]
    comment = Mike's Stuff!
    path = /home/paul/Mike's Stuff
    valid users = paul
    read only = No


[Pictures]
    comment = Piccies!
    path = /home/paul/Pictures
    valid users = paul
    read only = No


[Videos]
    comment = Vidz!
    path = /home/paul/Videos
    guest ok = Yes
paul@mic-w:~$

```

I've also redone the share permissions. I've set them (hopfully) so that I can not only read them on the laptop, but also modify if needed. You'd best tell me if these look okay now, please.

```
paul@mic-w:~$ net usershare info --long
WARNING: Ignoring invalid value 'share' for parameter 'security'
[Videos]
path=/home/paul/Videos
comment=Vidz!
usershare_acl=Everyone:F,
guest_ok=n


[Mike's Stuff]
path=/home/paul/Mike's Stuff
comment=My stuff...
usershare_acl=Everyone:F,
guest_ok=n


[Pictures]
path=/home/paul/Pictures
comment=Piccies!
usershare_acl=Everyone:F,
guest_ok=n


[Documents]
path=/home/paul/Documents
comment=General Docs.
usershare_acl=Everyone:F,
guest_ok=n


[HomeShare]
path=/home/paul/HomeShare
comment=Network Share
usershare_acl=Everyone:F,
guest_ok=n


paul@mic-w:~$

```

Apologies again for the mistakes. I don't think too well when I'm nearly asleep on my feet; I was trying to get the info to you before I crashed out, since we're like as not in different time-zones...

Anything needs changing, please let me know and we'll see what needs doing to modify them; you'll probably have to tell me which files need accessing, etc. I don't understand why one share for 'Videos' is allowing 'guest access', and the other one isn't; how have I ended up with that? Where do I need to make the modification.....do I need to go into 'samba.conf ' in order to change that one? I did indeed create the shares through Nautilus, so I don't quite understand how that's happened... And what's the warning about about the invalid value for the security parameter?

Sorry to have so many questions. I thought this ought to be within my capabilities, but it's quite possible I'm trying to run before I can walk here; this is uncharted territory for me. Despite the 30-odd years I've been fooling around with these things, this is NOT something I've attempted before.

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
There is still a mismatch. One share of a folder allows only paul and the other allows anyone with credentials.

Let's keep the shares in smb.conf since removing the ones created through Nautilus is less disruptive.

Just go back into nautilus, right click say your Pictures folder > Local Network Share > and unshare it. Then do it for all your other shares that you created in Nautilus.
When you run the following command it should come back empty:
```
net usershare info --long
```

When you are done add "paul" to the samba password database:
```
sudo smbpasswd -a paul
```
From puppy the user name would be paul and the password would be the one you set in smbpasswd.

Your smb.conf is pretty much the default which is good. If I were to make any change at all to this setup I would add a couple of entries but at this stage since we are trying to do this with an ip address it wouldn't make any difference.

---

### Post by Mike_Walsh on 2014-11-27
Hallo, Morbius.

Okay. I've deleted the shares in Nautilus, and have set the name and password in the Samba password database. 

Now; with YASSM open in Puppy, this is what I've got entered so far:-

[ATTACH=CONFIG]258244[/ATTACH]

Sorry to be asking what must be obvious to many people on here.....but what should I enter for 'Share'? Do I take it that although I've unshared the folders in Nautilus, the folders are still set for sharing in smb.conf?

Takes a wee while for info to filter through this thick skull of mine, but once it has, it sticks like glue; I don't forget it in a hurry.

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
Any of the shares you defined in smb.conf. So try documents first. It shouldn't matter if the D is capitalized or not.

---

### Post by Mike_Walsh on 2014-11-27
Hallo again.

Um. Yeah. Thought that's probably what you'd say...so I went ahead and tried it. With, and without firewalls.

Still getting 'No connection to [foldername]'.

Thoughts? Comments? Do you need a look at smb.conf itself?

My thought is that OK, printing works, but there data is flowing from Puppy to Ubuntu. With this, data is needing to flow in the opposite (or both?) direction(s). But wouldn't turning the firewall off remove any obstructions in the data path?

I'm a wee bit confused, here.....and getting more so by the minute. By rights, this SHOULD now be working, yes?

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
The problem we have here is that none of the usual diagnostic techniques seem to be working in puppy itself. There's also a mention of Samba-TNG in the menu in puppy. Samba-TNG is a fork of Samba. I have no idea how it works, why anyone sober would fork it, and why anyone sober would use it......

Go back to the ubuntu machine, open a terminal, and run this command:
```
nautilus smb://192.168.1.67/documents
```
You should get prompted for the paul user name and password and then it should open up to the contents of that share.

Just want to make sure that the samba client on your Ubuntu box can access the samba server on the same box.

---

### Post by Mike_Walsh on 2014-11-27
> **Morbius1 said:**
> The problem we have here is that none of the usual diagnostic techniques seem to be working in puppy itself. There's also a mention of Samba-TNG in the menu in puppy. Samba-TNG is a fork of Samba. I have no idea how it works, why anyone sober would fork it, and why anyone sober would use it......

Go back to the ubuntu machine, open a terminal, and run this command:
```
nautilus smb://192.168.1.67/documents
```
You should get prompted for the paul user name and password and then it should open up to the contents of that share.

Just want to make sure that the samba client on your Ubuntu box can access the samba server on the same box.
Hallo again.

Now then; I've tried your suggestion; THAT works. Client and server can both interact on the Ubuntu box. 

I had a thought that maybe the communication wasn't getting back in the opposite direction, so I've turned Puppy's firewall off temporarily, and 'pinged' it from Ubuntu. It's definitely seeing Puppy, so....I'm running out of ideas. Invariably, 99 times out of 100, it's something small, and easily overlooked, that gums the works up.

BTW, for some reason I appear to have TWO smb.conf files.....one of which is completely empty. Is that normal?

Regards,

Mike. :frown:

---

### Post by Morbius1 on 2014-11-27
>  BTW, for some reason I appear to have TWO smb.conf files.....one of which is completely empty. Is that normal?
You're killin' me. ;)
One should be at /etc/samba/smb.conf. Where's the other one.

---

### Post by Mike_Walsh on 2014-11-27
Hah! Is that the problem?

I'll show you where it is. Right here:-

[ATTACH=CONFIG]258249[/ATTACH]

Right beside the other one, in /etc/samba (the highlighted one is the empty file). I take it, from your response, that it shouldn't be there? :)

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
I don't know what that is but it does have a "." at the end so I'm fairly certain samba isn't using it. If it's empty remove it.

As for the problem at hand I'm not one to spend a lot of time on something that's not working. We can play around with this at a lower level:

On puppy if you run this command you should get a prompt for a password or some kind of error message:
```
smbclient //192.168.1.67/documents -U paul
```
Or if you really want to go nuts:
```
smbclient -d3 //192.168.1.67/documents -U paul
```
That will produce even more output but the problem is if the fix requires something to be done on puppy I have no idea how to fix it.

I would go back to the http server idea:

_On Ubuntu:_
Open a terminal
Change to the Documents folder:
```
cd /home/paul/Documents
```
Start the http server:
```
python -m SimpleHTTPServer
```

_On Puppy:_
Open a terminal
Run this command:
```
palemoon http://192.168.1.67:8000
```
Your browser should see the contents of paul's documents folder.

If it doesn't and you have already disabled all these firewalls I have no explanation. If you couldn't ping it my guess would have been that you are in a different network but ....

---

### Post by kevdog on 2014-11-27
Reading this thread reminds me of using samba long ago.  A big pain in the but.  In terms of your firewalls,  if you type 
sudo iptables -nvL
All the chains should be listed as accept.  This would confirm your firewall is off.

---

### Post by Mike_Walsh on 2014-11-27
Hallo, hallo, hallo!

Now then; we have SUCCESS. We also have some output (in case you're still interested enough to want to take a peek!).....and a few more queries.

I don't know what happened, but the first time I tried your idea for the simple http server, for some reason I couldn't get it to work. In fact, doing a wee bit of experimentation, I now know why. It seems that Chrome (which I use as my default browser) just WON'T have it. Quite possibly to do with all this 'sandboxing' they've introduced over the last several versions.

Using PaleMoon (which, as you probably know, is a fork of an older version of Firefox) OR Firefox itself, the SimpleHTTPServer does indeed work. However, Chrome (even version 32, which is the one that Puppy uses.....because they choose all their apps for lightness, and the older versions of Chrome were nowhere near as heavyweight as they've become in recent months), won't have it. If I try to start it up with Chrome:-

```
google-chrome http://192.168.1.67:8000
```

it simply times out and won't even try to connect. Anyway, there's no point it chasing that one all round the houses because the simple http server does work.....which is all I need. I don't really want two-way communication; and it's an easy enough matter to add an exception for port 8000 to Puppy's firewall.

*******************************************************************

For interest's sake, here's the terminal output from

```
smbclient -d3 //192.168.1.67/documents -U paul
```

[ATTACH=CONFIG]258250[/ATTACH]

I hope you can read that..! Let me know what, if anything, it tells you, please.

I tried removing the smb.conf. file from /etc/samba, but both 'Move to...' AND 'Move to Rubbish Bin' were greyed out, so I couldn't delete it. Anyway, since the simple http server does appear to work, certainly well enough for my relatively straight-forward requirements, I think I'm going to put Samba on the back burner for now!

Couple of questions; can you open up more than one folder at a time with the simple http server? And how long can you leave the simple http server running for?

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
2 things:

*** Your smbclient command from puppy successfully connected to the samba server.

Smbclient when used this way in a terminal is a lot like using ftp in a terminal. When you see this:
> smb: \>
That means the connection has been made and it's ready for an input command. If you were to enter something like this:
```
ls
```
It should have listed the contents of the ubuntu documents folder.

What this tells me is that something is wrong with YASSM.

Note: to close the connection enter:
```
quit
```

*** As for SimpleHTTPServer it will remain active until you close it: Ctrl+Z

This should be used only temporarily or as needed. It's really a programmers tool used to create a temporary http server to test out some code.

You can spawn off each folder to another instance of the browser I suppose. I should note that you can't download a folder only files. If you want to download a folder you need to archive it like a zip or something and then download that. A folder to http is something to be opened not a downloadable entity.

---

### Post by Morbius1 on 2014-11-27
I may have misinterpreted this part of your question:
>  can you open up more than one folder at a time with the simple http server? 
Um ..  no ... I don't think so .... maybe if you specified a different port you could ... I really don't know ;)

If you want to access all of your folders don't change directories when you issue the command. If you just open the terminal it defaults to that users home directory. If you issue the SimpleHTTPServer command at that point then your entire home directory is available to the client machine.

EDIT: I should note that you can do this in reverse. If you open up puppy's terminal and use the same command you can connect to it using puppy's ipaddress:8000 from Ubuntu. In fact this will work with Linux or OSX in both directions.

---

### Post by Mike_Walsh on 2014-11-27
Hm.

The one thing I don't understand is why you need to turn off the firewall in order for SimpleHTTPServer to work. As I understand it (and I'm perfectly willing to be corrected on this!), the firewall is set up to deny incoming (apart from certain exceptions), but to allow ALL outgoing...am I right?

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-27
Not an expert on firewalls I'm afraid. I'm always behind a router so I don't use one on each machine in my home lan. I would think that the attempted connection - albeit a read only one - to your http server is an incoming connection.

I'm shutting down for the day. All this time with puppy has given me horrible flashbacks to when I first used Debian about a hundred years ago and it's given me nightmares. I need a break.

---

### Post by kevdog on 2014-11-27
If you run the command iptables - nvL as root it is will give you your current firewall ruleset. Perhaps you could post yours here.

---

### Post by Mike_Walsh on 2014-11-28
Hallo, kevdog.

As requested, the output of 'sudo iptables -nvL':-

```
paul@mic-w:~$ sudo iptables -nvL[sudo] password for paul: 
Chain INPUT (policy DROP 4 packets, 144 bytes)
 pkts bytes target     prot opt in     out     source               destination         
14702 8861K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
14702 8861K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   144 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   144 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   144 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   144 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 2 packets, 80 bytes)
 pkts bytes target     prot opt in     out     source               destination         
13472 1668K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
13472 1668K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  515 46682 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  515 46682 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  515 46682 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  515 46682 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   144 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 7711 1199K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 6909 7641K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
   82 20272 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   31 13714 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
   51  6558 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 7711 1199K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 5246  422K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
  515 46682 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
   35 13858 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
   47  6414 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  160  9600 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
  353 37002 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:631
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:631
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
   47  6414 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 137,138
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 139,445
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:21
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:21
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8000


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8000
paul@mic-w:~$
```

I hope it means more to you than it does me. I can't fathom that lot out AT all...! ;)

Regards,

Mike.

BTW: I've added an exception for port 8000 to both incoming AND outgoing; that seems to have done the trick. Logically, I thought that you would only need to add the exception to the outgoing side for the rest of the firewall to remain secure, but giving it a bit more thought, of course, you need to add it to the incoming side, too, so that Puppy's request will go through...

Am I right? You appear to have a better grasp of this firewall stuff than I do!

---

### Post by Morbius1 on 2014-11-28
I was wondering if you would do me a favor so I can close out the samba part of this thread.

When I asked you to run the following command:
```
smbclient -d3 //192.168.1.67/documents -U paul
```
You successfully connected to the ubuntu samba server because you got the [COLOR=#0000cd]**smb: \>**[/COLOR] prompt:
[ATTACH=CONFIG]258256[/ATTACH]

Could you do that again please and when you do could you issue an ls command to get a listing of the contents of that share just so we can confirm it.

After the smb: \> just enter:
```
ls
```
That's a small "L" and an "s"

And afterwards to close the connection enter:
```
quit
```

---

### Post by Mike_Walsh on 2014-11-28
Hallo, Morbius.

It appears you're right. It DOES connect, and asks for a password; when I enter 'ls', it does list the contents of the directory. I was going to list it here for you; however, although I can make the rather odd copy/paste function work from Puppy on the desktop (simply highlight, no right click to copy; then middle click to paste) it refuses to function at all on here, so.....I'm afraid I can't give you the output (which I had hoped I could, just as proof). There's no way to emulate a middle-click with the touchpad buttons, and neither of my wireless mice appear to paste with the middle-click.

But to answer your question, yes, Samba does appear to work.....albeit in an odd, roundabout fashion. As you say, something's not quite right with YASSM; either that, or it's just the ancient hardware I've got on here!

Sorry about that.

Regards,

Mike.

---

### Post by kevdog on 2014-11-28
Was the firewall or iptables you listed for the Ubuntu server?

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:631
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:631
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
   47  6414 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 137,138
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 139,445
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:21
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:21
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8000

By default -- all input ports are closed and output ports are closed.  You've added these exceptions for the incoming ports listed above so I'm assuming this is the iptables file for the server.  I don't think you need upd ports 800, 21, and 22 on.  In fact if you are not using ssh or ftp you dont need ports 21 and 22 at all.  

Ideally I think what you want to do, is to mount the remote directory locally with use of the cifs shares.  I'll have to look up how to do this, however this will save you a lot of time and effort since you can drop and drag across multiple directories
Here is a post that should help you do this:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I'm assuming puppy has an /etc/fstab file.  This is where those changes would be made.

---

### Post by Mike_Walsh on 2014-11-28
Hallo Morbius!

Good news; Samba IS working in Puppy!

I was half-heartedly playing around with Puppy on the laptop this morning, trying to suss out what was causing the logjam. You remember you said to me to go into the YASSM login window (this one):-

[ATTACH=CONFIG]258259[/ATTACH]

and to log the details in, and it should connect? I tried it again this morning, and it still wasn't playing ball. However:-

There's two other YASSM selections in the Network Menu besides the Share login, aren't there? 'Share Search', & 'Share Select'. Previously, when I'd looked in 'Share Search', all it showed were three entries in the drop-down list;'Public', 'Fred's Folder', and 'Hidden@BTHub5' (that's the ID of our British Telecom supplied router at home; not exactly my router ID, but it gives you the idea....it's fairly similar). 

[ATTACH=CONFIG]258260[/ATTACH]

When I looked a little while ago, it's now got, in addition to the others, 'Documents@Mic-W' (that's my hostname on the Compaq for Ubuntu), 'Pictures@Mic-W', 'Videos@Mic-W', etc, etc. So I thought,"Aha! This looks promising", and did a bit of experimenting.

Highlighting from the drop-down list and selecting 'Show' merely brings up an empty window in Rox. However, it appears that highlighting from the drop-down, then clicking on 'Select' takes you to the login window, with all the details of the share you want pre-entered, along with your saved login details. Just click-on 'Mount'; Rox-Filer opens a YASSM window, and there you are.....the shares from the other machine.

So; a very big 'Thank you' from me for bearing with me, and helping me get this up & running. It seems that although Samba DOES work fine, the way that Puppy goes about it is, perhaps, a wee bit unconventional, and certainly different from doing it in Ubuntu. But, we got there in the end; and I've added another sizeable chunk to my knowledge of Linux along the way.

By the way, I can also access the Simple HTTP Server in Chrome, too.....now that I've got both firewalls configured with the necessary exceptions for port 8000! So I've gone from no way of doing file transfer, to at least TWO different ways of accessing them. 

MUCH appreciated. I'll mark this one as 'Solved', since we've finally answered the thread title...

Regards,

Mike. :D

PS: Incidentally, you remember telling me that the Simple HTTP Server would only allow you to view remote files, but not to download them? You CAN in PaleMoon; I haven't tried it in  FireFox or Chrome yet.....but I'm willing to bet you can with them, too. And I DO apologise for giving you 'Debian nightmares'....!!

I think, though, when all's said and done, that the way of accessing Samba in Puppy is in keeping with the spirit of the distro. It's as economical and as simple as the devs can make it.....to keep the OS as lightweight as possible. 'Nuff said, really.

Mike.

---

### Post by Mike_Walsh on 2014-11-28
Hi, kevdog.

The listing IS for the Ubuntu machine (I guess in this case it IS the 'server' for SAMBA)...

Regards,

Mike.

BTW; Ports 21 & 22 are on there simply because I was looking at just about EVERY Linux/Unix method of file-transfer I could think of.....including ftp AND ssh. If I don't need them, then of course, I'll remove them.

---

### Post by Mike_Walsh on 2014-11-28
@Morbius:-

One final question, if I may?

Since I deleted all the shares information in Nautilus, am I right in thinking that if I want to add any other folders/directories to Samba, then I simply edit the smb.conf file? I just want to be crystal clear on that one!

Regards,

Mike.

---

### Post by Morbius1 on 2014-11-28
I suppose the technically correct answer is: It's quite possible to use  both methods at the same time. The thing you want to avoid is using both  methods - at the same time - on the same folder. 

Each method has it's advantages. The nautilus method is easiest to use  and handles Linux permissions on the shared folder automatically but it  is limited in what it can do. For example there is no "valid users" option using using Nautilus. You can create a share that requires credentials  but you can't limit that to only one user as you have done with your  classic shares ( the smb.conf shares ). 

If you are new to all this and already have working shares the classic  way in smb.conf I'd stick with that method - why mess with something  that's already working.

---

