---
title: "Access shared Ubuntu folder from Windows XP"
date: 2007-01-17
forum: General Help
---

### Post by Snoochie on 2007-01-17
Hello,
Well, I seem to be on the run, so here's a brief question. I think the answer should be simple.
I want to be able to access shared folders on Ubuntu from XP. And vice versa, it works.
I installed Samba.
I can connect to Windows shares from Ubuntu > alt + f2 smb://xxx.xxx.xxx.xxx/Shared_
I can even connect to Windows shares in virtual machines.
I cannot however connect from XP to Ubuntu.
I made a folder and shared it using SMB, name "Test."
I then try to connect from Windows machine "\\ubuntu-desktop\Test" or "\\ubuntu-desktop" where ubuntu-desktop is the computer's name. I reach the point where I need to provide username and password. So what now?
Snoochie

---

### Post by ThatOtherGuy435 on 2007-01-17
if you open /etc/samba/smb.conf, you will notice a section with "; security = user"

If you change that to "secutiry = share", and then go down to the bottom of the file, where the shares are listed, and add the lines:

force user = nobody
force group = nobody

You should be able to connect.This is assuming the Ubuntu side of the share is on the ext3 filesystem - If it is NTFS you may run into the same problem I did, and have to force user/group to your own username.

Hope this helps!

-ThatOtherGuy

---

### Post by Snoochie on 2007-01-17
Hello,

Solved the problem.
I did the following:

sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba.

Works magically.
Cheers,
Snoochie

---

### Post by puelly on 2007-02-04
Can anyone please explain to me why the samba server only accepts my username and pass if I address it using its IP address instead of its host name?

Any help would be appreciated.

---

### Post by shazoor mirza on 2007-02-15
I am using ubuntu from some days. i have a problem, no, a big problem, that when I had Windows XP i used to coonect my laptop with my friends computer. but after i have installed ubuntu 6.06 LTS,I am not able to do this.

I am a newbie and want help.

i have also installed samba and tried to connect but in network server i am not able to browse the shared folders of my friend.

i dont know why this is going on

but i am really in trouble. it would be UBUNTU if anyone solve my problen and give me details what i should do to share my folder with windows

---

### Post by twygly on 2007-02-21
I had this working fine and then bounced the box and now I'm getting a request for username and password when trying to map a windows drive to the ubuntu server.

I tried the above suggestions and still get asked for a password, only difference is it assumes the user is Guest.

When it was working before it just worked - no requesting username and password!!!

Any ideas? What could possibly have changed?

---

### Post by bouncing jack on 2007-02-22
hi, i've had the same problem. 
i've tried ThatOtherGuy's solution , but was unable to save smb.conf because i don't have enough permissions... 
i've installed Ubuntu a day ago and i'm as new as they come,
what do i do now?
thanks.

---

### Post by baeckel on 2007-04-10
In order to save your smb.conf file you have to be in _S_uper_U_ser mode (kernel mode).

In Ubuntu, you can get into kernel mode by preceding your command line instruction with "sudo" example:```
sudo gedit /etc/samba/smb.conf
```

you will then be prompted for your administrator password which you created while installing your system.  Now when gedit opens your .conf file you will have the option to save it.



and remember folks...
- in a nation of swine all pigs are upward mobile -

---

### Post by ishwar on 2007-05-03
hello folks..
i have been using ubuntu for almost 4mnth now! 
my system is a 40 gig hd, with winxp and ubuntu dual boot.. partion is ntfs and ext3.. with a swap! well my problem is i could not access ubuntu from windows.. my system symply not letting me to do it! i dont know why. i have modyfied the smb.conf file like mentioned in the forum above and i also set my password,, and importantly win xp only shows me c: drive wich is ntfs. when i tried looking thru the systme settings in ctrl pannel of windows the other partitiones are mentioned as unknown in type.. i hope i have provided enough info.. pls any one help me with this. i could access and use windows (music pics )etc.. from ubuntu without any prob! 

and i m sure there is samba in my ubuntu!!

i m a newbie to computer! 

thanx in advance

ishwar

---

### Post by Conrad76877 on 2007-05-20
> **puelly said:**
> Can anyone please explain to me why the samba server only accepts my username and pass if I address it using its IP address instead of its host name?

Any help would be appreciated.

I believe that it might be an issue with DNS (DNS stands for Domain Name System) DNS is responsible for the mapping of IP addresses to FQDN (Fully Qualified Domain Name eg. [www.pdscsansaba.com](www.pdscsansaba.com) or machine name).  The reason I am stating the above is because:

a. If you have no router on your local area network and instead are using only a hub that has no intellegence - your machines might be having to look to an outside DNS server which cannot resolve and has no record of your computers existence besides its MAC. Hmmm - I really don't think an all out paragraph of DNS is necessary or wanted here so ..

b. You might be typing the address incorrectly... //my-machine/share

c.  It might be due to an incorrect mapping in lmhosts file as well (not sure about this but I have used hosts which resides in C:\WInnt\system32\drivers\etc\hosts to map machines without DNS server on a small network with a hub) Winnt will be Windows if newer than windows 2000

To fix this : 
A. Buy a router
B. place a record in the hosts file for the ubuntu machine ip      +    name
C. Shoot the windows machine - throw it in the garbage and send Billy Gates hate mail for trying to rule the world.
D. Switch to Ubuntu 7.04 Feisty Fawn on every computer at home like I did from Window Vista - And I am loving it! Thanks Ubuntu team you are doing an amazing job and have taken Linux for home users further than any previous linux!

Conrad;)

---

### Post by spartan778 on 2007-07-03
I ve installed samba. I try to access my windows files but I get a error message that says, cannot display the contents of the drive/folder.

---

### Post by SentientFluid on 2007-09-08
> **ThatOtherGuy435 said:**
> if you open /etc/samba/smb.conf, you will notice a section with "; security = user"

If you change that to "secutiry = share", and then go down to the bottom of the file, where the shares are listed, and add the lines:

force user = nobody
force group = nobody

You should be able to connect.This is assuming the Ubuntu side of the share is on the ext3 filesystem - If it is NTFS you may run into the same problem I did, and have to force user/group to your own username.

Hope this helps!

-ThatOtherGuy

Thanks, that's helped out immensely.  Prior to changing that I couldn't even connect to my Ubuntu box from a Windows computer.  Now I can connect and have read only access to to Ubuntu.

I have one folder that I want to be able to write to from my Windows computer.  How can I get that working?  Here's my smb.conf minus all the comments:

```

[global]
   workgroup = MSHOME

   server string = %h (Ubuntu)

   dns proxy = no

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   security = share

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   invalid users = root

   socket options = TCP_NODELAY

   writable = yes

wins support = no
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[shared]
  comment = Read Only
  path = /home/shared
  available = yes
  browsable = yes
  public = yes
  writable = no
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

[dropbox]
  path = /home/dropbox
  comment = Read and write
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup


```

In case you missed it, it's *[dropbox]* that I want to be writable.  Any ideas how I can get it so it's not just read-only?

---

### Post by trebor7_1 on 2007-09-22
> **Snoochie said:**
> Hello,

Solved the problem.
I did the following:

sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba.

Works magically.
Cheers,
Snoochie
Thanks Snoochie that worked for me!!!

Regards

Trebor

---

### Post by kngcrntrd on 2007-10-31
```
sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba
```

Thank you, Snoochie!!  Worked like a charm!

---

### Post by thinkoutsidewindows on 2007-12-26
> **Snoochie said:**
> Hello,

I can connect to Windows shares from Ubuntu > alt + f2 smb://xxx.xxx.xxx.xxx/Shared_



Is the xxx.xxx.xxx.xxx the IP adress of the computer or what?

I enter smb://sonydesktop/Shared_Documents

I have also tried using an address that I think I have found for the computer. Basically, I want to see shared documents on a networked XP machine from my Ubuntu machine and I can't get it. I've tried doing this... what am I doing wrong?

---

### Post by anne_maree on 2008-01-19
> **Snoochie said:**
> 
sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

> **baeckel said:**
> 
```
sudo gedit /etc/samba/smb.conf
```
you will then be prompted for your administrator password which you created while installing your system.  Now when gedit opens your .conf file you will have the option to save it.


Thank you guys. Long time browser, first time poster. Worked like a charm and allowed me to access my Ubuntu folders from my xp machine.

---

### Post by big_danmahony on 2008-02-07
> **Snoochie said:**
> Hello,

Solved the problem.
I did the following:

sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba.

Works magically.
Cheers,
Snoochie


Cheers mate,worked perfectly for me.

---

### Post by mreynaga on 2008-03-20
> **ishwar said:**
> hello folks..
i have been using ubuntu for almost 4mnth now! 
my system is a 40 gig hd, with winxp and ubuntu dual boot.. partion is ntfs and ext3.. with a swap! well my problem is i could not access ubuntu from windows.. my system symply not letting me to do it! i dont know why. i have modyfied the smb.conf file like mentioned in the forum above and i also set my password,, and importantly win xp only shows me c: drive wich is ntfs. when i tried looking thru the systme settings in ctrl pannel of windows the other partitiones are mentioned as unknown in type.. i hope i have provided enough info.. pls any one help me with this. i could access and use windows (music pics )etc.. from ubuntu without any prob! 

and i m sure there is samba in my ubuntu!!

i m a newbie to computer! 

thanx in advance

ishwar

samba has nothing to do with if you are dual booting, samba is for sharing files from one computer to another on a network, so when you are trying to access your ubuntu files from XP the reason it is not working is that your ubuntu install is turned off. by booting into XP it is the same as if you had 2 physical machines and went and powered off the ubuntu one. 

the reason you cant see your ubuntu files from within xp is that windows cannot read the formats of your ubuntu partitions, you cant run a dual booted machine and then try to access ubuntu stuff from within windows unless you create a partition that both OS's can read and store all your files there.

---

