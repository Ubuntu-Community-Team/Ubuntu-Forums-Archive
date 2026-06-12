---
title: "can't see windows network"
date: 2005-10-22
forum: General Help
---

### Post by Alfisti on 2005-10-22
After upgrading to Breezy I can't see my windows network computers. Before the upgrade I could see computers and shares. The only way to see shares is to write smb://computer_name/...  Any solutions?

---

### Post by Dolphin on 2005-10-22
Have you tried rebooting the other machines?

---

### Post by Alfisti on 2005-10-22
its a large network. computers reboot all the time...

---

### Post by Excession on 2005-10-22
I am experiencing a similar problem, but my install was fresh, not an upgrade. I'm running Breezy and I can't see the windows machines on my network. Sure I can navigate to them via IP/hostname or mount them manually, but the Network Servers part of 'Places' shows up nothing where once, just after the fresh install, it did.

My thread is here: [http://ubuntuforums.org/showthread.php?t=80349&highlight=browse+network](http://ubuntuforums.org/showthread.php?t=80349&highlight=browse+network)

No replies though. Maybe we'll get one here? ;)

---

### Post by Dr. Nick on 2005-10-23
My only guess would be to make sure you set the correct workgroup settings. But if the computer name makes the connection and not the IP it should be right. I will try it out tomorrow if I remember when my windows computer is on.

---

### Post by chiok on 2005-10-23
I have the same problem.  I upgraded from Hoary where it was working fine and also did a fresh install.  Both Breezy installs can't find my Windows computer.

(I'm on Bell Sympatico with pppoe had to do a few things to get that working. I am using a Belkin router.)

---

### Post by dtfinch on 2005-10-23
It works for me, but with a new problem. Just to display the list of computers on the network, it asked me for passwords to log into every single computer on the network, including itself (I had samba running).

---

### Post by rah1420 on 2005-10-23
Everybody who says "Check your firewall" and "reboot your Windows boxen", I believe we have a bug here.  I too am plagued with the "logging into MSHOME workgroup" problem (when my workgroup at home is simply WORKGROUP) and the missing Windows Networking dialog choices in the General tab.

Yes, there's a workaround.  Connect to the server you want to get to by doing a Places/Connect to Server/ and changing the service type to Windows Share, then filling in the computer name; you'll get a new window with all your shares mounted.  I SERIOUSLY hope that this is not an "enhancement" in Breezy because I started out with Ubuntu by installing hoary and immediately fell in love with it for **this one feature** of having a Network Places that "knew" about my network out of the box.

Silly, I know; but I was trying to find a distro that "just worked"  with as close to no innate Linux knowledge as possible.   Ubuntu is "it" for me and breezy has broken something that many newbie converts to Ubuntu would find a familiar landmark; a way to click through to their other machines.

End of rant.  :)

---

### Post by psypher on 2005-10-23
exact same problem guys. first it was popping up with the login box like someone else here and no combimation of correct passwords worked. now I too cannot see anybody on the network and when I try connect directly to the share the passwords don't work. This is a catastrophe. I agree. hoary was BRILLIANT, I NEVER had windows network problems, it was an abosolute pleasure to use, now I am stuck again with the functionality of warty, NOTHING, and the awesomeness of Breezy. NOT COOL!!!
any ideas anyone? this is quite serious I think, really tarnishes breezy and ubuntu reputation

---

### Post by fut21 on 2005-10-23
Have anybody reported this as a "bug" ?

---

### Post by rah1420 on 2005-10-23
I went over to bugzilla.ubuntu.com and checked the buglist.  Still trying to find whether it's been reported.

The closest thing I can find is 18065 and 15815 which both speak to the password dialog box only.   No mention of the fact that the underlying functionality that was in hoary is now apparently borken.  I am going to keep looking but if I can't find anything, I'm going to open a ticket in bugzilla for them to look at.  There are enough people here that will confirm it that they should be able to see it in short order.

---

### Post by rah1420 on 2005-10-23
Okay, one and all, here is what I discovered:

I looked at bugzilla, as I said, and found the following bugs that describe some, but not all of the symptoms that we're seeing.

18065, Nautilus ask password to list computer in Network server
15815, Nautilus requests password for unprotected SMB shares
8451, Shared folders requires a login
8859, Changing smb workgroup always hard, sometimes impossible  	
1778, Nautilus network browser not finding network
7245, Authentication dialog not shown when entering samba folder

Taken together, it looks like something is definitely wrong (and reported.)
Two of them, 8451 and 8859, were sent to gnome.org as tickets 319390 and 300196 respectively.  1778 also upstreamed to gnome 155739 but reading the text it doesn't seem like it's the same issue.

So yes, it seems like it's reported.  At this point I don't know if it's a gnome issue or a Ubuntu issue.  But someone knows about it.

(a bit later) There is a thread at [http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure) that tells you what to do.  I went in and edited my smb.conf file to change MSHOME to WORKGROUP and saved it and now the shares appear with no password prompting.

It isn't the nice way that it worked in hoary, but it does get the job done until they fix the bug.

---

### Post by traherom on 2005-10-23
[QUOTE=psypher]exact same problem guys. first it was popping up with the login box like someone else here and no combimation of correct passwords worked. now I too cannot see anybody on the network and when I try connect directly to the share the passwords don't work. This is a catastrophe. I agree. hoary was BRILLIANT, I NEVER had windows network problems, it was an abosolute pleasure to use, now I am stuck again with the functionality of warty, NOTHING, and the awesomeness of Breezy. NOT COOL!!!
any ideas anyone? this is quite serious I think, really tarnishes breezy and ubuntu reputation[/QUOTE]Yeah, I get the login box too, but hitting cancel works for me...

---

### Post by sourc3 on 2005-10-24
have you installed the samba package? cause i resolved the same problem by installing it and modifing some lines in the smb.conf file. Just make sure the workgroup is correct and change the line that says security=user with security=share. then reboot all the machines in the network. hope this helps!

---

### Post by Andilek on 2005-10-24
Well, this happens only on native windows. I am moving cross several networks and on Samba server it works, but on windows 2000 domain it does not. And at home I wanted to access share on my wife's PC on windows and I got refused too.
I have no time to test, but it might be caused by encryption method of samba client. May be it is not supporting it on Breezy.
I know when I played with it a little, I had samba server supporting opnly noncrypted passwords and as windows workstations send only crypted one, it refused to authorize untill I changed registers to disable encrypting passwords.
IMHO in Breazy the default settings are about to send unencrypted passwords and that is what windows servers do not accept.

---

### Post by anaoum on 2005-10-24
Hello,

i sometimes get this same problem. try apt-get installing smbfs. This might work.

---

### Post by sourc3 on 2005-10-24
Previously I omitted that I've installed the smbfs too. Sorry! Anyway I've tested this in my home network with linux and win xp pro machines and it works. No extra work done. Just changed the workgroup and the security=share option.

---

### Post by Tsume on 2005-10-24
Any fix for when the shares don't appear at all?

It used to work, then just stopped working... even after reboot.  I go into "Windows Network" and nothing is listed, where my workgroup "WORKGROUP" should be...

I tried installing the smbfs and samba and configuring it like yall said, but it still doesn't work.

---

### Post by Punterfpc on 2005-10-27
[QUOTE=Tsume]Any fix for when the shares don't appear at all?

It used to work, then just stopped working... even after reboot.  I go into "Windows Network" and nothing is listed, where my workgroup "WORKGROUP" should be...

I tried installing the smbfs and samba and configuring it like yall said, but it still doesn't work.[/QUOTE]

I have exactly the same problem. Dude, this blows...

---

### Post by Tsume on 2005-10-28
Different laptop, different wireless card, same problem still...

---

### Post by squibbon on 2005-11-01
For me it work when i disabled and again reactivated my network connection. the only problem is that i got Windows Network in the list of computers and that it always prompt me with a password. Yes, just cancel it and it will work fine.

---

### Post by sphillips53 on 2005-11-01
I have a new install of Breezy conected to a Windows XP computer by a router.  For me to be able to network successfully I had to set the workgroup in Samba to my Windows workgroup and set a Samba password using  the smbpasswd command for my Ubuntu user and log in with that password for each computer on the network.  This appears to be needed because of the security setting in the smb.conf file.  After changing security=user to security=share as suggested by sourc3 I no longer have to use the password to log in, which sacrifices a little security for convenience.

---

