---
title: "Good SSH client for noob?"
date: 2008-01-21
forum: General Help
---

### Post by Yuck on 2008-01-21
Hi,
I need to change the permissions on one file for my website, it's an oscommerce site. I've recently changed to Fasthosts(UK) and there techs tell me that I am not allowed to change permissions to 444 via ftp, which is what I have always previously done.
They tell me I can use a thing called putty which is a windows client, a non starter for a linux user :)

So as this is probably a one off thing, is there a really simple client that will just allow me to change permissions for this one file? If it is a commmand line application then the command needed would really be a bonus.

Thanks in advance

---

### Post by killermist on 2008-01-21
There's always the traditional ssh command

ssh user@host -p port

There's also lftp (if installed)
lftp sftp://user@host:port

konqueror has a SFTP/Fish IOslave that can handle it.
(in the konqueror address bar)
sftp://user@host:port
or
fish://user@host:port

[more notes]
If you're already comfortable with the command line, SSH is probably your best friend.
If you're more comfortable with a GUI, then konqueror is a better choice.  I don't know if Gnome has anything equivalent.
lftp is console based, but designed more for file transfers than just command execution.

---

### Post by HermanAB on 2008-01-21
I'd second Konqueror with the fish: ioslave, but I think Nautilus (the Gnome default file manager) can also do ssh.  You just have to click around in the menus to figure out how.

---

### Post by killermist on 2008-01-21
Some systems don't cooperate with fish.  
In particular, I've had problems if the system doesn't have bash.  This happens primarily on BSD machines, where the default shell is TCSH, and trying to figure out how to get bash loaded is impossible.  (the BSD machines I've had to deal with.  Not universally)
SFTP, on the other hand, tends to work almost universally.  I think there is also a backup IOSlave that can handle it as SCP, but I don't know if that would permit changing file permissions, which seems to be the goal.

---

### Post by Yuck on 2008-01-21
Now fixed , I didn't read killermists clear instructions.
Thanks again!



Hi again,
Thanks for all the info.
I've installed konqueror, and I've set up my shell password in my hosting control panel. I'm assuming that I simply enter the ssh host address in the top address bar? ie: [http://ssh.mydomain.com](http://ssh.mydomain.com) ?
At the moment I'm getting the following error message:

```
An error occurred while loading http://ssh.mydomain.com:
Timeout on server
 Connection was to ssh.mydomain.com at port 80
```

When setting my shell password it did say it will take up to an hour before it gets registered, I'm assuming I just need to wait a little longer.

Cheers.

---

### Post by killermist on 2008-01-21
For konqueror, use the location:
sftp://ssh.mydomain.com

It should pop up a dialog asking for username and passwoed credentials.  From there, it should drop you into your home directory.  Provided everything worked correctly, you should be able to find your file and chmod it using context menu/properties and reset them to what you need.

[edit]
Oh.  Now I'm the one that didn't understand.
I read more about the problem after you said you had resolved it, and thought you still had a problem.  Glad to hear you worked it out.

---

