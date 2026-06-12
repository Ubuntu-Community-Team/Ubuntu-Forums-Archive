---
title: "I am having problem creating ssh port forwarding"
date: 2015-06-04
forum: General Help
---

### Post by peter1897 on 2015-06-04
I am using Cygwin on Windows 7 and i am trying to create port forwarding to remote Ubuntu server. I am using this command:

```
ssh -v -i ubuntu2.pem ubuntu@52.25.217.245 -L 9999:localhost:9999
```

This is the output on logon concerning the port forwarding:

```
debug1: Local connections to LOCALHOST:9999 forwarded to remote address localhost:9999
debug1: Local forwarding listening on ::1 port 9999.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 9999.
debug1: channel 1: new [port listener]
debug1: channel 2: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-48-generic x86_64)
```

But i don't think it is working because if i try to make Firefox trafic goes through port 9999 i get error message: "The connection was reset" when i try to load a page in Firefox. The manual proxy configuration in Firefox are: Socks5, host= localhost, port= 9999.

From the debug log on the server side i get this output when i try to load a page with Firefox:

```
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 3: new [direct-tcpip]
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 4: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug1: channel 3: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49662 to ::1 port 9999, nchannels 5
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 3: new [direct-tcpip]
channel 4: open failed: connect failed: Connection refused
debug1: channel 4: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49663 to ::1 port 9999, nchannels 5
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 4: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug1: channel 3: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49664 to ::1 port 9999, nchannels 5
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 3: new [direct-tcpip]
channel 4: open failed: connect failed: Connection refused
debug1: channel 4: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49665 to ::1 port 9999, nchannels 5
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 4: new [direct-tcpip]
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 5: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug1: channel 3: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49666 to ::1 port 9999, nchannels 6
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 3: new [direct-tcpip]
channel 4: open failed: connect failed: Connection refused
debug1: channel 4: free: direct-tcpip: listening port 9999 for localhost port 9999, connect from ::1 port 49667 to ::1 port 9999, nchannels 6
debug1: Connection to port 9999 forwarding to localhost port 9999 requested.
debug1: channel 4: new [direct-tcpip]
channel 5: open failed: connect failed: Connection refused
```

Why i can't forward the Firefox traffic through port 9999? Where is the problem - in my Windows machine, in Firefox settings, or in the remote Ubuntu server?

---

### Post by Lars Noodén on 2015-06-04
That is connecting port 9999 on your local machine to port 9999 on your remote machine.  So if nothing is listening on your remote machine at port 9999 then Firefox won't find anything at [http://localhost:9999/](http://localhost:9999/) either.  If you want Firefox to connect to your remote machine and access the world via the remote machine then what you want is SOCKS proxying.   That is [option -D](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) with ssh.  Then you need to set Firefox's proxy information to find a SOCKS Host at localhost on port 9999.  

However, if you really are trying to connect to port 9999 on the remote machine and nothing is responding, you'll have to check on that machine to see what is listening there.

```

netstat -nltp

```

---

### Post by peter1897 on 2015-06-04
This is the output i get when i execute **netstat -nltp** on the remote Ubuntu server:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      6422/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      6422/sshd
```

What does it mean? Why port 9999 is not listed as listening?

---

### Post by Lars Noodén on 2015-06-04
You have the ssh daemon listening on port 22, as is normal, and no other listening applications.  Port 9999 is not listed as listening because there is nothing listening there.  That would only happen if you installed some software and configured it to listen to port 9999.  

Looking at your client, if you  have set the manual proxy configuration in Firefox to be: Socks5, host= localhost, port= 9999, then you want to use the SOCKS proxying option instead, also known as dynamic port forwarding.   

```

ssh -v -i ubuntu2.pem ubuntu@52.25.217.245 **-D 9999**

```

That will cause Firefox to connect to the world via your remote machine.

---

### Post by peter1897 on 2015-06-04
Using the **-D** option works but is it possible to forward the Firefox traffic through more than one remote machine? According to this guide [https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html), which i don't know if it is correct, i first have to create ssh tunnel with the **-L** option from my local machine to the first remote machine and then from the first remote machine i have to create ssh tunnel to the second remote machine with the **-D** option.

---

### Post by Lars Noodén on 2015-06-04
That site gets a lot of critique in other circles so I did not look too closely at it.  But to chain, one way is like this.

```

ssh -tt -L 9999:localhost:9998 host1.example.org ssh -D 9998 peter1897@host2.example.org

```

I've changed the port numbers to make it clearer what is going on, but you could add additional hosts in the middle.  It's going to add latency to the connection though.

---

### Post by peter1897 on 2015-06-04
Thanks, finally it works! I am trying to make this work from two days.

I have Tor service installed and running on the first remote machine. Can i make Firefox connect to the first machine and then connect to the second machine through Tor? Because now if i execute the chain command Firefox connects to the second machine but does not use Tor because if i check the IP address it shows the real IP address of the second remote machine.

---

### Post by Lars Noodén on 2015-06-04
It's possible to connect to Tor from the second machine.  I don't have machines handy to test, but I think it would be something like this:

```

ssh -tt -L 9999:localhost:9998 host1.example.org ssh -L 9998:localhost:9050 peter1897@host2.example.org

```

Replace 9050 with whatever Tor is listening to on that machine.  However, unless you make lots of settings changes to Firefox to make it look like the Tor Browser Bundle's settings it will stand out a bit.  In most cases you'd be better off just run the Tor Browser Bundle on the client machine in the first place.  There are bridges and obfsproxy available too.

---

### Post by peter1897 on 2015-06-04
If i try to connect to Tor from the second machine i get "connection refused" error. The tor service is listening on port 9050. But my goal is to connect from the first to the second machine through Tor so the second machine can't see that i am connecting from the first machine but from Tor.

I am doing this because i don't want my ISP to see that i am using Tor and see only that i am connecting to a server through ssh. And also if the government in the country where i am decide to forbid access to tor i want to be able to access it.

 So, my ultimate goal is: creating ssh tunnel from my local machine to first remote server and then from the first server creating anonymously ssh tunnel over tor to the second remote server. And then browsing anonymously with Firefox. I know how to make the security settings for Firefox so this is not a problem.

---

### Post by peter1897 on 2015-06-04
I followed this guide [https://www.howtoforge.com/anonymous-ssh-sessions-with-tor](https://www.howtoforge.com/anonymous-ssh-sessions-with-tor) and i setup all ssh connections from the first machine to the second machine to go through tor. I edited the file **/etc/ssh/ssh_config** and i inserted these lines:

```
Host *
CheckHostIP no
Compression yes
Protocol 2
ProxyCommand connect -4 -S localhost:9050 $(tor-resolve %h localhost:9050) %p
```

I am not sure what the **-4** option mean, is it releated to socks proxy type or something else, i couldn't find manual for ProxyCommand.

Now if i execute the ssh chain command it creates the two server tunnel and Firefox connects to the second remote server and i am able to browse internet. But how to check if Firefox traffic really goes through tor? If i check the IP address it shows the ip address of the second remote server as it suppose to be. Is there a command that will show to which IP's Firefox make requests when loading a web page? Something like the debug output for ssh login?

---

### Post by Lars Noodén on 2015-06-04
> **peter1897 said:**
> I am not sure what the **-4** option mean, is it releated to socks proxy type or something else, i couldn't find manual for ProxyCommand.

The -4 downgrades connect to use SOCKS 4 instead of SOCKS 5 and would be for the [connect](http://manpages.ubuntu.com/manpages/trusty/en/man1/connect.1.html) command that the [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) client has in its [configuration using the ProxyCommand directive](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html).  So info about ProxyCommand and the other options in ~/.ssh/config will be in the manual page for [ssh_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html).

---

### Post by Lars Noodén on 2015-06-04
> **peter1897 said:**
> I followed this guide [https://www.howtoforge.com/anonymous-ssh-sessions-with-tor](https://www.howtoforge.com/anonymous-ssh-sessions-with-tor) and i setup all ssh connections from the first machine to the second machine to go through tor. I edited the file **/etc/ssh/ssh_config** and...

That looks like it is running SSH over Tor.  So the client would be seen connecting to Tor and the server also, hopefully separately, be seen connecting to Tor.  It doesn't seem to be what you described as a goal earlier where you wanted to connect to a second machine using SSH and from that second machine go out through Tor.

---

### Post by peter1897 on 2015-06-04
My english is not very good so i may have not described very well what i am trying to do, but my goal is to create ssh tunnel over tor from the first server to the second server. And now i think the ssh connection is over tor because when i type **w** command on the second server it shows a IP address from the tor network for the logged in user. 

I wish that there is a way to check that Firefox traffic is also going over Tor. It should be that way but i just want to be sure.

If the **-4** option determines the Socks proxy type do i have to change it to **-5** because in Firefox i have selected Socks5 in proxy configuration?

---

### Post by Lars Noodén on 2015-06-05
Is this more or less what you are trying to set up?

```

 +------+       +------+
 | box1 +--ssh--+ box2 +--tor---WWW
 +------+       +------+

```

With the browser being on box 1.

---

