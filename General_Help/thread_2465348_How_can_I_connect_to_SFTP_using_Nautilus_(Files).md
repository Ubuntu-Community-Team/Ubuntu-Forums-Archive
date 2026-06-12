---
title: "How can I connect to SFTP using Nautilus (Files)"
date: 2021-07-30
forum: General Help
---

### Post by Paddy Landau on 2021-07-30
I've searched the internet for a solution. All solutions that I found apply to old versions of Nautilus, and I can't make it work on my current version.

I have access to a server via SFTP (I have the private RSA key, not a password). I can access it using FileZilla.

It would be helpful for me to be able to access the server via Nautilus (renamed Gnome Files, or so I read).

How can I access the server using SFTP via Nautilus?

More information:

[LIST]
[*]Ubuntu 20.04
[*]Nautilus 3.36.3-stable (the default that comes with Ubuntu)
[*]The server requires access over a custom port, not the default one.
[/LIST]
Thank you

---

### Post by tea for one on 2021-07-30
Is this attachment any help?

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
>  How can I access the server using SFTP via Nautilus?

Typing in a **ssh://** path in the location bar does not work??
```
ssh://remoteuser@remoteserver:Port
```

---

### Post by Paddy Landau on 2021-07-30
[FONT=Verdana]> **tea for one said:**
> Is this attachment any help?[/FONT]
Thanks for your reply. Unfortunately, no. I can enter the server there, but I don't get any option to put in the keyfile, or the port, etc., as shown in internet searches.

Maybe I'm entering the wrong details?

I've tried the following (without the square brackets, obviously).

sftp://[domain]
sftp://[domain]:[port]
sftp://[user]@[domain]
sftp://[user]@[domain]:[port]

I get the response, "Unable to access location. Permission denied."

I'm not surprised that permission was denied, because it didn't ask for credentials. I need to give Nautilus the private key (as I do with FileZilla).

---

### Post by Paddy Landau on 2021-07-30
> **scorp123 said:**
> Typing in a **ssh://** path in the location bar does not work??
```
ssh://remoteuser@remoteserver:Port
```
I only have SFTP access, not SSH access.

I've tried it, and it gives the same response.

---

### Post by dragonfly41 on 2021-07-30
I confess that I do not often use Nautilus. Prefer Krusader with UserActions (plugins).
However. Can you perhaps try a toolchain?  Nautilus > Thunar .. or Thunar directly.
From Nautilus select folder then >   Right click > Open With Other Application > Thunar

I found from reading threads that I needed these packages to be installed (use Synaptic Package Manager)  .

gigolo
gvfs
gvfs-backends
gvfs-bin
gvfs-common
gvfs-daemons
gvfs-fuse
gvfs-libs   

Now refer here ...

[https://askubuntu.com/questions/70423/how-do-i-connect-to-a-server-with-thunar-in-xubuntu](https://askubuntu.com/questions/70423/how-do-i-connect-to-a-server-with-thunar-in-xubuntu)

---

### Post by Paddy Landau on 2021-07-30
> **dragonfly41 said:**
> Can you perhaps try a toolchain?  Nautilus > Thunar .. or Thunar directly.
Thanks, but I'd rather stick to Nautilus is possible. Constantly switching between two different file managers will be confusing.

All the gvfs packages are already installed, but not gigolo (what an odd name to use!). I installed it, and restarted Gnome and Nautilus, but it made no difference.

---

### Post by dragonfly41 on 2021-07-30
[https://forum.xfce.org/viewtopic.php?id=9779](https://forum.xfce.org/viewtopic.php?id=9779)

"Gigolo is useful front-end for helping you manage the connections, but thunar is capable of mounting them manually if needed".

Gigolo only applies to Thunar usage.

If you wish to stick with only Nautilus then another path to explore is pyextensions.

[https://www.giuspen.com/nautilus-pyextensions/](https://www.giuspen.com/nautilus-pyextensions/)

[http://www.giuspen.com/software/nautilus-pyextensions_3.4.1-1_all.deb](http://www.giuspen.com/software/nautilus-pyextensions_3.4.1-1_all.deb)

Install with GDebi.

**[P.S.]**

Package python-nautilus needs to be installed to support extensions.

...

I really find toolchains to be very useful for productivity. I don't mind using several apps in a toolchain.
It is like a pipeline. You could link Nautilus front end to FileZilla (which you use). Or PuTTY. Or gnome-terminal.

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
> [FONT=Verdana][/FONT]
  get the response, "Unable to access location. Permission denied."

But if you access the same place via the "sftp" command line client ... that does work? 
```
sftp -P PortNr youruser@remoteserver:/path/to/location
```

Does that work and immediately take you where you wanted to go? Or do you also run into some kind of error?

---

### Post by Paddy Landau on 2021-07-30
> **dragonfly41 said:**
> If you wish to stick with only Nautilus then another path to explore is pyextensions.
This is getting complicated! I'll see if I can get that to work.
> **scorp123 said:**
> … if you access the same place via the "sftp" command line client ... that does work?
Great question!

I tried:
sftp [user]@[domain]:[port]/

It just sits there doing nothing! I can't see how to pass the keyfile to it anyway.

Reading the sftp manual, it says that details are passed to ssh. This confuses me, because I have only SFTP access and not SSH access — I checked with my host's support team, and they explicitly said so.

I wish that I understood the technical background better, because from what I understand SFTP means FTP over SSH, and yet I don't have SSH access, but FileZilla can connect! I know that I can't connect via SSH, because I've tried.

---

### Post by HermanAB on 2021-07-30
Check whether the underlying network services work using nslookup, telnet, dig or ssh:
$ nslookup [domain]
$ dig [domain]
$ telnet [domain]
$ sftp -vvv [user@domain]

The error messages will tell you what is amiss.

If it doesn't work try connecting with the IP address:
$ telnet ip.add.re.ss

If you get a prompt from the server, then the network is OK.  If you don't get a prompt then fix the system before carrying on, else you are just poking a dead horse.

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
>  I tried:
sftp [user]@[domain]:[port]/


What about the syntax I used above?
```
sftp -P port remoteuser@server:/path/to/location
```

> **Paddy Landau said:**
>  Reading the sftp manual, it says that details are passed to ssh. This confuses me... 

SFTP client will read **~/.ssh/*** too. So does Nautilus.

> **Paddy Landau said:**
>  ... because I have only SFTP access and not SSH access 

Yes, you won't get an interactive shell if you access that remote system. There are various ways to achieve that. But for Nautilus **ssh://** and **sftp://** are the same thing, for practical purposes (since it's not trying to achieve an interactive shell, just transfer files...). And Nautilus does respect settings in **~/.ssh/*** too, so if key authentication is properly configured and it works on the command line, then it should also work in Nautilus.

> **Paddy Landau said:**
>  ... because from what I understand SFTP means FTP over SSH ...

Only for historical reasons. SFTP apart from sharing the same three letters and apart from using the same or similar commands in its command line client (so people don't have to relearn everything) has nothing to do with the ancient FTP dinosaur from the 1970's. **SFTP is an integral sub-protocol of SSH.**  Your description of *"FTP over SSH"* is thus not accurate.

Since "sftp" and Nautilus should respect settings in **~/.ssh/*** ... let's do this: Let's write a custom **~/.ssh/config** file for that specific remote server. The content should be something like this:

```

Host nickname-for-your-sftp-connection   # this is just an alias so you don't have to type the whole damn IP address or DNS name every time
  Hostname real-server.fqdn.internet.address-or-ip
  Port 9999   # replace with actual custom port number
  User yourusername   #  which username should be tried by default?

```

Actual example from one of my own systems:

```

Host jump
  Hostname ssh-jump-host.cloudprovider.super-long-annoying-letters-and-numbers-string-right-here.servernetwork.country.tld
  Port 32578
  User clouduseraccount

```

So ... on my system when I type in e.g. 
```
ssh jump
sftp jump

```

... or when I open Nautilus with:
```
sftp://jump
ssh://jump

```

... then either will correctly perform an auto-login on the right machine and the right custom SSH port, using the right username and the right SSH keys. I don't ever get to see a password prompt. It just works.

Try this?

---

### Post by scorp123 on 2021-07-30
> **HermanAB said:**
> If it doesn't work try connecting with the IP address:
$ telnet ip.add.re.ss

If you get a prompt from the server, then the network is OK. 

Bold of you to assume that anyone still uses telnet these days and that you'd actually get any reaction whatsoever from anyone on port 23 ... :lolflag:

---

### Post by Paddy Landau on 2021-07-30
Well, those replies have been interesting and informative, thank you!

I have made some progress.

I've made an entry in my ~/.ssh/config file for this. I named the entry sg. Using sg, I get the following results.

```
sftp -vvv sg
```
This goes as far as asking for my password, but doesn't manage to connect. The final messages after entering my private key's password read:
```
debug3: sign_and_send_pubkey: RSA SHA256:[redacted]debug3: sign_and_send_pubkey: signing using ssh-rsa SHA256:[redacted]
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
[user]@[host]: Permission denied (publickey).
Connection closed.  
Connection closed
```

Connecting from Nautilus does similar, although I can't see error messages. In the connection field, I enter:
```
sftp://sg
```
Nautilus prompts me for the private key's password, and again gives me the message, "Unable to access location. Permission denied."

Progress… but still not success!

---

### Post by scorp123 on 2021-07-30
Looks to me like there's an issue with your SSH key based authentication. If the command line does fail then so will Nautilus.

But you said FileZilla works? Can you show us via screenshots (... maybe edit them and blur out or black out sensitive information!! ...) how you configured it there? We need to replicate that configuration for the command line. Then Nautilus will work too.

---

### Post by Paddy Landau on 2021-07-30
> **scorp123 said:**
> Looks to me like there's an issue with your SSH key based authentication. If the command line does fail then so will Nautilus.

But you said FileZilla works? Can you show us via screenshots (... maybe edit them and blur out or black out sensitive information!! ...) how you configured it there? We need to replicate that configuration for the command line. Then Nautilus will work too.
Ah… good point!

I forgot that when I gave FileZilla the key, it converted it into a different format (with the same password).

But, when I use that converted key file with either sftp (command line) or Nautilus, they both fail straight away. So, that's a regression; unless I have to pass some sort of parameter to sftp or Nautilus?

To answer your question, I've attached a screenshot of FileZilla's connection details. When I ask to connect, FileZilla simply asks me for the password. (I use a password manager to hold my password, so I know that I'm using the same password each time.)

I might have to come back to this tomorrow, as I'm running out of time for today.

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
>  I forgot that when I gave FileZilla the key, it converted it into a different format (with the same password).

Yes, FileZilla uses Putty's *.PPK format ...
[https://docs.oracle.com/en/cloud/paas/goldengate-cloud/tutorial-change-private-key-format/]("https://docs.oracle.com/en/cloud/paas/goldengate-cloud/tutorial-change-private-key-format/")

On Linux there's a command line tool with the name **"puttygen"** to convert SSH keys from one format into the other:
[http://manpages.ubuntu.com/manpages/bionic/man1/puttygen.1.html]("http://manpages.ubuntu.com/manpages/bionic/man1/puttygen.1.html")

A GUI program with that same name (PuttyGen.EXE) also exists on Windows.


> **Paddy Landau said:**
>  But, when I use that converted key file with either sftp (command line) or Nautilus, they both fail straight away. 

Of course. They expect keys to be in OpenSSH's format. And they expect that key to be in **~./ssh/id_rsa**  (that's me guessing from the screenshot and what I can see on it ...)

> **Paddy Landau said:**
>  So, that's a regression; unless I have to pass some sort of parameter to sftp or Nautilus?

Not a regression, but it seems you were trying to use a SSH key in Putty's *.PPK format on two applications that expect SSH keys to be in the traditional OpenSSH format. That will not work.

> **Paddy Landau said:**
>  To answer your question, I've attached a screenshot of FileZilla's connection details. When I ask to connect, FileZilla simply asks me for the password. 

Is that really a *password* ... or rather a *passphrase*?  If that's a passphrase we may have to work with **"ssh-agent"** too so the key auto-unlocks upon your login into the system.

Background info:
[https://en.wikipedia.org/wiki/Ssh-agent]("https://en.wikipedia.org/wiki/Ssh-agent")

---

### Post by Paddy Landau on 2021-07-30
Thanks for your replies, @scorp123.
> **scorp123 said:**
> Is that really a *password* ... or rather a *passphrase*?  If that's a passphrase we may have to work with **"ssh-agent"** too so the key auto-unlocks upon your login into the system.
Passphrase, password — aren't they the same thing in this context?

Can Nautilus work with ssh-agent? I hadn't heard of ssh-agent.

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
>  Passphrase, password — aren't they the same thing in this context? 

Not exactly. If password-based login is configured then you can get in no matter what the key says. You knew the correct username and the correct password and therefore you may pass and get in. With a passphrase it gets more complicated: Without knowing or providing the correct passphrase a SSH key will not be read. So even if you do know the correct remote username and do have the right SSH key ... without passphrase the key remains locked and the login will fail no matter what.

> **Paddy Landau said:**
>  Can Nautilus work with ssh-agent? I hadn't heard of ssh-agent.

Correctly setup the SSH agent is totally transparent to the system and "it just works" for the whole OS. So... no, Nautilus doesn't know how to handle SSH agent. But then again it does not need to. I haven't used GNOME in a while but if I remember correctly then GNOME's keyring should be able to handle it too ... Googling gives me links like this one:
[https://wiki.gnome.org/Projects/GnomeKeyring/Ssh]("https://wiki.gnome.org/Projects/GnomeKeyring/Ssh")

So I guess getting it configured in GNOME's keyring would make it work for Nautilus too...

Another more traditional way of getting SSH agent to work is to e.g. add these lines to your **~/.bashrc** :

```

AGENT_PID=$(ps -ef | grep ssh-agent | awk '{ print $2 }')
if [ -z "$AGENT_PID" ]; then
  echo "Starting SSH Agent!"
  eval `ssh-agent` && ssh-add ~/.ssh/id_rsa
  setx SSH_AUTH_SOCK $SSH_AUTH_SOCK
  setx SSH_AGENT_PID $SSH_AGENT_PID
  echo "SSH Agent running (PID: $SSH_AGENT_PID)"
else
  echo "SSH Agent already running (PID: $AGENT_PID)"
fi
echo

```

So this of course would only activate if you open a new Terminal ... but if you planned on using a command line tool anyway then this might be sufficient too? It would also work for the rest of the OS, the big downside just being that you'd need to manually open a Terminal before this stuff activates.

Since you intend to work with Nautilus this is a "Plan B" at best. "Plan A" should be to get it working with GNOME keyring.

---

### Post by Paddy Landau on 2021-07-30
> **scorp123 said:**
> Not exactly. If password-based login is configured…
I think that I understand what you're getting at. This is the passphrase for the private key itself, rather than a password to access SSH. I can't get in without the private key. I could generate a private key without a passphrase, in which case I wouldn't have to bother about it at all.

> **scorp123 said:**
> So I guess getting it configured in GNOME's keyring would make it work for Nautilus too...
I added the key using ssh-add as you described. It seems to be there, because if I exit the terminal and re-enter it, "ssh-add -l" and "ssh-add -L" both list the key.

Unfortunately, this hasn't helped Nautilus.

I opened the app Password and Keys (seahorse), and I could see the key there having been saved by Nautilus. But, I don't know how to add it there otherwise.

This seems to be unreasonably difficult for something so well established!

---

### Post by dragonfly41 on 2021-07-30
This is one tutorial I came across ..

[https://brinchmann.wordpress.com/2014/03/08/tutorial-how-to-use-sftp-with-keys-with-in-nautilus/](https://brinchmann.wordpress.com/2014/03/08/tutorial-how-to-use-sftp-with-keys-with-in-nautilus/)

it refers to ssh-add and I was about to post it here.

And I vaguely recollect reading a thread about proxy settings / gnome keys being one cause of failure to connect but I've lost the link.

P.S. Back to Thunar. Does that work?

---

### Post by scorp123 on 2021-07-30
> **Paddy Landau said:**
> This seems to be unreasonably difficult for something so well established!

Let's do the basics first and try to get it working on the command line, because the command line will give us more detailed error messages if something fails. So if you place your key e.g. in **~/.ssh/id_rsa** .. does e.g. this command work now?

```
sftp -P customport remoteuser@remoteserver:/path/to/directory

```

Because on the command line even if there is a passphrase then the command line tool itself should ask for it. If that is not even happening then we must have yet another problem.

Let's do the fancy GUI stuff once we get the basics figured out.

---

### Post by Paddy Landau on 2021-07-31
> **dragonfly41 said:**
> This is one tutorial I came across…
Thanks, but again, that is for an older version of Nautilus. In that version, Nautilus pops up a dialogue where you can enter the important details. The current version doesn't do that — it seems to assume that you don't have important details to enter!

I'm not going to try Thunar, because then I'd have to be constantly switching between file managers.
> **scorp123 said:**
> Let's do the basics first…
I found that I had to explicitly tell sftp where the keyfile is, because it wouldn't take if from ~/.ssh/config.
```
sftp -P [port] -i ~/.ssh/[keyfile] [user]@[host]:/
```
The response was:
```
Enter passphrase for key '/home/paddy/.ssh/[keyfile]':
[user]@[host]: Permission denied (publickey).
Connection closed.  
Connection closed
```
I don't know what FileZilla does differently apart from using a converted keyfile. When I retry sftp with the converted keyfile, sftp complains that the key has an invalid format.

I use a password manager to type the passphrase for me; I use the same entry for FileZilla, so I know that the passphrase is correct. Also, when I type the wrong passphrase, sftp just asks me again for the passphrase, but when I enter the correct one, it thinks for a moment before failing.

---

### Post by scorp123 on 2021-07-31
Let's take a step backwards here. What was the file named when it was given to you? And were any instructions included?

And when we look inside the file you were given: Does its content look something like this:
```

-----BEGIN OPENSSH PRIVATE KEY-----
...
... lots of seemingly random symbols, letters and numbers
...
-----END OPENSSH PRIVATE KEY-----

```

... or something like this:
```

ssh-rsa AAAAABBBBBCCCCC... very long string of symbols, letters and numbers ... ZZZZZ  remoteuser@server

```


Also, while we're at it: Can you please post the output of this command:
```
ls -alR ~/.ssh
```

I want to make sure we're not getting sabotaged by incorrect file permissions. SSH is very picky.

---

### Post by dragonfly41 on 2021-07-31
> [COLOR=#000000]I'm not going to try Thunar, because then I'd have to be constantly switching between file managers.[/COLOR]
The thinking was .. if it works in Thunar then the issue is with Nautilus.
If not then it is in SSH configuration.
Process of elimination. Then you can resume focus on on Nautilus.

---

### Post by Paddy Landau on 2021-07-31
> **scorp123 said:**
> What was the file named when it was given to you?
It's provided on their website as text to copy. So, you choose your own file name.
> **scorp123 said:**
> … were any instructions included?
No. They assume that you know what you're doing, but they do explain how to add it to FileZilla.
> **scorp123 said:**
> … when we look inside the file you were given…
It looks like this:
```
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTEDDEK-Info: DES-EDE3-CBC,6F2F983101E8D2D6


... lines of excrypted code ...
-----END RSA PRIVATE KEY-----
```
The converted file that FileZilla created looks like this:
```
PuTTY-User-Key-File-2: ssh-rsa
Encryption: aes256-cbc
Comment: imported-openssh-key
Public-Lines: 12
... lines of excrypted code ...
Private-MAC: ... line of encrypted code ...
```
> **scorp123 said:**
> … Can you please post the output of this command:
Here you are. There are no subdirectories, and I've shown only the relevant files. Apart from known_hosts, all files accessible to me only.
```
$ ls -AlRd ~/.ssh
drwx------ 2 paddy paddy 4096 Jul 31 13:33 /home/paddy/.ssh

$ ls -AlR ~/.ssh
-rw------- 1 paddy paddy 2204 Jul 31 13:33 config
-rw------- 1 paddy paddy 2681 Jul 26 19:08 id_rsa_SiteGround_multisite.ppk
-rw------- 1 paddy paddy 3311 Jul 26 12:50 id_rsa_SiteGround_multisite.priv
-rw------- 1 paddy paddy  752 Jul 26 12:50 id_rsa_SiteGround_multisite.pub
-rw-r--r-- 1 paddy paddy 3740 Jul 30 17:36 known_hosts
```

---

### Post by scorp123 on 2021-07-31
> **Paddy Landau said:**
>  Here you are. There are no subdirectories, and I've shown only the relevant files. Apart from known_hosts, all files accessible to me only.

On my systems this looks like this:
```

> ls -alR ~/.ssh
/home/sysadm/.ssh:
total 43
drwx------  2 sysadm sysadm    7 Jul 31 14:41 .
drwxr-x--- 26 sysadm sysadm   67 Jul 31 22:18 ..
-rw-------  1 sysadm sysadm 3397 Jun 25 04:33 authorized_keys
-rw-r--r--  1 sysadm sysadm  581 Feb  2 09:42 config
-rw-------  1 sysadm sysadm 2590 Jul 24  2020 id_rsa
-rw-r--r--  1 sysadm sysadm  562 Jul 24  2020 id_rsa.pub
-rw-------  1 sysadm sysadm 7418 Jul  4 23:47 known_hosts

```

---

### Post by dragonfly41 on 2021-07-31
A further outlier experiment:
Back in post #23 I referred to a link which I lost.

I have found it.  

Without giving any promises of success, can you run this command and post results for scrutiny:

[FONT=monospace][COLOR=#000000]gsettings list-recursively org.gnome.system.proxy

[/COLOR]
[/FONT]

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> [FONT=monospace][COLOR=#000000]gsettings list-recursively org.gnome.system.proxy[/COLOR][/FONT]
Here are the results.
```
org.gnome.system.proxy ignore-hosts ['localhost', '127.0.0.0/8', '::1']
org.gnome.system.proxy use-same-proxy true
org.gnome.system.proxy mode 'none'
org.gnome.system.proxy autoconfig-url ''
org.gnome.system.proxy.http use-authentication false
org.gnome.system.proxy.http enabled false
org.gnome.system.proxy.http authentication-password ''
org.gnome.system.proxy.http port 8080
org.gnome.system.proxy.http host ''
org.gnome.system.proxy.http authentication-user ''
org.gnome.system.proxy.https port 0
org.gnome.system.proxy.https host ''
org.gnome.system.proxy.ftp port 0
org.gnome.system.proxy.ftp host ''
org.gnome.system.proxy.socks port 0
org.gnome.system.proxy.socks host ''
```
EDIT: See my next post

---

### Post by Paddy Landau on 2021-08-01
Things have changed.

I decided to delete the old key, and recreate it from scratch, but this time without a password. Maybe the password was a limiting factor? Maybe the key was corrupted?

This helped.

The website accepted my new key and generated a brand new user. I amended ~/.ssh/config with the new username, discarding the old username.

I've made significant progress.

FileZilla still works, obviously with the new username and key.

My alias in ~/.ssh/config for this host is called sg. This now works:
```
$ sftp sg
Connected to sg.
```
I can access the remote files normally.
(Phew!)

Now, Nautilus does the following.
```
sftp://[username]@[host]:[port]/
```
This still gives, "Unable to access location. Permission denied.[/code]

However, putting this in gives a new error.
```
sftp://sg/
```
This prompts for the password, thinks for a while, and says, "Could not display sg (sftp). The file is of an unknown type."

So, that's progress, I guess. I just don't know how to proceed from here.

Thank you for all the time that you've put into this so far!

---

### Post by dragonfly41 on 2021-08-01
My idea was a blind alley following [this old thread]("https://askubuntu.com/questions/672518/cannot-connect-to-ftp-via-nautilus-but-filezilla-can").

Your proxy mode is 'none'. If it had been set to 'auto' we might have pursued it further.

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> My idea was a blind alley following [this old thread]("https://askubuntu.com/questions/672518/cannot-connect-to-ftp-via-nautilus-but-filezilla-can").

Your proxy mode is 'none'. If it had been set to 'auto' we might have pursued it further.
Well, thank you for your attempts. I do appreciate your time and effort.

I hope that someone else has an idea.

---

### Post by dragonfly41 on 2021-08-01
If I were in your shoes I would jump out of this alligator pit and try Nautilus in a newly created guest user account to test if the same problems arise.  Or even in Ubuntu in a fresh virtual machine in VirtualBox.

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> If I were in your shoes I would jump out of this alligator pit and try Nautilus in a newly created guest user account to test if the same problems arise.  Or even in Ubuntu in a fresh virtual machine in VirtualBox.
Good idea!

I created a brand new user, and copied across just the private key and config.

It's the same. I can access the remote server with sftp, but Nautilus still complains, "[COLOR=#000000]Could not display sg (sftp). The file is of an unknown type."[/COLOR]

---

### Post by dragonfly41 on 2021-08-01
Another user with same problem .. but no answer ..

[https://askubuntu.com/questions/1251293/nautilus-from-20-04-will-not-remember-custom-extensions-on-sftp](https://askubuntu.com/questions/1251293/nautilus-from-20-04-will-not-remember-custom-extensions-on-sftp)

Another reference ..

[https://linuxize.com/post/how-to-use-linux-sftp-command-to-transfer-files/](https://linuxize.com/post/how-to-use-linux-sftp-command-to-transfer-files/)

I would just use PuTTY client until this is solved. Law of diminishing returns applies.

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> Another user with same problem .. but no answer ..
Well spotted! I didn't find that in my searches. It seems that that person can connect, and only gets this error when accessing specific files. Whereas I get that error regardless when trying to connect in the first place.
> **dragonfly41 said:**
> Another reference ..
Thanks. That's for CLI commands. I've managed to make the CLI commands work. It's only Nautilus that's giving me problems!
> **dragonfly41 said:**
> I would just use PuTTY client until this is solved. Law of diminishing returns applies.
Well, I have FileZilla. I'll use that until I can get Nautilus to work. FileZilla is an excellent app, which usually does everything that I need, but for this specific host, Nautilus would be more convenient because of the workflow.

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> Another user with same problem .. but no answer ..
Actually, this link has proven useful. Comparing to other servers from the same host…

I can use the other servers without a problem from Nautilus. However, to access them, I need to give the correct starting directory, /home/[name]. E.g.
sftp://exa/home/mystart

But, the one that's giving me problems uses a virtual disk. The top-level directories within that virtual disk are directories from other servers (plural). I think that when Nautilus attempts to connect, it gets confused and fails.

It may be that this specific server just can't be used with Nautilus?

---

### Post by dragonfly41 on 2021-08-01
Do you have write permissions on that server?

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> Do you have write permissions on that server?
Yes, I do. I can create, delete and modify files in it.

But.

Now that you mention it, in all of its subdirectories, yes, but not in the "root" (home).

That shouldn't make a difference, though, because I can still access the server through sftp or FileZilla, right? Nautilus must be accessing the server somehow differently from sftp and FileZilla.

---

### Post by dragonfly41 on 2021-08-01
[Try this guide]("https://dev.to/yousufbasir/add-remote-server-location-to-ubuntu-nautilus-using-ssh-2i77")

And a further thought.

You wrote "I've managed to make the CLI commands work. It's only Nautilus that's giving me problems!"

Can you open terminal *from within Nautilus* (right click on folder, Open terminal here) and then apply terminal commands?

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> [Try this guide]("https://dev.to/yousufbasir/add-remote-server-location-to-ubuntu-nautilus-using-ssh-2i77")
Thank you. From the error messages, it seems that I can already connect. It's just that, once connected, Nautilus doesn't know what to do with it, almost as though the directory isn't a directory, and so it fails and disconnects.
> **dragonfly41 said:**
> You wrote "I've managed to make the CLI commands work. It's only Nautilus that's giving me problems!"
Can you open terminal *from within Nautilus* (right click on folder, Open terminal here) and then apply terminal commands?
I've just tested and, yes, I can; but remember that the connection has already failed, so this is just the normal terminal.

As a reminder from an earlier post, this specific server can be accessed via SFTP, but not SSH, by the host's design (probably not deliberately). (I have asked for SSH access, but they'll have to amend their systems to make it work, so it probably won't happen.)

That's a bit confusing, because SFTP connects via SSH, so I don't know how they prevented us from accessing the host with SSH while allowing it with SFTP! Maybe something to do with the port, I don't know? As I say, preventing SSH was most likely unintentional, probably a side effect of however they created the virtual disk.

---

### Post by dragonfly41 on 2021-08-01
[Perhaps they use this ploy?]("https://serverfault.com/questions/354615/allow-sftp-but-disallow-ssh")

---

### Post by Paddy Landau on 2021-08-01
> **dragonfly41 said:**
> [Perhaps they use this ploy?]("https://serverfault.com/questions/354615/allow-sftp-but-disallow-ssh")
Maybe!

---

### Post by sudodus on 2021-08-01
> **Paddy Landau said:**
> Thank you. From the error messages, it seems that I can already connect. It's just that, once connected, Nautilus doesn't know what to do with it, almost as though the directory isn't a directory, and so it fails and disconnects.

I've just tested and, yes, I can; but remember that the connection has already failed, so this is just the normal terminal.

As a reminder from an earlier post, this specific server can be accessed via SFTP, but not SSH, by the host's design (probably not deliberately). (I have asked for SSH access, but they'll have to amend their systems to make it work, so it probably won't happen.)

That's a bit confusing, because SFTP connects via SSH, so I don't know how they prevented us from accessing the host with SSH while allowing it with SFTP! Maybe something to do with the port, I don't know? As I say, preventing SSH was most likely unintentional, probably a side effect of however they created the virtual disk.

Maybe someone [else also] did not want people to log in and run commands via ssh and therefore made the system only allow running sftp.

---

### Post by dragonfly41 on 2021-08-01
Now I have just read about this approach .. [reverse SSH tunnelling]("https://www.howtogeek.com/428413/what-is-reverse-ssh-tunneling-and-how-to-use-it/")

---

### Post by scorp123 on 2021-08-01
> **Paddy Landau said:**
>  I decided to delete the old key, and recreate it from scratch, but this time without a password.

**You** created that passphrase??  Should have said that.

---

### Post by scorp123 on 2021-08-01
> **Paddy Landau said:**
>  Now that you mention it, in all of its subdirectories, yes, but not in the "root" (home).

Yes, because you're obviously in a SFTP-only jail.

> **Paddy Landau said:**
>  That shouldn't make a difference, though, 

But it does.

Can we now please try that command of mine again?

```
sftp -P customport remoteuser@server:/path/to/location
```

---

### Post by Paddy Landau on 2021-08-02
> **dragonfly41 said:**
> Now I have just read about this approach .. [reverse SSH tunnelling]("https://www.howtogeek.com/428413/what-is-reverse-ssh-tunneling-and-how-to-use-it/")
That's nice, but there's a catch-22. I can't SSH to the remote computer, but in order to set up the remote computer, I have to SSH to it. Hmm.
> **scorp123 said:**
> **You** created that passphrase??  Should have said that.
The the host's website created the initial key. So, to create the passphrase-less key, I deleted the initial key, created my own key, and the host's website uploaded the public key.
> **scorp123 said:**
> Yes, because you're obviously in a SFTP-only jail. … But it does.
OK.
> **scorp123 said:**
> Can we now please try that command of mine again?
This is interesting because it's confusing.

When I run this command, it works.
```
$ sftp sg
Connected to sg.
sftp> pwd
Remote working directory: /
sftp> ls
[shows list of subdirectories]
```

But, I open ~/.ssh/config, and copy-and-paste its "sg" values into your command, and it fails! Square brackets indicate the copied values.
```
$ sftp -P [customport] [remoteuser]@[server]:
[remoteuser]@[server]: Permission denied (publickey).
Connection closed.
Connection closed
```
For the path, I've tried omitting it (as shown above); connecting to root (/); and connecting to a subdirectory that I know is there.

It's strange. I have carefully checked that I copied-and-pasted the correct values, in full, and without extraneous characters, from ~/.ssh/config, so my brain says that it should be identical to "sftp sg". Clearly, I'm wrong!

However, as I mentioned earlier, I seem to have made progress to the point where Nautilus can now connect. It's just that, once connected, Nautilus doesn't know what to do with it, almost as though the directory isn't a directory, and so it fails and disconnects.

I think that all the help that I've received here has got to the point where we have a successful Nautilus connection; unfortunately, it has a failed "What do I do with this?" response from Nautilus.

I downloaded and tried Thunar, and it gave a weirder result. It thought for a bit, then opened my password manager! Why — and how — does it do that? I have uninstalled Thunar.

I think that, at this point, the question changes from "How do I connect using Nautllus?" to "How do I get Nautilus to understand what to do once connected?"

I'm going to accept defeat on this one, because it's taking too much time, and I at least have access via FileZilla or the terminal.

Thank you for all of your time and efforts.

**EDIT: See my next post…**

---

### Post by Paddy Landau on 2021-08-02
New information. I realised that the two sftp commands weren't identical, because I forgot to add the key. This works:
```
sftp -P [customport] -i ~/.ssh/[privatekey] [remoteuser]@[server]
```
That one is identical to "sftp sg".

---

### Post by dragonfly41 on 2021-08-02
Re: reverse SSH tunnelling

> That's nice, but there's a catch-22. I can't SSH to the remote computer, but in order to set up the remote computer, I have to SSH to it. Hmm.

I have not tried this myself but as I understand the article the general idea is *not* to SSH from local to remote, but rather the reverse (from remote to local) then slip in an SSH connection within that connection. Quite how you start this ping pong match I don't know.

---

### Post by scorp123 on 2021-08-02
> **dragonfly41 said:**
> Re: reverse SSH tunnelling

I have not tried this myself but as I understand the article the general idea is *not* to SSH from local to remote, but rather the reverse (from remote to local)

I use reverse-SSH daily. For Paddy to do this he'd need a shell account on the remote system to initiate the connection... and he does not have that as he has said multiple times.

Reverse-SSH is useful e.g. to create *"your own VPN"*. Example:

Where I work my office PC can SSH out, but the firewalls there forbid to SSH in. I am supposed to use Windows-based Citrix nonsense that most of the time does not work properly. So I wrote a systemd service for my work PC that SSH's into my system at home with a reverse tunnel. 

[https://ubuntuforums.org/showthread.php?t=2460821&p=14041285#post14041285]("https://ubuntuforums.org/showthread.php?t=2460821&p=14041285#post14041285")

And so this SSH connection sits there on my server at home. And when I want to get back into my work PC I can use that reverse SSH tunnel and get back in, even though the firewalls were supposed to block this. They can't. Because the connection was initiated from my work PC on the inside and that traffic is allowed.

The network security guys at my work place probably would not be happy if they knew about this (because I'm basically circumventing and bending their firewall rules whichever way I like...), but then again they don't strike me as being very "competent" anyway. And I'm pretty safe from any consequences. So using reverse SSH tunnels is not something I'd recommend risking if you can be fired easily from your job or if you are easy to replace. Only do this if you are like me in a BOFH position and they fear firing you more than keeping you :twisted:

But back to Paddy and his problem: NO, reverse SSH is not an option here since he does not have a shell account on the remote system and can neither SSH in and therefore not SSH out.

---

### Post by scorp123 on 2021-08-02
> **Paddy Landau said:**
> New information. I realised that the two sftp commands weren't identical, because I forgot to add the key. This works:
```
sftp -P [customport] -i ~/.ssh/[privatekey] [remoteuser]@[server]
```
That one is identical to "sftp sg".

Yaaay!! \\:D/  So ... how is that private key named at the moment?  If we can get the "sftp" command line tool to pick it up automatically then Nautilus might start working too... Because the error message that you were getting about *"Permission denied (publickey)"* was clearly about the tool not finding the key. We have to make it load that key... 

I will check if there are more magic parameters we can put into **~/.ssh/config** ... maybe there's a way to get the key loaded for exactly that connection. There should be.

---

### Post by scorp123 on 2021-08-02
Yes!!

Of course there is a parameter!  So ... your **~/.ssh/config** file should look like this:

```

Host nickname-for-your-sftp-connection
  Hostname real-server.fqdn.internet.address-or-ip
  Port 9999
  User yourusername
  IdentityFile /path/to/your/keyfile/id_rsa

```

Now your command should work just like this:
```
sftp sg
```

No specifying of any ports, no specifying of any key file, no error messages. Done correctly this should just work. And so should Nautilus, finally.

---

### Post by Paddy Landau on 2021-08-02
> **scorp123 said:**
> Now your command should work just like this:
```
sftp sg
```
Yes, you might have missed a couple of my posts. To summarise:

[LIST]
[*]"sftp sg" works perfectly.
[*]FileZilla works perfectly.
[*]Nautilus seems to connect with "sftp://sg", but then fails because it doesn't know what to do with "The file" (whatever "The file" might be): *Could not display "sg (sftp)". The file is of an unknown type.*
[*]I can access other servers from the same host using the same method, but unlike "sg", they don't use virtual disks. That's one big difference. The other big difference is that I can SSH into those other servers. Only "sg" prevents SSH.
[/LIST]
All of that makes me think that some configuration or processing in Nautilus is incorrect, failing to understand the "sg" server's virtual disk. After all, both FileZilla and sftp understand it just fine.

---

### Post by scorp123 on 2021-08-02
> **Paddy Landau said:**
> [*]Nautilus seems to connect with "sftp://sg", but then fails because it doesn't know what to do with "The file" (whatever "The file" might be): *Could not display "sg (sftp)". The file is of an unknown type.*

What if you specify the target path right away? e.g. try to access:
```
sftp://sg/path/to/where/you/are/supposed/to/go
```

And not just "sftp://sg" ... does that make any difference in Nautilus?

I'm starting to wonder if this might be some strange Nautilus issue... and maybe the earlier suggestions about trying this in e.g. Thunar were not so bad. If it's not too much of a burden: You could install a VM with Xubuntu and then try it out in there with Thunar. Just to see if Thunar when confronted with the same "~/.ssh/config" file will run into the same issue or not.

Another thing we might try: SSHFS

We'd let SSHFS handle the mounting of the SFTP directory. To Nautilus this would just look like a local folder.
[https://askubuntu.com/questions/87699/can-nautilus-setup-sshfs-like-instead-of-sftp]("https://askubuntu.com/questions/87699/can-nautilus-setup-sshfs-like-instead-of-sftp")
[https://furick.com/icbd/2017/08/mount-a-sftp-connection-to-a-folder-in-ubuntu-linux/]("https://furick.com/icbd/2017/08/mount-a-sftp-connection-to-a-folder-in-ubuntu-linux/")

I've read on numerous pages that SSHFS uses SFTP in the background to transfer files (and not plain "SSH" as the name might suggest). So if that is true then using SSHFS might work too.

---

### Post by Paddy Landau on 2021-08-02
> **scorp123 said:**
> What if you specify the target path right away?
That gives a different response.
"This location could not be displayed. Sorry, could not display all the contents of "[path]": The connection is closed (the underlying SSH process exited)."
So, if "the underlying SSH process exited", perhaps Nautilus is using SSH and not SFTP?
> **scorp123 said:**
> I'm starting to wonder if this might be some strange Nautilus issue…
I fully agree. It must be Nautilus at fault.
> **scorp123 said:**
> … maybe the earlier suggestions about trying this in e.g. Thunar were not so bad.
Well, I tried Thunar, and it was weird. It thought for a bit, then opened my password manager! How bizarre. There was no connection.
> **scorp123 said:**
> If it's not too much of a burden: You could install a VM with Xubuntu and then try it out in there with Thunar. Just to see if Thunar when confronted with the same "~/.ssh/config" file will run into the same issue or not.
I'll try that later today if I have time, and let you know.
> **scorp123 said:**
> Another thing we might try: SSHFS
Again, later today if I have time. I'm a bit overwhelmed at the moment.

I'll let you know, today or tomorrow.

Thanks again!

---

### Post by Paddy Landau on 2021-08-02
> **scorp123 said:**
> … install a VM with Xubuntu and then try it out in there with Thunar.
I installed Xubuntu into a VM.

I had the same results.

As with Nautilus, Thunar can open the other servers fine, but with "sg", it also complains that it doesn't understand the file that it's supposed to open.

As an experiment, I installed Nautilus, but the results were, again, identical.
> **scorp123 said:**
> Another thing we might try: SSHFS
I can't make sshfs work, even for the other servers that work perfectly with Nautilus, etc. :(


I'm going to let this go. It's taken an awful lot of time, and I rather suspect that it's simply not going to work. I'll live with FileZilla.

---

