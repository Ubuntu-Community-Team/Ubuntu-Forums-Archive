---
title: "How to enter the Default Keyring password via the command line?"
date: 2013-02-26
forum: General Help
---

### Post by pundip on 2013-02-26
I need to VNC into my desktop remotely however I need to unlock the keyring remotely from the commandline to do this. 

I have tried the python solution posted on this thread

[http://askubuntu.com/questions/18927/how-to-enter-the-default-keyring-password-via-the-command-line](http://askubuntu.com/questions/18927/how-to-enter-the-default-keyring-password-via-the-command-line) 

and it gives me the following error:

Traceback (most recent call last):
  File "/usr/bin/unlock-keyring", line 6, in <module>
    gnomekeyring.unlock_sync(None, getpass.getpass('Password: '));
gnomekeyring.IOError

The other solution does not tell me what command I need to unlock it the keyring.

I am running Ubuntu 10.04.4 LTS

---

### Post by matt_symes on 2013-02-27
Hi

[http://superuser.com/questions/141036/use-of-gnome-keyring-daemon-without-x](http://superuser.com/questions/141036/use-of-gnome-keyring-daemon-without-x)

Any good ?

Kind regards

---

### Post by pundip on 2013-02-27
Thanks matt for the link. I added the following lines
auth     optional  pam_gnome_keyring.so
session  optional  pam_gnome_keyring.so auto_start

to /etc/pam.d/login as instructed but still cant use VNC. I am not at the machine at the moment so I only have ssh access. 

The machine is set to auto login and I have added
echo -n "mypassword" | gnome-keyring-daemon --login 
with mypassword being replaced with my keyring password

and still not luck.

---

### Post by matt_symes on 2013-02-27
Hi

you will normally be connecting via VNC and not ssh ? 

will the target machine have gnome-keyring-daemon running before connection  ?

If gnome-keyring-daemon is not running before connection, the first thing to check is if gnome-keyring-daemon is started when you login.

If it starts it running but does unlock the keyring take a look in /var/log/auth.log to see if it is rejected or to see if it is even getting the password.

post back on your investigation. bear in mind though it's 60.30am here so i may not respond right away.

Kind regards

---

### Post by pundip on 2013-03-05
Hi matt,

    I normally connect using VNC client and don&#8217;t use SSH. The target machine does seem to have be running or at least there is a process running
 /usr/bin/gnome-keyring-daemon --start --components=secrets. 
In the log file this is the entry for when I try to connect via VNC client. At the machine I want to connect to there will be a popup asking the password. If I enter it once it will accept connections until I reboot and if I forget to unlock the keyring or reboot remotely I can&#8217;t connect via VNC.

Mar  6 11:20:57 armada gnome-keyring-daemon[2264]: PROMPT INPUT:#012#012[prompt]#012title=Unlock Keyring#012primary=Enter password for keyring 'Default' to unlock#012secondary=An application wants access to the keyring 'Default', but it$

Not related but I did find a lot of Chinese IP's trying to log in as root. 

Thanks in advance.

---

### Post by matt_symes on 2013-03-06
Hi

> Not related but I did find a lot of Chinese IP's trying to log in as root.

Hmm. Make sure your system is secure !!!!

Use VNC with ssh or someting like tightVNC. 

Use keys if you can and make sure any passwords contain alpha numerica characters and are long.

Lok down with iptables and other hardening techniques.

I don't use VNC personally so i cannot suggest anything off the off, especially if pam_gnome_keyring is not working for you as that is what i would have played around with.

I would have to read up like you have been.

Let's see what others suggest.

Kind regards

---

### Post by pundip on 2013-03-06
I think my SSH installation uses keys by default and I do use an alpha numeric password. It seems there is an pearl script that adds rules to the ip tables based on unsuccessful logins attempts found in the log files. Looks a little above my level but looks like worth trying. Thanks for the advice thus far.

---

