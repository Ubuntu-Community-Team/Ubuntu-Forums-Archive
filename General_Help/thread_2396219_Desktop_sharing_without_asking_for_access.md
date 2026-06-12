---
title: "Desktop sharing without asking for access"
date: 2018-07-12
forum: General Help
---

### Post by donb21 on 2018-07-12
When configuring screen sharing, the selections force the remote user to enter a password or have someone at the box to grant access on every connection.  How do you configure stock Ubuntu/Vino desktop sharing to not require approval for access and just connect and use it?

---

### Post by HermanAB on 2018-07-12
Hmm, I think that in a few days, after you were hacked and re-installed your machine, you should learn how to use SSH instead.
:D

---

### Post by TheFu on 2018-07-12
[http://ubuntuhandbook.org/index.php/2016/07/remote-access-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/07/remote-access-ubuntu-16-04/) shows options that don't need to be clicked. Looks pretty easy.  Is that not working?  What have you already tried?

I don't use VNC and allowing remote desktop control/viewing without requesting permissions would be a huge security failure everywhere I worked,  but there are a few situations where it could be handy - like in a classroom.

But like Herman says, if you allow access over the internet with this protocol, expect to be hacked.  Heck, the TSA was hacked doing something similar.

---

### Post by donb21 on 2018-07-12
Right, as soon as I read your replies, I realized that I was using a password on my current box, but it worked a little differently.  It uses the XFCE desktop, which came pre-configured with desktop sharing; I assumed the password setup was part of the client, not the server.  It's pretty much the same experience, so I'll use the require-a-password method (which worked fine).

I agree on the security concerns, my company would have automatically shut it down, without asking.  This is a home application where I'm using the box as a PVR, but still, a password is a good move. 

While we're on the topic, you mentioned ssh....I've already setup Putty for terminal sessions, is there something else you had in mind?

Don

---

### Post by TheFu on 2018-07-12
Use ssh-keys, never passwords, for access to network resources.  If you are using passwords for any network authentication, you've already failed security-101.  I suspect putty has a way to generate the public/private keys - google should help with that. I haven't used putty in about a decade.  On Linux, it is **ssh-keygen** (use 2048 or larger keys, probably want ed25515, not  the default) and use **ssh-copy-id** to push the public key to the server.  You can manually place the public key correctly if you like, but be very careful with  newlines, directory and file permissions. Get those wrong and ssh won't work.

If you are hoping for outside access to the LAN, either use a key-based ssh tunnel or a CA+key based VPN that you host. Commercial VPNs don't help.

There are thousands of things to know.  Those take time to learn.  Main things are to stay patched, have weekly, automatic, backups, if you don't have daily ones, always use keys, always block brute force attempts, and use some effective method to check the system logs daily.   Finding an issue early means a quick and usually painless solution.  Was helping someone who didn't do these things and let a problem continue for months. There was APT corruption. Not good. Expect he is wiping that system and starting over all because the system was allowed to run out of storage a few months ago and automatic security patching was left enabled.

---

### Post by HermanAB on 2018-07-13
Howdy,

If you configure SSH with keys, then it doesn't ask for passwords.

Using SSH, you can run remote graphical applications transparently on your local desktop:
$ ssh herman@server "gedit /home/herman/filename.txt"

The remote gedit will then pop up transparently on my local desktop - indistinguishable from gedit editing a file on the local machine.

In essence, if you already have a perfectly nice desktop system on your local machine, then it is quite pointless and tremendously inefficient to forward a remote desktop over a network, only to obliterate your local desktop.

SSH is therefore a more 'targeted' remote management system, that enables one to efficiently administer and use remote machines as if they are extensions of your local machine.

---

### Post by TheFu on 2018-07-13
Herman is correct, except that having a local X/Server is required for the **ssh -X** method to work.
Also, I've not had acceptable performance when using it outside the LAN.  It really needs 50+ Mbps connectivity - really throughput, not what any connection claims.  Inside the LAN, using remote X is much more convenient than any other method, by far.

There are X/Servers for Windows, but I found that running a small Linux virtual machine was better back when I still used Windows that way.  If you have a Linux desktop, this stuff sorta "just works" and works really well.  The free X/Servers weren't all that great.The commercial ones were full implementations, but beginners couldn't get them configured without a guru to help, plus the $120/seat cost wasn't tiny.  
Which is why I just used a Linux VM instead.  The X/Server was perfect. Performance was good-great and it was a real Linux desktop, which I've always preferred.  Whenever I'm on Windows I miss the "focus follows mouse" setting. I hate clicking to force focus.

---

