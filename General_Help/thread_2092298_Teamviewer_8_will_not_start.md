---
title: "Teamviewer 8 will not start"
date: 2012-12-07
forum: General Help
---

### Post by cmavr8 on 2012-12-07
Hello, I have recently installed TV 8 on my linux machine and it worked perfectly until I rebooted.

Now it complains:
"TeamViewer Daemon is not running
Please start teamviewerd and then restart TeamViewer."

I have no service called teamviewer or teamviewerd, so I cannot start it. I tried rebooting but didn't help.

Teamviewer 7 is no good because the other side is already running 8!

Thanks

PS: I just submitted a support ticket. Will let you know if they respond.

---

### Post by cmavr8 on 2012-12-08
Support replied and it works!

```
Dear Chris,

Thank you very much for your message.

Here you have some helpful commands for the daemon in Linux.

teamviewer --daemon status           show current status of the TeamViewer daemon
teamviewer --daemon start              start                              TeamViewer daemon
teamviewer --daemon stop              stop                              TeamViewer daemon
teamviewer --daemon restart          stop/start                   TeamViewer daemon
teamviewer --daemon disable        disable                         TeamViewer daemon - don't start daemon on system startup
teamviewer --daemon enable         enable                         TeamViewer daemon - start daemon on system startup (default)

If you have any further questions, please do not hesitate to contact us again.

Best regards
```

---

### Post by Buggrit on 2012-12-11
Nice tip cmavr8

Started the Daemon with

teamviewer --daemon start

It is now working well on Mint Linux 13 - Thanks

JB

---

### Post by gthm159 on 2012-12-18
Thanks, that was very helpful

---

### Post by Berenland on 2012-12-21
Hi all, 

Al those common errors with T.v. are gone now. 
they upgraded the package. and now it works fine!

regards

---

### Post by andx0 on 2013-01-10
The new version (8.0.16675 / Wine 1.5.19) doesn't start (using Ubuntu 12.04) ... 
ie. still need to use the "teamviewer --daemon start" command before starting.

Let's hope it will be solved soon ... :)

---

### Post by heinz0001 on 2013-01-14
Thanks!

---

### Post by Alfagulf on 2013-01-16
Thanks for reporting your experience.

I would like to add that in order to make Teamviewer 8 (Beta)  starts when I login into gnome, I had to modify my startup application so that it starts the Daemon first and then starts the teamviewer application.
But then I realized that the Daemon needs a sudo to start, and the sudo needs to prompt for a password.
This led me to search and find a solution [[COLOR="DeepSkyBlue"]**_here_**[/COLOR]]("http://askubuntu.com/questions/118472/how-do-i-launch-a-gui-application-as-root-on-user-login").


In the startup application, I had to create two entries, the first is to start the daemon like this:
[INDENT]sudo -k teamviewer --daemon start[/INDENT]

and the second entry is like this:
[INDENT]teamviewer[/INDENT]

---

### Post by Radogor on 2013-01-23
A simple way to add to the file /etc/rc.local the line /usr/bin/teamviewer --daemon start. This method also works with limited users.

---

### Post by sameersbn on 2013-01-28
Hello,

I *WAS* having this same issue.
Here is how i solved it and i believe it is the correct solution to this issue.

In the terminal, do the following.

```

cd /opt/teamviewer8/tv_bin/script
sudo cp teamviewerd.sysv /etc/init.d/
sudo chmod 755 /etc/init.d/teamviewerd.sysv
sudo update-rc.d teamviewerd.sysv defaults

```This will setup the teamviewerd.sysv script to execute at boot and hence you will always have the teamviewerd daemon running at all times.

The above changes will take effect at the next system reboot. You can manually start the service for the first time by doing, hence not requiring a reboot.

```

sudo service teamviewerd.sysv start

```

NOTE: this will always keep the teamviewerd running.

Regards
~Sameer

---

### Post by TPAKTOPUCTA on 2013-01-31
Thanks, that was very helpful

---

### Post by bob-linux-user on 2013-01-31
You can log on to someone else's pc using the Teamviewer website from any modern browser. That is very useful as you can do it from anywhere without installing anything.

---

### Post by cybergalvez on 2013-02-17
give this software a try and it just does not work! after a reboot it is useless

---

### Post by quein on 2013-02-26
Thanks. Works like a charm.

---

### Post by upasakalee on 2013-03-02
Thank you, Sameer. :)  Your advice helped me solve this issue.  Now I can use the TeamViewer Android app to control my desktop remotely without having to boot into Windows.

---

### Post by quietas on 2013-05-01
Thanks for the info to get the service running, but I can't log in. I get an authentication error when I put in the password I used for the unattended access. I've got a dozen windows system that work fine, but something is different in Linux. Go figure?

EDIT: I actually reversed the steps Sameer stated and used "sudo teamviewer --daemon enable" and that worked. I could connect and log in, after that it stalled and I can't connect again.

EDIT #2: On a side note for others, I did get it working. I had to change the authentication type to Teamviewer in the right click options on the client computer.

---

### Post by cmavr8 on 2013-05-01
Good you figured it out..
I now have problems with signing in to my teamviewer account through the program (website access works great). Go figure once again... :P

---

### Post by quietas on 2013-05-01
I did run into one issue that is weird. "teamviewer --passwd D!ngBell" would not work. It through an error with the !ngBell portion. I don't think Linux command line likes commands with an exclamation mark ! in it.

---

### Post by cmavr8 on 2013-05-01
Have you tried running it like this?:
> 
teamviewer --passwd "D!ngBell"

BTW, I hope this is not your real password!

---

### Post by quietas on 2013-05-01
> **cmavr8 said:**
> Have you tried running it like this?:


BTW, I hope this is not your real password!

Lol, not my password. Just one I made up trying variations. It seems to not like an exclamation while at command line. I used double and single quotes, but eventually got it working via the GUI.

---

### Post by cybergalvez on 2013-10-16
I know this is an old thread, but I got tired of trying to figure out why their upstart script was not working so I removed it (teamviewer --daemon disable) and installed supervisord and added teamviewerd -f as the program in its config file. works like a champ. hear is my teamview.conf file if anywone is interested
> 
[program:teamviewerd]
command=/opt/teamviewer8/tv_bin/teamviewerd -f
autostart=true
autorestart=true
startretries=5


---

### Post by ltirado on 2013-10-21
> **cybergalvez said:**
> I know this is an old thread, but I got tired of trying to figure out why their upstart script was not working so I removed it (teamviewer --daemon disable) and installed supervisord and added teamviewerd -f as the program in its config file. works like a champ. <snip>

Thank you! I just installed Ubuntu 13.10 on my desktop and the teamviewer service refused to start with upstart automatically and I couldn't figure out why either. I had tried post #10 on the first page but unfortunately this caused disconnects when I clicked on any object. Your suggestion of supervisord worked perfectly. To install it on Ubuntu via the repositories the command is:

```
sudo apt-get install supervisor
```

Next, I did:

```
sudo gedit /etc/supervisor/conf.d/teamviewer.conf &
```

and pasted the contents of the configuration file in the previous post, and saved the file. Restarted, and boom, working perfectly!

---

### Post by Mr_Bumpy on 2013-10-24
Since I don't wish to have the TeamViewer daemon running all the time, I made a script that starts the daemon when I launch the TeamViewer application. Then I just point the TeamViewer launch icon to the new script I created. I do this in KDE by right-clicking the K menu and selecting "Edit Applications...", then replacing the command for "TeamViewer 8" with the path to the script I created. I don't know how you do this in Ubuntu's Unity interface, so of someone wants to provide this step, that would be helpful.

Anyway, here is my script for KDE users:
```
#!/bin/bash
teamviewer --daemon status | grep "stop"
if [ $? -eq 0 ]
then
  kdesudo --comment "Please enter your password to start the TeamViewer daemon:" -c "teamviewer --daemon start"
fi
  /opt/teamviewer8/tv_bin/script/teamviewer
```

For standard Ubuntu users (also GNOME, XFCE or LXDE), replace the "kdesudo" line above with the following:
```
  gksudo "teamviewer --daemon start"
```

The only potential downside to this script is that the TeamViewer daemon remains running after the TeamViewer application is stopped. I haven't been able to figure out how to kill the TeamViewer daemon upon exiting the TeamViewer application. That being said, this is a lot better for my usage than having the daemon running all the time, every day, since I only use TeamViewer to occasionally provide tech help for family and friends.

---

### Post by arturobandini1978 on 2013-12-21
Thanks Sameer! Your solution also fixes the same problem encountered in teamviewer 9. Off course, you have to change the code where it says: teamviewer 8 :).

Grtz, Arturo

---

### Post by leonbravo on 2014-02-19
Still in version 9 sometimes daemon does not start automatically. Only way around is issuing command : teamviewer --daemon start as described previously.

---

### Post by Geyson_Rodriguez on 2014-03-07
Hi all,

The best way is:

[FONT=courier new]sudo ln -s /opt/teamviewer9/tv_bin/teamviewerd /etc/init.d/teamviewerd
sudo update-rc.d teamviewerd defaults[/FONT]

---

