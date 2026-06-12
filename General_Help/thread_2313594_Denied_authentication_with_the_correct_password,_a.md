---
title: "Denied authentication with the correct password, after setup of Auto-Login!"
date: 2016-02-13
forum: General Help
---

### Post by Shobuz99 on 2016-02-13
I'm not new to Ubuntu; but I am new to 14.04.3 LTS (I used 10.04 LTS for way too long...)

It appears I've somehow managed to "lock" myself out of authenticating anything I want to do;
such as access the gufw firewall, update my user accounts section, access my synaptic package, or even use sudo for anything.
Upon installation, I chose an encrypted pass phrase as extra security; which works fine on boot.
I also created a password to enter screen.
The password I created two days ago has worked fine up until I decided to setup auto-login.
Then my troubles began and I'm really at a loss to figure out how to get in.
As I said, my password for authentication is not successful any more. I don't know why.
I have forgotten a lot of what I did years ago, to set up Ubuntu the way I wanted it.
I'm stuck now, unless there is a way to get to Root and fix it..
Can anyone help? Is it something simple?
Please tell me what information you need me to provide, so i can go forward and fix this dumb mistake of mine.

Thank you very much
Shobuz99

---

### Post by Bucky Ball on 2016-02-14
Switch off auto-login and [then this]("http://www.psychocats.net/ubuntu/resetpassword")? A suggestion.

If you have auto-login switched on, when do you get the chance to enter your password, or your password no longer works when using stuff on the desktop?

On a side note, how did you get from 10.04 to 14.04? Clean install or via net to 12.04> 14.04? The latter can be fraught with danger as there's been a lot of changes since 10.04, as you can see. ;)

---

### Post by oldos2er on 2016-02-14
> **Shobuz99 said:**
> It appears I've somehow managed to "lock" myself out of authenticating anything I want to do;
such as access the gufw firewall, update my user accounts section, access my synaptic package, or even use sudo for anything.
Upon installation, I chose an encrypted pass phrase as extra security; 

If you mean to say you have an encrypted /home partition, this is known: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/353446/comments/2](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/353446/comments/2)

This is old too but contains some relevant information: 
[http://askubuntu.com/questions/11240/why-is-the-automatic-login-disabled-for-users-with-encrypted-home](http://askubuntu.com/questions/11240/why-is-the-automatic-login-disabled-for-users-with-encrypted-home)

---

### Post by Shobuz99 on 2016-02-14
> **Bucky Ball said:**
> Switch off auto-login and [then this]("http://www.psychocats.net/ubuntu/resetpassword")? A suggestion.

If you have auto-login switched on, when do you get the chance to enter your password, or your password no longer works when using stuff on the desktop?

On a side note, how did you get from 10.04 to 14.04? Clean install or via net to 12.04> 14.04? The latter can be fraught with danger as there's been a lot of changes since 10.04, as you can see. ;)

I will try your suggestions. Thank you. 
If I try to Unlock the User Accounts to switch off Auto-Login, it asks me for my password to authenticate.
When I type in the correct pw it fails. and says "Your authentication attempt was unsuccessful. Please try again."
When I have done this 3 times it stops giving me that message, but the "unlock" icon is still visible, meaning it's not unlocked.

I can still use everything on my desktop unless I need to authenticate with my password. 
I'm wondering if there is a "sudo command that will allow me to fix this?

Side note answer: I chose a clean install on an empty 160GB SATA drive that I had previously stored hundreds of MP3 files.
Once I did that, I decided to try 14.04 LTS. So I downloaded the distro and installed it.
First time through I messed up and didn't connect to the internet, immediately with a cable. 
But I did connect it during the jump to "install", from "Try it".
I didn't realize that wifi was not working with the CD in "Try Ubuntu" mode.
At that point the packages didn't completely install and the machine hung up. 
So I went back and re-formatted the drive as "empty" and the went through the whole process from the beginning
and made sure I had the laptop connected to my router via a CAT5 cable.
That time it worked flawlessly. I was extremely happy.
I chose the additional security of using an encrypted passphrase to get into the machine upon boot.
Then I created a password and all the necessary things to get it going. 
During the course of my happiness, I decided to try and install X11vnc to my machine.
I have a home network that connects 9 devices at any given time.
That install went well; but I had trouble with the server portion. I could view other devices with ssvnc,
But I couldn't connect to my 14.04 LTS machine from any other device, Windows or not (I still have an old Dell 1300 using 10.04 LTS)
I thought that I needed to adjust my gufw firewall, that I installed on my 14.04 LTS to make a rule to ALLOW the other devices
to connect based on their IP address, i.e. 192.168.xxx.xxx, etc.It didn't work.
Subsequently, I turned to the idea that the password access was blocking the ssvnc viewer from getting in.
I now think I was very wrong about that; but as I continued to search for an answer on the x11vnc and ssvnc forums,
I got frustrated and decided to change my machine to Auto-Logon no password required....and the rest I think you know already.

In summary, I have fouled this up beyond my own recognition. It's all my fault for being so anxious to use 14.04 LTS
the same way I used 10.04 LTS, and ignoring what must be some significant changes that have occurred.

Sorry for the long reply. I should have read your message here, before I sent you a reply to your PM's.
Again, apologies to you for all my mistakes. 

Shobuz99

---

### Post by Shobuz99 on 2016-02-14
hi oldos2er
Thank you, I'll try your suggestions and check out the links you sent.
Thank you for your help. :-)

Shobuz99

---

### Post by Shobuz99 on 2016-02-14
oldos2er,
I re-read your post after i checked out both links. I think I need to shut off Auto-Login,
using a sudo command to Root, before I can change my password. Otherwise I don't think it will work.
I say "think" because I'm afraid I might "dig my hole deeper" by doing the process recommended in
the link you suggested. That link, does not suggest that Auto-Login is running. 
Only that someone needs to change their password.

So if there is a way to actually undo the Auto-Login via Sudo "something", maybe I can then go and change the pw and fix it?

Thank you again for your help.
Shobuz99

---

### Post by oldos2er on 2016-02-14
If you boot into recovery mode from the grub menu, you can disable autologin from there without needing a password. If you're already booted into your system, you should change your password first.

You've successfully changed your password; now reboot into recovery mode, choose 'Drop to root shell.' Run ```
mount -o rw,remount /[code] to mount the root partition in read/write mode. Now run [code]nano /etc/lightdm/lightdm.conf.d/50-myconfig.conf
``` and delete the autologin-user line. If you boot normally now autologin should be disabled.

---

### Post by Shobuz99 on 2016-02-14
I lost my reply to you Oldos2er, but I'll be brief.. _It Worked_!!! 
I should've posted my reply before I marked it "Solved", but I didn't and I lost the first reply. Thank you.
Very quickly - I had one thing happen during my attempt to disable auto-login. 
The file ```
 myconfig.conf 
``` was Empty!
This puzzled me and I thought I had broken something worse than I could imagine...
As it turned out, I was able to change my password using the ```
 mount -o rw,remount / 
```
and then once I went through that process I rebooted again to "recovery mode" and went into
the ```
 myconfig.conf 
``` file AND it was STILL Empty!!
This rattled me; but I exited without saving and proceeded.
Next I booted normally and immediately went to the User Accounts feature and to my delight,
I was able to log in with my new password. Then I was able to shut off Auto-Login.
So in essence, it all worked with just that one quick. I am curious why the "myconfig" file was empty AND a New File!!?
Should it have been an existing file? I wonder.
Nevertheless, I am back and everyone's help; most especially yours, has got my problem solved.
Thank you very much!
BTW... I'm an old OS/2 user too. I also worked at IBM in Endicott, NY for 28.5 years. But I digress too quickly... :-)
best,
Shobuz99

---

### Post by oldos2er on 2016-02-15
You are welcome!

I still miss OS/2's Workplace Shell, wish there was something object-oriented like it for Linux.

---

### Post by Shobuz99 on 2016-02-15
I've thought about that too...but not for long. 
If Time Travel was possible, I'd be disappointed in the s l o w  p r o c e s s o r  speed when running any of the Windows
or OS/2 platforms back then. I did always like the way OS/2 "looked" much better than Windows at the time...
The OS/2 gui was much better for that time, too.
The early 1990's were a great time for me, in IBM and out; because I learned how to build my own 386 PC and run Windows 3.1 on it.
And then came Windows 95 and my head exploded, because IBM bought me an Aptiva with Win95 on it, and Howie Mandel's voice overs
for the help files!! LOL!
I remember buying memory at computer shows and envying the IS guys at work, that could afford a new machine with OS/2 instead of Windows.
Those were the days, my friend. ;-) 
thanks again for your help.
Shobuz99

---

