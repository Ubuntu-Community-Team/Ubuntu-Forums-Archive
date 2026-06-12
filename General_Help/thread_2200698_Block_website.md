---
title: "Block website"
date: 2014-01-20
forum: General Help
---

### Post by motorcity909 on 2014-01-20
Hi there

I'm looking to block some specific websites and wondered if there is a way to do this at a system level, such as the host file?

I looked at extensions on both Firefox and Chrome but the one I was using has been shown to be a horrible tracker piece of crap - [http://discuss.howtogeek.com/t/warning-your-browser-extensions-are-spying-on-you/12394](http://discuss.howtogeek.com/t/warning-your-browser-extensions-are-spying-on-you/12394)

My router doesn't have the ability to blacklist sites so I'm hoping I can do soemthing on the host file?

In the **etc** folder, I can see files called *hosts*, *hosts.allow* and *hosts.deny*, if that helps.  I'm guessing the last one might be the one I need!

Is it just a case of adding the website(s) to that file without a # in front of it?

Thanks as always
Dave

---

### Post by The Cog on 2014-01-20
/etc/hosts is the one. It's a lookup from IP address to a list of names (separated by spaces or tabs). You can block named hosts (not URLs but the basic host) by referring them to 255.0.0.0 like this:
```
0.0.0.1 blockme.com
```

Edit: After a bit of trial and error, 0.0.0.1 seems a good address to refer to.
And IP address before name.

---

### Post by motorcity909 on 2014-01-20
Thanks The Cog, I tried that but it didn't work.  I might be entering the code wrong.

Say I wanted to block [http://www.bbc.co.uk](http://www.bbc.co.uk).  Using a reverse IP address look up website, I can find it's IP address is **212.58.246.90**

So would the line to add to the hosts file be:

```
0.0.0.1 212.58.246.90 bbc.co.uk
```

Thanks again
Dave

---

### Post by The Cog on 2014-01-20
No, it would be:
```
0.0.0.1 www.bbc.co.uk
```
or to block both [www.bbc.co.uk](www.bbc.co.uk) and the parent bbc.co.uk:
```
0.0.0.1 www.bbc.co.uk bbc.co.uk
```
The idea is to deliberately give the **wrong** IP address for the blocked host name, so the browser cannot connect to it. 0.0.0.1 seems to work nicely as it gives a very quick error to the browser. 

Other people sometimes use 127.0.0.1 which gets the browser to try to connect to the local PC. The local PC will generally refuse the connection because it isn't running a web server. But of course, you might be running a web server, and even if not, 0.0.0.1 will fail quicker because it doesn't even try to connect.

---

### Post by SeijiSensei on 2014-01-21
Host files work well if you can control all the PCs using your network and can ensure you have changed the hosts files on all of them.  If the users have admin privileges, they can thwart your efforts by changing the host files themselves.

Other alternatives are to use iptables to write firewalling rules that block traffic at the router, or to use a proxy like [Squid]("http://www.squid-cache.org/") that lets you write more complex blocking rules based on URLs, IP addresses, domains or file types.  In both cases you would need to put a Linux box between the local network and the public Internet.

---

