---
title: "SSH x11 forwarding error"
date: 2023-04-07
forum: General Help
---

### Post by l6qu9d on 2023-04-07
As i am trying to SSH through X11 the server always comes back with the error

X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:11.0

When i than trouble shoot and use the following command:

grep X11Forwarding /etc/ssh/sshd_config

I get the following response:

[COLOR=#B42419][FONT=Menlo]**X11Forwarding**[COLOR=#000000] yes[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]#	[/COLOR]**X11Forwarding**[COLOR=#000000] no
[/COLOR][/FONT][/COLOR]


My question now is what does the second one that is off imply?

Does this mean something is overriding the standard setting in sshd_config?

When i nano in the settings X11 forwarding is on.

Any help would be extremely valued.

P.S. im using a standard mac terminal, xterm doesn't let me SSH to the server

---

### Post by ActionParsnip on 2023-04-07
The second line in the grep is a comment, so is ignored in every way. Do you have an X server running on the Mac? The application needs an X server on the client system to stick to.

This site suggests Quartz
[https://www.businessnewsdaily.com/11035-how-to-use-x11-forwarding.html](https://www.businessnewsdaily.com/11035-how-to-use-x11-forwarding.html)

---

### Post by l6qu9d on 2023-04-07
XQuartz runs on the client side when trying to ssh -X to the server

---

### Post by ActionParsnip on 2023-04-07
> **l6qu9d said:**
> XQuartz runs on the client side when trying to ssh -X to the server

It needs to be running, otherwise the application has no X server to run in.

---

### Post by ActionParsnip on 2023-04-07
> **l6qu9d said:**
> XQuartz runs on the client side when trying to ssh -X to the server

[https://youtu.be/UwQCq35TRXw](https://youtu.be/UwQCq35TRXw)

It needs installing as an extra piece of software. The video gives a good guide.

---

### Post by MAFoElffen on 2023-04-07
+1 to ActionParsnip's great answer. 

MAC OSX needs Quarts to render the graphics of ssh XForwarding. (Otherwise it has no compatible renderer.)

---

### Post by l6qu9d on 2023-04-09
The print of the terminal displays:
[COLOR=#000000][FONT=Menlo]/usr/bin/firefox: 12: xdg-settings: not found[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]X11 connection rejected because of wrong authentication.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]X11 connection rejected because of wrong authentication.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Error: cannot open display: localhost:10.0

Xquartz is not the issue, it is running, so it's already installed...

I'm pretty sure the issue lays in the settings on the server side[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-04-10
Make sure XForwarding actually works first...
```

ssh -X user_name@server_ip

```
Test with 'xeyes' or 'xclock'...

Then note that XForwarding has a problem rendering 'anything' installed on the remote server that is installed with Snap, so if Firefox on the remote XServer has Firefox installed as a Snap package, it will have a problem because of how it does sandboxing and the permissions associated with that... 

So to get around that... Then do this to set an Environment variable to extend that sandbox... as a work-around.
```

mafoelffen@Mikes-B460M:~$ export XAUTHORITY=$HOME/.Xauthority
mafoelffen@Mikes-B460M:~$ firefox --no-remote --no-xshm

```
At least that works on my Computers here...

---

