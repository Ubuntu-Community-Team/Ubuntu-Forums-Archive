---
title: "Hosts.txt in Ubuntu Possibly Corrupted"
date: 2008-03-15
forum: General Help
---

### Post by CD27 on 2008-03-15
Okay, I'm an IT in the US Navy, but my schooling only covered window's based OS's, not linux. So, I put linux as my primary OS on my laptop. Unfortunately, it doesn't seem to have any kind of internet secutirity as far as blocking porn sites, making sure you don't see nude pics on a yahoo image search, or going to sites that might contain viruses, etc.

I know about he hosts.txt file in windows, so I found the same thing in Linux and looked at it. I was testing it out (like an idiot, I didn't back it up), and put 127.0.0.1   [www.yahoo.com](www.yahoo.com). It worked of course, but when I went back to take it off, it didn't work...now I can't open my yahoo mail b/c I can't even get to the site....any help? sorry, I'm being a complete idiot.

CD

---

### Post by yabbadabbadont on 2008-03-15
The file is /etc/hosts

Just edit the file and remove the offending line.  You will need to start your editor with either sudo (terminal based editor) or gksudo (graphical editor) in order to save your changes.

Edit: You will also have to close and restart your browser most likely.  I've run into that myself in the past.

---

### Post by CD27 on 2008-03-15
how do I run it in terminal, if I click "run in terminal" it just shoots through it and doesn't let me edit it

Edit: or how about this, how do i set it up to automatically allow a specific site?

---

### Post by yabbadabbadont on 2008-03-15
It is a text file, you don't "run it", you edit it.  :D

In a terminal I would suggest using the nano editor, as it is easy to use.

```
sudo nano /etc/hosts
```

---

### Post by CD27 on 2008-03-15
it says, 

sudo: /etc/sudoers is mode 0666, should be 0440

Edit: I know it's a text file and how to edit it, sorry, i'm just not a linux guy, but i want to be :D

---

### Post by yabbadabbadont on 2008-03-15
How did you mess up the permissions on /etc/sudoers?  You didn't happen to run the "chmod" command on *everything* in /etc did you?  If so, your best bet is to back up any personal files and reinstall...

---

### Post by CD27 on 2008-03-15
nani? I went to the root user, right clicked on the etc folder, and set permissions to read and write on all, that's it. I set it to set it to all subfolders too. how would that hurt it?

Okay, is there a list or something that could tell me what the permissions for each item are supposed to be so I can reset them individuall?

---

### Post by yabbadabbadont on 2008-03-15
"how would that hurt it?"  You've just discovered how.  :D

And, no, there isn't such a list.  Reinstall time.  :(

---

### Post by CD27 on 2008-03-15
what about the "rmp" command, i've done a little research and I think i saw something somwhere that says that command could fix it

---

### Post by PeterJS on 2008-03-15
Generally you don't want to change the permissions on large portions of the file system outside of you home directory. As yabbadabbadont indicated if you changed the permissions on /etc/ (and everything under it) that would include /etc/sudoers. By giving /etc/sudoers world write permission you've allowed any user (regardless of privileges), to change the list of who is allow elevated permissions. So any account can give itself any permission it wants. Rather than allow the system to continue in this broken state, sudo locks itself down and refuses to grant any elevated privileges as it can't know which are legitimate requests, and which could be the result of tampering.

Your only hope of recovery with out re-installing at this point are if you've enabled the root account (despite all the warnings that you shouldn't) and can log in to that and rest the permissions on /etc/sudoers. But even then you have much bigger security issues to worry about. All user passwords are stored in /etc/shadow, which now has world read and write permission, so any user can read or arbitrarily set any password.

Your best bet is backing up your data, reinstalling, and calling it a learning experience.

---

### Post by CD27 on 2008-03-15
I'm not reinstalling, I've spent far too much time on here installing and updating stuff to just throw it away, there's always a simple way to fix everything, and if it's not simple, then i'll take the complex route. Yes, i have activated the root account, so is there some kind of list or something that tells you what the default permissions are for all original files (or at least the important ones) and if there isn't then why the heck isn't there because I've found alot of users who have run into this problem (and the system never gave me any kind of warning when i did this, why not?)

if it takes me a week to reset these permissions, I can do that, but i can't afford to reinstall my system. Changing my password isn't hard to do

---

### Post by PeterJS on 2008-03-15
> **CD27 said:**
> I'm not reinstalling, I've spent far too much time on here installing and updating stuff to just throw it away, there's always a simple way to fix everything, and if it's not simple, then i'll take the complex route. Yes, i have activated the root account, so is there some kind of list or something that tells you what the default permissions are for all original files (or at least the important ones) and if there isn't then why the heck isn't there because I've found alot of users who have run into this problem **(and the system never gave me any kind of warning when i did this, why not?)**
The system most certainly did warn you, you simple chose to ignore the warning. One of the function of sudo requesting a password is to let you know that what you're about to do will have system wide consequences, and you should probably very sure that you know what you're doing before you do it.

Well log in to root, and you can start resetting permission on things, I've attached the output of ls -l from my /etc/. Good luck.

---

### Post by CD27 on 2008-03-15
Okay, thanks a bunch. I'll get to work right now.

---

### Post by CD27 on 2008-03-15
Okay, I'm having a bit of a problem. I can't figure out how to change their permissions. I know i can go to users and groups and change those permissions, and I can right click and go to permissions, but i can't figure out how to change their modes and stuff like that.

---

### Post by yabbadabbadont on 2008-03-15
In a terminal window:
```
man chmod
```

---

### Post by jinx099 on 2008-03-15
oh boy...

Well, this may save you some time without reinstalling.  If I were in your situation, I would install a fresh clean copy of Ubuntu on a VM or on a second computer, and then copy over the /etc from that to your current computer.

Why exactly did you change all the perms in /etc?  Do you understand the security consequences of what you did?

---

### Post by CD27 on 2008-03-15
I understand now :D. Actually, that's not a bad idea. I have Virtual Box on my computer. I think I could do that. I changed the perms b/c I wanted to have access to the HOSTS file in my regular account, I didn't know anything about the folder I was messing with though...woops. I also didn't think that the program that I needed to fix the thing would have locked itself up like that.

Thanks for the great idea. However, one question...if my passwords are in there....and i write over them, won't it corrupt my way INTO the computer?

---

### Post by hyperair on 2008-03-15
I don't see why you need to mess up your /etc folder more. All you did was change the permissions right? In that case get a LiveCD, and from there change the permissions back to what it was before. Specifically, change everything especially /etc/sudoers back to 0660. (read/write for user and group but not all).

---

### Post by CD27 on 2008-03-15
yeah....so how do i do that? and again, my initial question, if by changing my /etc folder wouldn't that also corrupt my password and lock me completely out of the system?

---

### Post by hyperair on 2008-03-15
In a livecd, type into the run dialog: "gksudo nautilus". Navigate to /etc, and reverse the changes that you did before to your /etc. Changing the permissions of a file does not alter its contents in any way. So you won't corrupt anything unless you somehow bomb /etc/passwd and /etc/groups making them non-readable or something.

---

### Post by koenn on 2008-03-15
> **CD27 said:**
> 
However, one question...if my passwords are in there....and i write over them, won't it corrupt my way INTO the computer?
Yes, it would (if you copy all of /etc from a VM or a live CD, not if you only change the permissions).
keep a copy of the original /etc/passwd and /etc/shadow. These will have the wrong permissions, but at least the contents is correct and you can chmod those files.

Don't log off /reboot untill your 100% sure you know what your root password is. Reset it (eg after you've copied over /etc ) : in a terminal : passwd root
you can start a new console with ctrl+alt F1 (or F2, F3, ...) and log on there.
It's also a good idea to leave a root session open so you can switch to that and fix what you might mess up in an other session.

---

### Post by CD27 on 2008-03-15
okay, so i discovered a new problem, i can't run my virtual box program b/c it requires /etc to be working properly to do ANYTHING. So that option is down the drain. are you sure that i can run the live cd, then while running the liveCD's initial virtual trial/live linux, i can access my /etc from my installed hard drive and change it that way?

---

### Post by hyperair on 2008-03-15
Yes. you can.

---

### Post by CD27 on 2008-03-15
okay, i FINALLY got my live CD to boot up and am on it right now, so the only problem i have now is that I can't find the C drive, any options on that? I've done a search on the forum and haven't found anything about that yet, but i'm about to do a google search. If you can answer before that it'd be great. THANKS!

---

### Post by jinx099 on 2008-03-15
> **CD27 said:**
> okay, i FINALLY got my live CD to boot up and am on it right now, so the only problem i have now is that I can't find the C drive, any options on that? I've done a search on the forum and haven't found anything about that yet, but i'm about to do a google search. If you can answer before that it'd be great. THANKS!

You're not looking for the "C" drive, that is windows terminology.  What you are looking for is your / or "root" partition.  Chance are it is already mounted.  Take a look in /media/

---

### Post by koenn on 2008-03-15
Technically, you're looking for the 1st partition of the first hard drive, not C: or / 
jinx099 is right in that it may already be mounted on /media/hda1 or /media/sda1 or something like that. (you'll recognise it by the files en folders, probably)

you can check what's mounted where by running
```
mount
```

the mount command will also let you mount that partition if it did not get mounted automatically

---

### Post by CD27 on 2008-03-15
to update the thread, i've posted a new thread on this subject here: [http://ubuntuforums.org/showthread.php?t=725209&page=3](http://ubuntuforums.org/showthread.php?t=725209&page=3). Hope this helps even things out a bit.

---

### Post by hyperair on 2008-03-15
Well I've now posted in the other thread now too @.@

---

### Post by koenn on 2008-03-15
This thread got me wondering whether it is possible to batch process the changing of filesystem modes ('permissions') by copying them of a model system.

this worked for me :
```

(for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /home/test$FILE" ; done) |/bin/bash

```
needs to be run as root, of course.
if you run this from a live cd or so, change the '/home/test' to '/media/hda1' or wherever your target system is mounted
if running from a live CD, it will chmod only those files that also exist in /etc of the live-cd system


to see the commands but not execute them, run
```

for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /home/test$FILE" ; done

```
this can be redirected to a file to create a script : ( for ... done ) > file

---

### Post by CD27 on 2008-03-16
here is what I got (whew, six hours sleep, thank goodness- i didn't go to sleep till about 7:00 AM)



/bin/bash: line 3838: /media/had1/etc/ssl/certs/ValiCert_Class_2_VA.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3840: /media/had1/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3842: /media/had1/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3844: /media/had1/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3846: /media/had1/etc/ssl/certs/Verisign_Class_1_Public_Primary_OCSP_Responder.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3848: /media/had1/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3850: /media/had1/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3852: /media/had1/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3854: /media/had1/etc/ssl/certs/Verisign_Class_2_Public_Primary_OCSP_Responder.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3856: /media/had1/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3858: /media/had1/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3860: /media/had1/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3862: /media/had1/etc/ssl/certs/Verisign_Class_3_Public_Primary_OCSP_Responder.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3864: /media/had1/etc/ssl/certs/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3866: /media/had1/etc/ssl/certs/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3868: /media/had1/etc/ssl/certs/Verisign_RSA_Secure_Server_CA.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3870: /media/had1/etc/ssl/certs/Verisign_Secure_Server_OCSP_Responder.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3872: /media/had1/etc/ssl/certs/Verisign_Time_Stamping_Authority_CA.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3874: /media/had1/etc/ssl/certs/Visa_International_Global_Root_2.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3876: /media/had1/etc/ssl/certs/Visa_eCommerce_Root.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3878: /media/had1/etc/ssl/certs/a145806c.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3880: /media/had1/etc/ssl/certs/a15b3b6b.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3882: /media/had1/etc/ssl/certs/a2df7ad7.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3884: /media/had1/etc/ssl/certs/a3896b44.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3886: /media/had1/etc/ssl/certs/a6776c69.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3888: /media/had1/etc/ssl/certs/a7605362.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3890: /media/had1/etc/ssl/certs/aaa45464.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3892: /media/had1/etc/ssl/certs/b0f3e76e.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3894: /media/had1/etc/ssl/certs/b3fec4ff.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3896: /media/had1/etc/ssl/certs/b5f329fa.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3898: /media/had1/etc/ssl/certs/b8609e8a.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3900: /media/had1/etc/ssl/certs/bcdd5959.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3902: /media/had1/etc/ssl/certs/bda4cc84.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3904: /media/had1/etc/ssl/certs/beTRUSTed_Root_CA-Baltimore_Implementation.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3906: /media/had1/etc/ssl/certs/beTRUSTed_Root_CA.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3908: /media/had1/etc/ssl/certs/beTRUSTed_Root_CA_-_Entrust_Implementation.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3910: /media/had1/etc/ssl/certs/beTRUSTed_Root_CA_-_RSA_Implementation.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3912: /media/had1/etc/ssl/certs/bf87590f.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3914: /media/had1/etc/ssl/certs/brasil.gov.br.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3916: /media/had1/etc/ssl/certs/c19d42c7.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3918: /media/had1/etc/ssl/certs/c215bc69.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3920: /media/had1/etc/ssl/certs/c33a80d4.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3922: /media/had1/etc/ssl/certs/c527e4ab.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3924: /media/had1/etc/ssl/certs/c9bc75ba.0: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 3926: /media/had1/etc/ssl/certs/ca-certificates.crt: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3928: /media/had1/etc/ssl/certs/cacert.org.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3930: /media/had1/etc/ssl/certs/ccb919f9.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3932: /media/had1/etc/ssl/certs/cdaebb72.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3934: /media/had1/etc/ssl/certs/d2adc77d.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3936: /media/had1/etc/ssl/certs/d537fba6.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3938: /media/had1/etc/ssl/certs/d78a75c7.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3940: /media/had1/etc/ssl/certs/d8274e24.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3942: /media/had1/etc/ssl/certs/ddc328ff.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3944: /media/had1/etc/ssl/certs/e268a4c5.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3946: /media/had1/etc/ssl/certs/e28f6bbc.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3948: /media/had1/etc/ssl/certs/e7b8d656.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3950: /media/had1/etc/ssl/certs/ed049835.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3952: /media/had1/etc/ssl/certs/ed524cf5.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3954: /media/had1/etc/ssl/certs/ed62f4e3.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3956: /media/had1/etc/ssl/certs/f3cf1e8e.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3958: /media/had1/etc/ssl/certs/f4996e82.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3960: /media/had1/etc/ssl/certs/f64d9715.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3962: /media/had1/etc/ssl/certs/f73e89fd.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3964: /media/had1/etc/ssl/certs/f950ccc2.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3966: /media/had1/etc/ssl/certs/ff783690.0: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3968: /media/had1/etc/ssl/certs/signet_ca1_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3970: /media/had1/etc/ssl/certs/signet_ca2_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3972: /media/had1/etc/ssl/certs/signet_ca3_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3974: /media/had1/etc/ssl/certs/signet_ocspklasa2_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3976: /media/had1/etc/ssl/certs/signet_ocspklasa3_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3978: /media/had1/etc/ssl/certs/signet_pca2_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3980: /media/had1/etc/ssl/certs/signet_pca3_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3982: /media/had1/etc/ssl/certs/signet_rootca_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3984: /media/had1/etc/ssl/certs/signet_tsa1_pem.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3986: /media/had1/etc/ssl/certs/spi-ca.pem: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 3988: /media/had1/etc/ssl/certs/ssl-cert-snakeoil.pem: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 3990: /media/had1/etc/ssl/openssl.cnf: No such file or directory
chmod: missing operand after `710'
Try `chmod --help' for more information.
/bin/bash: line 3992: /media/had1/etc/ssl/private: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 3994: /media/had1/etc/sysctl.conf: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 3996: /media/had1/etc/syslog.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 3998: /media/had1/etc/terminfo: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4000: /media/had1/etc/terminfo/README: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4002: /media/had1/etc/ucf.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4004: /media/had1/etc/udev: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4006: /media/had1/etc/udev/rules.d: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4008: /media/had1/etc/udev/rules.d/00-init.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4010: /media/had1/etc/udev/rules.d/11-hplj10xx.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4012: /media/had1/etc/udev/rules.d/20-names.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4014: /media/had1/etc/udev/rules.d/25-iftab.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4016: /media/had1/etc/udev/rules.d/40-permissions.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4018: /media/had1/etc/udev/rules.d/45-hplip.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4020: /media/had1/etc/udev/rules.d/45-libgphoto2.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4022: /media/had1/etc/udev/rules.d/45-libsane.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4024: /media/had1/etc/udev/rules.d/60-symlinks.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4026: /media/had1/etc/udev/rules.d/65-persistent-input.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4028: /media/had1/etc/udev/rules.d/65-persistent-storage.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4030: /media/had1/etc/udev/rules.d/80-programs.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4032: /media/had1/etc/udev/rules.d/85-alsa.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4034: /media/had1/etc/udev/rules.d/85-hal.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4036: /media/had1/etc/udev/rules.d/85-hdparm.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4038: /media/had1/etc/udev/rules.d/85-hwclock.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4040: /media/had1/etc/udev/rules.d/85-ifupdown.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4042: /media/had1/etc/udev/rules.d/85-pcmcia.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4044: /media/had1/etc/udev/rules.d/90-modprobe.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4046: /media/had1/etc/udev/rules.d/99-udevmonitor.rules: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4048: /media/had1/etc/udev/rules.d/README: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4050: /media/had1/etc/udev/udev.conf: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4052: /media/had1/etc/uniconf.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4054: /media/had1/etc/update-notifier: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4056: /media/had1/etc/updatedb.conf: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4058: /media/had1/etc/usplash.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4060: /media/had1/etc/vim: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4062: /media/had1/etc/vim/vimrc: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4064: /media/had1/etc/vim/vimrc.tiny: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4066: /media/had1/etc/vnc.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4068: /media/had1/etc/w3m: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4070: /media/had1/etc/w3m/config: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4072: /media/had1/etc/w3m/mailcap: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4074: /media/had1/etc/wgetrc: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4076: /media/had1/etc/wpa_supplicant: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4078: /media/had1/etc/wpa_supplicant/ifupdown.sh: No such file or directory
chmod: missing operand after `640'
Try `chmod --help' for more information.
/bin/bash: line 4080: /media/had1/etc/wvdial.conf: No such file or directory
chmod: missing operand after `755'
Try `chmod --help' for more information.
/bin/bash: line 4082: /media/had1/etc/xml: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4084: /media/had1/etc/xml/catalog: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4086: /media/had1/etc/xml/catalog.old: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4088: /media/had1/etc/xml/docbook-xml.xml: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4090: /media/had1/etc/xml/docbook-xml.xml.old: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4092: /media/had1/etc/xml/scrollkeeper.xml: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4094: /media/had1/etc/xml/sgml-data.xml: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4096: /media/had1/etc/xml/sgml-data.xml.old: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4098: /media/had1/etc/xml/xml-core.xml: No such file or directory
chmod: missing operand after `644'
Try `chmod --help' for more information.
/bin/bash: line 4100: /media/had1/etc/xml/xml-core.xml.old: No such file or directory
ubuntu@ubuntu:~$ 


it wouldn't show everything, so this is what I got on the first one


this is the second code:



 /home/test/etc/ssl/certs/10d149a2.0
chmod 777
 /home/test/etc/ssl/certs/11a09b38.0
chmod 777
 /home/test/etc/ssl/certs/11f154d6.0
chmod 777
 /home/test/etc/ssl/certs/124bbd54.0
chmod 777
 /home/test/etc/ssl/certs/128b9c8d.0
chmod 777
 /home/test/etc/ssl/certs/1689a10b.0
chmod 777
 /home/test/etc/ssl/certs/19899da5.0
chmod 777
 /home/test/etc/ssl/certs/256fd83b.0
chmod 777
 /home/test/etc/ssl/certs/2edf7016.0
chmod 777
 /home/test/etc/ssl/certs/2fb1850a.0
chmod 777
 /home/test/etc/ssl/certs/31044350.0
chmod 777
 /home/test/etc/ssl/certs/3ad48a91.0
chmod 777
 /home/test/etc/ssl/certs/3c58f906.0
chmod 777
 /home/test/etc/ssl/certs/3e223c08.0
chmod 777
 /home/test/etc/ssl/certs/3e7271e8.0
chmod 777
 /home/test/etc/ssl/certs/408e388a.0
chmod 777
 /home/test/etc/ssl/certs/412bea73.0
chmod 777
 /home/test/etc/ssl/certs/4166ec0c.0
chmod 777
 /home/test/etc/ssl/certs/4184de39.0
chmod 777
 /home/test/etc/ssl/certs/4643210f.0
chmod 777
 /home/test/etc/ssl/certs/47996b5c.0
chmod 777
 /home/test/etc/ssl/certs/4d654d1d.0
chmod 777
 /home/test/etc/ssl/certs/4fbd6bfa.0
chmod 777
 /home/test/etc/ssl/certs/54edfa5d.0
chmod 777
 /home/test/etc/ssl/certs/594f1775.0
chmod 777
 /home/test/etc/ssl/certs/5aba72f7
chmod 777
 /home/test/etc/ssl/certs/5aba72f7.0
chmod 777
 /home/test/etc/ssl/certs/5cf9d536.0
chmod 777
 /home/test/etc/ssl/certs/5ed36f99.0
chmod 777
 /home/test/etc/ssl/certs/5f5e5caa.0
chmod 777
 /home/test/etc/ssl/certs/61f6c934.0
chmod 777
 /home/test/etc/ssl/certs/6c55cf77.0
chmod 777
 /home/test/etc/ssl/certs/6e8bf996.0
chmod 777
 /home/test/etc/ssl/certs/6f5d9899.0
chmod 777
 /home/test/etc/ssl/certs/6fcc125d.0
chmod 777
 /home/test/etc/ssl/certs/709afd2b.0
chmod 777
 /home/test/etc/ssl/certs/72bf6a04.0
chmod 777
 /home/test/etc/ssl/certs/72fa7371.0
chmod 777
 /home/test/etc/ssl/certs/731f03a5.0
chmod 777
 /home/test/etc/ssl/certs/74c26bd0.0
chmod 777
 /home/test/etc/ssl/certs/755f7420.0
chmod 777
 /home/test/etc/ssl/certs/75680d2e.0
chmod 777
 /home/test/etc/ssl/certs/7651b327.0
chmod 777
 /home/test/etc/ssl/certs/788c9bfc.0
chmod 777
 /home/test/etc/ssl/certs/7999be0d.0
chmod 777
 /home/test/etc/ssl/certs/7d3cd826.0
chmod 777
 /home/test/etc/ssl/certs/7d453d8f.0
chmod 777
 /home/test/etc/ssl/certs/819a45f6.0
chmod 777
 /home/test/etc/ssl/certs/8470719d.0
chmod 777
 /home/test/etc/ssl/certs/86f32474.0
chmod 777
 /home/test/etc/ssl/certs/8f7b96c4.0
chmod 777
 /home/test/etc/ssl/certs/8fe643df.0
chmod 777
 /home/test/etc/ssl/certs/95750816.0
chmod 777
 /home/test/etc/ssl/certs/97b4211c.0
chmod 777
 /home/test/etc/ssl/certs/9ec3a561.0
chmod 777
 /home/test/etc/ssl/certs/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/AOL_Time_Warner_Root_Certification_Authority_1.pem
chmod 777
 /home/test/etc/ssl/certs/AOL_Time_Warner_Root_Certification_Authority_2.pem
chmod 777
 /home/test/etc/ssl/certs/AddTrust_External_Root.pem
chmod 777
 /home/test/etc/ssl/certs/AddTrust_Low-Value_Services_Root.pem
chmod 777
 /home/test/etc/ssl/certs/AddTrust_Public_Services_Root.pem
chmod 777
 /home/test/etc/ssl/certs/AddTrust_Qualified_Certificates_Root.pem
chmod 777
 /home/test/etc/ssl/certs/America_Online_Root_Certification_Authority_1.pem
chmod 777
 /home/test/etc/ssl/certs/America_Online_Root_Certification_Authority_2.pem
chmod 777
 /home/test/etc/ssl/certs/Baltimore_CyberTrust_Root.pem
chmod 777
 /home/test/etc/ssl/certs/Certum_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Comodo_AAA_Services_root.pem
chmod 777
 /home/test/etc/ssl/certs/Comodo_Secure_Services_root.pem
chmod 777
 /home/test/etc/ssl/certs/Comodo_Trusted_Services_root.pem
chmod 777
 /home/test/etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_1.pem
chmod 777
 /home/test/etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_2.pem
chmod 777
 /home/test/etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_3.pem
chmod 777
 /home/test/etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_4.pem
chmod 777
 /home/test/etc/ssl/certs/Entrust.net_Global_Secure_Personal_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Entrust.net_Global_Secure_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Entrust.net_Premium_2048_Secure_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Entrust.net_Secure_Personal_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Entrust.net_Secure_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Equifax_Secure_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Equifax_Secure_Global_eBusiness_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Equifax_Secure_eBusiness_CA_1.pem
chmod 777
 /home/test/etc/ssl/certs/Equifax_Secure_eBusiness_CA_2.pem
chmod 777
 /home/test/etc/ssl/certs/GTE_CyberTrust_Global_Root.pem
chmod 777
 /home/test/etc/ssl/certs/GTE_CyberTrust_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/GeoTrust_Global_CA.pem
chmod 777
 /home/test/etc/ssl/certs/GlobalSign_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_CLASE1_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_CLASE3_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_CLASEA1_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_CLASEA3_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_Chained_CAs_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_Servidores_root.pem
chmod 777
 /home/test/etc/ssl/certs/IPS_Timestamping_root.pem
chmod 777
 /home/test/etc/ssl/certs/QuoVadis_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/QuoVadis_Root_Certification_Authority.pem
chmod 777
 /home/test/etc/ssl/certs/RSA_Root_Certificate_1.pem
chmod 777
 /home/test/etc/ssl/certs/RSA_Security_1024_v3.pem
chmod 777
 /home/test/etc/ssl/certs/RSA_Security_2048_v3.pem
chmod 777
 /home/test/etc/ssl/certs/Security_Communication_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Sonera_Class_1_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Sonera_Class_2_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Staat_der_Nederlanden_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/TC_TrustCenter__Germany__Class_2_CA.pem
chmod 777
 /home/test/etc/ssl/certs/TC_TrustCenter__Germany__Class_3_CA.pem
chmod 777
 /home/test/etc/ssl/certs/TDC_Internet_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/TDC_OCES_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Personal_Basic_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Personal_Freemail_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Personal_Premium_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Premium_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Thawte_Time_Stamping_CA.pem
chmod 777
 /home/test/etc/ssl/certs/UTN-USER_First-Network_Applications.pem
chmod 777
 /home/test/etc/ssl/certs/UTN_DATACorp_SGC_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/UTN_USERFirst_Email_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/UTN_USERFirst_Hardware_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/UTN_USERFirst_Object_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/ValiCert_Class_1_VA.pem
chmod 777
 /home/test/etc/ssl/certs/ValiCert_Class_2_VA.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_1_Public_Primary_OCSP_Responder.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_2_Public_Primary_OCSP_Responder.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_3_Public_Primary_OCSP_Responder.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_RSA_Secure_Server_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Secure_Server_OCSP_Responder.pem
chmod 777
 /home/test/etc/ssl/certs/Verisign_Time_Stamping_Authority_CA.pem
chmod 777
 /home/test/etc/ssl/certs/Visa_International_Global_Root_2.pem
chmod 777
 /home/test/etc/ssl/certs/Visa_eCommerce_Root.pem
chmod 777
 /home/test/etc/ssl/certs/a145806c.0
chmod 777
 /home/test/etc/ssl/certs/a15b3b6b.0
chmod 777
 /home/test/etc/ssl/certs/a2df7ad7.0
chmod 777
 /home/test/etc/ssl/certs/a3896b44.0
chmod 777
 /home/test/etc/ssl/certs/a6776c69.0
chmod 777
 /home/test/etc/ssl/certs/a7605362.0
chmod 777
 /home/test/etc/ssl/certs/aaa45464.0
chmod 777
 /home/test/etc/ssl/certs/b0f3e76e.0
chmod 777
 /home/test/etc/ssl/certs/b3fec4ff.0
chmod 777
 /home/test/etc/ssl/certs/b5f329fa.0
chmod 777
 /home/test/etc/ssl/certs/b8609e8a.0
chmod 777
 /home/test/etc/ssl/certs/bcdd5959.0
chmod 777
 /home/test/etc/ssl/certs/bda4cc84.0
chmod 777
 /home/test/etc/ssl/certs/beTRUSTed_Root_CA-Baltimore_Implementation.pem
chmod 777
 /home/test/etc/ssl/certs/beTRUSTed_Root_CA.pem
chmod 777
 /home/test/etc/ssl/certs/beTRUSTed_Root_CA_-_Entrust_Implementation.pem
chmod 777
 /home/test/etc/ssl/certs/beTRUSTed_Root_CA_-_RSA_Implementation.pem
chmod 777
 /home/test/etc/ssl/certs/bf87590f.0
chmod 777
 /home/test/etc/ssl/certs/brasil.gov.br.pem
chmod 777
 /home/test/etc/ssl/certs/c19d42c7.0
chmod 777
 /home/test/etc/ssl/certs/c215bc69.0
chmod 777
 /home/test/etc/ssl/certs/c33a80d4.0
chmod 777
 /home/test/etc/ssl/certs/c527e4ab.0
chmod 777
 /home/test/etc/ssl/certs/c9bc75ba.0
chmod 644
 /home/test/etc/ssl/certs/ca-certificates.crt
chmod 777
 /home/test/etc/ssl/certs/cacert.org.pem
chmod 777
 /home/test/etc/ssl/certs/ccb919f9.0
chmod 777
 /home/test/etc/ssl/certs/cdaebb72.0
chmod 777
 /home/test/etc/ssl/certs/d2adc77d.0
chmod 777
 /home/test/etc/ssl/certs/d537fba6.0
chmod 777
 /home/test/etc/ssl/certs/d78a75c7.0
chmod 777
 /home/test/etc/ssl/certs/d8274e24.0
chmod 777
 /home/test/etc/ssl/certs/ddc328ff.0
chmod 777
 /home/test/etc/ssl/certs/e268a4c5.0
chmod 777
 /home/test/etc/ssl/certs/e28f6bbc.0
chmod 777
 /home/test/etc/ssl/certs/e7b8d656.0
chmod 777
 /home/test/etc/ssl/certs/ed049835.0
chmod 777
 /home/test/etc/ssl/certs/ed524cf5.0
chmod 777
 /home/test/etc/ssl/certs/ed62f4e3.0
chmod 777
 /home/test/etc/ssl/certs/f3cf1e8e.0
chmod 777
 /home/test/etc/ssl/certs/f4996e82.0
chmod 777
 /home/test/etc/ssl/certs/f64d9715.0
chmod 777
 /home/test/etc/ssl/certs/f73e89fd.0
chmod 777
 /home/test/etc/ssl/certs/f950ccc2.0
chmod 777
 /home/test/etc/ssl/certs/ff783690.0
chmod 777
 /home/test/etc/ssl/certs/signet_ca1_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_ca2_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_ca3_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_ocspklasa2_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_ocspklasa3_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_pca2_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_pca3_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_rootca_pem.pem
chmod 777
 /home/test/etc/ssl/certs/signet_tsa1_pem.pem
chmod 777
 /home/test/etc/ssl/certs/spi-ca.pem
chmod 644
 /home/test/etc/ssl/certs/ssl-cert-snakeoil.pem
chmod 644
 /home/test/etc/ssl/openssl.cnf
chmod 710
 /home/test/etc/ssl/private
chmod 644
 /home/test/etc/sysctl.conf
chmod 644
 /home/test/etc/syslog.conf
chmod 755
 /home/test/etc/terminfo
chmod 644
 /home/test/etc/terminfo/README
chmod 644
 /home/test/etc/ucf.conf
chmod 755
 /home/test/etc/udev
chmod 755
 /home/test/etc/udev/rules.d
chmod 644
 /home/test/etc/udev/rules.d/00-init.rules
chmod 644
 /home/test/etc/udev/rules.d/11-hplj10xx.rules
chmod 644
 /home/test/etc/udev/rules.d/20-names.rules
chmod 644
 /home/test/etc/udev/rules.d/25-iftab.rules
chmod 644
 /home/test/etc/udev/rules.d/40-permissions.rules
chmod 644
 /home/test/etc/udev/rules.d/45-hplip.rules
chmod 644
 /home/test/etc/udev/rules.d/45-libgphoto2.rules
chmod 644
 /home/test/etc/udev/rules.d/45-libsane.rules
chmod 644
 /home/test/etc/udev/rules.d/60-symlinks.rules
chmod 644
 /home/test/etc/udev/rules.d/65-persistent-input.rules
chmod 644
 /home/test/etc/udev/rules.d/65-persistent-storage.rules
chmod 644
 /home/test/etc/udev/rules.d/80-programs.rules
chmod 644
 /home/test/etc/udev/rules.d/85-alsa.rules
chmod 644
 /home/test/etc/udev/rules.d/85-hal.rules
chmod 644
 /home/test/etc/udev/rules.d/85-hdparm.rules
chmod 644
 /home/test/etc/udev/rules.d/85-hwclock.rules
chmod 644
 /home/test/etc/udev/rules.d/85-ifupdown.rules
chmod 644
 /home/test/etc/udev/rules.d/85-pcmcia.rules
chmod 644
 /home/test/etc/udev/rules.d/90-modprobe.rules
chmod 644
 /home/test/etc/udev/rules.d/99-udevmonitor.rules
chmod 644
 /home/test/etc/udev/rules.d/README
chmod 644
 /home/test/etc/udev/udev.conf
chmod 644
 /home/test/etc/uniconf.conf
chmod 755
 /home/test/etc/update-notifier
chmod 644
 /home/test/etc/updatedb.conf
chmod 644
 /home/test/etc/usplash.conf
chmod 755
 /home/test/etc/vim
chmod 644
 /home/test/etc/vim/vimrc
chmod 644
 /home/test/etc/vim/vimrc.tiny
chmod 644
 /home/test/etc/vnc.conf
chmod 755
 /home/test/etc/w3m
chmod 644
 /home/test/etc/w3m/config
chmod 644
 /home/test/etc/w3m/mailcap
chmod 644
 /home/test/etc/wgetrc
chmod 755
 /home/test/etc/wpa_supplicant
chmod 755
 /home/test/etc/wpa_supplicant/ifupdown.sh
chmod 640
 /home/test/etc/wvdial.conf
chmod 755
 /home/test/etc/xml
chmod 644
 /home/test/etc/xml/catalog
chmod 644
 /home/test/etc/xml/catalog.old
chmod 644
 /home/test/etc/xml/docbook-xml.xml
chmod 644
 /home/test/etc/xml/docbook-xml.xml.old
chmod 644
 /home/test/etc/xml/scrollkeeper.xml
chmod 644
 /home/test/etc/xml/sgml-data.xml
chmod 644
 /home/test/etc/xml/sgml-data.xml.old
chmod 644
 /home/test/etc/xml/xml-core.xml
chmod 644
 /home/test/etc/xml/xml-core.xml.old
ubuntu@ubuntu:~$ 




i see some errors appeared

---

### Post by CD27 on 2008-03-16
of course, I didn't run that as root either...woops! here's the same thing in root:


ubuntu@ubuntu:~$ sudo (for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /media/had1$FILE" ; done) |/bin/bash
bash: syntax error near unexpected token `for'
ubuntu@ubuntu:~$ 



ubuntu@ubuntu:~$ sudo for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /home/test$FILE" ; done
bash: syntax error near unexpected token `do'
ubuntu@ubuntu:~$

---

### Post by CD27 on 2008-03-16
whenever I try to regular boot, this is what I get:

udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:17
udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:45
udved:[2497] lookup_group:specified group 'nvram' unknown
Udved:[2497]: add_to_rules: do not reference parent sysfs directories directly, that may break with a future kernel, please fix it in /etc/vdev/rules.d/65-persistent-storage.rules:12


I forget if those are "udevd" or "udved".

---

### Post by CD27 on 2008-03-16
don't know how much it'll help, but, "bump"

---

### Post by CD27 on 2008-03-16
this thread looks like it has merged back with the other thread now, so I'm linking it to there, all further posts here should go in the other thread:

[http://ubuntuforums.org/showthread.php?t=725209&page=4](http://ubuntuforums.org/showthread.php?t=725209&page=4)

---

### Post by yabbadabbadont on 2008-03-16
You would already have a working system by now if you had reinstalled as suggested yesterday....  :roll:

---

### Post by CD27 on 2008-03-16
It's not happening. I refuse to reinstall, i want to fix the problem.

---

### Post by hyperair on 2008-03-16
Use this:
```

#!/usr/bin/python

mountdir='/media/root/';

import os,sys;

def copypermissions(src,dest):
sys.stdout.write(src + ".....");
	try:
		os.chmod(dest,os.stat(src).st_mode);
		print "OK";
	except:
		print "FAIL";

copypermissions('/etc',os.path.join(mountdir,'/etc'));

for root,dirs,files in os.walk("/etc"):
	for f in files:
		src = os.path.join(root,f);
		dest = os.path.join(mountdir,src);
		
		if (os.path.exists(dest)):
			copypermissions(src,dest);
	for d in dirs:
		src = os.path.join(root,d):
		dest = os.path.join(mountdir,src):
		
		if (os.path.exists(dest)):
			copypermissions(src,dest);

```

Replace "/media/root/" with the appropriate path of your installation's root directory.

Use the text editor, save it on the LiveCD desktop, give the file execute permissions (right click->properties->permissions). Double click on it and click run in terminal.

This script looks at each file's permissions in /etc of the LiveCD and copies them over to the installation's /etc. This should fix your problem.

---

### Post by danwood76 on 2008-03-16
It is the best way to fix the problem, it will also give you a nice fresh clean install.
You will probably be able to dump the installed software list whilst using the chroot command so you would get all your software back.

So mount your drive to say /media/foo then

```

chroot /media/foo
sudo dpkg --get-selections | grep '[[:space:]]install$=' \| awk '{print $1}' > package_list

```
save the file package_list (which will be in the root of the /media/foo directory) to your external drive for re importing later.

Reinstall is the best and only way to ensure a complete working system IMO.

Also you've already destroyed all your settings on the system (thats whats contained in the /etc folder) so you dont have a lot else to loose.
The best thing to do is have your home directory on a seperate partition that way reinstalls are really easy as youy will never loose your stuff.

Just remember that the permissions for each directory are set that way for a reason and changing them will break your system or create security holes.

[http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/)
That guide will show you how to re import the software list, you will need to enable the repositories you had enabled before.

---

### Post by koenn on 2008-03-16
> /bin/bash: line 3838:** /media/had1/**etc/ssl/certs/ValiCert_Class_2_VA.pem: No such file or directory
chmod: missing operand after `777'
Try `chmod --help' for more information.
/bin/bash: line 3840: /media/had1/etc/ssl/certs/Verisign_Class_1_Public_ Primary_Certification_Authority.pem: No such file or directory
chmod: missing operand after `777'

1/  /media/had1 is wrong,  it's probably /media/h**da**1 but you should actually verify that 

2/ you need to be root. It's complicated to run such a long command with pipes ( | ) through sudo. 
To become root, do ```
sudo -i 
```, then run the command

3/ I'm not sure where the "chmod: missing operand after `777'" comes from. Maybe it'll disappear if you fix 1/ and 2/. I didn't get that error when i did  a testrun here.
Note that the (for ... done) part of the statement builds a command line like
chmod 755 /media/hda1/etc/some_file , which is then passed to /bin/bash for execution.
you may have removed a space somewhere, or put in a line break by accident ?

---

### Post by koenn on 2008-03-16
> **yabbadabbadont said:**
> You would already have a working system by now if you had reinstalled as suggested yesterday....  :roll:
yeah, but where's the fun in that ?

---

### Post by koenn on 2008-03-16
Had another look at those commands - they still work for me :
```


## messed up /etc in /home/test
root@kix:/home# /ls -Ral /home/test/etc/ 
...

/home/test/etc/X11/xkb/geometry/sgi_vndr:
drwxrwxrwx 2 root root  4096 2008-03-15 23:59 .
drwxrwxrwx 5 root root  4096 2008-03-15 23:59 ..
-rwxrwxrwx 1 root root 10457 2008-03-15 23:59 indigo
-rwxrwxrwx 1 root root 15030 2008-03-15 23:59 indy
...


## dry run, no op
root@kix:/home# for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /home/test$FILE" ; done
...
chmod 755 /home/test/etc/X11/xkb/geometry/sgi_vndr
chmod 644 /home/test/etc/X11/xkb/geometry/sgi_vndr/indy
chmod 644 /home/test/etc/X11/xkb/geometry/sgi_vndr/indigo
...


## fix and check
root@kix:/home# (for FILE in $(find /etc); do echo -n  "chmod " ; stat -c %a $FILE ; echo " /home/test$FILE" ; done) |/bin/bash
root@kix:/home# ls -Ral /home/test/etc/ 
...
/home/test/etc/X11/xkb/keycodes/sgi_vndr:
drwxr-xr-x 2 root root 4096 2008-03-15 23:59 .
drwxr-xr-x 4 root root 4096 2008-03-15 23:59 ..
-rw-r--r-- 1 root root 2368 2008-03-15 23:59 indigo
-rw-r--r-- 1 root root 3743 2008-03-15 23:59 indy

...


```

---

### Post by CD27 on 2008-03-16
To update with you guys. I had a little help by "JediProgrammer" just about all day today. We were instant messageing and we did a lot of pretty cool things with the system, but ultimately, it was almost impossible to fix. We solved the udev issues, we solved the rules issues, we even solved the user and password issues, but when it finally came down to it, we simply couldn't get it to actually mount the hard drive. It could see it, but for some reason it simply wouldn't mount it.

Evently I decided to give up and just take the step of reinstalling Linux (:() though some people think that was the best thing to do to begin with, I think it was the first step of failure. I don't want to give up and reinstall, I wanted to actually solve the issue. I simply look at this as a failure on my part. This crash certainly was severe due to such a small thing. All I did was give the /etc directory read and write rights on all three categories and checked the "apply to all subcategories". THTA'S IT.

simply enough, we couldn't fix the problem, and JediProgrammer, thank you so much for your help. You didn't have to take all that time to do all that work, but you did, thank you. If there is not one already, I would like to move for the request that there be a full manual written on this kind of crash, giving the /etc directory unacceptable rights. This crashed my ENTIRE system, top to bottom and unless you REALLY know what you're doing, you're not gonna fix it.

Thank you people for helping me as well, and for lending me your services. If there is any way, I would like to ask one more question, I backed up my files on a list (dpkglist.txt), but i'm unable to figure out the code to get it to install them all again. when i put in sudo dpkg --set-selections < dpkglist.txt, but it didn't really do anything.

---

### Post by hyperair on 2008-03-16
Use apt-get instead:
```

sudo xargs -d \\n -a dpkglist.txt apt-get install

```


p.s. I wish you had tried the Python script I put up. It might have helped matters. =\

---

### Post by Zill on 2008-03-16
> **CD27 said:**
> ... If there is not one already, I would like to move for the request that there be a full manual written on this kind of crash, giving the /etc directory unacceptable rights. This crashed my ENTIRE system, top to bottom and unless you REALLY know what you're doing, you're not gonna fix it.
I don't know how much you know about Free and Open Source software such as Ubuntu Linux but the idea is that we all contribute in whatever way we can.

You have discovered a dropoff in the documentation.  So, if you want to help others avoid the same pitfalls, feel free to write up a suitable document which could then be published within the Ubuntu Wiki help system.

---

### Post by hyperair on 2008-03-16
Better yet, create an article on what NOT to do on Ubuntu. Messing up your /etc folder is like screwing around with your Windows registry. To me it seems like common sense not to mess the permissions of that folder up, but to a newcomer, probably not.

---

### Post by koenn on 2008-03-16
> **CD27 said:**
> This crash certainly was severe due to such a small thing. All I did was give the /etc directory read and write rights on all three categories and checked the "apply to all subcategories". THTA'S IT.

It's not as "small" as you seem to think. /etc holds all system and application configuration, so, as hyperair pointed out,  it's similar in function to the Windows Registry.
Does the following sound familiar ?
> Warning - Serious problems might occur if you modify the registry incorrectly by using Registry Editor or by using another method. These problems might require that you reinstall the operating system. Microsoft cannot guarantee that these problems can be solved. Modify the registry at your own risk.

---

### Post by CD27 on 2008-03-16
I was actually thinking about that. In fact, I think I'll try and work on something about what NOT to do with Ubuntu Linux, but i'll need some things from other users, experiences, events that totally crashed their computers, things like what I did, that i as a newcomer simply did not know and really didn't have much of a warning (asking a password is hardly a warning :| to me). So, i'll start a new thread about what NOT to do in Ubuntu Linux and see if i can't get it publised once i've written the article.

---

