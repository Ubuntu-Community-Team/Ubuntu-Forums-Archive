---
title: "Scripting XDMCP for vnc4server"
date: 2007-03-30
forum: General Help
---

### Post by UncleB on 2007-03-30
Hello all,

I've been using various (but mainly Cirrocco's) guides for setting up a VNC server that connects to a login Window. And, what's more, it all works. But as I'm new to all this I keep killing off my Ubuntu builds and reinstalling them. As they're usually headless I wanted to be able to script the VNC server setup. All of this seems relatively straightforward except the XDMCP part at the beginning...

Setup XDMCP:
[LIST=1]
[*]click System -> Administration -> Login Window
[*]click Remote tab
[*]select "Same as Local"
[*]click Configure XDMCP
[*]remove check from Honour indirect requests
[/LIST]

This is the only bit that needs to be done through the GUI. 

After all that preamble my question is:

Do any of you more experienced folk know how to achieve that from the CLI? 

If so then I could make a post-install script for it.

Thanks in advance for any help.

---

### Post by UncleB on 2007-04-25
In the end I find out how. 

You have to edit /etc/gdm/gdm.conf-custom. Search for the section on XDMCP and change it to the following:

```
[xdmcp]
Enable=true
HonorIndirect=false
```

---

