---
title: "Question on installing a FTP server"
date: 2024-07-18
forum: General Help
---

### Post by satimis on 2024-07-18
Hi all,

I have to ask a question which I have done long time ago.  "How to install FTP server on my PC ?

I have >40 WP websites running on HostGator server.  To admin the files on each website I can install FileManager plugin on each of them.  But I have to install >40 FileManager plugins.  Therefore I start the idea to setup a FTP server on my PC to remote-admin all my websites.  I have done it long time before and it worked.

I found following document;
Set up an FTP server
[https://ubuntu.com/server/docs/set-up-an-ftp-server](https://ubuntu.com/server/docs/set-up-an-ftp-server)

Please advise whether I can install the FTP server on my daily working PC drive.  OR I have to add a new SSD on the PC to install the FTP server?

Thanks

Regards

[B][COLOR="#FF0000"]EDIT
====
OR is there a better way ?[/COLOR][/B]

---

### Post by currentshaft on 2024-07-19
How would installing FTP on your desktop help you administer remote websites? Your question makes little sense to me. Consider using SSH for remote access to files and hosts instead.

---

### Post by ActionParsnip on 2024-07-19
If you can SSH to the server then you have an SFTP server. You can connect securely using your usual username and password and you will get the permissions of your user

---

### Post by ActionParsnip on 2024-07-19
> **currentshaft said:**
> How would installing FTP on your desktop help you administer remote websites? Your question makes little sense to me. Consider using SSH for remote access to files and hosts instead.
You can upload new web server files to the server using FTP (yuck) then restart the service. One way I can think of

---

### Post by dragonfly41 on 2024-07-19
Apart from primary advice to use SSH you could experiment with installation of webmin.

---

### Post by satimis on 2024-07-19
> **dragonfly41 said:**
> Apart from primary advice to use SSH you could experiment with installation of webmin.
Hi@dragonfly41,

Good suggestion.  Thanks.

I have run both SSH and FTP before without problem but never tried Webmin.  I'm interested to learn technology new to me.

On Googling I found following documents.
How to Install Webmin on Ubuntu 22.04 and How to Use it
[https://www.ssdnodes.com/blog/how-to-install-and-use-webmin-on-ubuntu-22-04/](https://www.ssdnodes.com/blog/how-to-install-and-use-webmin-on-ubuntu-22-04/)

How To Install Webmin on Ubuntu 22.04
[https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-22-04)

I suppose that it is sufficient for me to start?  Do I need a new drive?  Or just install Webmin on a Ubuntu 24.04 desktop PC which is my daily working PC.  Thanks

Regards

---

### Post by dragonfly41 on 2024-07-19
Well I have not used it for some time but it ran on my previous 20.04. I am on 22.04 so I think that now you have reminded me I will now install it again for personal use.  I am an enthusiast of desktop automation.  For example you can link webmin (and other apps) to Albert (another recommendation) through Python plugin.
I am a bit busy but will install webmin to compare notes.  

I do understand that SSH is preferred when dealing with the big bad world out there but I'm fairly safe I hope in my cocoon here. What I like about webmin is that custom scripts can be written for all number of tasks.

P.S. to answer your question you do not need a new drive. Just install webmin on your 22.04 desktop (pseudo server) which I will now do, to sync notes.  You access through [https://localhost:10000](https://localhost:10000) from memory. Anyways instructions are clear and there is a webmin forum. A refinement is to install ngrok so that you can access webmin dashboard from afar. But security eyebrows raised at this point.

---

### Post by satimis on 2024-07-19
> **ActionParsnip said:**
> You can upload new web server files to the server using FTP (yuck) then restart the service. One way I can think of
Hi@ActionParsnip,

It is the suggestion of a Moderator of WordPress Org Forum, after reading my report of "Low Severity Problems" warning which is caused by 4 now_longer_used packages.   I'm not the only user suffering this warning.  Then the moderator suggested me to access my server via SFTP or FTP removing them if I don't expect to install "File Manager" plugin on all my websites.

The easiest way to get the job done is on File Manager plugin.  I have done it on several of my websites, running File Manager, to rename those problematic packages to "packagename.old" then done.  But not all my >40 websites have "File Manager" plugin installed.  I have to install it, at least, on >30 websites therefore the Moderator suggested me using SFTP or FTP to get the problem fixed.

Regards

---

### Post by currentshaft on 2024-07-19
> **satimis said:**
> It is the suggestion of a Moderator of WordPress Org Forum, after reading my report of "Low Severity Problems" warning which is caused by 4 now_longer_used packages.   I'm not the only user suffering this warning.

We are not WordPress users. We have no idea what this means.

> **satimis said:**
> Then the moderator suggested me to access my server via SFTP or FTP removing them if I don't expect to install "File Manager" plugin on all my websites.

This moderator is giving you dangerous advice which will put your data at risk.

> **satimis said:**
> The easiest way to get the job done is on File Manager plugin.

It's really not. The easiest way is to connect to the remote instance over SSH and have direct access to the files you need to change, without installing anything else and without using a network protocol from 50 years ago. SSH is secure, efficient and easy to use.

Both of the other suggestions to use File Manager or webmin are also going to create additional risk for your data.

---

### Post by TheFu on 2024-07-19
To push updates to webservers, I'd say to use rsync as part of a script that does a few other things, like optimizing images for websites, and any conversions of input files into the HTML you probably want.  I routinely use pandoc to convert markdown files into other formats (html, text, PDF, and sometimes presentations).  The key thing is to have a script that updates the website(s) in a repeatable way.  Scripting means it is 1 command and you are done. You can run it 1 time or 50 times, the results should be the same.  rsync prevents sending files that haven't changed, so it is more efficient (there are exceptions, but not many).

rsync uses ssh by default, so security is well handled, assuming your webhost isn't stupid and allows only FTP access. If they are stupid, they need to be fired.  Plain FTP should have died out around 2002. Since that time, there have been multiple, better, more secure, methods.  ***Friends don't let friends use plain FTP for anything.***

There are many things that Wordpress has been doing for decades that make little sense.  Their use of plain FTP for updates is one.  They know this.  They aren't dumb, but they realize that any change will freak out non-technical people.  Back when MS-Windows supported plain FTP directly in File Exploder, perhaps it made _some_ kind of sense.  I disagree, but we are all free to have our opinions. 

SFTP is natively supported for almost all Linux File managers. Nothing special should be needed.  Just install the "ssh" package on your desktop and that should be enough.  To make it easier, you can setup ssh-keys between your desktop and the remote systems.  Use **ssh-copy-id** for this after you create 1 or more ssh-keys.  All ssh-based tools honor ssh-keys, so rsync and sftp will uses those keys.  Unlock the key 1 time per login to your desktop.  That should make all ssh-based connections available without any password prompts until you logout of your desktop.  ssh with keys is both more secure AND more convenient.  That never happens with security stuff. This is the only instance I know about where it happens.  You should use it.

---

