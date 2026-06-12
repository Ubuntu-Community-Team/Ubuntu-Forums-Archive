---
title: "[SOLVED] Slow downloading"
date: 2008-06-17
forum: General Help
---

### Post by hellkine on 2008-06-17
When I start to download the installation files it downloads at 1 kib/s with like (119:40:14 remaining) Can anyone help me I use wubi a while back and it worked pretty good but now its downloading slow :(

---

### Post by z0mbie on 2008-06-17
I've you're updating, you should set local mirrors to speed up download:


	1. System > Administration > Software Sources
	2. select Download from: > Other... > Select Best Server
		-repeat this 3 times to get the fastest server.

---

### Post by hellkine on 2008-06-17
I'm downloading it so I can get it up and running because I dont like windows. I'm downloading Ubuntu through Wubi and it is at 650 bytes/s I have a 10 meg connection is there a problem with the server or something or is it on my part.

---

### Post by Exonimus on 2008-06-17
what you could do is download the ubuntu image and download wubi seperately, place in same folder, disable network connections and let wubi install from the image instead of downloading everything from the wubi server(s?)(it will do that automatically if you dont have an internet connection)

ubuntu image from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and you already have wubi. Again, place them in the same folder, don't use the version that's on the ubuntu cd.

---

### Post by hellkine on 2008-06-17
Im doing that right now Ill post to tell you if it works.

---

### Post by hellkine on 2008-06-17
I got it to install Now I rebooted picked ubuntu and when I go there it gives me a error about something floppy I will write it down and post it here I was looking for support on the error on other threads. Also it wont let me do anything expect do the command thing but I dont know how to use that.

Edit:This is the error i'm getting
find --set-root--ignore-floppies/Ubuntu/install/boot/vmlinuz

Error 15: file not found

So im guess a files missing any help?

---

### Post by hellkine on 2008-06-17
Fixed im using ubuntu now I was using the alter disc and not the desktop one.

---

### Post by oohwewubi on 2008-07-21
> **Exonimus said:**
> what you could do is download the ubuntu image and download wubi seperately, place in same folder, disable network connections and let wubi install from the image instead of downloading everything from the wubi server(s?)(it will do that automatically if you dont have an internet connection)

ubuntu image from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and you already have wubi. Again, place them in the same folder, don't use the version that's on the ubuntu cd.

Hi,
I'm having the same issues.  I tried this answer and either I did something wrong or it doesn't work for me.  I tried down;oading wubi but like the op the download was at 1kib/sec and time remaining kept going up.  I then saved wubi and tried to run it from there and got the same slow problem. then I read this post and went to the link above and got the same slow download.  I have DSL that's all I know about my internet connection.  Any suggestions would be deeply appreciated.

---

### Post by ago on 2008-07-21
It might be that the server is busy, there are several mirrors available [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) or you can use bittorrent

You need the 8.04.1 DESKTOP ISO.

---

### Post by oohwewubi on 2008-07-21
> **ago said:**
> It might be that the server is busy, there are several mirrors available [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) or you can use bittorrent

You need the 8.04.1 DESKTOP ISO.
Thank you ultimately the bitorrent worked.  Now I have both wubi and ubuntu in the same folder but wubi keeps asking me to connect to   the internet.  Am I missing something?

---

### Post by ago on 2008-07-21
> **oohwewubi said:**
> Thank you ultimately the bitorrent worked.  Now I have both wubi and ubuntu in the same folder but wubi keeps asking me to connect to   the internet.  Am I missing something?

Make sure you use wubi rev 506
Make sure there are no other ISOs laying around
Make sure you are using a DESKTOP ISO
Check the md5 of the ISO against the md5 in [http://releases.ubuntu.com/8.04.1/MD5SUMS](http://releases.ubuntu.com/8.04.1/MD5SUMS)

If none of the above helps see the wubi log which is in your user temp folder.

---

### Post by oohwewubi on 2008-07-22
Thank you.  I had an extra ubuntu laying around from earlier I forgot to erase. I had wubi in the folder with it but they are now together and it didn't ask for internet connection during install. :)  After reboot I was expecting it to give me a choice between wubi and windows but it went straight to windows. 

Update: ok it was giving me the choice at reboot...if you blink you miss it!  I am now completely, installed...I an"t thank you enough Ago.

---

### Post by novabobogun on 2008-12-17
Instead of confusing Wubi with placing the iso in the folder Wubi creates, try downloading the iso from ubuntu, download daemon tools lite, run the iso and select install in windows. Then you delete the original iso you got off the site, i'm not sure if it works but i'm going to try it.

---

