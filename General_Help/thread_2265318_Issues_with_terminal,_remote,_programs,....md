---
title: "Issues with terminal, remote, programs,..."
date: 2015-02-14
forum: General Help
---

### Post by brokenyouth on 2015-02-14
Hello,
I currently have a dedicated server with ubuntu server running on it.
In order to connect to it, I have ubuntu desktop installed in VirtualBox.
My goal is to connect to my dedicated server using teamviewer, I don't know of any other way to connect to it like "remote desktop in windows".
Therefore I installed the desktop on the server and teamviewer using the terminal.
But I can't start any program.
Regardless if text editor or teamviewer or whatever, I get: Gtk-WARNING: **: cannot open display: ""
I have searched google for hours, tried alot.
Then once, it worked but TeamViewer had no ID (network issue? but obviously server internet is working). I disabled the firewall and restarted the server.
Then again I couldn't start anything and I can't find the solution anymore.
I tried VNC connection also, no success. Only some errors.
I am clueless, thanks for any help.

---

### Post by nerdtron on 2015-02-14
It's a bit confusing. You tried teamviewer from where? from the VM Ubuntu to the Server Ubuntu?

Does your server have a GUI? Can't you just use ssh, and operate the server using the command line?

---

### Post by brokenyouth on 2015-02-14
I tried to start teamviewer from ubuntu server.
I installed a GUI with terminal, as ubuntu server has none by default.
I need the GUI because I am unfamiliar with ubuntu and I am not used to operating stuff with terminal and such...
The issues:
1. Cant start programs on ubuntu server.
2. Cant connect to it to see the desktop (teamivewer, vnc)...

---

### Post by ajgreeny on 2015-02-14
Is the GUI running by default on your server or do you just start it when you need it?

---

### Post by brokenyouth on 2015-02-14
Well I don't really know, I used
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install ubuntu-desktop

It's ubuntu 14.10 by the way.[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-02-14
You're making your life a lot harder than it needs to be.
Operating most server features from the command line using ssh is *easy*.
As others have written, managing a server using a GUI is inadvisable for long term. It's harder, longer, and  more complex to set up, it consumes much more resources, it provides a  much greater attack surface, and it limits your conceptual flexibility.

But to answer your specific question:
Ubuntu Desktop's login screen includes a simple remote-login option. Use it to connect.

One problem with X-based applications (like VNC) is that the X server on your server isn't running all the time. It only starts when someone with a login account logs in, and it terminates when that user logs out. But X-based applications connecting remotely need it to already be running; they don't have permission to start the X server. Chicken-and-egg problem with several solutions...but the recommended solution ( remote-login option ) is already installed on Ubuntu Desktop.

---

