---
title: "Seeking help with ssh-server set up"
date: 2021-06-12
forum: General Help
---

### Post by paydaydaddy on 2021-06-12
I am running a desktop with Kubuntu 18.04.05 LTS. I have been using dropbox to share pdf files with an ipad for several years. This just recently stopped working. In searching the internet for a work around, it seems that using openssh-server on the linix desktop and FE File Explorer on the ipad might be a good solution. So far I have not been able to make it work. I suspect that the problem is the openssh-server set up on the desktop. I may have messed up some of the "script" for openssh-server while attempting to configure. I tried to uninstall and reinstall openssh-server, but the questionable code remains. I would greatly appreciate some input from some kind soul with knowledge of these things.

---

### Post by &amp;KyT$0P# on 2021-06-12
> **paydaydaddy said:**
> So far I have not been able to make it work. 

What exactly does happen when you try to ssh in?

Few things to check:
[LIST]
[*]Are both your iPad and your computer on the same LAN?
[*]Do you have a firewall on your computer that is blocking the connection?
[*]What changes, if any, did you make to your [FONT=Courier New]/etc/ssh/sshd_config[/FONT] ?
[*]As a test, can you ssh into the computer from itself at 127.0.0.1?
[/LIST]

---

### Post by paydaydaddy on 2021-06-12
Please understand that I am ignorant of much of this. The ipad and the desktop are on the same LAN, I think. I just replaced my router last week. The desktop is hard wired, the ipad is wireless. I have taken steps see that the firewall, if active, is open to communicate on the correct port. I think I was finally able to purge and re-install openssh and all related files. I read about testing by sshing the computer into itself, but I lack the knowledge to do so.

---

### Post by &amp;KyT$0P# on 2021-06-12
> **paydaydaddy said:**
> I read about testing by sshing the computer into itself, but I lack the knowledge to do so.

Just open Terminal and run
```
ssh -p [COLOR="#FF0000"]<your_port>[/COLOR] [COLOR="#FF0000"]<your_username>[/COLOR]@127.0.0.1
```
Replace [COLOR="#FF0000"]<your_port>[/COLOR] and [COLOR="#FF0000"]<your_username>[/COLOR] with that information for your system.  If your port is 22 you don't need to explicitly have the [FONT=Courier New]-p 22[/FONT] in the command.

---

### Post by paydaydaddy on 2021-06-12
Interesting. It seemed as though the computer was going to log into it'self, and then access was denied due to invalid password. There is only one password to this computer that I am aware of.

---

### Post by paydaydaddy on 2021-06-12
Have done lots of reading and have gained only a tiny bit of understanding. The written tutorials are pretty much beyond what my limited knowledge allows me to do with any level of confidence.  Halogen2's help has convinced me that I need to configure either openssh-server or client, or both. I was able to save one of the default configs as a text file, but don't know what to do with it. No wonder guis have become so popular. Any suggestions other that invest in win10?

---

### Post by &amp;KyT$0P# on 2021-06-12
> **paydaydaddy said:**
> Interesting. It seemed as though the computer was going to log into it'self, and then access was denied due to invalid password. There is only one password to this computer that I am aware of.

Sorry for the stupid question, but you are sure you typed it right?

If so can you try putting an [FONT=Courier New]AllowUsers[/FONT] directive in [FONT=Courier New]/etc/ssh/sshd_config[/FONT] for your username (and then do [FONT=Courier New]sudo systemctl restart sshd[/FONT] to load the changes)? (This will specify that only your username is allowed to connect over ssh.  Refer to [FONT=Courier New]man sshd_config[/FONT] for more info.)

I'm not sure how to help further if that doesn't work, but adding one or more [FONT=Courier New]-v[/FONT] arguments to the ssh command might provide some useful information for someone who knows this more than me.

---

### Post by paydaydaddy on 2021-06-12
I have read that a root password is needed in addition to the user login password. Do you think this is good information?

---

### Post by TheFu on 2021-06-12
ssh-server is one of the easiest things to get working. The defaults "just work" and are secure enough for use on a LAN.

Let's reset everything back to the beginning:
```
sudo apt purge openssh-server
```
That will remove any prior config settings in /etc/ssh/ which is what you want.

Next, let's install a fresh ssh and some minimal brute-force prevention.
```
sudo apt install ssh fail2ban
```
That's it on the server.  "ssh" is a meta package that includes both the ssh server and ssh client. You want both on every Linux system.

If you have a firewall enabled, you'll need to open the 22/tcp port.  If not, nothing extra need be done.  You have ssh-server, sftp-server, scp and all the expected ssh tools now.

On any client system that is on the same LAN, run 
```
ssh {userid}@{server-IP}
```
So, the userid is optional, if the local username and remote username are identical. It is always safe to specify.
```
ssh thefu@172.22.22.4
```
is what the command would look like on my client to connect to the .4 IP on my LAN.  A password prompt will be displayed. Enter the correct password, and I'm in.  That's it. Nothing more to this.

If the connect doesn't work, then either the connection is being blocked on the network somewhere or you don't know the correct password for that userid.  If you've screwed with tcp-wrappers or firewalls, all bets are off. We won't be able to help you figure those out since there are thousands of things that could have been modified which screw up connections.  But because this happens so often, I've written an ssh-troubleshooting guide: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
Hope that is helpful.

Sorry, I can't help with anything related to Apple.  Had an Apple machine for 3 weeks and it drove me crazy.

---

### Post by TheFu on 2021-06-12
> **paydaydaddy said:**
> I have read that a root password is needed in addition to the user login password. Do you think this is good information?

NO!!!!!! Ubuntu doesn't have a root password and you don't need it. That is bad information.  In fact, attempting to ssh into an Ubuntu system using root shouldn't be allowed by default.  It is a bad security practice.  

BTW, using passwords for access is a bad security practice. For ssh, we usually use ssh-keys for authentication. Until you get the connection working, we won't go there.

---

### Post by paydaydaddy on 2021-06-13
it appears that I was able to get the desktop to log into itself. That is progress. I will see if I can use what I have learned to get the ipad to connect. Thanks for your help so far.

---

### Post by paydaydaddy on 2021-06-13
I have 2 nearly identical ipads that I use to keep track of music scores, chord charts, set lists, and such. I now have one of them that links up perfectly with the linux desktop. The other one has been repeatedly denied access. There has to be a reason, but so far it has eluded me. Kind of makes me nostalgic for the days of lugging around a trunk full of notebooks.

---

### Post by TheFu on 2021-06-13
We cannot help without seeing the actual commands and output from those commands.
We cannot read your mind or magically know what is happening until you show us.  Text would be best. Please don't be obtuse. ;)

---

### Post by paydaydaddy on 2021-06-13
I followed your advice. Once I got the desktop to log into itself it was a matter of paying close attention to usernames and passwords on the ipads.

---

### Post by TheFu on 2021-06-13
> **paydaydaddy said:**
> I followed your advice. Once I got the desktop to log into itself it was a matter of paying close attention to usernames and passwords on the ipads.

Well, computers actually do care about accurage usernames and correct passwords, so there isn't much anyone can do to help you there ... unless you setup ssh-keys.  Then you'll be prompted to unlock the key once per login/boot, but never again.  At least it works that way on Unix systems. No clue what apple does or does not allow.  ssh-keys are both more convenience AND more secure.

---

