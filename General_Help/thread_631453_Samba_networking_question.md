---
title: "Samba networking question"
date: 2007-12-04
forum: General Help
---

### Post by seandiggity on 2007-12-04
I recently set up a samba share on an Ubuntu Server 7.10 installation.  I have no problem configuring /etc/samba/smb.conf, setting up the users, or accessing the share from a Windows machine.  My only question is:

Is there some way to set up the share so that users will get a warning message (or not be able to access a file) if another user has it open?

I have users connecting at work that have very basic computer skills, and I set up the samba share so that they could "Map network drive" once in Windows and then never have to worry about connection settings again.  I know the best solution would probably be version control with CVS and then using TortoiseCVS on Windows to check files in/out, but I think that's going to be way too complicated for these users.  If they get an error or warning message of some sort, so that they don't edit the same files simultaneously, I think that would be a good enough solution (in this case).

Anyone have any ideas?  I'm hoping there's something somehow built into samba...

---

### Post by koolkatkiwi on 2007-12-05
> **seandiggity said:**
> I recently set up a samba share on an Ubuntu Server 7.10 installation.  I have no problem configuring /etc/samba/smb.conf, setting up the users, or accessing the share from a Windows machine. (etc.).

Hi. If you have no problem setting up samba shares between two computers, could you pleeeeeeease share it with me and the rest of us? I've been Googling this for a week - spent almost every day trying to do this. The number of times I've changed files, ownership and privileges, configured and re-configured, added users and groups in an attempt to get it going doesn't even bear thinking about. I've followed every tutorial that Google threw up (that I could understand) plus results from searches on this forum. I've tried both samba and nfs in desperation - neither can be configured to allow read/write access on my systems.

I have two computers: "kath" on one floor with main user "koolkatkiwi" and "bill" on the other floor with main user "kath". All I want to do is be able to have full share access - read/write -  on each computer's /home folder - e.g. be able to fully access /home/koolkatkiwi and /home/kath on either computer. It would seem a simple thing, but it is not, judging by the unsolved threads all over the internet.

I apologise for asking this, and don't want to hijack your thread. If I start a new thread with this, will you come onto it and share your answer? Thanks in advance.

Cheers,
Kath:KS

---

### Post by Aseld on 2007-12-05
I can't speak for the original poster, but if you start a new thread with your Samba problem I'll certainly try to help.

---

### Post by elite_angel on 2007-12-05
What are the errors you encountered? I'm willing to help if you post it...

---

### Post by seandiggity on 2007-12-05
I'd be happy to share, koolkatkiwi.  Assuming you've got the samba packages installed correctly, that you've unblocked ports 137-139 and 445, and that nothing else is blocking connections (e.g. denyhosts), this smb.conf should be helpful (it's a version I modified from a KnoppMyth installation a while back):

```
;
; /etc/samba/smb.conf
;
; Configuration file for the Samba suite for Debian GNU/Linux
;
; Please see the manual page for smb.conf for detailed description of
;       every parameter.
;

[global]
        load printers = yes
        guest account = nobody
        name resolve order = lmhosts host wins bcast
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spa$
        socket options = IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=81$
        preserve case = yes
        obey pam restrictions = yes
        encrypt passwords = true
        passdb backend = smbpasswd
        passwd program = /usr/bin/passwd %u
        dns proxy = no
        printing = bsd
        server string = SERVERNAME %v
        invalid users = root
        unix password sync = false
        workgroup = WORKGROUP
        syslog only = no
        os level = 20
        printcap name = /etc/printcap
        syslog = 0;
        security = user
        panic action = /usr/share/samba/panic-action %d
        short preserve case = yes
        max log size = 1000

wins support = no

[printers]
comment = All Printers
path = /tmp
printable = yes
public = yes
writable = yes
browsable = yes
create mode = 0700

[SHARE]
path = /SHARE
valid users = USER1 USER2
read only = no
create mask = 0777
directory mask = 0777
available = yes
public = yes
writable = yes
browsable = yes

```

**Notes on this smb.conf: **You're going to need to change most of the stuff in caps above to lowercase equivalents (SERVERNAME, WORKGROUP, /SHARE, USER1, USER2), adding shares as appropriate.  Also, these settings are very permissive, and you should change them appropriately once you get the connection working (see the smb.conf manual).  You may also want to change "load printers = yes" to "load printers = no" and comment out the [printers] lines, depending on your setup.

**About unix/samba users:** Rather than explain in my own words, I'm pasting from this excellent tutorial at [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

> Install Samba

If you don&#8217;t already have Samba installed, now would be a good time to do it:
[I]
sudo apt-get install samba[/I]

In order to keeps things clean and easy to manage, we&#8217;ll set up a new user account to own the share. This account name will be used when connecting to the share from within Windows. For the purposes of illustration, I will be creating a share called sandbox with the username and group also being sandbox.

Create the new group and user account with no login privileges:

[I]sudo groupadd sandbox
sudo useradd --gid sandbox --shell /bin/false sandbox[/I]

To avoid creating a redundant home directory, you can add:

*--home /nonexistent*

to the end of the previous command.

Now you need to add a matching Samba account. You&#8217;ll be prompted to set a password - make note of this as this is what you will use to connect to the share from within Windows.

*sudo smbpasswd -a sandbox*

Next you&#8217;ll need to create a directory to be used as the share (assuming you don&#8217;t already have one). Create a directory, setting the username to your usual login and group to sandbox. Then chmod the directory 775 (assuming you wish both yourself and the virtual appliance to have read/write access). Here is what I entered:

[I]cd $HOME
mkdir sandbox
sudo chown russ:sandbox sandbox
sudo chmod 775 sandbox[/I]

When you write to the share from within Ubuntu, new files will be created with the default permissions 644 with the username and group being your own user account. When your Windows client connects to the share, it will access it as if it were the local system user sandbox and so the group permissions will apply and you won&#8217;t be able to write to any files created from within Ubuntu.

To get around this problem, we can set the groupid bit for the sandbox directory which means all new files created will inherit the permissions of the parent and so the sandbox user from within Windows will be able to make read and write changes as desired.

*sudo chmod g+s sandbox*

If you don&#8217;t understand the above, don&#8217;t worry, just chmod the directory with the command above and all should be well.

**About firewalls:** If you've got a GUI, you should probably install firestarter and unblock ports 137-139 and 445 for incoming connections.  If you want to set up a basic iptables firewall yourself, see this tutorial: [http://wiki.vpslink.com/index.php?title=HOWTO:_Quick_n%27_Dirty_IPTables-Based_Firewall](http://wiki.vpslink.com/index.php?title=HOWTO:_Quick_n%27_Dirty_IPTables-Based_Firewall)

If you only want to allow incoming samba connections, make sure you change the "ALLOWED" line in the firewall.sh from the tutorial above to look like this:
```
## Specify ports you wish to use.
#
ALLOWED="80 137 138 139 445"
```

**IMPORTANT EDIT:** I don't think I emphasized this enough but IF YOU USE THE COMPUTER FOR ANYTHING ELSE BUT SAMBA, YOU'LL NEED THOSE PORTS UNBLOCKED. PORT 80 IS ESPECIALLY IMPORTANT. Ports 22 (SSH), 25 (SMTP), 443 (SSL), and 21 (FTP) might be necessary too if you have a general-purpose server.

**About my original post:**  Please, can somebody answer my question (even if they only have a vague clue as to a solution)?

---

### Post by wolfvorkian1 on 2007-12-05
Sounds like you are having a nightmare. Have you tried this video tutorial? Very easy to follow and it enabled me to network 3 XP computers and I Linux with little problem. I did have to mess with the firewalls some but other than that it worked like a charm. Good luck. 

[http://tinyurl.com/3avurg](http://tinyurl.com/3avurg)

> **koolkatkiwi said:**
> Hi. If you have no problem setting up samba s
I have two computers: "kath" on one floor with main user "koolkatkiwi" and "bill" on the other floor with main user "kath". All I want to do is be able to have full share access - read/write -  on each computer's /home folder - e.g. be able to fully access /home/koolkatkiwi and /home/kath on either computer. It would seem a simple thing, but it is not, judging by the unsolved threads all over the internet.

I apologise for asking this, and don't want to hijack your thread. If I start a new thread with this, will you come onto it and share your answer? Thanks in advance.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-12-05
Wow! What a lot of info that I didn't find in other tutorials! As I'm in the opposite time zone, must go to bed now, but will try all these solutions tomorrow after work, and report back in a DIFFERENT THREAD that I'll start, called "Samba and NFS Share Problems", so this thread can go on and people can help solve seandiggity's problem. Thanks, seandiggity, and sorry for hijacking. Will exit now, but I'll keep an eye on here too, so as to learn as much as I can. Thanks to you all, and hope to see you in the other thread.

Cheers,
Kath:KS

---

### Post by seandiggity on 2007-12-05
No problem, I just hope I get some sort of advice soon; I don't even know where to begin looking for a solution, really.  Also, that 866 GHz machine you listed in your sig must be pretty damn powerful ;)

---

### Post by The_Apprentice on 2007-12-05
> **Aseld said:**
> I can't speak for the original poster, but if you start a new thread with your Samba problem I'll certainly try to help.


Mine's been haning around for a while......

[http://ubuntuforums.org/showthread.php?t=629295](http://ubuntuforums.org/showthread.php?t=629295)

---

### Post by koolkatkiwi on 2007-12-06
> **seandiggity said:**
>  Also, that 866 GHz machine you listed in your sig must be pretty damn powerful ;)

Ha-ha! :lol: Now, come on! I've always been told that the best thing about Linux is that you can run it quite nicely on a 386. Well, not Ubuntu of course ;-) , but really, it runs very nicely on this, and I can surf the net (fast, on broadband) to my heart's content, researching, do my emails, even watch YouTube videos, while multi-tasking. The latter is where it can get hairy if you have too many programs open, but hey! The P3 866 is great as a "Linux Learner" and a second computer.

Cheers,
Kath:KS

---

### Post by seandiggity on 2007-12-06
No, I was serious: a 866 GHz processor has got to be pretty damn powerful; a *866 MHz* processor, on the other hand...

Sorry, that was my attempt at a joke :lol:

I'm actually running Ubuntu on  two machines slower than that, although not with Gnome or KDE.  It really provides a contrast when you hear about somebody paying ~$2000 (US) for an ubermachine with Vista on it.

---

### Post by koolkatkiwi on 2007-12-06
:) Hee-hee. The old typo will get you every time. I fixed that in my Profile, so now nobody will be able to figure out your comments.

I am starting my own thread, called: "Samba and NFS Share Problems". Sorry to change the subject on you in this thread. I tried all those tutorials mentioned here - this is the result:

Before: Both my computers could access the internet, via a modem/router that they are both plugged into. After: Only the main computer has internet access (I hadn't messed with this one). The second one - that I tried these tutorials on - has lost all connectivity and networking capacity.

Before: Both my computers could see each other via Samba, and see all the folders on the other computer, but not access the files in the folders. I was almost there with Samba - just needed to sort out the permissions. After: Neither computer can see the other computer at all, nor see or access any of the files on the other.

There is something seriously wrong here. I wish I had left it alone. Is there anythiing like "System Restore" in Ubuntu?

Can anyone help me in the other thread? I'll leave this one now.

Cheers,
Kath:KS

---

