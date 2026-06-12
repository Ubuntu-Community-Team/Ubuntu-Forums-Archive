---
title: "Sharing Desktop using 2 computers"
date: 2013-01-25
forum: General Help
---

### Post by Pulka on 2013-01-25
Hi.

I'm starting to feel the need of having an extended monitor for my desktop computer. The problem is i don't want to spend more money.
I have a laptop that could perfectly be useful for that, but don't know if it's possible to connect them that way.

Let me try to explain. I use mainly my desktop computer and it would be great if i had a second monitor to be viewing two documents (for example) at the same time. Can i share what i'm doing in desktop computer with the screen of the laptop?

---

### Post by sudodus on 2013-01-25
I don't know a standard way to use a laptop directly as a monitor for another computer, but there are alternatives.

You can simply use ***ssh*** to get a window (that can be maximized) on the laptop's screen.

```
ssh -X user@desktop
```

---

### Post by Pulka on 2013-01-25
for that i need to define a hostname or configure it. How to?

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> for that i need to define a hostname or configure it. How to?

You need to make the desktop computer an ssh server. It is easy, if you are only working inside a local area network, behind a router with a firewall. Then you can use password authentication. Otherwise (or anyway if you wish to have higher security) use public key authentication.

I think the client is installed by default in all Ubuntu versions and flavours. See this link for the server

[[COLOR="Red"]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

---

### Post by sudodus on 2013-01-25
I made a quick check with ssh from my laptop with Lubuntu 12.04 to run graphics programs via ssh -X.

- The web browser pcmanfm works
- Libreoffice works
- Evince does not work, but you can use Xournal as a viewer for pdf files
- Gimp works (for pictures and to edit single pdf pages)
- Leafpad works

---

### Post by Pulka on 2013-01-25
Ok...i did

ssh -X user@remotehost

from my desktop to laptop, but all i get is in terminal now i have control over laptop. How do i open software?

i tried "firefox" and got this message

Error: no display specified

---

### Post by tokyo08 on 2013-01-25
hmmmm, you might have to spent some extra money, for a connection wire?

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> Ok...i did

ssh -X user@remotehost

from my desktop to laptop, but all i get is in terminal now i have control over laptop. How do i open software?

i tried "firefox" and got this message

Error: no display specified

Firefox works for me (but it complains a little before the GUI window shows up.

Chromium-browser works too (with less complaints).
--
Do you run the command
```
ssh -X user@remotehost
``` in a terminal window?
Can you run simple text mode commands like

```

pwd
ls -l
echo $DISPLAY

```
What happens when you run ```
xlogo
```

---

### Post by Pulka on 2013-01-25
ok...did a restart. I can access my laptop from my desktop, but i can't  access my desktop from my laptop

desktop - laptop: works

laptop-desktop: error

i get this message

```

ssh: connect to host remotehost port 22: Connection timed out
```

---

### Post by sudodus on 2013-01-25
Run ```
echo $DISPLAY
``` when logged in via SSH, that is type it on the laptop's keyboard.

You can use that display id to redirect the output from a terminal window of the desktop.

In my case the output of the command is [FONT="Courier New"]localhost:10.0[/FONT]. So I type the following command on the desktop's keyboard and get the graphic window on the laptop's screen.

```
firefox --display localhost:10.0
```
This way also evince will work
```
evince --display localhost:10.0 file.pdf
```

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> ok...did a restart. I can access my laptop from my desktop, but i can't  access my desktop from my laptop

desktop - laptop: works

laptop-desktop: error

i get this message

```

ssh: connect to host remotehost port 22: Connection timed out
```
Where did you install the openssh-server? Alias where program sshd is running?
```
ps -A | grep sshd
```
It seems that you installed the server in your laptop, which is OK. I was thinking the other way, but it is no problem. You can have it either way (or both ways if you install the server software in both computers).

---

### Post by Pulka on 2013-01-25
Ok...i just learned a lot today :) Thank you very much.

But this doesn't solve my problem because what i need is to use my desktop content in my laptop screen

What happend with what you told me is that firefox opens in laptop but i still have to control it in laptop

---

### Post by Pulka on 2013-01-25
I installed client and server on both computers. It's a problem?

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> Ok...i just learned a lot today :) Thank you very much.

But this doesn't solve my problem because what i need is to use my desktop content in my laptop screen

What happend with what you told me is that firefox opens in laptop but i still have to control it in laptop

Yes, that is how it works. Is that a problem? It should not be too far away anyway. And you can always close a window with

***ctrl + C***

in the window, from where you called it.

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> I installed client and server on both computers. It's a problem? It is OK. This way you can find a way to work, that suits your way of thinking (which is the client and server).

***Edit***: Maybe you have not found all the posts that I have written. Please have a second look, and notice that you can 'pull' an application window from the other computer, or 'push' a window to the other computer.

---

### Post by Pulka on 2013-01-25
> **sudodus said:**
> Maybe you have not found all the posts that I have written. Please have a second look, and notice that you can 'pull' an application window from the other computer, or 'push' a window to the other computer.

now you lost me. You're saying i can push my chrome window opened in desktop to my laptop?

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> now you lost me. You're saying i can push my chrome window opened in desktop to my laptop?
OK. You cannot push a window that is already opened, but you can push a new window to be opened on the screen of the other computer.

See post #10. That example requires that you started the ssh connection from your laptop. And then use a terminal window of the desktop to run the command.

---

### Post by Pulka on 2013-01-25
ok...understood. The problem is i can't connect to desktop from laptop. 
connection timed out

---

### Post by windscape on 2013-01-25
Hi,

Is openssh-server installed and running on your desktop?

---

### Post by Pulka on 2013-01-25
> **windscape said:**
> Hi,

Is openssh-server installed and running on your desktop?

yes...just restarted to be sure

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> ok...understood. The problem is i can't connect to desktop from laptop. 
connection timed out

- Can you connect from the desktop to itself with ssh?

- Did you install things symmetrically? The same kind of configuration of the ssh-server in the desktop as in the laptop?

- Is sshd running in both computers?

- Is there some difference concerning firewalls?

- Do you use the correct userID@computerID for both computers?

- Did you exit the ssh session from the desktop to the laptop before trying to run the other way? (I'm not sure if it would work simultaneously.) You can let both servers run. I know that is OK.

---

### Post by Pulka on 2013-01-25
> **sudodus said:**
> 

- Can you connect from the desktop to itself with ssh?



connection refused

> **sudodus said:**
> 
- Did you install things symmetrically? The same kind of configuration of the ssh-server in the desktop as in the laptop?


think so

> **sudodus said:**
> 
- Is sshd running in both computers?


yes

> **sudodus said:**
> 
- Is there some difference concerning firewalls?

don't know. How do i check it?


> **sudodus said:**
> 
- Do you use the correct userID@computerID for both computers?

yes

---

### Post by sudodus on 2013-01-25
> **Pulka said:**
> connection refused

This should work. I think you need to search for ideas at the internet för example

[[COLOR="Red"]http://askubuntu.com/questions/30080/how-to-solve-connection-refused-errors-in-ssh-connection[/COLOR]]("http://askubuntu.com/questions/30080/how-to-solve-connection-refused-errors-in-ssh-connection")

[[COLOR="red"]http://askubuntu.com/questions/104659/ssh-connection-getting-refused[/COLOR]]("http://askubuntu.com/questions/104659/ssh-connection-getting-refused")

[[COLOR="red"]http://stackoverflow.com/questions/8522375/ssh-connection-refused[/COLOR]]("http://stackoverflow.com/questions/8522375/ssh-connection-refused")

[[COLOR="red"]http://unix.stackexchange.com/questions/21302/ssh-connection-refused-how-to-troubleshoot[/COLOR]]("http://unix.stackexchange.com/questions/21302/ssh-connection-refused-how-to-troubleshoot")

This last link shows how to check that a port is open and connected. I tested in my computer, and it gives proper information.

> Steps for debugging the above problem:

    Use nmap tool to know which ports are open in that server. nmap is a port scanner. Since it may be possible that ssh server is running on a different port. nmap will give you a list of ports which are open.

```
$ nmap myserver
```

2 . Now you can check which server is running on a given port. Suppose in the output of nmap, port 2424 is open. Now you can which server is running on 2424 by using nc(netcat) tool.

```
$ nc -v -nn myserver portno
```
Suppose the output of 2424 port is:

myserver 2424 open SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5

This means ssh is running on 2424.

Keep on changing the portno in the above command and check for all the ports which are listed open by nmap.


---

### Post by Pulka on 2013-01-25
Thank you very much for your help.
Will check this links tomorrow.

---

### Post by sudodus on 2013-01-25
There are alternatives. Searching the internet for

***use laptop as extra screen***

I found one commercial one, ***Maxivista***, and one that is free for personal use, ***ZoneScreen***. See for example this link

[[COLOR="Red"]http://forum.videohelp.com/threads/342146-Possible-to-use-laptop-screen-as-external-screen[/COLOR]]("http://forum.videohelp.com/threads/342146-Possible-to-use-laptop-screen-as-external-screen")
--
***Remmina*** is a remote desktop connection client able to display and control a remote desktop session. It can connect to a VNC platform as well as windows terminal servers (or xrdp in linux). The difference to ssh is that it is not only single windows, but a whole remote desktop, that is shown.

Run Remmina in the computer you want to have a screen and a server, for example xrdp in the other computer.

```
remmina serverIP
``` will start a screen. So if you want the picture in the laptop, install xrdp in the desktop and Remmina in the laptop.
--
I think Maxivista and Zonescreen do what you want (keeping the keyboard control and mouse at the desktop computer). But they are Windows applications (might work in linux via Wine). Remmina is similar to ssh concerning keyboard and mouse.

---

### Post by Pulka on 2013-01-25
Ok...i just need onw more push here.


Tryed Synergy software and it is working using

laptop - server
desktop - client

But i can't  make desktop as a server. It always gives me an error of timed out.
How can i solve this? I'm almost there!

---

### Post by sudodus on 2013-01-26
> **Pulka said:**
> Ok...i just need onw more push here.


Tryed Synergy software and it is working using

laptop - server
desktop - client

But i can't  make desktop as a server. It always gives me an error of timed out.
How can i solve this? I'm almost there!

Which operating system (distro, version, flavour) are you running in the desktop, and which one are you running in the laptop?

It is probably the same problem with all your network programs. I think the port (where the server program is listening) is closed. Or the client is trying to connect to another port than that of the server. Did you try the tips quoted in post #23?

[FONT="Courier New"][SIZE="3"]nmap ...[/SIZE][/FONT]
and
[FONT="Courier New"][SIZE="3"]nc ...[/SIZE][/FONT]

---

### Post by Pulka on 2013-01-26
> **sudodus said:**
> Which operating system (distro, version, flavour) are you running in the desktop, and which one are you running in the laptop?


Laptop - Xubuntu 12.04
Desktop - Ubuntu 12.04

Just did a little test activating ufw in laptop and imediatly synergy stoped working. 
So i tried to remove ufw from boot in desktop computer, but still i can't use Desktop as a server

> **sudodus said:**
> 
It is probably the same problem with all your network programs. I think the port (where the server program is listening) is closed. Or the client is trying to connect to another port than that of the server. Did you try the tips quoted in post #23?

[FONT="Courier New"][SIZE="3"]nmap ...[/SIZE][/FONT]
and
[FONT="Courier New"][SIZE="3"]nc ...[/SIZE][/FONT]

---

### Post by Pulka on 2013-01-26
```
Starting Nmap 5.21 ( http://nmap.org ) at 2013-01-26 11:14 WET
Nmap scan report for xx-desktop (127.0.1.1)
Host is up (0.00039s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
80/tcp   open  http
9001/tcp open  tor-orport

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

```

No port 22. How can i add it?

---

### Post by sudodus on 2013-01-26
> **Pulka said:**
> Laptop - Xubuntu 12.04
Desktop - Ubuntu 12.04

Just did a little test activating ufw in laptop and imediatly synergy stoped working. 
So i tried to remove ufw from boot in desktop computer, but still i can't use Desktop as a server
Read ```
man ufw
``` and have a look at this link

[https://wiki.ubuntu.com/BasicSecurity]("https://wiki.ubuntu.com/BasicSecurity")

Try ```
sudo ufw disable
``` to disable the firewall. Could be potentially dangerous, so it's only a temporary solution. Instead run the firewall and allow ssh or whatever service you want to run with some command like
```
sudo ufw allow 22/ssh
``` It is better to use another port (with a very different port number) and to allow traffic only from certain computers addresses for example
```
sudo ufw allow from 192.168.0.0/16
```

You can easily find more examples browsing the internet.

---

### Post by sudodus on 2013-01-26
> **Pulka said:**
> ```
Starting Nmap 5.21 ( http://nmap.org ) at 2013-01-26 11:14 WET
Nmap scan report for xx-desktop (127.0.1.1)
Host is up (0.00039s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
80/tcp   open  http
9001/tcp open  tor-orport

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

```

No port 22. How can i add it?
It seems you are running TOR, or at least you have configured the computer for it. Then I guess you want increased security, and it is a bad idea to allow port 22, which is commonly used to attack systems. Maybe you could be happy with an SSH server on the laptop, and connect like I explained before to use its screen (to push a window to be opened there).

---

### Post by Pulka on 2013-01-26
Already tried all that.

Just found out that Synergy tries to use port 24800. It's not a problem with firewall because even when it's disabled i can't  connect

---

### Post by Pulka on 2013-01-26
> **sudodus said:**
> It seems you are running TOR, or at least you have configured the computer for it. Then I guess you want increased security, and it is a bad idea to allow port 22, which is commonly used to attack systems. Maybe you could be happy with an SSH server on the laptop, and connect like I explained before to use its screen (to push a window to be opened there).

Thank you for all your help :)
Synergy is perfect for me. Having two computers working with diferent resources allows me to have more windows and programs running.

It's just frustrating that i can use it with laptop as a server, and not desktop. It would be better to have the desktop keyboard for production

---

### Post by Pulka on 2013-01-26
I can't believe it! After 48 hours searching and trying everything, just found the solution.

All is working now

Found the solution here:
[http://www.martynhaigh.com/blog/2012/08/30/accepting-incoming-tcp-ip-connections-in-kubuntu/](http://www.martynhaigh.com/blog/2012/08/30/accepting-incoming-tcp-ip-connections-in-kubuntu/)

basically all i needed was

```
sudo iptables -I INPUT -p tcp --dport 24800 -j ACCEPT
```

---

### Post by sudodus on 2013-01-26
> **Pulka said:**
> I can't believe it! After 48 hours searching and trying everything, just found the solution.

All is working now

Found the solution here:
[http://www.martynhaigh.com/blog/2012/08/30/accepting-incoming-tcp-ip-connections-in-kubuntu/](http://www.martynhaigh.com/blog/2012/08/30/accepting-incoming-tcp-ip-connections-in-kubuntu/)

basically all i needed was

```
sudo iptables -I INPUT -p tcp --dport 24800 -j ACCEPT
```
Congratulations :KS

Thank you for sharing your solution with the Ubuntu Forums.

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

