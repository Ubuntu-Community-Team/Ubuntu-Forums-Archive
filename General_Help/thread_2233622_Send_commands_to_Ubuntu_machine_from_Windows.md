---
title: "Send commands to Ubuntu machine from Windows"
date: 2014-07-09
forum: General Help
---

### Post by quadrplax on 2014-07-09
I have a machine running Ubuntu 14.04 which I would like to be able to remotely send commands to, to be able to use as a server. To connect it to ethernet it would need to be in a place where it is physically not accessible. My router is slow so even an intranet-based remote desktop connection in torture to use. I would like to be able to send terminal commands, and ideally get feedback from them, from my main computer which runs Windows 7. Is there any way to do this?

---

### Post by Gyokuro on 2014-07-09
Hi

I would enable ssh on your Ubuntu box and on Windows you can use/download putty.

- HTH

---

### Post by Lars Noodén on 2014-07-09
Usually the best way to have remote access to a server is to use the package [openssh-server](http://packages.ubuntu.com/trusty/openssh-server) and then connect via SSH.  Most systems, including Ubuntu, have an SSH client pre-installed so you can connect with that.  If you still have Windows on the older machines you will have to install your own SSH client, and [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) or something like that will do the job.  

Note that as soon as you connect the machine to the net, other machines will be probing it.  One of the best ways of mitigating that is to disable password login for the OpenSSH server and then use keys or certificates for authentication.  That's very easy to set up in Linux, OS X or BSD.  I'm sure it can be done even in Windows, though like everything else it is probably more complicated. 

Once you have the SSH server up and running and can log in, you can interact with the shell at the exact same level as if you were sitting at the machine itself.

---

### Post by quadrplax on 2014-07-09
The PuTTY to openssh-server connection works fine, tested it on cd and cp commands. However, if I try to run an application it does not work. With gedit it gave me
```
(gedit:3753): Gtk-WARNING **: cannot open display:
```
(No, I did not cut that code off by mistake). I tried running a java application and it said:
```
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
```
I'm obviously pretty new to networking like this, how would I go about fixing this problem? Seeing the GUI programs from my host machine would be nice, but isn't necessary at all.

---

### Post by Lars Noodén on 2014-07-10
If you want to run graphical programs on the remote machine but have them display on your local machine, then use X11 forwarding.  That would be the **-X** option, note that it is a capital X not a lowercase one.  

```

ssh -X  quadrplax@someserver.example.com

```

Be sure to read the -X section in the manual page for ssh for the details.  Over time you'll also pick up using the shell which, once you know it, is far more flexible, powerful and faster.

---

### Post by steeldriver on 2014-07-10
Note that the equivalent of the -X switch in PuTTY is a check box 'Enable X Forwarding' under Connection --> SSH --> X11

[ATTACH=CONFIG]254612[/ATTACH]

Also note that on Windows, this will only work if you have a 3rd party X server running - you can do that either via cygwin or a standalone X server such as Xming

A different approach is to forward the whole desktop remotely using VNC / FreeNX etc.

---

### Post by quadrplax on 2014-07-10
Ok steeldriver, that works fine. I am also trying to get a remote desktop set up so I have it if needed ([http://ubuntuforums.org/showthread.php?t=2233675]("http://ubuntuforums.org/showthread.php?t=2233675&p=13069573#post13069573")).  One of the problems I see with this, however, is that I loose access if  I disconnect from the server. Obviously, one of the benefits of a  dedicated server is I won't have to leave my main machine on always. For  example, I started a Minecraft server, (accidentally) put the server to  sleep, and when I woke it back up the server was still going. However,  logging in via PuTTY took me to a new session, and I no longer had  access to the server console. So I think what I'm saying is I'd like to  continue the session I left off on whenever I reconnect.

---

### Post by Lars Noodén on 2014-07-10
The way to keep the minecraft console accessible even after a disconnect / reconnect would be to use a terminal multiplexer like screen or tmux.  screen has been around longer, but I am now partial to tmux.  There's a lot written about both.  Either way, start one 'tmux' or 'screen' and then start your minecraft server.  Then you are free to disconnect your ssh session yet still can reconnect.

To reconnect, log in with SSH, then run 'tmux a' or 'screen -rd' to reattach to the (default) session.  Both can get quite fancy if you want to take it further.

---

### Post by quadrplax on 2014-07-10
Ok, Xming and screen are both working great. One (hopefully) last problem though: they don't work together. Yes, I can start a screen session, and open a GUI program, which will open it on my host PC. Yes, I can reconnect to the screen session after. The problem is when I leave the screen session the GUI-based program is terminated.

---

### Post by quadrplax on 2014-07-11
Bump #1, though I probably won't bump this again if nobody responds  because I should probably just use remote desktop for GUI-based  applications.

---

### Post by Gyokuro on 2014-07-11
Hi

If I understand you correct you should start your application on your remote system via: **application &** or example: **xeyes &**

- HTH

---

### Post by Lars Noodén on 2014-07-11
tmux and screen work only for regular text-based applications.  

For graphical applications you'll have to look at VNC / FreeNX.  It's been too long since I've used VNC so I can't remember if it can resume broken connections.  I do remember that it's not so fast.  FreeNX is unfamiliar to me but from what I've read it is supposed to perform a bit better than VNC.  VNC has to be tunneled, I'm not sure about FreeNX.

---

### Post by The Cog on 2014-07-11
I am told you can run a minecraft server without a GUI. Launch it with java rather than with javaw, and add the argument **nogui** at the end. A bit like this:
```
java -jar minecraft.jar nogui
```
There should be some memory settings in the command as well but I forget the details - they don't need changing.

You still need to run it in screen or tmux to avoid breaking the text console it's running in though.

---

### Post by quadrplax on 2014-07-11
Yes, I know you can run Minecraft servers without a GUI, but that is just one example, I would like this system to be more flexible, as I could see myself running other things on it. Isn't VNC just remote desktop? Because I just got that working, so I have that if needed. I can't test right now, but you're saying simply adding "&" will make it run the graphical part on the screen of the server, and let me still access the command line for it with screen? That should be fine for my purposes right now. Will Mark as Solved if that's the case.

---

### Post by The Cog on 2014-07-12
VNC confuses me. 

It can be a desktop viewer, showing you the local desktop that an attached screen would have. 

There is also an X server that creates a virtual GUI inside the machine when you connect, and shows you that, not the physical one. MS would probably call this a "terminal server". This virtual GUI also dies when you disconnect, so this is not the sort you want. 

Both require desktop software to be installed on the server. I'm not sure which VNC packeges in the Ubuntu repositories are which type.

---

### Post by quadrplax on 2014-07-12
Meh, it's not worth it. I set the screen resolution to 1280x720 and VNC (Remote Desktop) gives surprisingly little lag, I'll Mark this as Solved, the original problem is anyway.

---

