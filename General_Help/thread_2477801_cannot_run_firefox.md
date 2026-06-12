---
title: "cannot run firefox"
date: 2022-08-08
forum: General Help
---

### Post by chat-4432 on 2022-08-08
ubuntu server 22.04
when i try [https://askubuntu.com/questions/1150493/is-it-possible-to-install-firefox-on-ubuntu-with-no-desktop-enviroment](https://askubuntu.com/questions/1150493/is-it-possible-to-install-firefox-on-ubuntu-with-no-desktop-enviroment)
startx
firefox

it shows

```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console.
/usr/bin/firefox: 12: xdg-settings: not found
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:10.0



```
what should i do ??

---

### Post by sudodus on 2022-08-08
Are you running from the console or via ssh? If via ssh, you should add the option -X
```

ssh -X ...

```

Edit: I notice the word 'proxy'. Are you running via proxy? Could that be limiting what you can do?

And if via ssh, what system and desktop are you running in the client?

---

### Post by chat-4432 on 2022-08-08
i think i dont use proxy
i use ssh
when i try
ssh -X startx
firefox
it show
```
ssh: Could not resolve hostname startx: Temporary failure in name resolution
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:11.0

```what should i do ??

---

### Post by sudodus on 2022-08-08
Are you running from the console (a monitor connected to the computer running Ubuntu Server) or via ssh from another computer? If running from the console, you should not involve ssh. But your computer needs some program packages, that you would not need, when running via ssh from another computer.

In case you run from the console, I suggest the following commands
```

sudo apt update
sudo apt install xinit fluxbox
sudo apt install xterm   # if you wish, to get a command line tool in the graphical environment

```

Probably you have xinit already (but anyway). Fluxbox is a simple window manager (simpler than a full graphical desktop environment, yet enough to manage for example Firefox).

See also [this link](https://askubuntu.com/questions/886313/what-is-the-simplest-way-to-have-remote-gui-access-to-ubuntu-16-04-server-from/886398#886398)

---

### Post by arraybolt3 on 2022-08-08
```
ssh -X user@hostname
firefox
```

Try that. If it's painfully slow, try this instead:

```
ssh -X -C user@hostname
firefox
```

Note that "user" and "hostname" need to be replaced as appropriate for your setup - if your username is "Bob" and your system's hostname is "remoteFirefoxServer", then you'd run "ssh -X bob@remoteFirefoxServer" or "ssh -X -C bob@remoteFirefoxServer".

---

### Post by chat-4432 on 2022-08-08
i use mobaxterm
it my mistake i use console 
after install package
when i try 
$ ssh -X startx
firefox
```
ssh: Could not resolve hostname startx: Temporary failure in name resolution
/usr/bin/firefox: 12: xdg-settings: not found
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:10.0

```
when i not involve ssh
$ startx
firefox


```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console.
/usr/bin/firefox: 12: xdg-settings: not found
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:10.0

```both got the same error.
when i 
$ firefox
```
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:10.0

```

i aslo try to install [COLOR=#232629][FONT=-apple-system]chromium[/FONT][/COLOR] [https://serverfault.com/questions/1091926/running-chrome-on-ubuntu-server-how-to-solve-xdg-settings-not-found-using](https://serverfault.com/questions/1091926/running-chrome-on-ubuntu-server-how-to-solve-xdg-settings-not-found-using)
but got similar  error
$ chromium-browser
```
MoTTY X11 proxy: Unsupported authorisation protocol
[8730:8730:0809/044728.815928:ERROR:ozone_platform_x11.cc(247)] Missing X server or $DISPLAY
[8730:8730:0809/044728.816065:ERROR:env.cc(226)] The platform failed to initialize.  Exiting.

```


what should i do ??

---

### Post by chat-4432 on 2022-08-08
> **arraybolt3 said:**
> ```
ssh -X user@hostname
firefox
```
when i try
$ firefox
```
/usr/bin/firefox: 12: xdg-settings: not found
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:11.0
X11 connection rejected because of wrong authentication.
```

---

### Post by sudodus on 2022-08-09
> **sudodus said:**
> Are you running from the console (a monitor connected to the computer running Ubuntu Server) or via ssh from another computer? If running from the console, you should not involve ssh. But your computer needs some program packages, that you would not need, when running via ssh from another computer.

In case you run from the console, I suggest the following commands
```

sudo apt update
sudo apt install xinit fluxbox
sudo apt install xterm   # if you wish, to get a command line tool in the graphical environment

```

Probably you have xinit already (but anyway). Fluxbox is a simple window manager (simpler than a full graphical desktop environment, yet enough to manage for example Firefox).

See also [this link](https://askubuntu.com/questions/886313/what-is-the-simplest-way-to-have-remote-gui-access-to-ubuntu-16-04-server-from/886398#886398)

Did you install **[FONT=Courier New]xinit[/FONT]** and **[FONT=Courier New]fluxbox[/FONT]** according to my previous post?

With those packages installed, you should be able to run
```

startx

```
and get a graphical window manager. And there you should be able to right-click and get menus where you can find how to start **[FONT=Courier New]firefox[/FONT]**.

Maybe it is easiest to install also **[FONT=Courier New]xterm[/FONT]**, and learn where to find **[FONT=Courier New]xterm[/FONT]**, and from an **[FONT=Courier New]xterm[/FONT]** window you can start all programs, that are installed, for example **[FONT=Courier New]firefox[/FONT]**.

---

### Post by ajgreeny on 2022-08-09
Have you allowed X11 forwarding in your server's ***/etc/ssh/sshd_config*** file?

By default I think it is disabled so you will need to enable it by addong a line ***X11Forwarding yes*** to that file to allow it to happen.

---

### Post by chat-4432 on 2022-08-09
i have already install [B][FONT=&amp]xinit[/FONT] and [B][FONT=&amp]fluxbox
[/FONT][/B][/B]xinit is already the newest version (1.4.1-0ubuntu4).
fluxbox is already the newest version (1.3.5-2.1).
xterm is already the newest version (372-1ubuntu1).
when i try 
startx
it shows
```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console.



```

---

### Post by chat-4432 on 2022-08-09
> **ajgreeny said:**
> Have you allowed X11 forwarding in your server's ***/etc/ssh/sshd_config*** file?

By default I think it is disabled so you will need to enable it by addong a line ***X11Forwarding yes*** to that file to allow it to happen.
 i have already checked sshd_config 
it show
X11Forwarding yes

---

### Post by ActionParsnip on 2022-08-09
What operating system are you connecting from please?
Instead of running Firefox remotely, why not setup an SSH tunnel, then set that as the proxy. Your traffic will appear to come out of the remote server but the browser will run on the client system...

---

### Post by chat-4432 on 2022-08-09
i use windows laptop ssh >> linux pc (ubuntu server)
i want to use firefox running on my linux pc show graphical to my laptop
> **ActionParsnip said:**
> What operating system are you connecting from please?
Instead of running Firefox remotely, why not setup an SSH tunnel, then set that as the proxy. Your traffic will appear to come out of the remote server but the browser will run on the client system...
how should i do that ??

---

### Post by ActionParsnip on 2022-08-09
If you are running Windows then you need an X server for the application to stick to. Windows doesn't have one by default. You can use Xming to run an X server and the application will run ok

---

### Post by ActionParsnip on 2022-08-09
Or an SSH tunnel as a proxy
[https://www.math.ucla.edu/computing/kb/creating-ssh-proxy-tunnel-putty](https://www.math.ucla.edu/computing/kb/creating-ssh-proxy-tunnel-putty)

---

### Post by chat-4432 on 2022-08-09
i think probem is in my mobaxterm i can access x11 before (mobaxterm already x11 built in)
but rn i can't access x11 idk why
maybe because port forwarded ??

---

### Post by chat-4432 on 2022-08-09
> **ActionParsnip said:**
> If you are running Windows then you need an X server for the application to stick to. Windows doesn't have one by default. You can use Xming to run an X server and the application will run ok
Xming does't work 
i got the same error 
```
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console.
/usr/bin/firefox: 12: xdg-settings: not found
MoTTY X11 proxy: Unsupported authorisation protocol
Error: cannot open display: localhost:10.0

```
when i double click Xming in my taskbar
it show
Exiting will close all screens running on this display
There are currenly 0clients connected.
Proceed with shutdown of this display/server?

---

### Post by TheFu on 2022-08-10
You need to be running an X/Server on the system you are sitting behind.  You do not run "startx" on either system.
BTW, snap packages really don't like to be run over remote X11 tunnels. Expect some complaints and security dumps, before the X/Client (firefox) dies.

If you need/want to run firefox on the other system and have it displayed locally, don't use the snap version of firefox ... or chromium ... or any other program.

I run firefox and thunderbird remotely through an ssh tunnel for each all-the-time.  Right now, I'm typing in a firefox window running on another machine, just being displayed on the machine I happen to be sitting behind.  The local machine is running 18.04 and the remote system is running 20.04.  No snap packages involved, because they don't work without some added steps. I haven't tried the recently, so those added steps that were working a year ago, may not work anymore.

---

### Post by chat-4432 on 2022-08-10
which command/how to use install apt package ?
i try command above but it force to install snap package.

---

### Post by sudodus on 2022-08-10
[This link shows how to install Firefox via apt.](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)

You can find other tutorials if you browse the internet with the search string 'apt firefox ppa' (without quotes)

---

### Post by chat-4432 on 2022-08-10
i can finally run firefox but[B]
i can't even use x11 all gui package[/B] 
such as gedit (my gedit isn't snap package)


```
MoTTY X11 proxy: Unsupported authorisation protocol


(gedit:7912): Gtk-WARNING **: 12:54:05.626: cannot open display: localhost:10.0
```
i can use nano instead but  there are still problem
anyone know how to fix those ??

---

### Post by TheFu on 2022-08-10
I can only suggest that you stop trying to make a terminal magically become an X/Server.  If you want X/Windows, run a real X/Server on your local machine.  In short, don't use motty
or MS-Windows.  Use a real X11 server which almost every Linux desktop provides.  Then all this stuff "just works".

Since around 2005, I learned that running a small Linux with a GUI inside a virtual machine on my local Windows system worked best and was the most compatible.  There are some tiny Linux distros with X/Windows that use 24MB of space. They fly inside a VM and are 100% compatible with remote X.

---

### Post by sudodus on 2022-08-10
I can confirm that gedit works via ssh between two Ubuntu computers (one server and one client).

We can help you with Linux tools, but if you have problems with some Windows tool or the environment in Windows, you should either start using a Linux system and its tools also at the client side, or ask for help where people are specialized in Windows and tools in that operating system.

---

