---
title: "SSH-ing"
date: 2008-02-16
forum: General Help
---

### Post by Wangsta on 2008-02-16
So here's what I've been told SSH can do for me:

1. I will be able to use any computer I allow, anywhere in the world, to access files on a computer that is running the ssh-server program.

2. I will be able to edit files on that computer across this SSH connection.

3. I will even be able to execute graphical programs from the server computer, even programs like firefox.

Is this all true? I've installed openssh-server on to computers. I've SSHed on each computer to other users on that computer.  I tried to connect one to the other. The computer I'm trying to connect to is called, let's say, 'server' and so is the user.
This is the code I tried to use:
```
sudo ssh server@server
``` I expected this not to work, and I got this response.```
ssh: server: Name or service not known
```
I then looked up the id address of the computer I was trying to connect to, using this site: [http://www.ip-adress.com/]("http://www.ip-adress.com/").
This is what I got: ```
sudo ssh server@<ipaddress>
ssh: connect to host <ipaddress> port 22: Connection refused 
```

Both computers were on. What am I doing wrong?

---

### Post by earobinson on 2008-02-16
[http://wiki.earobinson.org/index.php5?title=Ubuntu_Quick_Install#SSH](http://wiki.earobinson.org/index.php5?title=Ubuntu_Quick_Install#SSH)

install that on the server

---

### Post by Wangsta on 2008-02-16
I already have.
By the way, I didn't do anything to make the "server" computer a server, other than installing openssh-server.

---

### Post by x1a4 on 2008-02-16
> **Wangsta said:**
> 
ssh: connect to host <ipaddress> port 22: Connection refused


By default Ubuntu has most ports closed.  Open port 22 to accept connections from your computers.  

> 3. I will even be able to execute graphical programs from the server computer, even programs like firefox.

To get ssh to run X applications run it with the **-Y** (capital Y) switch, like so: 
```
ssh -Y username@hostname
```

If the -Y switch doesn't work use -X although it is less secure.  
From the ssh man page:
> 
X11 forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host (for the user&#8217;s X authorization database) can access the local X11 display through the for&#8208;warded connection.  An attacker may then be able to perform activities such as keystroke monitoring.

For this reason, X11 forwarding is subjected to X11 SECURITY extension restrictions by default.  Please refer to the ssh -Y option and the ForwardX11Trusted directive in ssh_config(5) for more information.


**Don't run ssh through sudo!**

---

### Post by Wangsta on 2008-02-16
Thank you very much, but how do I open Port 22?

---

### Post by x1a4 on 2008-02-16
Get root priviledges: ```
sudo -s
```
then
```

/sbin/iptables -A INPUT -p tcp --destination-port 22 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --source-port 22 -j ACCEPT

```
This will enable port 22 for the TCP protocol.  If you prefer you can replace tcp with udp. 
To undo this replace ACCEPT with REJECT.

Save the new configuration: ```
/etc/init.d/iptables save
```

If you prefer a GUI, install a firewall.  **guarddog** (Qt), **firestarter** (GTK), or **kmyfirewall** (Qt).  Do a search of the repositories and you'll probably find more, but either one of these three is your best bet.

---

### Post by az on 2008-02-16
> **Wangsta said:**
> Thank you very much, but how do I open Port 22?

The port is not closed.  You don't need to play around with any firewall rules.  The port becomes "open" when something listens to it:  So when you install ssh (ssh-server) on the machine, the port becomes open.

Are you behind a router?  Forward the port.

---

### Post by Wangsta on 2008-02-16
---------The other stuff worked,(as in executed right, but I still can't connect) but the "/etc/init.d/iptables save" part told me there is no such file.By the way, I just realized that both computers are connecting to the same internet source, so they have the same ip. how do I distinguish between them?--------

wait, yeah, they're behind a router. But I don't know how to forward the port either...

---

### Post by Sokertes on 2008-02-17
Did you start the ssh server via

sudo /etc/init.d/ssh start

on the server end?

You will not be able to connect until the ssh server has been started.


Sokertes

---

### Post by Herman on 2008-02-17
:) Hello Wangsta,
If you have more than one Ubuntu computer in your LAN, it is easy to use one computer to scan the other computers in the LAN for open ports. 
Just go 'System'-->'Administration'-->'Network Tools', and hit the 'Port Scan tab.
Type in the LAN  IP address of each computer you want to check.
You can check the LAN IP address for each computer with the 'ifconfig' command.

You can install Nmap for port scanning too if you want, it gives you a lot more options.

Ubuntu computers have no open ports by default, but as soon as we install SSH, port 22 will show up in port scans.
I have never seen it fail to show up. If it doesn't show up then you probably haven't installed SSH server, but something else instead.
There shouldn't be any need to do anything with IPtables.
The port will be password protected, so even though the port is open as long you have a good strong password it should still be secure. 
If you're paranoid, install Firestarter and turn it off only when you want to use SSH. 

It is best to test SSH  between computers inside your LAN to make sure it's working before progressing to the internet.

[COLOR=#000000] The file /etc/ssh/sshd_config is the one to edit for changing your settings for SSH. You can set a different port number than 22 here.
You can use the command '[/COLOR]less /etc/services' to see what port numbers not to use, but pick some random port number for each computer in your LAN instead of the default 22. Each computer in your LAN can have a different port number.

Then forward the port numbers you chose through your router and through your broadband modem.

How you accomplish port forwarding depends on what kind of hardware you have, we all have different hardware so it's hard to give anyone specific advice.
  It's best to read the documentation that came with your equipment.

Here is a link to a website that shows you how to set up port forwarding with all kinds of different equipment. [PORT Forward.com]("http://www.portforward.com/default.htm")

[COLOR=#000000][CanYouSeeMe.org - Open Port Check Tool]("http://www.canyouseeme.org/"), is a useful site to check whether your port forwarding efforts have worked, that site also shows you your internet IP number too.

[/COLOR]Then go somewhere to a remote location and connect to a PC in your home or office. It should work.
[COLOR=#000000]You can connect to each computer by your internet IP number and the individual port number you allocated each of your computers earlier.[/COLOR]

Then once you have it sorted out that far look at adding more security if you think you need it. (RSA keys and so on).

Regards, Herman :)

---

### Post by az on 2008-02-17
> **Wangsta said:**
> 
wait, yeah, they're behind a router. But I don't know how to forward the port either...

That's the problem.  And it has nothing to do with your Ubuntu box.   You need to read your router's documentation.

> **Sokertes said:**
> 
You will not be able to connect until the ssh server has been started.


As it has been said, the ssh deamon is started when the ssh-server package is installed and every time you boot after that.  The only time it would be stopped is if you stopped it yourself.

---

### Post by Herman on 2008-02-17
:) Wangsta, Are you using a finished (released) version of Ubuntu? 
If you are using Hardy Herron already, be aware that it's not ready for general use yet and expect lots of things not to work in it. 
You should post in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")-->                               [**Development (Hardy Heron)**]("http://ubuntuforums.org/forumdisplay.php?f=305") section of Ubuntu Web Forums if you are running Hardy Herron already.

Hardy Herron won't be released for general use until sometime in April and if you want a nice operating system you can actually use, you should install Gutsy Gibbon or earlier.
If you already have Hardy Herron installed, the best thing to do would be to divide your hard drive in half, (partition it), and install Gutsy Gibbon beside it.
Read this thread here about that, [dual boot gutsy/hardy]("http://ubuntuforums.org/showthread.php?t=637847")    Then try SSH networking in Gutsy Gibbon. It works. :)         .
It's very nice of people to be testing Hardy Herron already but remember, lots of things won't work yet in Hardy Herron and it may break on you, only experienced Ubuntu users should be testing Hardy Herron at this stage.
I'm only guessing, but that's probably what your problem is, I'm not sure.

Regards, Herman :)

---

