---
title: "Need help with SFTP server"
date: 2014-07-09
forum: General Help
---

### Post by Zukaro on 2014-07-09
I was wondering if anyone knew how I could hide my SFTP server from being seen from browsers.  As it is currently, if I go to my server's address in my browser (and stop my browser from blocking access to the port I'm running this on) it shows me the entire file system.  As a result, I'm able to view anything on the server without logging in.

I'm not sure how to fix this.  At no point does the browser ask me to login either in order to see all this stuff (if it asked me to login there would be no issue (which is why I tested this in the first place, I wanted to make sure my browser would either be unable to display this, or ask me to login first)).


I'm using Ubuntu Server 14.04, and am using OpenSSH as the SFTP server.  I've not setup any form of a chroot jail sort of thing, as this SFTP server will only be used by myself, so I'm not worried about having access to the entire file system once logged in.  What I don't want though, is for random people to have the ability to see what's on my server.

---

### Post by TheFu on 2014-07-10
sftp is part of ssh.  Methods used to secure ssh will also secure sftp.  Those include fail2ban, not running on the standard port and never using passwords for authentication, only ssh-keys.  If someone can authenticate with your keys, then they deserve access.

---

### Post by Zukaro on 2014-07-10
> **TheFu said:**
> sftp is part of ssh.  Methods used to secure ssh will also secure sftp.  Those include fail2ban, not running on the standard port and never using passwords for authentication, only ssh-keys.  If someone can authenticate with your keys, then they deserve access.

This isn't an authentication issue (at least, I don't think it is).  The browser doesn't ask for a username or password at any point, it just shows the filesystem.  Files are not modifiable but are downloadable (essentially it's all read only), and I'm not sure how to fix this.  However, I have been unable to replicate the results.  But I feel as if this is due to the browser not handling SFTP properly, as the browser seems to refuse to attempt to load the page anymore (it gives no error messages and doesn't even attempt to load the link).

I have tried changing the permissions of the home directory so that "other" has no access.  I'm not sure if this will make a difference or not though when it comes to this issue specifically (and due to being unable to get the browser to show me the page anymore (which occurred before these changes), I don't seem to have a way to test this).

---

### Post by TheFu on 2014-07-10
If the URL isn't "sftp://" then you aren't using sftp in the browser and have a far worse security issue to solve.
ssh/scp/sftp all use the userid provided on the remote system - the userid of the current system is automatically provided if no userid is provided for CLI-based ssh/scp/sftp connections. Don't know anything about a brower supporting sftp - never heard of that.

If you are testing this from the same machine, don't expect it to work. Hopefully the browser will see this is wrong and make a local file system connection to avoid the encryption overhead.

So .... exactly which program is being run on the client?  Also the exact URL used would be extremely helpful.

---

### Post by Zukaro on 2014-07-10
> **TheFu said:**
> If the URL isn't "sftp://" then you aren't using sftp in the browser and have a far worse security issue to solve.
ssh/scp/sftp all use the userid provided on the remote system - the userid of the current system is automatically provided if no userid is provided for CLI-based ssh/scp/sftp connections. Don't know anything about a brower supporting sftp - never heard of that.

If you are testing this from the same machine, don't expect it to work. Hopefully the browser will see this is wrong and make a local file system connection to avoid the encryption overhead.

So .... exactly which program is being run on the client?  Also the exact URL used would be extremely helpful.

The URL begins with sftp://
I wasn't expecting it to work when I tried it (and I had to allow the port I'm running this on through the browser, as by default FireFox blocks ports which wouldn't normally be used) but for some reason it connected.  I'm not testing it on the same machine, I have it on another machine running on the same LAN.

The way I connect to the sftp server normally is using Nautilus, I tested to see if I could connect using FireFox as I wanted to make sure it would not be accessible from the browser.


The browser no longer attempts to load the page however, so I'm not sure what happened the first time, but considering I could see the entire file system I obviously want to look into this.  The URL is: sftp://192.168.2.5:21/ (I'm currently only running this on my LAN).

I think after rebooting the sftp server I was no longer able to access it via the browser however, and have since been unable to replicate these results.  I had searched around online about the issue and found that it seems someone else had a similar issue (but I didn't find any solution, and it seems the issue went away after he reboot the server as well).  So I'm not sure if this is just a bug with OpenSSH or if I screwed up somewhere.

---

### Post by TheFu on 2014-07-10
I can only guess that nautilus mounted it using gvfs and firefox saw that mount and used it. Eventually, it became stale and died.  I was unaware that any web browser supported sftp. News to me.

Is there a chance that you told nautilus to remember your credentials or that they match between the 2 systems or that you've setup key-based authentication?

---

### Post by Zukaro on 2014-07-11
> **TheFu said:**
> I can only guess that nautilus mounted it using gvfs and firefox saw that mount and used it. Eventually, it became stale and died.  I was unaware that any web browser supported sftp. News to me.

Is there a chance that you told nautilus to remember your credentials or that they match between the 2 systems or that you've setup key-based authentication?

I've set Nautilus to remember my credentials

---

### Post by Zukaro on 2014-07-12
I managed to get Firefox to connect again, here's a screenshot.


[ATTACH=CONFIG]254671[/ATTACH]

---

### Post by TheFu on 2014-07-12
Sftp doesn't listen on port 21 - unless you changed the default?

So - that means firefox is connected via FTP - which is bad, bad, bad and shouldn't be used by 99.9999999% of the world.

---

### Post by Zukaro on 2014-07-12
> **TheFu said:**
> Sftp doesn't listen on port 21 - unless you changed the default?

So - that means firefox is connected via FTP - which is bad, bad, bad and shouldn't be used by 99.9999999% of the world.

I changed the port to use 21 as I won't be using that port for anything else.  I don't see how Firefox could be connected using FTP if I'm using SFTP though?

---

### Post by TheFu on 2014-07-12
You are correct, but mozilla is full of bugs so I never assume something that doesn't make sense to me isn't broken. I trust the port of the "sftp" - hence my comment.

ftp works over port 20 and 21 doesn't it?  Just seems odd to use a port reserved for a different service to me.  Generally, I put ssh/scp/sftp on high ports 60K+ if I don't want them on the default. This is usually handled at the router, the machine settings stay with the default - so I explicitly must use a different port when external, but defaults work on the LAN.

However ... I opened firefox and pointed it at a few different machines with ssh/scp/sftp running.  It uses ssh-keys, of that I'm certain.  I moved the ~/.ssh/ directory and retested - it failed.

---

