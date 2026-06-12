---
title: "samba folder sharing in breezy"
date: 2005-10-22
forum: General Help
---

### Post by dictator88 on 2005-10-22
Once again I have found myself with a problem. Samba has worked for me in many linux versions but for some reason I have run into problems with ubuntu. I am currently running breezy. THe basic problem is that when I share a folder in ubuntu using smb, (weither it be from the gui or typing it in the smb.conf file), when I try to access it from a windows machine I get a user and pass prompt. Even if I put the ubuntu main user and pass in it just keep poping back up as if it isn't accepting it.  Now I don't know if this has anything to do with it but here is another problem I have noticed. When in ubuntu, and I goto (places > network servers) I get the "authentication required" "you must log in to access (ubuntu's IP)". When I again use the main user and pass it just keeps poping back up. Any clue what is going on here? Below is the lines from the smb.conf that shows what I am tring to share. 
#
[curthome]
path = /home/curthome/global
available = yes
browseable = yes
public = yes
writable = yes 
  Now, doesn't get any more clear then that!? Any idea's?

---

### Post by rah1420 on 2005-10-22
If it makes you feel any better, I'm getting that too, with a twist:

I reconfigured my ubuntu machine to a static IP from DHCP, and the prompt that I'm getting is still that I must log into the DHCP address of what the machine **used** to be.

Not only that, but something is going on with the network configuration.  I have no place to specify the parameters for Windows Networking so this machine is prompting me to log into domain MSHOME and I have a simple "WORKGROUP" specified.   I know I could go in and edit files, but I'm not sure what else is borken.

Very strange.

---

### Post by orzechowskid on 2005-10-22
I had to add myself as a samba user before I could access shares.  Try this:

$ sudo smbpasswd -a <your user name>

you'll get asked for your linux account password, then have the ability to set your Samba password.  Wait a couple of minutes, then try browsing your share again.


(edit:  spelled the name of the command wrong the first time.  it's 'smbpasswd', with two s)

---

### Post by dictator88 on 2005-10-22
right? As a matter of fact, I changed all my windows machine to MSHOME, just in case, there was a bug somewhere. Didn't help.

---

### Post by rah1420 on 2005-10-22
I still want to know why it "worked" like it did in hoary, and now it doesn't.   (grumble)

I'll try setting my password.  However, my guess is that it still won't let me browse my windows network and I'll be damned if I run around changing everyone to MSHOME just because something happened in breezy.  :roll:

---

### Post by dictator88 on 2005-10-22
Your a genius!!!!! That worked. If I may ask, why did that work. Is samba not grabbing the current password? Better yet, will this need done after every boot?

Thanks again.

---

### Post by der.brain on 2005-10-22
Hi from germany,

I am not sure but it looks there is a really big bug in the schare option of Breezy.
If you read the NFS problems it is easy to guess that the SMB problem is to find in the same corner. 

Workaround:

If you go over CONNECT TO SERVER (sorry i have the german version) choose WINDOWS SHARE in SERVER, type the ip adress of the computer you want access  leave everthing else empty you will connect and a smb icon on you desktop for this computer will apear (store the passwd) after this SMB works fine.

I guess it is why you need a autentification at the Masterbrowser ( for win2K and XP) to browse the windows net and this is messed up. So if you are connected with one computer you are also connected to the hole win network and perhaps you are allowed to browse it.

This is what i find out last night. anyone else who wwork on the problem especially ... whart is with the f... NFS problem if you go over the gui ...

did anybody know anything about this ?

---

### Post by rah1420 on 2005-10-22
interestingly enough, even though I added a password via smbpasswd, it did not work for me.   Perhaps because I do not have the samba server loaded.  I only have the samba client, as I have no samba shares on this machine - I only wish to get one from another machine on the network.

---

### Post by rah1420 on 2005-10-22
der.brain, thanks, that helped a lot.   

Using the connect to server option, selecting a windows share from the dropdown gave me what I want.  I didn't even have to type the IP address; I just typed the name of the machine ("Storagebox.")  It prompted me once for the useless password and I cancelled; then my shares on Storagebox were visible.   That did the trick for me, until they fix the problem.

---

### Post by manicka on 2005-10-22
This how-to has worked for me in breezy and hoary

[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

---

### Post by rah1420 on 2005-10-23
There's' a thread at  [http://www.ubuntuforums.org/showthread.php?t=80628](http://www.ubuntuforums.org/showthread.php?t=80628) that is discussing this issue.  I found a bunch of bugzilla entries on this issue, so it sounds like a bug.

(a little later...) 

However, I did take your advice and simply edited my workgroup entry in smb.conf and I can get to all my shares now. 

It's just a shame that it doesn't work like it did in Hoary, because that was a lot easier and more intuitive.

---

### Post by der.brain on 2005-10-26
O.K. the howto dicribes "hard mounting" breeze should work with "virtual mounting" means mountig over the gui.


I thing the "my floppy is not mountable" is the same thing.

and if you try the f... disks manager it also does not mount my ntfs partition.

To me it looks like a major thing all the same kind?

My english is to bad to bring this in the bugzilla but may be some of you can bring this i clear words? 


Best Regards

Michael

---

### Post by Punterfpc on 2005-10-27
Ok, I have a really wierd problem... When I first installed Breezy, it recognized my XP machine, I could not access it for life of me, but it did at lease SEE it there. This wasn't a big problem because I set up Samba on my laptop (the one running Breezy) and, after doing the whole "sudo smbpasswd -a <username>", I was able to access ubuntu from XP by going to My Network Places > Workgroup Computers > MSHOME. I copied multiple gigabyes of data from XP to Ubuntu So I know that whole deal works (or should I say WORKED). Now, when I go to Places > Network Servers > Windows Network, it no longer detects the XP computer. Not at all. But, that's not all, I also can no longer access the Samba shares from my XP platform. 

I have read all the forums and I think my problem may be somewhat unique in nature. I have Ubuntu set up to use eth0 for network access. I have it and the XP pc hooked up to a Linksys router. This makes my LAN. Two computers. Ok, now, that seems simple enough. But, I also, sometimes have my laptop on wireless; the router is not a wireless router. I have an AP coming out of my XP pc that serves up an Internet connection via ICS.

I connected to the shares on Ubuntu while connected to the wirelesss setup (as opposed to the router/wired way) just to see if it worked. It did, but tremendously slow (wireless B access point...). I decided I didn't like that so I went back to the wired setup and since then nothing has worked. Sticking with the router setup, I tried using static IPs instead of DHCP. THat didn't work. I uninstalled Firestarter entirely. I fiddeled around with the smb.conf file, trying different things I have seen in the forums. Nothing seems to work. I, of course also tried restarting both PCs (even though that may or my not have been neccesary on the Ubuntu pc). Also, I tried using Synaptic to reintsall all of Samba and it's most direct dependencies. I also tried doing the Connect to Server thing where you basically put the IP addy in to connect. 

Absolutely nothing has worked. I am still stuck not able to view either pc from either other pc. :(  My best guess is that the Samba Server simply is not running on the Ubuntu PC. That's the only conclusion I have logically come to. Is there any way to manually start the service? :confused: Any help will be graciously appreciated!

---

### Post by motionblur on 2005-11-03
[QUOTE=orzechowskid]I had to add myself as a samba user before I could access shares.  Try this:

$ sudo smbpasswd -a <your user name>

you'll get asked for your linux account password, then have the ability to set your Samba password.  Wait a couple of minutes, then try browsing your share again.


(edit:  spelled the name of the command wrong the first time.  it's 'smbpasswd', with two s)[/QUOTE]

That worked like a charm.  Thank you!

---

