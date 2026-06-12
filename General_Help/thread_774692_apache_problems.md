---
title: "apache problems"
date: 2008-04-29
forum: General Help
---

### Post by Poirot on 2008-04-29
Hi all,

I have installed apache2 and have it running with ssl.

Unfortunately it seems that every time I reboot it crashes.
However, there seem to be apache processes running.

```
graeme@graeme-home:~$ ps -e | grep apache
 5904 ?        00:00:00 S91apache2
 5913 ?        00:00:00 apache2ctl
 5918 ?        00:00:00 apache2

```

I have found that doing this solves the problem

```

graeme@graeme-home:~$ sudo killall apache2
graeme@graeme-home:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                      httpd (no pid file) not running
Apache/2.2.8 mod_ssl/2.2.8 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server localhost:443 (RSA)
Enter pass phrase:

OK: Pass Phrase Dialog successful.
                                                                                                               [ OK ]

```

I'm a bit out of my depth here, I'm not really sure what's going on. I had to change the set up when I upgraded to Hardy and now I need to enter the pass phrase each time I restart apache.

Can someone please help me to understand what's going on here?

---

### Post by Monicker on 2008-04-29
That looks like the prompt for an ssl certificate.  Did you redo the certificate when you upgraded?  If there is a password on the certificate, what you are seeing is normal.

---

### Post by cdenley on 2008-04-29
When you reboot, there is a prompt for the certificate password on the main terminal. Other scripts may have output text after the prompt appeared. If you hit enter, it will probably print the password prompt again. Apache won't start completely until you enter this password.

---

### Post by ebelog on 2008-04-29
Here's a good how-to page for creating ssl certificates:
[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

It includes a section near the bottom about creating a key file which doesn't require a password so that you can start up Apache more conveniently (see the code snippet below). You can try going through these steps to see if it clears up your issue. Make sure to substitute your own file names instead of mars-server.key

```
[root]# cd /etc/httpd/conf/ssl.key
[root]# cp mars-server.key mars-server.key.org
[root]# openssl rsa -in mars-server.key.org -out mars-server.key
[root]# chmod 0400 mars-server*
```

---

### Post by Poirot on 2008-04-30
Thanks guys,

If I understand correctly, the nature of the certificate I create determines the behaviour of apache to some degree. It prevents me from restarting apache unless I have the passphrase. I am fine with this, it seems a sensible security measure.

However, the set up I have is currently for testing and developing so I reboot the machine all the time.

On rebooting, apache used to just work. I could point my browser at [https://localhost/](https://localhost/) and my development system would be presented.

Since the upgrade and the new certificate (which I am beginning to understand) I can't do this, apache seems to be running but corrupted in some way. I need to kill all apache processes before restarting apache each time I reboot.

```

graeme@graeme-home:~$ sudo killall apache2
graeme@graeme-home:~$ sudo /etc/init.d/apache2 restart

```


If I just restart without killing the processes I get this

```

graeme@graeme-home:~$ sudo /etc/init.d/apache2 restart
[sudo] password for graeme: 
 * Restarting web server apache2
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

So my problem is minor but irritating, apache seems to lock itself up on reboot. Is this an intentional result of the certificate I have used? Should I simply consider a less secure certificate for development?

Thanks for the help, I am feeling happier already.

---

### Post by ebelog on 2008-04-30
Apache won't fully start because it's waiting for the SSL Certificate pass phrase. You can deal with the issue by either setting up a certificate that doesn't need a pass phrase on startup, or you can set httpd to not start at boot time so that it doesn't get into that hung state. If you choose the latter, you'll need to manually start Apache after each reboot.

I've always set up keys which don't require pass phrases on development systems, because it's more convenient, and because the security risk is minimal. You'll have to decide for yourself how you want to balance the convenience vs. security.

---

### Post by pepijn on 2010-05-17
I have the exact same problem as poirot. And even though there were some helpful answers in this thread (thanks!) there isn't a solution.

Going for a less secure server seems unnecessary. The exact same configuration (with same website) on RHEL4 *does* work. Should this be filed as a bug?

---

### Post by cdenley on 2010-05-17
> **pepijn said:**
> I have the exact same problem as poirot. And even though there were some helpful answers in this thread (thanks!) there isn't a solution.

Going for a less secure server seems unnecessary. The exact same configuration (with same website) on RHEL4 *does* work. Should this be filed as a bug?

There isn't a solution because there isn't a problem or a bug, as far as I can tell. If your certificate requires a passphrase, then apache will wait for it to be entered before it can finish starting. There is no way around it. If you need apache to start unattended, then remove the password.

---

### Post by pepijn on 2010-05-17
Thanks for your reply, cdenly

However, if you read poirot's last post in this thread, you'll see (as i understand it) that before he can enter the pass phrase he has to kill all apache processes. 

> 
On rebooting, apache used to just work. I could point my browser at [https://localhost/](https://localhost/) and my development system would be presented.

Since the upgrade and the new certificate (which I am beginning to understand) I can't do this, **apache seems to be running but corrupted in some way**. I need to kill all apache processes before restarting apache each time I reboot.

and 

> It prevents me from restarting apache unless I have the passphrase. I am fine with this, it seems a sensible security measure.


This is the problem I'm having too. I don't care it asks me for the password at startup - I actually want this kind of security - but I'm not able to enter it, (no response) because apache hangs at this point.

(before i found this thread i created my own: [http://ubuntuforums.org/showthread.php?p=9305004](http://ubuntuforums.org/showthread.php?p=9305004))

---

### Post by cdenley on 2010-05-17
> **pepijn said:**
> Thanks for your reply, cdenly
This is the problem I'm having too. I don't care it asks me for the password at startup - I actually want this kind of security - but I'm not able to enter it, because apache hangs at this point.

Apache doesn't hang, it waits for your input. The init script fails because apache hasn't written the PID file yet. Perhaps you can consider it a bug that apache doesn't write its PID file before prompting for an SSL pass phrase. That isn't ubuntu-specific, though, and that would probably have to be changed upstream. For all I know, there could be a reason for it, though.

---

### Post by cdenley on 2010-05-17
I looked into it a little more, and the master process for apache2 hasn't been started yet when it waits for the passphrase input. I suppose it could write a pid file with the process that prompts for a passphrase, then overwrite it when it starts the master process, though.

Also, I looked to see how this issue works with upstart in lucid. It seems you can't enter the passphrase when the init script is started by upstart. I think that is a bug. Currently, you would have to kill apache, then start it from the terminal if your ssl key has a passphrase.

---

### Post by pepijn on 2010-05-17
Thanks again, and I'm sorry if I have trouble understanding some things (PID file?). I'm new to most of this. I did more research the last hour and found out that apache can't access the .key file after a reboot.

Then I don't have any access (no response from the system) unless I ssh into the server, kill all apache2 processes and start apache2 manually.

There is some evidence suggesting that there is something wrong with the way apache2 starts up (without the required privileges?) after a reboot. Changing the ownership/location of the .key file does not seem to make a difference.

btw. it seems your right in saying that this is not a bug in ubuntu, but maybe the server manual (that I used for this setup) can be updated with some troubleshooting/known issues info.

-- this is a reply to your second last post, btw. Didn't see the new one until I posted this one. Thanks so much for your time!!

---

### Post by pepijn on 2010-05-17
Anyway, you seem to hit it spot on in:

> I looked into it a little more, and the master process for apache2 hasn't been started yet when it waits for the passphrase input. I suppose it could write a pid file with the process that prompts for a passphrase, then overwrite it when it starts the master process, though.

Also, I looked to see how this issue works with upstart in lucid. It seems you can't enter the passphrase when the init script is started by upstart. I think that is a bug. Currently, you would have to kill apache, then start it from the terminal if your ssl key has a passphrase.

I helps to know that it is not just me. ;)

---

### Post by cdenley on 2010-05-17
It is reading your key fine. Apache's init script is starting apache. Apache then prompts for a password to decrypt your key. After it decrypts the key, it finishes starting apache and writes a PID file. This file contains the PID (process ID) of the master apache process. It is what is used to stop running processes.

Depending on what version of ubuntu you are using, apache may be waiting for you to type the password on the main console even though output from other init scripts have buried the password prompt dialog. If this is the case, simply press enter from the main local console, and you should get a fresh prompt. In lucid, the password prompt doesn't get buried, but it looks like upstart doesn't allow it to read keyboard input, so it will wait for a password until you kill it.

---

### Post by pepijn on 2010-05-17
I am running lucid (10.04 ubuntu server). What you're saying makes a lot of sense. I.e. keyboard input is not allowed.

It's a pity that i'm not experienced enough to change the upstart behavior of apache and/or ubuntu.

---

### Post by cdenley on 2010-05-18
I think I found a workaround for both issues. **This is for lucid!**
```

sed -e 's/^ENV=/tty > \/tmp\/a2sslpasstty\nENV=/' /etc/init.d/apache2|sudo tee /etc/init.d/apache2
echo '#!/bin/bash
TTY=`cat /tmp/a2sslpasstty`
echo $@ > $TTY
echo -e -n "Enter your SSL key password: " > $TTY
read -e -s -t 60 PASS < $TTY
echo $PASS'|sudo tee /usr/local/bin/a2sslprompt
sudo chmod 700 /usr/local/bin/a2sslprompt
sed -e 's/SSLPassPhraseDialog *builtin/SSLPassPhraseDialog exec:\/usr\/local\/bin\/a2sslprompt/' /etc/apache2/mods-available/ssl.conf|sudo tee /etc/apache2/mods-available/ssl.conf

```

This custom password prompt dialog will read the password when started by upstart, unlike apache's builtin function. For some reason, it doesn't display any more output after the password is entered, so it may not appear that it worked but it did. Apache was started, and if you press enter again you will have a login prompt.

Also, the script's input prompt will time out after 60 seconds. If you don't enter a password in that time, apache fails to start, and you can start it later with the init script without having to kill anything.

---

### Post by pepijn on 2010-05-18
Wow, that was fast! :-)

I see that your nearing your 3,400th bean, therefore who am I to question your skills. ;-) I did spend a lot of time on the machine to get it to work, and I'd be curious if I should wait for an official update... or if there is an easy way to undo this, in case it doesn't work as advertised...

---

### Post by cdenley on 2010-05-18
> **pepijn said:**
> Wow, that was fast! :-)

I see that your nearing your 3,400th bean, therefore who am I to question your skills. ;-) I did spend a lot of time on the machine to get it to work, and I'd be curious if I should wait for an official update... or if there is an easy way to undo this, in case it doesn't work as advertised...

All that does is add one line to /etc/init.d/apache2, create the script /usr/local/bin/a2sslprompt, then edit one line in /etc/apache2/mods-available/ssl.conf. This should undo everything.
```

sed -e 's/SSLPassPhraseDialog.*$/SSLPassPhraseDialog  builtin/' /etc/apache2/mods-available/ssl.conf|sudo tee /etc/apache2/mods-available/ssl.conf
sed -e '/^tty.*$/d' /etc/init.d/apache2|sudo tee /etc/init.d/apache2
sudo rm /usr/local/bin/a2sslprompt

```
I wouldn't expect a fix anytime soon. I don't think a bug report even exists.

[https://bugs.launchpad.net/ubuntu/+source/apache2](https://bugs.launchpad.net/ubuntu/+source/apache2)

If you don't create one, maybe I will tomorrow.

---

### Post by pepijn on 2010-05-18
Hey cdenley,

I ran the script you wrote, and it works (!) in so far that i am now able to enter the ssl pass phrase, and boot continues with tomcat. After that i'm not able to log in (which isn't a change really). I.e. I'm not asked for username/pwd. 
This is not a problem really, since I don't need direct (local) access to the server. The main thing is that when the server needs a reboot for some reason, apache now starts correctly, without a kill or anything.
Great work! Thanks.

If you have an idea why it doesn't take me to log in, that would be appreciated of course.

---

### Post by cdenley on 2010-05-18
> **pepijn said:**
> If you have an idea why it doesn't take me to log in, that would be appreciated of course.
I said that would happen. Not sure why. Pressing enter gave me a login a prompt.
> **cdenley said:**
> 
For some reason, it doesn't display any more output after the password is entered, so it may not appear that it worked but it did. Apache was started, and if you press enter again you will have a login prompt.

---

### Post by pepijn on 2010-05-18
I got that from your post, but hitting enter again doesn't change it or take me anywhere.

But before the fix, it wouldn't take me to login either. Even after I ssh'd into the machine and killed apache. It would continue with starting tomcat and after that just a blinking cursor.

---

### Post by pepijn on 2010-05-18
I removed the pass phrase temporarily to see if it would allow startup to proceed to login. 
It does start apache2 without asking for the phrase but still doesn't take me to login...

So i guess that is a separate issue. it did work before i started messing around with ssl. But I don't know what it could be.

If you (or any other helpful forum member ;-) ) could point me into the right direction with this, it would be greatly appreciated.

---

### Post by cdenley on 2010-05-19
The problem was much simpler than I thought! Everything I did was so unnecessary. Undo anything you may have done:
```

sed -e 's/^SSLPassPhraseDialog.*$/SSLPassPhraseDialog  builtin/' /etc/apache2/mods-available/ssl.conf|sudo tee /etc/apache2/mods-available/ssl.conf
sed -e '/^tty/d' /etc/init.d/apache2|sudo tee /etc/init.d/apache2
sudo rm /usr/local/bin/a2sslprompt

```

Now adding "stty sane" to /etc/init.d/apache2 should fix the lucid problem.
```

sed -e '/^ENV=/i stty sane' /etc/init.d/apache2|sudo tee /etc/init.d/apache2

```

You still have to enter the password on the local console or kill apache before the init scripts are usable. That is just how apache works.

I filed a bug report.
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/582963](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/582963)

---

### Post by pepijn on 2010-05-19
You're the man! This is why I choose to use ubuntu as a distro. Great support!

Oh, and I fixed the other login issue i had by reinstalling gnome core. I guess the deinstall of x-windows system / ubuntu-desktop through apt-get autoremove leaves some residue. (Perhaps with --purge it would revert ALL changes to boot.) 

> You still have to enter the password on the local console or kill apache before the init scripts are usable. That is just how apache works.

I can live with that. ;-)

---

