---
title: "vinagre vnc color depth"
date: 2008-04-27
forum: General Help
---

### Post by gillis on 2008-04-27
Hello i am using vnc a lot to administrate my systems.
With 8.04 the standard vnc client is vinagre. I want to know how you can set the amount of colors to lets say 256. So far i didnt find out how to do that. And since i am connecting to external servers by the internet a full color vnc is terribly slow. 
Are there any alternative good vnc clients in the repository?

---

### Post by ryanhaigh on 2008-04-27
Tightvnc is very good if you have used the tightvnc server as it has features specifically for low bandwidth connections. It has many configuration options some of which are probably applicable to any vnc server. To lower bandwidth requirements I always have the user set the resolution to 800x600.

---

### Post by gcbzzzz on 2009-08-09
So, no way to lower colors on vinagre?

what about in vino?

---

### Post by jasonhoekstra on 2009-10-31
Also curious if anyone finds the answer..... I've looked at man pages and --help, doesn't seem anyway possible to scale back the colors using Vinagre.

---

### Post by chuckh1958 on 2009-11-06
Same here. Love the simple clean interface of vinagre but like the OP I am remote controlling servers over the internet. Scaling back to 8 bit color would make it much faster.

---

### Post by configt on 2009-11-17
I too have been searching for a way to do this.  I was shocked to see that the package made for Ubuntu is nearly unconfigurable in comparison to the separately available packages.  On one hand it is nice to have it seemlessly integrated with minimal OTB configuration, but on the other hand the control is really stripped down to almost nothing.  Add the fact that since 9.04 vinagre doesn't work with compiz, and it becomes very compelling to throw it out and install a separate vnc package.

I am looking forward to having the control and features put back into ubuntu's OTB vnc.

---

### Post by configt on 2009-11-17
Here we go.  Grdc (easily installed from synaptic package manager) connects to vino/vinagre server.  I just tested it across a 384Kbps link and although the graphics were pretty rough looking, it was much more usable than the default client.  You can configure the color depth using Grdc as the client.

I read about this work around solution here:

[https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/203782](https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/203782)

---

### Post by chuckh1958 on 2009-11-17
> **configt said:**
> ... Add the fact that since 9.04 vinagre doesn't work with compiz, and it becomes very compelling to throw it out and install a separate vnc package.

Actually vinagre works well with compiz. I think the first version that came out with 9.04 may have had problems but a subsequent release fixed it.

---

### Post by chuckh1958 on 2009-11-17
I just installed grdc and I think this application is much nicer than vinagre.

---

### Post by emil_donca on 2012-04-21
> **gcbzzzz said:**
> So, no way to lower colors on vinagre?

what about in vino?


There's one way, but pretty convoluted. Indeed, this vinagre client is hardly configurable.

Use the Bookmarks menu to save a bookmark. While you do this, there are some options there that you can tick. I also tick scaling with aspect ratio preserved and fullscreen. Then when you load the bookmark it will have these options applied.

What I would further like, is a way to be able to load one of these bookmarks from the command line. Or alternatively, to be able to specify the options in a .vnc file (which vinagre is able to load but it doesn't ppear to read any options except host=).

---

### Post by oldos2er on 2012-04-21
Closed, necromancy.

---

