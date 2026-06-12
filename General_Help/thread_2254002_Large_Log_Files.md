---
title: "Large Log Files"
date: 2014-11-24
forum: General Help
---

### Post by Forbees on 2014-11-24
started the other month in in a different tread i posted where  ~/.xsession-errors.old would grow to a size of 40gig. i'm running on a 68gig SSD so you can see this being a problem. this was also running ubuntu 12.04

decided i was overdue for a clean update anyway so i did  a fresh install of 14.04

now the unity log file in upstart is growing to be 40+gigs. i've had 14.04 installed on this machine for only two weeks now... and i haven't really installed anything other than mdadm.

i imagine the log files are getting huge for a reason, but so far the only solution i can find is just deleting them when they get so big.

this computer is serving as an HTPC that i stream movies from one city to the next - so all access to it unless i drive for an hour is remote - and it only gets turned off when i have to restart for updates

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ended up being a filled with a botnet op IP's trying to access through vino's open port. tunneling through SSH solved it

---

### Post by Lars Noodén on 2014-11-24
What messages are filling the logs?  It might be good to identify the source of the problem and fix that.

---

### Post by Forbees on 2014-11-24
it looked like it's just full of IP addresses and URL's.....

gnome-session-Unity.log and gnome-session-Unity.1.gz

are the main culprits

---

### Post by Lars Noodén on 2014-11-24
Would you be able to post some examples of the lines that repeat a lot?  Someone here might spot the problem.

---

### Post by Forbees on 2014-11-24
Will do when I get home from work. Currently the files are about 300 and 600 megs.... but I'm on the road with just my phone at the moment. Didn't expect a reply so quick

---

### Post by Forbees on 2014-11-24
okay home now, gnome-session-Unity.log is now at 12gigs compared to the 600megs 5 hours ago... definitely growing fast 

```
24/11/2014 07:50:43 AM      static-40-152-132-188.sadecehosting.net
24/11/2014 07:50:43 AM      66-192-171-130.static.twtelecom.net
24/11/2014 07:50:43 AM      s15521007.onlinehome-server.info
24/11/2014 07:50:43 AM      mail.phfloan.com
24/11/2014 07:50:43 AM      222.234.2.145
24/11/2014 07:50:43 AM      s15510800.onlinehome-server.info
24/11/2014 07:50:43 AM      static-50-121-137-174.drr04.chtn.wv.frontiernet.net
24/11/2014 07:50:43 AM      123.111.231.19
24/11/2014 07:50:43 AM      mail.phcraig.com
24/11/2014 07:50:43 AM      95.211.109.133
24/11/2014 07:50:43 AM      75-132-59-95.dhcp.stls.mo.charter.com
24/11/2014 07:50:43 AM      66-192-171-130.static.twtelecom.net
24/11/2014 07:50:43 AM      61.78.62.167
24/11/2014 07:50:43 AM      67.214.107.178
24/11/2014 07:50:43 AM      static-50-121-137-174.drr04.chtn.wv.frontiernet.net
```

there's some of it... pretty much all just looks like this

```
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
24/11/2014 07:51:24 AM      106.240.241.58
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
24/11/2014 07:51:24 AM      95.211.109.133
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
24/11/2014 07:51:24 AM      hosted-for-minecraft.net
``` ....... i don't play minecraft? so no idea what the heck this is about

```
24/11/2014 07:52:05 AM      mail.endurancedirect.com
24/11/2014 07:52:05 AM      69.58.96.42
24/11/2014 07:52:05 AM      mail.endurancedirect.com
24/11/2014 07:52:05 AM      mail.endurancedirect.com
``` never heard of this either

```
4/11/2014 07:52:05 AM      mail.endurancedirect.com
24/11/2014 07:52:05 AM      ticbrasil.com.br
24/11/2014 07:52:05 AM       Q\D1h\FF
24/11/2014 07:52:05 AM      mail.endurancedirect.com
24/11/2014 07:52:05 AM      ticbrasil.com.br
24/11/2014 07:52:05 AM       Q\D1h\FF
24/11/2014 07:52:05 AM      mail.endurancedirect.com
24/11/2014 07:52:05 AM      ticbrasil.com.br
24/11/2014 07:52:05 AM       Q\D1h\FF
``` Q/D1h/FF?

and since it's 12gigs of data had to use tail to find anything more recent
```
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 AtkObject* unity_a11y_get_accessible(nux::Object*): assertion 'object != NULL' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 atk_object_ref_state_set: assertion 'ATK_IS_OBJECT (accessible)' failed
ERROR 2014-11-24 13:49:22 unity <unknown>:0 atk_state_set_contains_state: assertion 'ATK_IS_STATE_SET (set)' failed
ERROR 2014-11-24 13:49:22 unityy <unknown>:0 g_object_unref: assertion 'G_IS_OBJECT (object)' failed

``` so here's some actual errors finally... but there's still a **** tun of stuff being logged in there i don't get

---

### Post by dragonfly41 on 2014-11-24
I'm surprised that a basic google search has not provided clues ..

search .. ~/.xsession-errors.old

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=~%2F.xsession-errors.old&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=vpdzVMHPE-GB7Qac44CYCg](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=~%2F.xsession-errors.old&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=vpdzVMHPE-GB7Qac44CYCg)

One common clue is that you are using SSD ... as is this poster.

[http://vsido.org/index.php?topic=279.0](http://vsido.org/index.php?topic=279.0)

---

### Post by Forbees on 2014-11-24
most the google searches say to delete it(which i do about every 3-4 days), or they're unsolved, second one is a tactic i tried when i was on 12.04, and the after the next reboot from updates i had to reconfigure x-server (it ended up being faster and easier to just install 14.04 which is why i did)

but thanks for looking... i can't say i've looked on every single post out there but i've yet to find a real answer

---

### Post by Forbees on 2014-11-24
update. now at 16gigs
```
24/11/2014 05:08:23 PM      ip-185-35-177-209.trakiacable.bg
24/11/2014 05:08:23 PM      ip-185-35-177-209.trakiacable.bg
24/11/2014 05:08:23 PM      50-242-203-233-static.hfc.comcastbusiness.net
24/11/2014 05:08:23 PM      190.143.107.195
24/11/2014 05:08:23 PM      212.117.156.225.static.012.net.il
24/11/2014 05:08:23 PM      70.33.238.149
24/11/2014 05:08:23 PM Client Protocol Version 3.3

** (vino-server:1845): WARNING **: Deferring authentication of 'mail.phfloan.com' for 5 seconds

```

couldn't have anything to do with using vino to remote access the computer could it?

---

### Post by dragonfly41 on 2014-11-24
[http://filthypants.blogspot.co.uk/2013/02/xsession-errors-log-filling-hard-drive.html](http://filthypants.blogspot.co.uk/2013/02/xsession-errors-log-filling-hard-drive.html)

vino zeitgeist ??

p.s. I'm shutting down for tonight.

---

### Post by Forbees on 2014-11-24
well i can't get rid of vino....... but i also didn't see any errors involving vino... just the one warning message.

the majority of the file is just the randon IP addresses and URL's... no idea what those are or why they need to be logged

---

### Post by Forbees on 2014-11-24
another update

log is up to 26gigs now, seemingly no change in whats logged.... just more IP's and URL's...... is there a way to change what goes into this log file? can i make it so it only logs errors?

---

### Post by SeijiSensei on 2014-11-25
Which log file is this?  It doesn't look like any I've seen.  It's certainly not anything produced by rsyslog.

---

### Post by dragonfly41 on 2014-11-25
There are many similar experiences reported in this thread ...

[http://ubuntuforums.org/showthread.php?t=1517991](http://ubuntuforums.org/showthread.php?t=1517991)

But see post #36 discussing vino-server WARNING

Warning message seems to be a similar to yours.


**[later edit]**

I see this line (below) in your log referring to comcastbusiness.net (which is also in the thread above). Coincidence?

24/11/2014 05:08:23 PM      50-242-203-233-static.hfc.comcastbusiness.net


The poster in #36 above wrote ...

> I notice a brute force attack on the desktop (I had
a good password), and the log fills with the invalid attempts to connect to VNC.

---

### Post by Forbees on 2014-11-25
hmmm well my password for vino is only 6 characters.... but my password after vino connects is 23 characters..... i suppose a brute force could be related. i know some of those say comcast business which is the ISP i'm using to connect


but still from the look of the log we're talking like 50 attempts a second or something 

gnome-session-Unity.log is the log that's going crazy on me. the xseesion-errors log was a problem on 12.04, but hasn't gone crazy on me since i upgraded to 14.04 

the only solutions i've found so far are either delete it periodically, or remove the ability for the machine to write to it. i'm hesitant to do the second option because i tried it for the xsession-errors problem on 12.04 and on my next restart my xserver was bricked - not completely related, but since i stopped it from logging i couldn't find the problem. which is why it's running 14.04 now instead of 12.04

---

### Post by Forbees on 2014-11-25
took a minute to run through the posts of the other tread... wish it wasn't closed. it does look like it could be a brute force on Vino. i think i'll beef up the password to be safe, but that still won't stop attempts being logged

maybe there's a way to stop vino from logging? or change what gets logged? i feel like vino should have it's own log file, not sharing the unity one

---

### Post by Lars Noodén on 2014-11-25
> **Forbees said:**
> maybe there's a way to stop vino from logging? or change what gets logged? i feel like vino should have it's own log file, not sharing the unity one

VNC (vino et al) mustn't ever be exposed to the open net.  The encryption is not good enough and that is one reason you may be seeing brute force.  The recommended way of using VNC is to tunnel it through SSH.  The way to do that is have the VNC server only listen to localhost and have UFW (iptables) blocking the usual VNC ports.  Then connect from the client with ssh and tunnel to the VNC port.  Then on the client connect the VNC client to the localhost's tunnelled VNC port.  

That will also quiet the logs in addition to making it rather hard for anyone unauthorized to get in.

---

### Post by Forbees on 2014-11-25
that sounds like a pretty good idea to me lol. got a link for an idiot proof tutorial? when i set this up i originally wanted to do vnc through SSH, i remember using it like that on 8.10, but forgot how i did it... i ended up getting lazy when i realized that vino seemed to do the trick. but it is sounding like going through SSH would solve the problem

update on the unity log - currently 40gigs, my SSD is now full. tail output shows just the same IP address, all logged about 30 minutes ago before there was no more room to log. going to delete the log again to keep the system running till i get the SSH VNC figured out.

---

### Post by Lars Noodén on 2014-11-25
In the mean time, if all the probes are coming from the same ip's you could block them manually at the local firewall with UFW.

---

### Post by dragonfly41 on 2014-11-25
I don't know if post #34 might help ... or if it is a red herring ...

> 
I succeeded in getting the file back down to normal size (or non existent at all) by reinstalling compiz-core. 
Just run the following command in the terminal to reinstall the compiz-core files:
 	 	[FONT=courier new]sudo apt-get install --reinstall compiz-core

[/FONT]

---

### Post by Lars Noodén on 2014-11-25
vinagre, the client, supports SSH tunnelling as one of its options, so it can be done more easily.  I think screenshots might not be needed:

1)

On the target, make sure OpenSSH server is installed and running.
Then, start UFW and allow SSH.  This needs to be done once in the terminal unless you are running GUFW.

```

sudo ufw allow ssh
sudo ufw enable

```

GUFW would be recommended.

Then start and configure the VNC server, Vino.  Choose:

[list]
[*] Allow other to view ...
[*] Allow others to control ...
[*] Require the user to enter this password ...  (Do not re-use the password from anything else.)
[/list] 

If there is remote access only to the target machine then also uncheck the choice "You must confirm each access ..."

Be sure to disable "Automatically configure UPnP ..."

2)

Then on the client, run Vinagre to connect the remote target host.

Choose "connect"
Protocol VNC
host: localhost
use host _____ as SSH tunnel (For the tunnel, enter the user- and hostname for the remote target which is running OpenSSH server.)

Choose "connect"
Enter the SSH password for the remote account
Enter the VNC (insecure) password for Vino

---

### Post by Forbees on 2014-11-25
okay, got openSSH installed with [this ]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") tutorial, opened the port for ssh on server side

client machine is running windows so i used [this]("http://helpdeskgeek.com/how-to/tunnel-vnc-over-ssh/") to get the tunnel set up


was able to tunnel in and from the server side and disabled port forwarding for vino... so in theory i should be all set now yes? will update later today on log file size currently 1.2gigs


but it sounds like this might fix everything, just have to wait and see. 


now i understand people seeing port 5900 open and trying to get in, but whats stopping the same thing from happening on port 22?

---

### Post by Lars Noodén on 2014-11-25
> **Forbees said:**
> now i understand people seeing port 5900 open and trying to get in, but whats stopping the same thing from happening on port 22?

Fewer people will try because it is much harder (usually) to get an SSH password, since system passwords are usually longer and mixed letters, numbers and symbols and the encryption is solid.  If you want to not worry about password guessers at all, then set up key-based authentication for SSH and turn off password authentication.  The guessers are mainly large botnets of Windows machines.  Changing ports for SSH won't do much since all ports get scanned and then the attacks adjust to the port available, but if you have keys-only authentication they can try all they want to no avail.

---

### Post by Forbees on 2014-11-25
i was looking at the key-based, but it was a little confusing on setup... the password i'm using is 18 characters long.... so i think i should be safe on that

---

### Post by Forbees on 2014-11-25
everything seems to be good now :) .... well on the file size.... magically after an update and reboot i have some strange new problems. so off to make a new thread and mark this as solved!!

thanks a bunch guys

---

