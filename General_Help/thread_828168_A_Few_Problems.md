---
title: "A Few Problems"
date: 2008-06-13
forum: General Help
---

### Post by ToaStOmGi on 2008-06-13
First problem. Whenever it ry and run the Synaptic Package Manager, this pops up.
[IMG]http://i30.tinypic.com/a4plrq.png[/IMG]

The other problem. Im trying to install limewire and when  try and install the package it says this.
[IMG]http://i26.tinypic.com/e5mf88.png[/IMG]
But there is no other program running as you can see.

So, whats wrong?

P.S: I've tryed restarting, didnt help.

---

### Post by The Tronyx on 2008-06-13
Per the first pop-up window, did you run: **sudo** dpkg --reconfigure -a ?

You need to use sudo as noted when it says, "requested operation requires superuser privilege."

---

### Post by cdtech on 2008-06-13
Did you try to run the command:
sudo dpkg --configure -a

Make sure you have no other Package Manager running, look in your Systems > Preferences > Sessions and click on the Current Session tab.

Hope this helps ya......

---

### Post by snowpine on 2008-06-13
Hi Josh, you are on the right track! You just need to add 'sudo' to execute a command as the superuser:

```
sudo dpkg --configure -a
```


edit: Great minds think alike!

---

### Post by avtolle on 2008-06-13
On the second problem, close all file manager applications, then start the one you want to use, all as is set forth in the error message.

---

### Post by ToaStOmGi on 2008-06-13
> **avtolle said:**
> On the second problem, close all file manager applications, then start the one you want to use, all as is set forth in the error message.
As i said in my post, i dont have any open, except the limewire one.

---

### Post by avtolle on 2008-06-13
If you had the terminal up trying to do the dpkg command, there likely was the greyed out cog wheel in the top panel, which indicates a package manager is working. Please note that this stays active a bit (short or long) after trying to do anything with packages, files, etc, and could have been the cause of the conflict, if you were trying to install limewire shortly afterwards. Just a thought.

---

### Post by snowpine on 2008-06-13
> **ToaStOmGi said:**
> As i said in my post, i dont have any open, except the limewire one.

What about "flashplayer installer"? :)

---

### Post by ToaStOmGi on 2008-06-13
Ok so, an update. I did sudo dpkg --reconfigure -a and it did this. Didnt really get me anywhere.
[IMG]http://i30.tinypic.com/2zejnra.png[/IMG]

2nd part. Are any of these causing the limewire isntallation problem?
[IMG]http://i31.tinypic.com/10y3m6g.png[/IMG]

---

### Post by ToaStOmGi on 2008-06-13
> **snowpine said:**
> What about "flashplayer installer"? :)
Thats just the download, it isnt open, its jsut on my desktop from when i installed it the other day. These problems started to occur today.

---

### Post by ToaStOmGi on 2008-06-13
> **avtolle said:**
> If you had the terminal up trying to do the dpkg command, there likely was the greyed out cog wheel in the top panel, which indicates a package manager is working. Please note that this stays active a bit (short or long) after trying to do anything with packages, files, etc, and could have been the cause of the conflict, if you were trying to install limewire shortly afterwards. Just a thought.
No, i tryed to install limewire and do that code at 2 different times. I tryed to install limewire before i did that also, so im sure its not what your talking about.

---

### Post by avtolle on 2008-06-13
On the second set of screenshots, it looks like the files listed were configured and installed. Thus, the lack of response from running the same command after the message. You already have the answer to the super user error message.
Part 2: do you have compiz effects running? I don't use it, but many threads have revealed problems that arise with desktop effects running while trying to accomplish tasks, which are resolved by turning the desktop effects off, then trying again.

---

### Post by ToaStOmGi on 2008-06-13
Alright ya, ill try and turn them off and try it. And the superuser message didnt get e anywhere, alls it did was say that stuff but it didnt do anything.

---

### Post by ToaStOmGi on 2008-06-13
Another update:
What you said avtolle worked. i turned off compiz and it worked, thanks =].

After limewire s done installing im going to try the package manager and see if compiz was causing that not to work as well.

---

