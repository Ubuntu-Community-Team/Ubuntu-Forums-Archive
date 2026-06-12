---
title: "How to make X11 requests from remote (ssh -X) apps only show remote windows?"
date: 2021-05-14
forum: General Help
---

### Post by &amp;KyT$0P# on 2021-05-14
I'm trying to set up a Xubuntu machine to also be accessible from another machine on the local network using [FONT=Courier New]ssh -X[/FONT] (in addition to being accessible physically).  Since this method of remote connection reuses the client's window manager, I set up plank so I could have a dock and Applications menu from the remote machine.  plank works, and I can get plank to list windows if I do
```
bamfdaemon &
```
before starting plank.  But then the remote plank also lists *local* windows (!), including applications that aren't on the "server" machine.

How to get plank / bamfdaemon to only list remote windows?  i.e. only show windows from the machine on which plank is installed?

(All machines in question are running Xubuntu 20.04.  And I did try other dock applications, but only plank works for me.)

---

### Post by &amp;KyT$0P# on 2021-05-19
bump

---

### Post by HermanAB on 2021-05-19
Well, I have been using Linux since about 1996 and I have never before heard of Remote Plank.  It is quite possible that nobody else here, has either and you are on your own.  Try to find the developer web site and see if there is a support forum.

BTW, if I need to connect to another computer, run a remote app, or transfer files around, I just use straight up SSH.  It works well enough as is, without additional carpentry. (I'm busy building a fence and it requires about 90 planks of 4 meters each, which is creating a mind boggling amount of shavings and saw dust - but Linux Plank isn't one of them fortunately).

---

### Post by dragonfly41 on 2021-05-19
I found this article recently when learning more about ssh -X (from scratch) and you might find some relevant tips ..

[https://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-to-run-graphics-applications-remotely](https://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-to-run-graphics-applications-remotely)

I use Docky, by the way.

---

### Post by &amp;KyT$0P# on 2021-05-19
> **HermanAB said:**
> Try to find the developer web site 

Looks like [this]("https://launchpad.net/plank") is it.  If no suggestions here, I might try plank's irc channel when I next get chance to do live chat.

> BTW, if I need to connect to another computer, run a remote app, or transfer files around, I just use straight up SSH.

Yes, that too is going to be involved with what I'm trying to do.

@dragonfly41: I saw that link, unfortunately it doesn't help here.

---

### Post by him610 on 2021-05-19
Here is a utube video introducing plank - [https://www.youtube.com/watch?v=8BKD7NolZZA]("https://www.youtube.com/watch?v=8BKD7NolZZA")

> How to make remote Plank over SSH only show remote applications?
Maybe the plank people could better answer your question.

---

### Post by ActionParsnip on 2021-05-20
If you are running a remote X server, why not just run the GUI apps from the terminal and run them that way? It'll be seamless with your local desktop too. Makes more sense IMHO
What applications are you wanting to run anyway? Maybe there is a sleeker solution to your needs

---

### Post by HermanAB on 2021-05-20
Exactly.  There is no need for the extra timber.  One can either launch remote applications directly from the remote ssh shell, or run a remote file browser and use that to run the remote applications if you are mouse click happy.

---

### Post by &amp;KyT$0P# on 2021-05-20
> **ActionParsnip said:**
> If you are running a remote X server, why not just run the GUI apps from the terminal and run them that way?

I would like a full list of the .desktop files for applications I can launch, I would like to launch applications using the same commands as the .desktop files, and I don't want to spawn a lot of terminals/connections or do a lot of [FONT=Courier New]program & program & ...[/FONT] which can quickly get messy.

> **HermanAB said:**
> run a remote file browser and use that to run the remote applications

Interesting suggestion, thanks HermanAB!  I have thunar and pcmanfm.  I'll look into this.

> **dragonfly41 said:**
> I am interested in learning how this remote app service is built from cloud Ubuntu.

Sorry dragonfly41 I don't understand how that helps me and I'm not interested in commercial or web-based solution

---

### Post by &amp;KyT$0P# on 2021-05-20
> **HermanAB said:**
> run a remote file browser and use that to run the remote applications

Thanks again HermanAB for this suggestion.  I've tested it with pcmanfm and although this is not as nice as using plank, it works for me.

But, all of this still does not answer my questions:

1) How can a remote application run over [FONT=Courier New]ssh -X[/FONT] even know about local windows?

2) Is it possible to "turn this off" or otherwise get remote programs to only list windows from the machine on which they're installed?

Sorry I seem to have caused chaos by naming the specific programs I'm working with, I've been pretty exhausted and I realise now that my question is actually more general than any one program.

---

### Post by him610 on 2021-05-20
>  this is not as nice as using plank, it works for me
It seems like you are the only one familiar with plank, so that makes you the subject matter expert. When you figure it out you can come back and fill us in :)

---

### Post by Holger_Gehrke on 2021-05-21
> **halogen2 said:**
> 
1) How can a remote application run over [FONT=Courier New]ssh -X[/FONT] even know about local windows?


By asking the X-server for a list of windows.

Holger

---

### Post by HermanAB on 2021-05-21
“1) How can a remote application run over ssh -X even know about local windows?“ It doesn’t. SSH forwards the X requests from the remote to the local machine.  The local X server handles the windows.  The app doesn’t care which X server does it.

---

### Post by ActionParsnip on 2021-05-21
you can see the commands in the .desktop files with:
```

grep Exec /usr/share/applications/filenamehere.desktop

```
You can then see the command it runs. You can then copy that and run it in the terminal (I suggest backgrounding it with an ampersand.   Eg    gedit & )

But again, what do you do on the remote system once you connect? Why are you connecting at all? What activities do you do on the remote system once you are on there?

---

### Post by &amp;KyT$0P# on 2021-05-21
> **HermanAB said:**
> “1) How can a remote application run over ssh -X even know about local windows?“ It doesn’t. SSH forwards the X requests from the remote to the local machine.  The local X server handles the windows.  The app doesn’t care which X server does it.

Thanks HermanAB, this is very helpful.  I was not aware that using [FONT=Courier New]ssh -X[/FONT] flipped the notion of client/server.

Is it possible to configure the local X server to restrict remote requests to windows from the host issuing the request?

---

### Post by HermanAB on 2021-05-21
"ssh -X flipped the notion of client/server." No, X and SSH don't really flip anything.  The X server serves up the machine screen, keyboard and mouse and makes them available to clients who want to use these devices.  SSH contains a built in X client, which connects the distant machine X server to the local machine X server.

Everything is here:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by scorp123 on 2021-05-21
> **halogen2 said:**
> I'm trying to set up a Xubuntu machine to also be accessible from another machine on the local network using [FONT=Courier New]ssh -X[/FONT] (in addition to being accessible physically). 

Why not **X2go**?
[https://wiki.x2go.org/doku.php/doc:newtox2go]("https://wiki.x2go.org/doku.php/doc:newtox2go")

---

### Post by &amp;KyT$0P# on 2021-05-21
> **scorp123 said:**
> Why not **X2go**?

Tried it and no.  It aborts if the openssh-server is not installed on the client.  That's a non-starter.

---

### Post by TheFu on 2021-05-21
Running a WM over a remote X connection isn't really supported.  I've never heard of plank before which is why I didn't respond.  I know that snaps have trouble running remote, unless we manually link the .Xauthority into the correct place on the X/Client machine.

Apps that require direct access to a GPU will fail to work as well. Obviously, a remote X11 connection doesn't have access to any GPU.

If you want a full remote desktop, then I can only suggest x2go as well.  Last month, I did a bunch of testing around how well/bad that worked and posted in another thread.  Initially, my posts were incorrect for the core problem. At the end, I tried to got back through and correct the things that did and did not work with x2go and wayland, but did work with X11 or x2go+xorg.
x2go does NOT require any ssh-server on the client machine.  There are default settings which may seem to require that, but those can be turned off. Mainly is it local printing and local directory shares.  These work in x2go using sshfs and an ssh-tunnel with the remote system as the client - that usually isn't possible over the internet.

Now, if you use KVM + Spice, then the clients can run QXL video drivers and remote access seems to work very well over virt-viewer using the spice protocol. Alas, this is only possible for VMs running under KVM or Xen. To my knowledge, no other hypervisors support SPICE.  Just looked to see if virtualbox supports SPICE - nope. It is a feature request. Same for VMware hypervisors. None seem to support spice.  When spice was first released, there were plans for it to be the remote desktop protocol for any Linux systems. That goal seems to have been retracted back to just KVM/QEMU and Xen.

---

### Post by &amp;KyT$0P# on 2021-05-21
> **TheFu said:**
> Running a WM over a remote X connection isn't really supported.  

Are you saying that restricting remote X11 requests to windows from that remote host, requires running a full window manager from the remote machine?

---

### Post by scorp123 on 2021-05-21
> **halogen2 said:**
> It aborts if the openssh-server is not installed on the client.

Never had that. And I've built thin clients with this thing so I am pretty sure I know what I'm doing...

---

### Post by TheFu on 2021-05-21
> **halogen2 said:**
> Are you saying that restricting remote X11 requests to windows from that remote host, requires running a full window manager from the remote machine?

No. What I'm saying is there are standards for what a WM should and should not do.  Some of the new WMs do not conform to those standards and will either not work or work poorly.

---

### Post by &amp;KyT$0P# on 2021-05-22
My window manager is Openbox and I can't find any setting for this in Openbox configuration?

I would prefer not to have a full remote desktop, is the type of filtering I'm seeking possible without that?

---

### Post by TheFu on 2021-05-22
> **halogen2 said:**
>  
But, all of this still does not answer my questions:

1) How can a remote application run over [FONT=Courier New]ssh -X[/FONT] even know about local windows?
 Because it is the X/Server providing the list, not the remote X/Clients.

> **halogen2 said:**
>  
2) Is it possible to "turn this off" or otherwise get remote programs to only list windows from the machine on which they're installed? Doubtful, since the X/Server is kinda the entire point.[/QUOTE]

---

### Post by TheFu on 2021-05-22
> **halogen2 said:**
> Thanks HermanAB, this is very helpful.  I was not aware that using [FONT=Courier New]ssh -X[/FONT] flipped the notion of client/server.

Is it possible to configure the local X server to restrict remote requests to windows from the host issuing the request?

ssh uses the C/S as most people expect.  The local machine is the client and the remote machines is the server.

X11 swaps that. The "server" is the machine you sit behind that does the displaying, sending keyboard and mouse events to the clients and all the remote programs (or local programs) are the X/Clients sending requests to the server. When we use ssh -X  (or ssh -Y), all we are doing is
[LIST=1]
[*]setting up a tunnel between the local and remote system
[*]telling the X/Windows system we want X11Forwarding to be used through a specific X-display port
[*]automatically setting a new DISPLAY environment variable, so the correct X-display port is used
[/LIST]

It gets a little fuzzy around the mouse since there are different implementations.  The X/Server knows the most about it, but it also knows which widget it is over and keyboard/mouse events are sent to the windowID and passed in the different layers to the most specific widget that will accept the specific Xevent type.  There are software-mice and hardware-mice implementations.  But none of this is usually important.

Gee - who'd a thunk all that X/Windows Developer training would finally payoff 25 yrs later?  Now If I could just unload the (7) 2inch thick paper books on X11, that would be nice. The complete set came with the training.

---

### Post by &amp;KyT$0P# on 2021-05-22
> **TheFu said:**
> Doubtful, since the X/Server is kinda the entire point.

Thanks TheFu, that answers my remaining questions.  It's weird that this type of filtering doesn't exist.  Fortunately in my specific case all machines involved are trusted and under my administrative control, so at least this won't be a security problem.

For cases where this would be a problem, maybe I can work something with a Xephyr?  Will experiment with that a bit before marking this solved.

* [FONT=Courier New]firejail --x11 --noprofile openbox[/FONT] and doing SSH from a Terminal launched inside the Xephyr does isolate the remote windows from (enough of) the local windows.  Considering this thread as solved as it'll get.  Thanks again all for the help :KS

---

### Post by TheFu on 2021-05-22
X11 is designed to be network agnostic.  Even the local X/Clients connecting to an X/Server on-the-same-machine use IP-sockets to communicate.  The fact that the X/Client could be on a different machine and across the globe isn't really important for X.

It seems you've come to a technique that few people use.  Basically, you want an integrated desktop, but without the desktop.
With most WMs, we can add menu items that run whatever commands we like.  I have a few menuitems in my fvwm that run remote commands for me.
fvwm supports functions, so I have one that does remote ssh sessions.  Here's the line that creates a menu entry to be clicked:
```
+ &istar FuncFvwmRloginSshRxvt  istar
```
And the terminal+ssh 
```
AddToFunc FuncFvwmRloginSshRxvt \
  I Exec rxvt-unicode -fs 18 -bg black -fg white -fa 'Monospace' -name $0 -n $0 -title $USER@$0 -e ssh -X $0 
```

I suppose I could find all the .desktop files on the remote system, pull those back to my workstation, then modify them to use ssh -X:
$ more ~/bin/thunderbird.sh 
```
ssh -X regulus "/usr/bin/firejail /usr/bin/thunderbird" & 
```
But for the stuff I use all the time, I've setup accel keys to launch them or just use tab-completion in a terminal to launch.  That means I'm consistent in the things I've decided to run more protected. Clearly, I'm using ssh-agent and ssh-keys for authentication to remove the prompt hassles.

---

