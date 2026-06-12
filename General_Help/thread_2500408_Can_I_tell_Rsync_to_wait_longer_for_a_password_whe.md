---
title: "Can I tell Rsync to wait longer for a password when connecting to a remote system?"
date: 2024-09-01
forum: General Help
---

### Post by goemonburo on 2024-09-01
I know this might not be specifically an Ubuntu question, it's more a bash shell or rsync question, but I'm really hoping someone can help.  

I have a shell script to backup my system and it uses rsync to first go to all three places and synchronize them with a central location, then the script uses Duplicity to back the central location (with all the newly refreshed files/folders), to another drive that's stored physically offsite.  

It works well but I have a problem in that if I don't happen to be sitting at the computer when it heads to a new system and requires password input, it times out, so that when I enter the password (after finally returning as seeing it needed it), instead of entering THAT system it just throws an error and moves to the NEXT system, skipping the one that was overlooked.  

Is there a way to tell Rsync to wait longer for a password (like a day?) before treating it as timed out?  

Thank you!

---

### Post by currentshaft on 2024-09-01
If you're using ssh as the rsync transport mechanism, you should be using public-key authentication instead of passwords.

---

### Post by Doug S on 2024-09-01
Wouldn't it be the login grace time for sshd? which can be set in /etc/ssh/sshd_config or via the command line:

```
       -g login_grace_time
               Gives the grace time for clients to authenticate themselves (default 120 seconds).  If the client fails to authenticate the user within this many seconds, the server disconnects and exits.  A value of zero indicates no limit.
```

I didn't try it and I don't know if something else might timeout in the tcp connection state also.

---

### Post by aljames2 on 2024-09-01
I’m not sure what the point is of using a script to run a backup scheme where passwords are required. As mentioned, SSH Key based authentication without passwords would be the way to connect between hosts. 

If instead the password query is coming from trying to run an elevated rsync command, there is a way to configure an elevated user account to run only rsync, without a password. I tend to disable root login on my hosts and instead use a specific user account to run this single elevated command that I need for backing up. That command can be configured to run without a password over a key based SSH connection. I have several scripts that are launched by cron to do my pulls. I just have to make sure the computers are on, which they usually are.

---

### Post by goemonburo on 2024-09-01
I'm afraid I'll need a little more help assuming anyone has the time, as the ssh-keygen seems to be taking me away from what I'm trying to do.  1)  I am backing up several different users onto a system that doesn't include those users.  So I ran into issues using ssh-keygen because most of the instructions seem to assume you're backing up "userX" on one system to "userX" on the remote one.  In this case I'm backing up "userX, userY, userZ" to a folder on UserB's system, then backing up UserB.  

When I tried making a key for UserX, UserY, and UserZ I got an error that a key already exists.  So maybe that's the most elegant way to accomplish this but it seems to veer me into a different thing.

I know there may be other ways to do this but to be honest, the easiest seemed to be just giving me a bit more time to enter the password, which was my question.   Would anyone know if this is possible?

---

### Post by aljames2 on 2024-09-01
If your method has been working as you need, except for this password timing issue, did you investigate/try the suggestion provided by @Doug S

---

### Post by goemonburo on 2024-09-02
> **aljames2 said:**
> If your method has been working as you need, except for this password timing issue, did you investigate/try the suggestion provided by @Doug S

Thank you, no, somehow I skipped over that and hadn't seen it.  I don't know if it's an ssh or an rsync issue.  Is this something I set on my side or does it need to be set in each of the locations as well?

---

### Post by dragonfly41 on 2024-09-02
> [COLOR=#000000]the easiest seemed to be just giving me a bit more time to enter the password, which was my question. Would anyone know if this is possible?
If time (or other condition) is what you want then a simple use of Actiona a UI emulator will paste in a variable such as password at a given date/time - like cron but with widgets.[/COLOR]

---

### Post by TheFu on 2024-09-02
There are timeout periods for all tcp connections set in the kernel.  Trying to keep connections open too long will eat resources and eventually, no new network connections will be possible.  There have been tcp attacks abusing this part of the tcp protocol, so most systems are setup with less than 3 minutes before a connection timeout happens.  

Probably just best to run the **rsync** when you are there or leaving the system and can enter the password, if you aren't willing to setup ssh-keys.  Using ssh-keys is the normal solution method.  It is 2 commands.  ssh-keygen and ssh-copy-id.  Normally, backups need to be performed as root to maintain the correct timestamps and permissions.

---

### Post by goemonburo on 2024-09-03
Thank you all for the info.  I've tried to adjust the timeout variable (both on my local and remote machines) and it doesn't seem to work.  Do I need to source the config after adjusting that variable?

I appreciate the suggestions.  Probably will try the ssh-keygen method if I can't get more time from the login timeout.  Seems very complicated, though.

---

### Post by Doug S on 2024-09-03
It seemed to work for me. I did it just as a test, but otherwise agree with the comments from the others.
Anyway, I changed the sshd_config file as so:

```

doug@s19:~/config/etc/ssh$ diff -u sshd_config.24.04.original sshd_config
--- sshd_config.24.04.original  2024-09-02 10:58:17.367097735 -0700
+++ sshd_config 2024-09-03 20:11:45.040473573 -0700
@@ -29,7 +29,7 @@

 # Authentication:

-#LoginGraceTime 2m
+LoginGraceTime 1440m
 #PermitRootLogin prohibit-password
 #StrictModes yes
 #MaxAuthTries 6
doug@s19:~/config/etc/ssh$

```

And the connection status while the client rsync waits for the password:

```

doug@s19:/media/backup/backup/rpi3$ ss -o -t
State   Recv-Q   Send-Q Local Address:Port     Peer Address:Port           Process
ESTAB 0           52         192.168.111.136:ssh 192.168.111.122:54934 timer:(on,232ms,0)
ESTAB 0             0         192.168.111.136:ssh 192.168.111.122:63092 timer:(keepalive,119min,0)  [COLOR="#FF0000"]<<< It is this one[/COLOR]
ESTAB 0             0         192.168.111.136:ssh 192.168.111.122:50446 timer:(keepalive,87min,0)
doug@s19:/media/backup/backup/rpi3$

```

I'll edit this later with more entries, but it should wait for a day. I tested shorter timeouts already.

EDIT: The above was about 11 hours ago. I entered the password for the waiting rsync command just now and it worked fine.

---

### Post by goemonburo on 2024-09-04
Well, this is turning into quite the mess.  I've configured passwordless login, for user A and user B on the remote machine, but when I try to run my rsync, it won't allow me to connect as root anymore...and if I can't connect as root, I don't have permissions to sync the files that I need to.  

I think the issue is that a connection is fine if it's from my local machine as a normal user, but not as root.  Do I repeat the passwordless login process AS ROOT as well?  (For example, if I "sudo ssh-keygen" instead of just "ssh-keygen"?!)

Thank you!

---

### Post by TheFu on 2024-09-04
**ssh-keygen** just creates the keys. It has nothing to do with properly placing the key on the remote system, in the correct account.  That's what **ssh-copy-id** does.

If you'd show your work, then we could have corrected the issue already.

Most people would create a different userid and allow that user to run **sudo** commands necessary for their backups without any password.  But you should do it your way, until you get to that point and understand the risks of allowing any remote root access.  I was careful with my wording above.  I didn't say to use root for remote connections.  I said 
 > Normally, backups need to be performed as root
Perhaps I was too subtle in my wording. Sorry.

BTW, it would be a good idea NOT to use RSA ssh-keys.  Use one of the others that are supported, then specifically push those non-RSA public keys to the correct account on the remote system.

---

### Post by goemonburo on 2024-09-04
Thank you for the additional suggestions.  I don't know what "show my work" means, I did do the ssh-keygen and the ssh-copy-id, is there a command to run to show that?  

Anyway, it's a step in the right direction.  Thank you!  I appreciate the help.

---

### Post by TheFu on 2024-09-04
> **goemonburo said:**
>   I don't know what "show my work" means

Remember in math class when you'd just write the answer, "42" and you'd get 50% credit because you didn't show your work?  Same thing.
If you don't show the EXACT commands
AND
the exact output, then you didn't show your work and we don't know what you did wrong or the hard way.

Saying it didn't work, but not showing your work means everyone has to guess.  We are volunteers.  Please don't make helping you so hard.  Helping others is fun for us, but only when it isn't like digging a 30ft hole with a rake would do just as well.

---

### Post by goemonburo on 2024-09-04
Okay, then this is what I did:

ssh-keygen -f keyname

ssh-copy-id -i ~/.ssh/keyname [email]user1@remote.ip.add.here[/email]
ssh-copy-id -i ~/.ssh/keyname [email]user2@remote.ip.add.here[/email]

I can now successfully ssh without authenticating with a password to both user1 and user2.  

But I cannot do that when I'm using "sudo ssh [email]user1@remote.ip.add.here[/email]" I need to do this rsync as sudo so that it correctly accesses the folders and files.  If I run it as a regular user, I get lots of permission errors. 

Now when I try to run the program that used to work fine with "sudo" and prompt me for passwords, it instead says "Permission denied (publickey)."  

Sounds like 1) you'd suggest not having run ssh-keygen as above but instead with one of the other options, and two, to create a separate user with sudo permissions (on the local?  or remote? machine).  

But ideally, I'm guessing that I need to somehow add another key or add the same key to a different place (root? sudo?) so that I can get passwordless authentication while in "sudo."  I might be most of the way there (assuming I stick with RSA).  

Thank you as always for help; I'm certainly not trying to make things difficult for anyone.

---

### Post by TheFu on 2024-09-05
Looks like you are missing the idea that sudo runs programs as a different userid.  

**sudo ls ** will first change to the root userid, change the HOME environment variable to whatever /etc/passwd says that the root userid should use for HOME, then run the '**ls**' command.  It doesn't run root's startup scripts. It doesn't change the directory.  So, in your example, using  **sudo ssh [email]user1@remote.ip.add.here[/email]**, the keys used are pulled from $HOME/.ssh/id_rsa (the default) which is in /root/.ssh/id_rsa ... which isn't what you intended, I'm guessing.  

On the remote machine, you are connecting with user1 ... so it looks in ~user1/.ssh/id_rsa.pub for the matching public key there.   Was that what you wanted?  Really?

BTW, most ssh-based tools will support the "verbosity" option.  To see what is actually being used, just add -v and add more v's to get more verbose debug information.  Normally, -vv is sufficient to understand what isn't working as expected, but -vvv will get enough details that it is usually too much.

I don't see why you'd want to use sudo on the local side, but not on the remote side too?  Call me confused.

---

### Post by goemonburo on 2024-09-05
Thank you for the additional info.

I'm using "sudo" on the local server because when I do that, I don't get floods of error messages about files not being accessible.  I believe that's because the user1 and user2 are different users than user1 on the local machine...but I don't know if that's true.  But that's why I have been doing that.  

It sounds like you're saying that sudo isn't working because it isn't getting a proper key pair.  Could you explain what I need to do to set it up?  Do I need to copy my local user1 key to root on remote system?  Or do I create a root local key and copy it to the root remote?

---

### Post by TheFu on 2024-09-05
sudo used to start the command only impacts the local machine. It has no baring on the remote machine file/directory access.

You really should switch to doing system-level backups, not 1 user at a time.  If you want to do 1-user at a time backups, then you need to setup those users on the local system too and use user1@local ---> user1@remote for those files only.  Seems harder to me than using a real backup tool and running it with the needed privileges on both sides of the connection, but that's your choice.

---

### Post by goemonburo on 2024-09-06
All fine to suggest and any suggestions considered, but can we back up to answering the question:  "How do I fix the Permission denied (publickey)"?  That's really what I need.  

I feel like I've come into a shop asking "How do I fix my scooter?" and am getting told "The best way is to buy this Lamborghini."  Not trying to say that a Lamborghini won't fix the issues and might indeed be better than a scooter, but it's not what I'm trying to do and it's not what my question was.  What was working was working great before, with the ONE issue that it required me to sit there and wait for it to chug through so I could supply the passwords...which I thought might be fixed by extending that timeout window.

Instead, I've gone through the process to make passwordless-ssh-authentication, but did that fix things?  No.  It created a different issue.  And I'd ideally just like to fix the "Permission denied" error.  I think if I can do that, then I'll be all set.  My system for backups has been fine, it's been a stable, solid way to back up what I need to.

I don't really want to embark on a long road of replacing something that was working fine with a complicated system-level backup that I'll have to learn and which could easily have vastly MORE bugs and issues that I'll have to beg for help for.  :-)  

Anyway, thanks again to all on this thread.  It is probably frustrating to offer advice that isn't appreciated.  But does anyone out there know what I need to do to fix a "Permission denied" error?
Alternatively, does anyone know how I can extend the ssh login time to something like...two hours?  Either of those will easily answer my question.

---

### Post by 1fallen on 2024-09-06
> **goemonburo said:**
> 
  But does anyone out there know what I need to do to fix a "Permission denied" error?
Alternatively, does anyone know how I can extend the ssh login time to something like...two hours?  Either of those will easily answer my question.

I'll give it my best shot, I too ran into this about 8 months ago on 24.04 Devel.
I first checked in 
```
ls -l .ssh

```

The private key should have read and write permissions only for the user and no other permissions for the group and others. Mine did not.
My fix was:
```
chmod 600 ~/.ssh/id_rsa
```
Also the public key shouldn&#8217;t have write and execute permissions for group and others. So My change:
```
chmod 644 ~/.ssh/id_rsa.pub
```
Now that I have the correct permissions, I can connect to ssh again. At this time, **"it will ask your admin password"** to unlock the keys.

EDIT: Going through my notes, it wouldn't hurt to check your /home permissions as well mine were changed to "777" and that's No Good.
```
stat /home/$USER
  File: /home/me
  Size: 82            Blocks: 66         IO Block: 16384  directory
Device: 0,56    Inode: 2           Links: 33
Access: (0750/drwxr-x---)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2024-09-06 11:34:07.682570266 -0600
Modify: 2024-09-06 11:34:07.410573686 -0600
Change: 2024-09-06 11:34:07.410573686 -0600
 Birth: 2024-07-16 18:03:58.252613387 -0600
```
```

stat .ssh
  File: .ssh
  Size: 3             Blocks: 2          IO Block: 512    directory
Device: 0,56    Inode: 128         Links: 2
Access: (0700/drwx------)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2024-09-06 11:37:55.975362466 -0600
Modify: 2024-07-16 18:04:11.492446940 -0600
Change: 2024-07-26 10:21:32.447868621 -0600
 Birth: 2024-07-16 18:04:11.491446952 -0600
```

---

### Post by TheFu on 2024-09-06
You are correct.  I know of no way to solve the issue reported initially.  The solution to that is to use ssh keys so you are never prompted for a password for this specific task.  Everything after that is an "implementation detail" for your specific situation.

I understand why you can feel like I'm offering a Lamborghini. You have a broken scooter with a key. What we initially suggested was a scooter with keyless start.  In thinking through that solution, other details (user1/user2) were offered which made it a two scooter with keyless starting problem.  Soon, other details were offered which pointed out that using 1-user backup solutions would be less great to using a system-wide backup solution.  It is still a scooter, just with n+1 seats.  Heck, even my backups aren't a Lamborghini.  I use only F/LOSS tools. If I had a Lamborghini, I'd be using an expensive, commercial, backup tool like Netbackup (is that even sold anymore?).

The 2-seat, keyless start for rsync is adding more and more complexities.  I get that you don't feel like 2-seats are needed, but they are to address the permissions problem, IMHO. At restore time, there will be problems with the method being used.  At least I think there will.  I ran into similar issues 20+ yrs ago when I used rsync for backups too.

I'll leave it to others to try to explain things differently. Hopefully they will be clearer than I.  Obviously, it is my failure. Sorry.

---

### Post by Doug S on 2024-09-06
> **goemonburo said:**
> Alternatively, does anyone know how I can extend the ssh login time to something like...two hours?  Either of those will easily answer my question.
??? I did in earlier replies. I also tested it and it worked fine. I tested having rsync waiting for about 11 hours when I had a 1 day timeout set. See my [earlier post]("https://ubuntuforums.org/showthread.php?t=2500408&page=2&p=14203772#post14203772").

---

### Post by goemonburo on 2024-09-06
Thank you @TheFu, this post (above) made me chuckle.  Yes.  It's more than just a scooter.  #facepalm.

Thank you for your help and your humor.  :-)  Nobody has failed; no apologies needed.  I really genuinely appreciate the help and you kindly did what you could.

---

### Post by goemonburo on 2024-09-06
@Doug S, I have no idea how I missed this, I am so sorry.  Let me try this and get back to you.  Thank you for posting!!  This is probably exactly what I need.  (Though I now need to figure out how to revoke the passwordless login....or to force a password in this case....)

---

### Post by goemonburo on 2024-09-08
Hey guys, I have to BEG for help here, as I've now left the country and it appears something in the setup for the above has now turned OFF any kind of password-enter option for SSH.  I'm unable to connect via my computer OR phone, as they don't have keys and it seems to just accept keys now.  There's no 2nd option or backup that prompts for a password.  I will keep going with his when I get back from my business trip but could someone tell me if a) I can pass a key pair to the system remotely at this point (being totally, apparently, locked out) or alternatively, can I possibly rename the .ssh file as .ssh-old by getting a buddy to go to my house, sit at the actual machine, and dutifully copy the ssh terminal commands that will let him do that so I can return to a password-entry option while abroad?

I didn't realize that what I was doing was setting my system up to ONLY accept keys.  

Any help greatly appreciated, as I need to access this computer via a ssh tunnel and am thus far unable to do so.  

Thank you in advance!!

---

### Post by aljames2 on 2024-09-08
It sounds like you are now asking about opening up your SSH to the internet. In my opinion, Key based authentication is a must for this use. I mean, it is possible to open up your SSH to the Internet, using password only access, but not usually recommended.

The authentication method you choose is defined in the sshd_config on the server. This is set up & tested before you leave home.

To be honest, I thought we were talking about rsync & SSH timeout. A user provided you a solution to extend that time out, but you haven’t reported on that.

You can turn off key based auth in the sshd_config file on the server, and you can turn on password authentication in that same file. If key based authentication is turned off, then SSH will not look for keys. Furthermore, if password auth is turned on, then SSH will ask for & look for the password used to authenticate the first time between these hosts.

There are lots of examples you can find online how to configure your sshd_config file within the context of the type of SSH session you are requesting. I use a VPN for remote access from the Internet, but I know a lot of folks do use SSH tunneling, but my guess is 99% of them use key based authentication.

---

