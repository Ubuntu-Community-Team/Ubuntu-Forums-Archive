---
title: "No Xvnc or XDMCP"
date: 2007-02-12
forum: General Help
---

### Post by j-san on 2007-02-12
Hi,

Until today I was happily running Xvnc to have a secondary display over the network.

(See: [http://www.ubuntuforums.org/showthread.php?t=122402&highlight=Xvnc+separate+sessions](http://www.ubuntuforums.org/showthread.php?t=122402&highlight=Xvnc+separate+sessions) if you are interested.)

Today after apt-get update && apt-get upgrade it did stop working, I can connect to the session and get the authentication dialog, but as soon as I enter the vnc password the connection closes.

To troubleshoot I tried first to run Xvnc manually to see if I could spot something dodgy doing: 

sudo Xvnc -rfbport=8000 -securitytypes=none

It did work fine, I could connect to it using a vnc viewer which displayed the standard grey X screen with a X cursor, so Xvnc is ok.

But Xvnc is not the only thing that broke:

I used to acces my edgy box from my XP box too using XDMCP and X-Win32/Xming, now all I get is a nice empty X window with a nice X cursor...

(Of course XDMCP is enable, it always has been on my box).

I have been trying to find out where the problem is for hours and I can not find anything wrong...

Help me please...

---

### Post by grumpymole on 2007-02-12
It's probably this [bug]("https://launchpad.net/bugs/78282"), introduced a short while ago with a security upgrade to vnc4server.

There is a workaround: see [here]("http://grumpymole.blogspot.com/2007/02/edgy-and-feisty-vnc4server-still-not.html").

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by j-san on 2007-02-13
Hi,

Warren, thank you very much, it turn that the bug you mention seems to be the responsible, downgrading the vnc4server package fixed the issue.

I did bang my head against the table for hours and all it was is a bug...

I did not know you could downgrade a package, this has been a first.

Very frustrating experience, in case someone else runs on the same problem here is what I did:

```

sudo apt-get install vnc4server/edgy

```

and then I created the file:

```

sudo vim /etc/apt/preferences

```

and wrote inside:

```

Package: vnc4server
Pin: version 4.1.1+xorg1.0.2-0ubuntu1
Pin-Priority: 1001

```

To pin the package and prevent apt-get/aptitude from updating it.

That did for Xvnc, but... what can I do for regular X over XDMCP? any idea where can I start looking? I can not find what's wrong either... :(

---

