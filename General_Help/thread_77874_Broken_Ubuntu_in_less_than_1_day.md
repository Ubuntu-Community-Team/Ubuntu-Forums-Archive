---
title: "Broken Ubuntu in less than 1 day"
date: 2005-10-17
forum: General Help
---

### Post by shazbot on 2005-10-17
Okay I new at Linux, have tried several versions before, Mandrake, Suse etc but always found them to complicated to be worth the while

So anyway installed 5.10 Ubuntu, went farly well, started playing around the WiFi which was working, but must have done something as when I boot I get an error message saying that GRUB cannot work correctly as /etc/hosts is missing 'ubuntuASUS' and therfore cannot connect to the Internet

And can't use system, admin as this no longer gives me access the reseau where I can modify anything

Now I can see that this a file hosts in the /etc folder but cannot add anything to it and it just contains one line of text

Can some please help, otherwise back to windows, as must admit its hard to break XP, but Linux in 1 day :(

---

### Post by dlpfmVfH on 2005-10-17
did you try it with sudo ??
(sudo will give you superuser access)

for example: sudo nano "filename.."
or if you prefer gui...sudo gedit "filename..."

---

### Post by BIGtrouble77 on 2005-10-17
[QUOTE=shazbot]Okay I new at Linux, have tried several versions before, Mandrake, Suse etc but always found them to complicated to be worth the while

So anyway installed 5.10 Ubuntu, went farly well, started playing around the WiFi which was working, but must have done something as when I boot I get an error message saying that GRUB cannot work correctly as /etc/hosts is missing 'ubuntuASUS' and therfore cannot connect to the Internet

And can't use system, admin as this no longer gives me access the reseau where I can modify anything

Now I can see that this a file hosts in the /etc folder but cannot add anything to it and it just contains one line of text

Can some please help, otherwise back to windows, as must admit its hard to break XP, but Linux in 1 day :([/QUOTE]

The truth is that you will break you linux install a few times as you learn.  That's the nature of the beast, especially if you're a power user.  Things like your grub config and xorg.conf should be backed up because they are so critical.  

The good news is after you learn a bit your system will be significantly more stable than windows and you won't have to worry about virus' or spyware.  You will go through these growing pains.

---

### Post by shazbot on 2005-10-17
sorry but sudo is new to me so I need explicit instructions

when I type in sudo in the terminal as I presume that is what I should do I get the message sudo: unable to lookup ubuntuASUS via the gethostbyname()

so what do I have to do

Thanks

---

### Post by BIGtrouble77 on 2005-10-17
just try:
```
sudo su
```

That will let you edit the file as root (the system administrator)

---

### Post by afonic on 2005-10-17
Generally, reinstall ubuntu (as from what I understand you had just installed it, so you have no data in it) and make sure you don't break it again.

Read [www.ubuntuguide.org](www.ubuntuguide.org) (ALL OF IT!) and the wiki before you start changing stuff again! :-)

---

### Post by shazbot on 2005-10-17
Re install a whole system because of a missing file, now thats is heavy

sudo su gives me the same message unable to look up ....

Common U guys is there nobody and give me a way to replace a simple text file

play with wifi and F**k a whole system up, at this rate Bill gates will stay light years ahead of Linux and I find that a great shame

---

### Post by Hikaru79 on 2005-10-17
There's no need to reinstall anything if the only problem is a borked /etc/hosts file. Paste the output of /etc/hosts here. Also, what is your computer's hostname?

---

### Post by JediPottsy on 2005-10-17
[QUOTE=shazbot]Okay I new at Linux, have tried several versions before, Mandrake, Suse etc but always found them to complicated to be worth the while

Can some please help, otherwise back to windows, as must admit its hard to break XP, but Linux in 1 day :([/QUOTE]


2 things...suse is incredibly simple - so simple tht i hate it, 2nd about the XP thing....Blaster? Sasser, welchia...many times i have done a straight install from xp cd (no service packs) and while only going on to get sp2 BSOD....thts a 2 hour break.

Third :D Welcome to Ubuntu- brilliant OS, dont worry i broke linux a few times before i got things working correctly. Neway always backup xorg.conf and grub before you make changes, ie

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

In windows most accounts are admin, so any virus that gets onto the OS, has admin privilage - and this sucks.

LInux is different, every account is basic, and in order to do anything you need to enter the root (admin) password.
Ie, sudo - which grants root privilage for one command - so that any virus that may get onto the system, it still wont get root privilage.

checkout [www.ubuntuguide.org](www.ubuntuguide.org) - remember that its for hoary not breezy, so that not many things work. But simple things that do not require installing new things will work, ie getting a windows partition to work.

---

### Post by shazbot on 2005-10-17
# The following lines are are desiarable for IPv6 capable hosts

That is all that is the host file

as I cannot write anything in it

The host name is 'unbuntuASUS'

---

### Post by Hikaru79 on 2005-10-17
Well, there's your problem. Replace your current /etc/hosts file with this:
```

127.0.0.1 localhost.localdomain localhost unbuntuASUS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
You said your hostname was unbuntuASUS . I'm not sure if that was a typo and if it should say ubuntuASUS instead (the extra 'n' after the first u). In any case, if it is, just replace it in the conf file I posted. That should fix your problem :) Good luck.

---

### Post by shazbot on 2005-10-17
Thanks but still dont how to replace a file that I cannot write to or replace

So I'm going to just wipe the system, windows may be dangerous, although have never had a virus, or been hacked (just anti virus programs and Firewalls to protect me) and I've got 15 different PC running in my office, 

but never have I managed to break XP as easaly as I broke Linux

Maybe I will re install,but for the moment its a no go

Thanks for taking time anyway

---

### Post by Hikaru79 on 2005-10-17
[QUOTE=shazbot]Thanks but still dont how to replace a file that I cannot write to or replace

So I'm going to just wipe the system, windows may be dangerous, although have never had a virus, or been hacked (just anti virus programs and Firewalls to protect me) and I've got 15 different PC running in my office, 

but never have I managed to break XP as easaly as I broke Linux

Maybe I will re install,but for the moment its a no go

Thanks for taking time anyway[/QUOTE]
Ack, no!! All you have to do in order to replace read-only files is use 'sudo'. As in ```
sudo gedit /etc/hosts
```

I'm sorry, but if you're not willing to read the documentation enough to know even THAT, then the problem is with the user, not with Ubuntu.

---

### Post by shazbot on 2005-10-17
In a way I agree, but when using Macs I never read a book, Windows I never read a book either

Does this mean that to use Linux one must spend time learning and reading, this will keep Joe the public from using linux :( 

Thanks again ;)

PS stuborn bugger as I am, shall give it a day or two and probably be back

---

### Post by bb002 on 2005-10-17
Linux gives you access to more stuff than windows or mac does. And some of it is extremely sensitive to being messed with.

In linux being able to boot to the command line means it is fixable. in windows that's not going to happen, you be lucky to even be able to back up your stuff short of moving the hdd to another box. And I don't even know if mac has a command line. I barely know how to start safari in mac (only one mac in my entire work place and that one is a laptop that a staff member brings in).

---

### Post by BIGtrouble77 on 2005-10-17
[QUOTE=shazbot]In a way I agree, but when using Macs I never read a book, Windows I never read a book either

Does this mean that to use Linux one must spend time learning and reading, this will keep Joe the public from using linux :( 

Thanks again ;)

PS stuborn bugger as I am, shall give it a day or two and probably be back[/QUOTE]

If you don't like to read any documentation then stick with windows.  Windows is a phenominal os if you need a purely visual work environment.  I suggest learning how to make a ghost disc for reimaging your system after you get hoards of virus' and spyware.

---

### Post by wahur on 2005-10-18
[QUOTE=Hikaru79]Ack, no!! All you have to do in order to replace read-only files is use 'sudo'. As in ```
sudo gedit /etc/hosts
```
[/QUOTE]
Having the same problem as original poster I suggest you read WHAT his problem is. Namely sudo is broken. When he, or me, for that matter, attempt to run sudo  this is what we get:

unable to lookup here_goes_my_hostname via gethostbyname()

And thats it. Only I did not have even to bug with wifi, it was the situation immediately after the install of Kubuntu 5.10. Right now I have no idea how to get admin rights. 
Of course, except with firing up my trusty Knoppix and editing config files from there.

---

### Post by wahur on 2005-10-18
Ahh and BTW, this was my first line of /etc/hosts

```
127.0.0.1 localhost
```

When I edited it to

```
127.0.0.1 localhost laane
```

where laane is my hostname, nothing changed. When I get back home I will try if making it to
```
127.0.0.1 localhost.localdomain localhost laane
```

would help

---

