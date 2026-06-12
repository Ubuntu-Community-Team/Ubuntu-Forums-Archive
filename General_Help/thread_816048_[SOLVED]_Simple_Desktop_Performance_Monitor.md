---
title: "[SOLVED] Simple Desktop Performance Monitor"
date: 2008-06-02
forum: General Help
---

### Post by azurepancake on 2008-06-02
I am searching for a very simple performance monitor desktop widget. Something that displays CPU, RAM, hard drive capacity and the like. I've seen a few in screen shots that are all text, with no fancy graphics that just sit on your desktop. 

Can anyone recommend one to me? 

Thanks!

---

### Post by kshane on 2008-06-02
> **azurepancake said:**
> I am searching for a very simple performance monitor desktop widget. Something that displays CPU, RAM, hard drive capacity and the like. I've seen a few in screen shots that are all text, with no fancy graphics that just sit on your desktop. 

Can anyone recommend one to me? 

Thanks!

Conky is one.  It's pretty configurable, too

Kevin

---

### Post by azurepancake on 2008-06-02
Conky is exactly what I was looking for. Thanks a bunch!

---

### Post by azurepancake on 2008-06-02
This has got me wondering.. 

Could there be a way to use Conky to monitor our small businesses file server from another system? Our file server runs Ubuntu Server edition, therefor lacks a GUI. It does not have a display and I access it via SSH. If there was someway to link Conky up with it that would be most awesome.

Any ideas?

Thanks again!

---

### Post by roycrom on 2008-06-03
If you run an X server on the workstation you want conky to display its stats on then you can set the $DISPLAY variable on the Ubuntu server to point to your workstation, I just tried it - it works fine.
If your workstation is a windows box then you will have to install an X server - if your workstation is linux then it should be as simple as doing an "# xhost + <Server IP Address>" on the workstation and setting the DISPLAY variable in your ssh session, then start up Conky.

HTH

---

### Post by azurepancake on 2008-06-04
Well I am very glad to hear that this will be possible. I just need to clear a few things up before I actually do this. Please excuse my ignorance, for I am quite new at administrating Linux.

From my understanding, the "DISPLAY" variable tells X where to display certain information. I am guessing this is how the workstation with Conky (Ubuntu Hardy) receives the servers statistics? To be honest, I am not sure where to edit this variable!

I suppose XHOST is used to give the server access to my workstations X server or is it the other way around?

Again, I apologize for my misunderstanding. 

Thanks very much!

---

### Post by roycrom on 2008-06-04
Hello Azurepancake,,

Your Ubuntu Server is the X client - your PC is the X server.

If your PC is a Linux PC, you can open up a command prompt and type ```
$ xhost + <Ubuntu Server IP>
```
This tells your PC(X server) to accept X from your Ubuntu Server(X Client)

Then open up an SSH connection to your Ubuntu server and issue the command```
export DISPLAY=<PC IP Address>:0
``` directly at the command prompt.
e.g.```
$ export DISPLAY=192.169.1.10:0
```

This means that when you run anything on the Ubuntu Server, it will attempt to send the display to <PC IP Address>

You can check it has been set correctly by just running```
echo $DISPLAY
```
Now you can try running Conky on the Ubuntu Server and hopefully Conky should pop up on your PC.

You could also look into SSH X Forwarding - this is going a bit further and you start messing with the sshd_config file - but it can be useful - especially if port 22 (SSH Port) is the only port open between your PC and server (Due to firewalls restrictions)

Hope this makes things a bit clear

---

### Post by peakshysteria on 2008-06-04
Is there a way besides the terminal to start and shut down conky? And how do I shut it down? ```
sudo killall conky
```?

---

### Post by roycrom on 2008-06-04
First,

conky should run without an sudo, meaning you can kill it without an sudo - i.e. ```
$ conky &
$ pkill conky
```

Or you can just close the window that conky pops up in!

Secondly, AzurePancake had no GUI on the server so had to start it via command line - although I'm sure it wouldn't be too much of a job to write a little script to ssh to a remote box, set the $DISPLAY environment variable and start/stop conky.

Even easier if you have a GUI on the box and just want to start/stop conky on that box.  Just create a custom launcher on your panel with the correct commands.  When I installed conky on Hardy, it did't put an entry in the menu so I think you would have to do it that way.

---

### Post by azurepancake on 2008-06-04
Thanks very much for clearing that up to me Roycrom, much appreciated.

I am running into one little problem though. Everything worked great while setting it up, but when I issue the "Conky" command over the SSH session, it responds with the following:

```
Conky: can't open display: 192.168.1.9:0
```

This is after issuing:

```
$ xhost + 192.168.1.100
``` 

from the Linux workstation (192.168.1.100 is the servers address).

I then SSH into the server and typed:

```
export DISPLAY=192.168.1.9:0
```

192.168.1.9 being my workstations IP address. The "echo $DISPLAY" command outputs:

```
192.168.1.9:0
```

So I am not sure why it would be doing this. Could it possibly be a permission issue of some sort? 

Thanks again!

---

### Post by roycrom on 2008-06-05
Can you run```
$ sudo iptables -L
``` on both server and client and post the results here?  It looks like you did everything correctly.  Maybe iptables is blocking the X communication.

---

### Post by roycrom on 2008-06-05
OR - ssh X forwarding is pretty straightforward.  Saves you messing about with IPTables too.

On your Server(X client) - you need to make sure that the following line is uncommented in /etc/ssh/sshd_config
```
X11Forwarding yes
```
Then restart the ssh daemon
```
/etc/init.d/ssh restart
```
Check no-one else is logged in - this may chuck them out!
On your workstation, if you now log in with
```
$ssh -X 192.168.1.100
```
then when you are logged in to the server, issue the command
```
echo $DISPLAY
```hopefully, it should return something along the lines of
```
localhost:10.0
```
if so, try starting conky, it should send X back through your ssh connection.

---

### Post by azurepancake on 2008-06-05
Okay, I first checked /etc/ssh/sshd_config and X11Forwarding was uncommented and was marked "yes" on the Ubuntu server.

I then logged out and logged back in using "ssh -X 192.168.1.100".

I issued the echo $DISPLAY command and oddly the output was just a blank line, like so:

```

me@192.168.1.100:/etc/ssh$ echo $DISPLAY

me@192.168.1.100:/etc/ssh$ 

```

So I got curious and tried the command, "export DISPLAY=localhost:10.0", but when I tried to start Conky, I get the following error again:

```
Conky: can't open display: localhost:10.0
```

I then checked out the iptables with "sudo iptables -L" which outputted:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

I'm not quite sure what that output means. 

Thanks very much for your patience!

---

### Post by roycrom on 2008-06-09
Hi Azurepancake, sorry for the delay - can you run this command on your PC which you initiate the SSH connection from:
```

$ grep -i forwardx11 /etc/ssh/ssh_config

```
if they are commented out like this:
```

#   ForwardX11 no
#   ForwardX11Trusted yes

```
then try uncommenting them and reconnecting with
```
ssh -X 192.168.1.100
```
then cross your fingers ;)

---

### Post by azurepancake on 2008-06-09
Ack, still no luck!

I ran "$ grep -i forwardx11 /etc/ssh/ssh_config" on my personal computer, that initiates the SSH session and it outputs:

```

#   ForwardX11 no
#   ForwardX11Trusted yes

```

So I used nano to uncomment them in the ssh_config file and typed in "ssh -X 192.168.1.100" to make the connection. I then checked the $DISPLAY variable with "echo $DISPLAY" and it outputted a blank line, like before.

Because of this, I tried assigning "localhost:10.1" as the DISPLAY variable and then attempted to run conky, in which outputted the following error in return:

```

Conky: can't open display: localhost:10.0

``` 

I just don't know what could possibly be holding Conky back.. OH well, I'm sure we will figure this out eventually. 

Thanks!

---

### Post by roycrom on 2008-06-10
It isn't conky that's the issue here - it's the X forwarding.

have a look at this page [[COLOR="Red"]X over SSH[/COLOR]]("http://www.cag.lcs.mit.edu/~wentzlaf/faq/ssh_X.html") - it basically tells you to do everything that I said previously - however, right at the end in the Q&A section, it mentions having to have "xauth" installed on the remote machine - maybe this is where we are falling over.  Install it on the Ubuntu Server using ```
 sudo apt-get install xauth
```
Now logout and back in to your Ubuntu server over ssh with the -X flag (Make sure that it is upper case - lower case x DISABLES X forwarding!) and try to launch conky again.
If it works - please let me know!

---

### Post by azurepancake on 2008-06-10
Woot, that did it! This is pretty damn awesome! All I had to do was log-in remotely and install xauth.

Thanks so much for your assistance and your patience. Not only do I have remote monitoring of the server, but I also learned some valuable information about X and SSH. 

Thanks again!

---

### Post by roycrom on 2008-06-11
No problem, glad we got there in the end. :guitar:

You should now be able to use this method to run anything on the remote server that has a gui/graphical front end - not just conky.

And thanks for taking the time to report back with how you got on :)

---

