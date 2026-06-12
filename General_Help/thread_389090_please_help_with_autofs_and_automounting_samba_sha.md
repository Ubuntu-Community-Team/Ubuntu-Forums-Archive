---
title: "please help with autofs and automounting samba shares"
date: 2007-03-20
forum: General Help
---

### Post by mmoalem on 2007-03-20
hi there all - been looking for a way to automount my samba shares on my ubuntu client the same way windows does 'map network drives', ie instead of manually mounting through LinNeighborhood (my current way of mounting network drives).
my setup is:
server name: MYSERVER
shared drive: PHILIPS1
samba shares dont use login and password, they are open to all on home netowrk
following [http://www.greenfly.org/tips/autofs.html](http://www.greenfly.org/tips/autofs.html) i have added to /etc/auto.master this line:
> /mnt    /etc/auto.smb   --timeout=60
and created an executable auto.smb with this lines:
> #!/bin/bash

# $Id: auto.smb,v 1.3 2005/04/05 13:02:09 raven Exp $

# This file must be executable to work! chmod 755!

philips1    -fstype=smbfs,username=ROOT,uid=1000,gid=1000	://MYSERVER/PHILIPS1

restarted autofs but it there is nothing in /mnt
what am i doing wrong?

---

### Post by gepatino on 2007-03-20
automount dirs are 'created' when you invoke them, in your case, try 'cd /mnt/philips1' and the do a ls, you should see the contents of the shared folder.

how does it works? mount point are only mounted when used, if you do an ls on /mnt you are not using the mountpoint philips1. 

To make it more userfriendly, you can create a dir with simlinks to these mount points, so the user is able to enter directly to the automounted dir. For example:

/shares/philip1 -> /mnt/philip1

So when te user enters /shares he/she sees a dir named philip1 even if /mnt/philip1 is not mounted yet.

---

### Post by mmoalem on 2007-03-20
cd /mnt/philips1 returns:
> bash: cd: /mnt/philips1: No such file or directory

so as i said earlier, /mnt is completly empty of folders or files, something else is wrong in my configuration...

---

### Post by dannyboy79 on 2007-03-20
i don't bother with autofs, I just have the samba shares in my fstab. the only downfall to this is if the samba share isn't available, then you'll see errors in log files but the normal user wouldn't even know it. if the share is available it'll be available when you start your computer. here ya go

[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by mmoalem on 2007-03-20
thanks dannyboy for your advise but i do prefer the idea of autofs precisely for the reason you mentioned. my server is not on all the time and at times i would start my ubuntu client while the server is off and than turn the server on later. in any case i would like a mountpoint that on accessing it it will look for the shared srive and mount it automatically and the share is not available just let me know so.  windows handles it very easliy and i thought there must be a way for linux to do the same, it looks to me that autofs should do it that way...

---

### Post by dannyboy79 on 2007-03-20
it does do it that way, you're just having problems with it. I am providing you an alternative but you're not interested in trying it why?? So what if you turn your server on after your client, than you simply type in 
sudo mount -a
and you're cifs share is right there for ya. Hell I could write up a script that pings your server at certain intervals and then if the ping is successful it would mount your share. Sure it's the ideal way of doing it but it works!!! That's what I love about linux, there is a million ways to do something where in winbloz, there's only a few and it's all based on what programs I'd have to buy whereas in linux I just download it for free or use the base tools in linux. I started about a year ago and simply love linux, Ubuntu.

---

### Post by mmoalem on 2007-03-20
hi dannyboy - i will try many shortcuts and hacks as needed - the reason i dont want it to go through fstab is that my wife and others less it inclined are using my ubuntu client while i'm not around and my wife in particular not interested in learning hacks and the likes - she wants to point and click and it all works.... and she is very likely to turn on the server and client in whatever order she feels like that day.... thats whi at the moment i keep a windows partition for her to log into but i would like to remove it so one requirment is that the music files on the server can be there for her whenever she wants in whatever order she wants
autofs seems like a neat solution if only i could get it to work...
and again i do appriciate you replying to this posting and even if it seems that i am not inclined to try your solution i am greatfull to you for trying to help.
cheers
michel

---

### Post by gepatino on 2007-03-20
what if you do:

ls /mnt/philips1

if autofs is running (/etc/init.d/autofs start) it should do the trick

---

### Post by mmoalem on 2007-03-20
gepatino thanks for the help however ls /mnt returns nothing
i have changed auto.master line to this:
> /mnt/autofs /etc/auto.smb --timeout=60
and restarted autofs 
folder /mnt/autofs been created by autofs so ls /mnt returns:
> autofs
ls /mnt/autofs again returns nothing

maybe i'm missing something in the system...? i have smbclient and smbfs installed and as explained above it works perfectly through LinNeighborhood but maybe there is something else need to be done other than jusy installing autofs and writing the auto.master file?

---

### Post by gepatino on 2007-03-20
The issue here is that the automatic mount points does not exist until you try to read them.

in auto.master you are defining /mnt/autofs as the root dir for your mounts, that will be controlled by auto.smb, where you define the mount point philip1 (inside /mnt/autofs)

so you should try this:

ls /mnt/autofs -> shows nothing, ok
ls /mnt/autofs/philip1 -> should show the contents of the share
ls /mnt/autofs (again) -> shows philip1

this is the expected behavior, in the first ls philip1 doen't exists becouse it haven't been mounted by autofs (since you are not trying to acces philip1 but reading /mnt/autofs)
after accessing philip1, it becomes visible in /mnt/autofs until timeout is reached.

if this does not work this way, try restarting autofs, but it should work. i've done this several times.

because of that 'strange' behavior that shows or hides mounts, it's recommended that you create some symlinks pointing to the 'phantom' dirs, say:

ln -s /mnt/autofs/philip1 /mnt/philip1

so when you do ls /mnt you'll see /mnt/philip1 even if /mnt/autofs/philip1 is not mounted yet

---

### Post by mmoalem on 2007-03-20
ok lets go through it again.
this is the shell output
> michel@gateway:~$ sudo /etc/init.d/autofs restart
Stopping automounter: done.
Starting automounter: done.
michel@gateway:~$ ls /mnt
autofs  philips1  PHILIPS1  philips2  samba
michel@gateway:~$ ls /mnt/autofs
michel@gateway:~$ ls /mnt/autofs/philips1
ls: /mnt/autofs/philips1: No such file or directory
michel@gateway:~$ ls /mnt/autofs/philips2
ls: /mnt/autofs/philips2: No such file or directory

(philips1, philips2, PHILIPS1, samba are folders i created in some earlier attempts to get it working but they are empty)

this is my /etc/auto.master:
> #
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/mnt/autofs  /etc/auto.smb   --timeout=60

this is my /etc/auto.smb:
> #!/bin/bash

# $Id: auto.smb,v 1.3 2005/04/05 13:02:09 raven Exp $

# This file must be executable to work! chmod 755!

philips1    -fstype=smbfs,username=ROOT,uid=1000,gid=1000	://MYSERVER/PHILIPS1
philips2    -fstype=smbfs,username=root,uid=1000,gid=1000	://MYSERVER/PHILIPS2


also just in case i have redirected sh to bash rather than dash

---

### Post by dannyboy79 on 2007-03-20
what happens if you try to ping MYSERVER. does it return anything or does it say host unreachable? or what about
 
**smbtree**

or 

**findsmb**

or

**smbclient -L MYSERVER**

please post what all this stuff returns and we'll see if your issue is with name resolution and not with autofs.

also, please show the output from this

**ls -la /etc/ | grep auto.smb** 
(NOTE: the thing between /etc/ and grep is a pipe, this is the shift key + the key below the backspace key.)

I also notice that you're using the depricated smbfs, cifs is basically taking this over and in my experience you get better transfer speeds. Here is a tutorial for you to try using AUTOFS cause I know you want that hbut instead of smbfs it uses cifs. this guide is based on ubuntu also.

[http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)
although it does count in passwords so I don't know if it'll work for ya since you don't have any. post the other info I asked for and I can maybe help some more.

---

### Post by mmoalem on 2007-03-20
here are the outputs...
> michel@gateway:~$ ping MYSERVER -w 10
ping: unknown host MYSERVER

> michel@gateway:~$ ping 10.0.0.3 -w 10
PING 10.0.0.3 (10.0.0.3) 56(84) bytes of data.
64 bytes from 10.0.0.3: icmp_seq=1 ttl=64 time=4.68 ms
64 bytes from 10.0.0.3: icmp_seq=2 ttl=64 time=0.243 ms

> michel@gateway:~$ smbtree
Password: 
MSHOME
        \\MYSERVER                      vaioserver server (Samba, Ubuntu)
                \\MYSERVER\IPC$                 IPC Service (vaioserver server (Samba, Ubuntu))
                \\MYSERVER\PHILIPS2       
                \\MYSERVER\PHILIPS1       
                \\MYSERVER\print$               Printer Drivers

> michel@gateway:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
10.0.0.3        MYSERVER      +[MSHOME] [Unix] [Samba 3.0.24]

> michel@gateway:~$ smbclient -L MYSERVER
Password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        PHILIPS1        Disk      
        PHILIPS2        Disk      
        IPC$            IPC       IPC Service (vaioserver server (Samba, Ubuntu))
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------
        MYSERVER             vaioserver server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        MSHOME               MYSERVER

> michel@gateway:~$ ls -la /etc/ | grep auto.smb
-rwxr-xr-x   1 root   root       278 2007-03-20 17:05 auto.smb
-rw-r--r--   1 root   root       278 2007-03-20 16:19 auto.smb~
-rw-r--r--   1 root   root       716 2007-03-20 14:27 auto.smb.bak


hope it sheds some light...

---

### Post by mmoalem on 2007-03-21
ok just been aware of the existence of fusesmb. is that a valid alternative to autofs?

---

### Post by dannyboy79 on 2007-03-21
> **mmoalem said:**
> here are the outputs...
hope it sheds some light...
***Section 2 but read first!!***
DId you check to make sure you have autofs compiled into your kernel? According to this link: ([http://www.linux-consulting.com/Amd_AutoFS/autofs-4.html#ss4.1](http://www.linux-consulting.com/Amd_AutoFS/autofs-4.html#ss4.1)) Run this:
```
sudo cat /proc/filesystems
```
and you should see 
nodev   autofs          
IF not, you can compile it as a module. Again use the above link.
I am curious though, what client computer are you trying to access these shares from??? It appears to me that you are simply trying it out on itself. I don't know how that works? Another thing, do you actually have a user on your computer called ROOT? Also, you don't have a password line for ROOT even if that user did exist. Try out this line:
-fstype=smbfs,guest,uid=1000,gid=1000
instead of yours just to test it.
***Section 1 but read second:***I wrote this first but then I started to review the original link in your thread 1 so this is what I was originally thinking but then changed my mind and instead of erasing it, I left it to see if this might help also. 
Well, it does shed some light. For 1 thing your name resolution within your network is NOT working. Why doesn't your other boxes show up? If its a windows box than it should appear? There is no point to what you are doing then if you're saying that you want a share to work after the machine turns on, so if you're setting this up in your client and your server, that doesn't make any sense. The way you were talking, you would make the shares call for a windows or another samba share not it's own?? I'll still try to help even though I don't understand it. See how you couldn't ping by hostname but you could by IP. This will stop autofs from working if you're using MYSERVER within your auto.smb. Another thing I notice is that your auto.smb file wasn't previously executable, this is another problem, but I see by the time stamp you made it executable at 17:05 on 2007-03-20. So, change your auto.smb's lines from

philips1 -fstype=smbfs,username=ROOT,uid=1000,gid=1000 ://MYSERVER/PHILIPS1
philips2 -fstype=smbfs,username=root,uid=1000,gid=1000 ://MYSERVER/PHILIPS2 

to

philips1 -fstype=smbfs,username=ROOT,uid=1000,gid=1000 ://10.0.0.3/PHILIPS1
philips2 -fstype=smbfs,username=root,uid=1000,gid=1000 ://10.0.0.3/PHILIPS2 

and see if that works. Also, did you review and make sure you followed the guide I posted? The guide uses auto.cifs but it doesn't matter because it's very similar. I don't know about the fusesmb package as I have already informed you how I handle this issue, I don't have any issues using my fstab and cifs as the mounting filesystem. I have passwords on all my machine so I use a credentials file so I am not sure how it works when you don't have a password. Also, have you checked out /var/log/messages or /var/log/syslog for any activity? These will let yuou know possibly why it's failing, whether it's authentification or what. You can use the log viewer under system, admin or just use gedit or cat | tail. I can't really suggest anything more because if you're following the guide I linked and doing what I suggested there is no reason it shouldn't be working. good luck

---

### Post by mmoalem on 2007-03-21
hi dannyboy !
ok first in regard to your suggestions
*sudo cat /proc/filesystems* returns* nodev autofs* so it looks ok
changing user to guest and MYSERVER to ip address didnt make a difference either
my client is ubuntu running on laptop, server has etch running on headless machine, dhcp  provided by adsl modem/router.
now to your fstab suggestion - this morning i had enough and gone ahead with your fstab recommendation and it works fine. i dont like leaving an unsolved problem unsolved (which is probably why i insisted on getting autofs to work rather than going with autofs) especially as the whole experience is a learning curve and if i get autofs working i will lean something new.
anyway, i guess for now i can try and write a script executable by all to mount all in fstab and show my wife how to click on it when she needs it.
BTW cifs didnt work for me in fstab, only smbfs, it returned some error in regarding to finding the server - should i stick with smbfs? what are the advantages of cifs? and also in regard to fusesmb - any ideas about it? what are the advantages with it?
cheers
michel

CORRECTION cifs working but i have to put ip address instead of server name

---

### Post by dannyboy79 on 2007-03-21
I agree with the unresolved thing, I too am a stickler about resolving something that "should work". I am new to linux myself, 1 year with Linux and Ubuntu. I merely did the fstab way because I didn't know about autofs or fusesmb when I wanted to mount a windows share on my ubuntu box. Well you never answered my question, did you check your messages and syslog for output. The original link you posted showed some great info about failures in the log files. 

You are going to want to fix the fact that you can't ping by hostname. Open your /etc/hosts file and add your computers and their ip's. check this out for help: ([http://ubuntuforums.org/showthread.php?t=379646&page=3&highlight=ping+hostname](http://ubuntuforums.org/showthread.php?t=379646&page=3&highlight=ping+hostname)) and read all the pages in that thread and you should have that fixed than hopefully my guide for autofs will work. It uses the smbclient command which we did test earlier and you were successful!

Also, now that you got cifs working, please try this guide word for word despite your feelings and you thinking that it won't work ([http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)). Don't forget to use the exact same username you used when you did the cifs fstab for this autofs thingy and don't forget to unmount the cifs share and comment out that line in your fstab temporarily before you play around with autofs. When you create the credentials file for each of your boxes, just put the username equal to a user on the box and leave the password entry blank, if that doesn't work, than try to erase the password line. Like I said, I have a password for all my machines since almost all guides always use them. I know it's a pain to enter it but at least it works.

If it doesn't work, when you post back, please provide the output from all the following commands:

cat /etc/auto.cifs

cat /etc/auto.master

cat /etc/fstab      (NOTE: make sure you provide me the one that has the added cifs mount in it even if it's commented out)

ls -la /etc/ | grep auto.cifs

ls -la /etc/ | grep auto.smb.     (if that doesn't return anything maybe put a * at the end. what I am looking for is to see if you created the credentials file. once that returns the result I want to see the cat command of that)

cat /etc/auto.smb.*

cat /var/log/message | tail

cat /var/log/syslog | tail

IMPORTANT PART: in the guide he says to make sure you change where it says *user* to your personal username. He's talking about this line;
mountopts="-fstype=cifs,file_mode=0644,dir_mode=0755,uid=**user**,gid=users"
make sure you pick your username.

---

### Post by mmoalem on 2007-03-21
thanks dannyboy for sticking with this post... i will try your suggestions later on tonight and will post results after that...

---

### Post by dannyboy79 on 2007-03-21
yeah. I do enjoy helping. I wouldn't have over 1,700 posts within 1 year if I didn't. That means I have made almost 5 posts every single day for 1 year. Horray!!

---

### Post by mmoalem on 2007-03-21
well the good the bad and the ugly...
followed your suggestions about the hosts file and the link to howtoforge tutorial and it works! i got autofs to work and mount the shares on demand.
so the bad and the ugly... well it seems that after all that the fstab solution might be in some ways neater.... the problem i came across was that after creating symlinks to the shares (with autofs until you try to access a share it does not exist in the filesystem which means unless you know its address you can find it - so you need a symlink) if the shares were unaccessible (like during server reboot or when turned off) the folder which contains the synlinks would take ages to open/accessed, it just kind of freezes for a minute or so, i assume that it is because it is waiting for a reply from the network. in the grand scheme of things its a little annoyance but one never the less (using the fstab solution the mounting point is much more responsive - if it is not mounted that it shows empty folder)
so where does this leave me? i have to confess to a certain amount of satisfaction of getting this to work but i am tempted to going back to fstab... it was working but i did get stuck trying to write a script (mount -a) executable by all users - ubuntu doesnt allow the mount all command to be executed by anyone other than root - i know that i can create a shortcut like: 'gksu mount -a' but that will require the user to input password another little annoyance...
so two working solutions and none that is seamless...
maybe i should check what fusesmb is all about...
cheers

---

### Post by dannyboy79 on 2007-03-22
i just looked over the original link you posted and there seems to be some more great info at the bottom especially the part about the script he created. he states that the script smbbrowse he created works so that it won't fail when browsing password protected shares so maybe it'll work the same for unreachable servers and happen a little quicker than the minute or so you say it takes? [http://www.greenfly.org/tips/autofs.html](http://www.greenfly.org/tips/autofs.html)
you could try fusesmb but I have never used it. also, what about using the "users" option in your fstab entry although since smbfs and cifs are mounted by smbmount I don't know if that would work. then if the share didn't get mounted at startup because the server was offline, but now it's available, you can just create a little icon on your desktop, then they double click it and instead of it running mount -a, it should just mount it manually. Not sure if that would cause problems with fstab, maybe it should mount it to a different location on the same level? one folder named music and another names music-retry. 

Also, can you please post back how you got your autofs to work because I know the guide I pointed you to didn't have an option for non-password protected shares then maybe I can post a new thread informing people how to do that and I'll mention your name. good luck

---

### Post by mmoalem on 2007-03-22
on my setup i used
> username=guest
password=

---

### Post by mmoalem on 2007-03-23
ok things are far from perfect....
yesterday things seemed ok but i did have some wiered bugs... i will try to describe it.
lets say my shares are A and B and inside A all i have is a folder called photos - so i first time i use file manage to look into /mountpoint/A i see the folder photos. i get out of the folder and look again into it and now it has three folders photos, A and B... later i  look again into /mountpoint/A/A and it has photos, A and B ... an endless loop i think.... 
after few hours i look into the trash and it has 1251 files (folders and symlinks) by the names A and B) and i havent deleted anything during that time...
anyway this morning i tried to start my client without the server and i it was slow and the Desktop disapeared so i looked as systemlog and daemon.log both showed the system keep on trying to connect to the server
> Mar 23 11:05:27 localhost automount[5540]: lookup(program): lookup for MYSERVER failed
Mar 23 11:05:27 localhost automount[5540]: failed to mount /cifs/MYSERVER
this continued for 10 minutes until i started the server...

in short - i dont like it, i dont like it at all...
not sure if its a configuration error or a bug but i might opt for an fstab solution until feisty is out and than i will try again on clean install

i have looked at the script you mentioned but it seems a little bit above my head to try to adapt it to my case, i did try the -nonstrict option mentioned there but it did not help

---

### Post by dannyboy79 on 2007-03-23
sounds to me like your symlinks aren't working right. 

The script uses all variables so you don't have to modify it
(NOTE: don't forget to install this, libfilesys-smbclient-perl)

#!/usr/bin/perl

# auto.smbbrowse -- by greenfly (greenfly@greenfly.org)
# This script will output the proper autofs configuration 
# based on the servername it is passed.

# here is an example entry in /etc/auto.master to use this script,
# the most important thing is the -nonstrict option, otherwise if a single
# smb filesystem can't be mounted as guest, none will:
# /var/autofs/smbbrowse   /etc/auto.smbbrowse     --timeout=60,-nonstrict

# once installed, to use, cd to /var/autofs/smbbrowse/server/share
# ls /var/autofs/smbbrowse/server/ will list all available shares on that server

# on debian: apt-get install libfilesys-smbclient-perl
# otherwise: perl -MCPAN -e 'install Filesys::SmbClient'
use Filesys::SmbClient; 

my $mount_options = "-fstype=smbfs,guest";


my $server = shift(@ARGV);

my $smb = new Filesys::SmbClient();

# get list of file shares
my @shares = browse("smb://$server");


# start the output
print "$mount_options\t";

foreach(@shares)
{
   s/ /\\ /g;
   print "/$_ //$server/$_ ";
}
print "\n";




#------------------------------------------------------------------------------
# Method that browse content of $rep and output the list of file shares
#------------------------------------------------------------------------------
sub browse
{
   my ($rep) = @_;
   chop($rep) if ($rep=~/\/$/);
   return undef if (!$rep);

# Read directory
   my $D = $smb->opendir($rep) || die "Can't read $rep:$!\n";
   my @f = $smb->readdir_struct($D);
   $smb->close($D);
# Sort file by name
   @f = sort { $a->[1] cmp $b->[1] } @f;

   my @ftemp;
   foreach $f (@f)
   {
# filter out everything that isn't a file share
      if($f->[0] == 3){ push @ftemp, $f->[1]; }
   }
   @f = @ftemp;

   return @f;
}

**This line and nothing below is part of the script.** Just copy and paste it into a file called auto.smbbrowse and put it inside /etc/ and make it executable. Then add an entry in your auto.master for where ever you'd like the multiple nested shares to show up. Maybe a folder like /mnt/autofs/smbbrowse/. So the entry in your auto.master would be

/mnt/autofs/smbbrowse   /etc/auto.smbbrowse     --timeout=60,-nonstrict

(NOTE: You should delete all your symlinks and comment out your other lines within your auto.master so they don't all mess each other up as I am not sure if they would)
then to run it (you could just run it to see what servers are up and then what shares are available with guest access, but this is only information, you don't need to run it for your shares to show up cause it's handled by autofs when you simply browse to the folder /mnt/autofs/smbbrowse), you would just type in 
/etc/auto.smbbrowse MYSERVER
and it will list the shares for that server, for example something like this should show up
-fstype=smbfs,guest     /photos //MYSERVER/photos
in an environment with multiple server names, you can always type in smbtree to get all the available servers.

Then if you go to the location, /mnt/autofs/smbbrowse/  the server would show up first so it should be then /mnt/autofs/smbbrowse/MYSERVER, then when you browse that folder you should see shares that are accessible by guests.

OR

go here and try his script. when you get the webpage, just use your web browser and do a find or search, type in autofs and you'll right where the article is, it's about 1/4 of the way down. all the instructions are there. [http://www.holviala.com/~kimmy/diary/2004/11/index.html](http://www.holviala.com/~kimmy/diary/2004/11/index.html)

Again, let me know how it goes. I wanted to ask, are you able to write to these auto mounted shares??? I wouldn't think so because you're mounting them as guest and normally when samba mounts a share as guest, it doesn't allow write access only reading. So please let me know so I can inform others. This wouldn't be a problem is you enacted usernames and passwords of course, unless it's not a problem and you can write to the folders.

---

### Post by mmoalem on 2007-03-23
hi dannyboy - will try wour script later when i have some time for play... 
in regard to your question - indeed i am able to write to the shares but i think it is because the way i set the samba shares server side and the fstab on the server to allow anyone read/write permissions - to be honest i cant remember exactly what i did but if you want i can get back to the samba config and fstab on the server to check my settings
cheers
michel

---

### Post by mmoalem on 2007-03-23
ok, tried the second suggestion first (the link you reffered me too - it looked simple cut and paste method so i thought i will try it first) and it doesnt work for me similar endless loop of mount points. to demonstrate this is the output of the ls command:
> michel@gateway:~$ ls /mnt/smbfs/MYSERVER/philips1
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/philips1
ls: /mnt/smbfs/philips1: No such file or directory
michel@gateway:~$ ls /mnt/smbfs/PHILIPS1
ls: /mnt/smbfs/PHILIPS1: No such file or directory
michel@gateway:~$ ls /mnt/smbfs/10.0.0.3
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/10.0.0.3/philips1
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/MYSERVER/philips1/philips1
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/MYSERVER/philips1/philips1/philips1
philips1  philips2  print

not sure whats going on with this endless loop effect....

---

### Post by dannyboy79 on 2007-03-23
whenever you get errors, please always post the contents of the files we're tweaking. So if you followed that guide please post the auto.master, the auto.smbfs, and the rest of them that you are using. Also, please post the output from ls -ls /etc/ | grep auto (or ls -ls /etc/ | grep auto*) then we'll go from there.  Also, are you trying this all from your client? Or are you doing this on your server. IF your doing this on your server than I am guessing thats why this is happening. Also, did you remove all the old symlinks? DId you make sure that /sbin/mount.smbfs was a symlink, then rename it old-.... but don't remove it in case you need it and put the one in it's place.

When you do ls /mnt/smbfs/MYSERVER
you should get back the available shares phillip1, phillip2, and print. Don't foget, all this is done on your client NOT YOUR SERVER. If you did this on your server than yeah, your going to get an endless loop!!!

---

### Post by mmoalem on 2007-03-23
all i am doing is on the client only
i have downloaded the scripts from the websites and followed the instructions as to the letter (inc changing /sbin/mount.smbfs to /sbin/mount.smbfs.bak and copying the downloaded mount.smbfs to /sbin). the only difference is the password file where i wrote:
> username = guest
password = 
domain   = 

here are some of the output you requested:
> michel@gateway:~$ ls -ls /etc/ | grep auto
  4 -rwxr-xr-x  1 root   root      1258 2007-03-21 18:49 auto.cifs
  4 -rw-r--r--  1 root   root      1258 2007-03-21 18:46 auto.cifs~
  4 -rw-r--r--  1 michel michel     116 2007-03-23 13:01 auto.label
  4 -rw-r--r--  1 root   root       559 2007-03-23 13:22 auto.master
  4 -rw-r--r--  1 root   root       393 2007-03-22 22:58 auto.master~
  4 -rw-r--r--  1 root   root       581 2007-03-19 23:24 auto.misc
  4 -rwxr-xr-x  1 root   root      1308 2007-03-19 23:24 auto.net
  4 -rwxr-xr-x  1 michel michel     487 2007-03-23 13:01 auto.nfs
  4 -rwxr-xr-x  1 root   root       271 2007-03-21 18:25 auto.smb
  4 -rw-r--r--  1 root   root       270 2007-03-21 14:14 auto.smb~
  4 -rw-------  1 root   root       716 2007-03-20 14:27 auto.smb.bak
  4 -rwxr-xr-x  1 michel michel     784 2007-03-23 13:01 auto.smbfs
  4 -rw-------  1 root   root        25 2007-03-21 18:46 auto.smb.MYSERVER
  0 -rw-------  1 root   root         0 2007-03-21 18:46 auto.smb.MYSERVER~

> michel@gateway:~$ ls /mnt/smbfs/MYSERVER
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/MYSERVER/philips1
philips1  philips2  print
michel@gateway:~$ ls /mnt/smbfs/MYSERVER/PHILIPS1
philips1  philips2  print


---

### Post by dannyboy79 on 2007-03-23
yeah, I am guessing that since you have so many of these you need to either rename them so they don't get used or delete them. So make sure you get rid of all of them except auto.smbfs (make sure it's the 1 from the latest guide), auto.label, auto.nfs, plus the auto.master from the last guide you followed. Also, you didn't post the output from auto.master. please post the output from smbtree as well.

---

### Post by mmoalem on 2007-03-23
tried the script you poseted from greenfly
and this some output:
> michel@gateway:~$ sudo /etc/init.d/autofs restart
Stopping automounter: done.
Starting automounter: done.
michel@gateway:~$ /etc/auto.smbbrowse MYSERVER
-fstype=smbfs,guest     /PHILIPS1 //MYSERVER/PHILIPS1 /PHILIPS2 //MYSERVER/PHILIPS2 /print$ //MYSERVER/print$ 
michel@gateway:~$ ls /mnt/smbbrowse/MYSERVER
PHILIPS1  PHILIPS2  print
michel@gateway:~$ ls /mnt/smbbrowse/MYSERVER/PHILIPS1
ls: /mnt/smbbrowse/MYSERVER/PHILIPS1: No such file or directory
michel@gateway:~$ ls /mnt/smbbrowse/MYSERVER
PHILIPS2  print
michel@gateway:~$ ls /mnt/smbbrowse/MYSERVER/PHILIPS2
ls: /mnt/smbbrowse/MYSERVER/PHILIPS2: No such file or directory
michel@gateway:~$ ls /mnt/smbbrowse/MYSERVER
print

maybe its an access issue with guest but it does not happen with the other solutions both other autofs scripts and fstab - i have full access as guest

---

### Post by mmoalem on 2007-03-23
correction to the above: i have forgot to retrn /sbin/mount.smbfs to the original symlink (from the one i dropped in through the previous attempt)
now it seems to work. i have just created symlinks to the mounted shware and i will see how it behave over the day

---

### Post by dannyboy79 on 2007-03-23
you keep mixing all these different things after you don't get it to work right away. why don't you stick with one solution and troubleshoot it till it works. also, PLEASE. when you post back, whether you are successful or if you it still doesn't work. PLEASE post the output from the required files that you use to get it to work so that we can either trouble shoot it or we can help others. I thank you if you do this and others will thank you also.

---

### Post by asimonelli on 2007-04-17
I use the --ghost option in the start-up script /etc/init.d/autofs :

daemonoptions='--ghost'

This creates a ghost version of the share for you to click on and then it will mount the drive.  Sort of the equivalent to the symlinks method only built into autofs.  That way if you ever remove autofs, you don't have to delete any symlinks manually.

---

### Post by deromka on 2007-04-20
Hi all,

Had the same problem, but finally solved it by installing smbfs package!!!

'sudo apt-get install smbfs' solves this issue.

worked for me with autofs

enjoy!

---

