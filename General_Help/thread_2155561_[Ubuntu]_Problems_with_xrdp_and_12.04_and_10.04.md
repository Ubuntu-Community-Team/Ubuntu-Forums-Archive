---
title: "[Ubuntu] Problems with xrdp and 12.04 and 10.04"
date: 2013-06-18
forum: General Help
---

### Post by cookbook on 2013-06-18
I'm trying to connect to a computer running ubuntu 12.04 from a windows XP computer using mstsc. I've already installed xrdp through sudo apt-get install xrdp, but I can't establish a connection with the 12.04 computers at all.

On the other hand, there is a 10.04 computer with which I am able to establish a connection through xrdp, but using either the OK button to try to log in or the Cancel button results in a protocol error, reading 

"Because of a protocol error, this session will be disconnected. Please try connecting to the remote computer again"

yielding the same result every time. I also installed x11rdp on the 10.04, but trying to log in through the x11rdp module results in the same error. Any insights are appreciated!

---

### Post by cookbook on 2013-06-18
I'm trying to connect to a computer running ubuntu 12.04 from a windows  XP computer using mstsc. I've already installed xrdp through sudo  apt-get install xrdp, but I can't establish a connection with the 12.04  computers at all.

On the other hand, there is a 10.04 computer with which I am able to  establish a connection through xrdp, but using either the OK button to  try to log in or the Cancel button results in a protocol error, reading 

"Because of a protocol error, this session will be disconnected. Please try connecting to the remote computer again"

yielding the same result every time. I also installed x11rdp on the  10.04, but trying to log in through the x11rdp module results in the  same error. Any insights are appreciated!

---

### Post by cookbook on 2013-06-18
I'm trying to connect to a computer running ubuntu 12.04 from a windows  XP computer using mstsc. I've already installed xrdp through sudo  apt-get install xrdp, but I can't establish a connection with the 12.04  computers at all.

On the other hand, there is a 10.04 computer with which I am able to  establish a connection through xrdp, but using either the OK button to  try to log in or the Cancel button results in a protocol error, reading 

"Because of a protocol error, this session will be disconnected. Please try connecting to the remote computer again"

yielding the same result every time. I also installed x11rdp on the  10.04, but trying to log in through the x11rdp module results in the  same error. Any insights are appreciated!

---

### Post by HiImTye on 2013-06-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you trying to connect with an NX compatible client?

---

### Post by cookbook on 2013-06-19
When I try to connect to the ubuntu computer, I am met by this screen after logging in:
[IMG]http://oi40.tinypic.com/s1u51k.jpg[/IMG]

After which it stalls for a few seconds before closing without an error message.

Although it should look more like [http://www.youtube.com/watch?v=jbJ2tbXcHus#t=01m19s](http://www.youtube.com/watch?v=jbJ2tbXcHus#t=01m19s)

Any insights to this problem would be greatly appreciated

---

### Post by cookbook on 2013-06-19
When I try to connect to the ubuntu computer, I am met by this screen after logging in:
[IMG]http://oi40.tinypic.com/s1u51k.jpg[/IMG]

After which it stalls for a few seconds before closing without an error message.

Although it should look more like [http://www.youtube.com/watch?v=jbJ2tbXcHus#t=01m19s](http://www.youtube.com/watch?v=jbJ2tbXcHus#t=01m19s)

Any insights to this problem would be greatly appreciated

---

### Post by matt_symes on 2013-06-19
**Threads merged.**

Please do not create multiple threads on the same subject.

I dilutes community effort to help you and creates work for staff.

**EDIT:**

Please, one thread and only one thread. You can always ask staff to move it for you if you feel it's in the wrong place.

---

### Post by Toz on 2013-06-19
> **cookbook said:**
> I'm trying to connect to a computer running ubuntu 12.04 from a windows  XP computer using mstsc. I've already installed xrdp through sudo  apt-get install xrdp, but I can't establish a connection with the 12.04  computers at all.
Is there a firewall running on the 12.04 computer? If so, have you allowed port 3389 through? What does this command show:
```
sudo ufw status verbose
```

---

### Post by cookbook on 2013-06-19
> **Toz said:**
> Is there a firewall running on the 12.04 computer? If so, have you allowed port 3389 through? What does this command show:
```
sudo ufw status verbose
```

Running 
```
sudo ufw status verbose
```
gives

```
status: active
logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip
To         Action        From
--         ------        ----
22/tcp     ALLOW IN      Anywhere
22/tcp     ALLOW IN      Anywhere (v6)
```

---

### Post by HiImTye on 2013-06-19
it's not a firewall issue, as they are connecting through SSH, I suspect it's a client that doesn't support NX

edit: try this client [http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Toz on 2013-06-19
xrdp doesn't connect through ssh - it uses port 3389.

Try:
```

sudo ufw allow 3389
```

---

### Post by HiImTye on 2013-06-20
> **Toz said:**
> xrdp doesn't connect through ssh - it uses port 3389.

Try:
```

sudo ufw allow 3389
```I saw 127.0.0.1 in the screenshot and assumed that they were port forwarding over ssh (ignoring the ip in the titlebar)

in that case, yes, you need to either set up an ssh port forward, or open up the rdp port  
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by cookbook on 2013-06-20
> **Toz said:**
> xrdp doesn't connect through ssh - it uses port 3389.

Try:
```

sudo ufw allow 3389
```

I tried this on both the NX and the mstsc client and I recieved the same aforementioned window on the x11rdp, and this detail report from the NX client from the 10.04

[IMG]http://i41.tinypic.com/2n16rye.jpg[/IMG]

and the same one from the 12.04, which I guess is a step in the right direction, considering that it couldn't establish a connection with the 12.04's before I allowed the ports. Also when I use mstsc to xvnc, it can connect but shows a blank desktop to the 12.04. However, using x11rdp gives the same connection log as the 10.04 used to give (and still gives)

Also, if I try using xvnc with 10.04 I get this message
[IMG]http://i41.tinypic.com/mie4jq.jpg[/IMG]


It may be useful to note that after trying to connect with x11rdp, the window kills itself after the 'connected' message, but does not do so after failing to connect to xvnc

---

### Post by cookbook on 2013-06-20
The current state through x11rdp on all versions being
[IMG]http://oi40.tinypic.com/s1u51k.jpg[/IMG]

---

### Post by Toz on 2013-06-20
I'm finding this confusing. Here is what I did to get an rdp connection from a windows box to an ubuntu box:

_On Ubuntu_
```
sudo apt-get install xrdp
```
```
sudo ufw allow 3389
```

_On Windows_
Using Remote Desktop Connection, specified ip address of Ubuntu box

If you try that, does it connect? If not, what messages show up? Also have a look at /var/log/xrdp-sesman.log.

---

### Post by Toz on 2013-06-20
> **cookbook said:**
> The current state through x11rdp on all versions being
[IMG]http://oi40.tinypic.com/s1u51k.jpg[/IMG]

When you are prompted to login, which module do you select? Try the default "sesman-Xvnc" module.

---

### Post by Toz on 2013-06-20
Also found [this link]("http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/"), which states you may need to install gnome-session-fallback if you are using Unity.

---

### Post by cookbook on 2013-06-21
> **Toz said:**
> Also found [this link]("http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/"), which states you may need to install gnome-session-fallback if you are using Unity.

If I try to connect through the xvnc module, I get this error message:
[IMG]http://i41.tinypic.com/mie4jq.jpg[/IMG]

And through the 12.04 with the xvnc module, it works.

---

### Post by Toz on 2013-06-21
What about with the "sesman-Xvnc" module?

---

### Post by cookbook on 2013-06-21
Yeah, by xnvc I meant the sesman-xvnc module, sorry

---

### Post by Toz on 2013-06-21
> And through the 12.04 with the xvnc module, it works. 
So, the connection is established with 12.04 but not with 10.04?

---

### Post by cookbook on 2013-06-21
> **Toz said:**
> So, the connection is established with 12.04 but not with 10.04?

Yes, this is correct. Would seeing the connection log for connecting successfully to the 12.04 through the sesman-xvnc module be informative?

Also, when I try to install gnome-session-fallback, I get "Couldn't find package gnome-session-fallback"
I did make the .xsession file before though

---

### Post by Toz on 2013-06-21
Good news about 12.04.
I don't think gnome-session-fallback existed for 10.04. I'm afraid I don't know what to suggest for 10.04 - it is end of life.

---

