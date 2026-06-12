---
title: "In-house streaming from Windows computer"
date: 2017-03-23
forum: General Help
---

### Post by cytoph on 2017-03-23
Hi, this is my very first thread on this forum and I have a very special idea, but I hope I can be helped.

[B]I think of the following setup with two computers:
[/B]
[LIST]
[*]One with intermediate hardware and ubuntu installed for normal desktop use (like browsing, listen to music, watch movies, etc.)
[*]The other one with high-end (or just good gaming) hardware and Windows 10 for - of course - gaming and software that's not available on linux (Adobe CC, MS Office. etc.)
[/LIST]

[B]It would be perfect, if I could work like this:
[/B]
I mainly use the linux computer. If I want to play a game or start e.g. Adobe Photoshop, I want to click a shortcut/run a script and on my windows computer the specified game/application should be automatically started and streamed (or anything else) to my linux computer in full screen oder window mode depending on the started application/game.


[B]Now my question is simply:
[/B]
Is there a way to get this to work? And if yes, how?
I thought of an approach with moonlight stream, but I don't think I can start the applications on my Windows computer with a script from my linux computer and then automatically start streaming it.
Another idea was via steam in-house stream, but at this very moment I could not test this, with software, that is not officially a steam software.

P.S.: If this thread is not int the correct forum please be so kind and move it to where it should be.

---

### Post by Perfect Storm on 2017-03-23
Moved to General Help.

---

### Post by dragonfly41 on 2017-03-23
By coincidence I'm learning how to use Fabric to run remote scripts  on a remote server (but not for gaming).
[http://docs.fabfile.org/en/latest/usage/interactivity.html](http://docs.fabfile.org/en/latest/usage/interactivity.html)
That might be one useful tool in your toolbox.

Regarding video streaming on Windows you might look at Red5 (java based) although it is somewhat dated.

So to summarise the idea, build some front end GUI in Linux using Fabric for automation of running remote scripts (could be just python scripts or something more elaborate).

Then install Red5 on Windows and access via port 5080 on Windows server.

Red5 is not to be confused with Red 5 Studios.

You could also try Fabric to run remote scripts to run moonlight stream (which you started looking at).

---

### Post by sp40140 on 2017-03-23
If I understand correctly, you are asking for Application (Games) virtualisation. There are enterprise vendors like Citrix which provide this. However, Gaming is beast which I don't think will work as it relies heavily on the GPU of Windows machine for performance. So, you likely can run some scripts, but getting native windows performance by streaming to linux machine is not likely to work.

---

### Post by Delvien on 2017-03-23
I do this currently OP. I have my windows machine running a vm linux server, for various things, and then the host os running steam 24/7 for in-home stream games

I then use my laptop as my main rig, whetheris docked to my main display, or lounging around the house. When I want to just use my windows 10 pc for non-game things I use chrome remote desktop (its been the fastest and most realiable so far of all the services i've tried.)

But I am very open to others opinions and solutions in the matter, as any improvement would be greatly welcomed.

---

### Post by sp40140 on 2017-04-02
I just came across this thing. You should look into:
[https://xpra.org](https://xpra.org)

---

### Post by SeijiSensei on 2017-04-02
For media sharing, you can use DLNA-based streamers like Plex or minidlna.  They're in the repositories.

However I find the easiest solution is simply to open the file over the network with player software like SMPlayer.  Export the directory where the files are stored using Windows and connect to the share from Ubuntu.  There are various ways to do this.  I recommend creating a permanent connection like this:  [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by cariboo on 2017-04-02
For videos streaming, seeing as minidlna is no longer maintained, I's suggests [Serviio]("http://serviio.org/download"). It runs on Windows, OSX, Linux and others. There is a 15 day free license that renews when ever you reboot the server.

---

