---
title: "Using SSH with Firefox as an Encrypted Proxy"
date: 2007-12-05
forum: General Help
---

### Post by xluryan on 2007-12-05
I have 2 computers running linux (the way it should be), one is my personal computer, the other is a server in a remote location. I want to use the remote computer as a proxy, and I'd like to do it through SSH so all the network traffic gets encrypted.

After I've got that set up, I'd like to use Firefox for surfing the internet. So I'll need to enter the proxy address in Firefox.

So I'm trying the command:
```

ssh -D 1080 user@xx.xx.xx.xx

```

After I have logged in successfully, I go to Firefox, enter localhost for the proxy address, and 1080 for the port.

But when I try to go to websites, none of them load. What am I doing wrong?

---

### Post by xluryan on 2007-12-06
Bump.

---

### Post by moonpup on 2007-12-07
First off this is a multi step process...I'll give you a brief overview but you'll need to learn about configuring squid if you don't know how. Here's a good link to follow and includes how to setup squid to use a username and password before it allows you access to it. It's written based on rpm (redhat) commands. You'll need to know the ubuntu equivalents. You can most likely stop at the point where it tells you about forcing users to use the proxy section.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

1) The remote server must be running a proxy server... in this case most likely squid. Squid should be setup to only accept connections from the local network only. Do not open this up to the outside world. Also, using the default port 3128 is fine.

2) Follow the above how-to which will give you a basic, but good enough install to make this work. Again, you can most likely stop at the point where it tells you about forcing users to use the proxy section.

3) You won't (and don't) open a port on the firewall for squid as you'll be connecting through ssh

4) On your workstation, set firefox to use localhost on port 3128 for proxy settings.

5) Make your ssh connection to the server with ssh -L 3128:localhost:3128 username@server

Remember to change port #'s if necessary. If you remote server accepts ssh connection on a different port from 22, then add a -p port# to the above ssh command. As long as you are not blocked by a firewall, you should be good to go. Just open the ssh connection first and then firefox.

Hope this helps!

---

### Post by xluryan on 2007-12-07
Wow, that's pretty in depth. But actually, I found out an easier way to do it:

Open an SSH tunnel like so:
```

ssh -D #port user@domain.com

```

Once you've logged in, go to the preferences in firefox, and in the proxy screen use 'localhost' with the port number you chose from above IN ONLY THE SOCKS BOX. Leave the rest blank. And then go to [www.whatismyip.com](www.whatismyip.com) to make sure you're going through a tunnel.

Enjoy :)

---

### Post by babounours on 2008-02-17
it is also possible with privoxy on server, using port 8118 by default

---

