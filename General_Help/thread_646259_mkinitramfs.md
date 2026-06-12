---
title: "mkinitramfs"
date: 2007-12-21
forum: General Help
---

### Post by choward666 on 2007-12-21
I've a problem with extracting and then "rebuilding initramfs".  I've recently download a program which, in order to remove the demo feature, you must extract from the ISO and .img file by using the follwing command:

 gunzip -c < ~Desktop/cult/cult.img | cpio -ivdum

This populates the ~Desktop/cult directory with the contents of the cult.img.  Once extracted, you are to edit a .conf file in the "conf" directory.  I do so and the proceed to the next step:

Rebuild the initramfs

Not much help after that.  I have this directory ~/Desktop/cult/ in which I wish to rebuild the cult.img (which is x-gzip mime type).  I'm assuming I use the "mkinitramfs" command, but every time I do, it rebuilds using my (what I assume is kernel/user environment -- I'm a newb) into the cult.img file instead of the desired directory.  I've used the following variations of the "mkinitramfs" command:

mkinitramfs -o ~/Desktop/cult/cult.img
mkinitramfs -o ~/Desktop/cult/cult.img -r ~/Desktop/cult/
mkinitramfs -o ~/Desktop/cult/cult.img -d ~/Desktop/cult/

I contacted the codtech people who designed the software, but they wish to charge me 100 EUR in order to obtain a direct link of the iso with the changes already made (kind of defeats the purpose of open source and GNU--but I can respect their Microsoft approach.)  They do state clearly in their WIKI, that we are more than welcome to change any aspect of the software, but leave a very terse description how to do so.

Again, my goal is to create the .img file using the desired directory, not my default kernel.. or whatever it is.  Any help would be appreciated

-Chris

Here is a link to the wiki article I mentioned above:
[http://cult-thinclient.wiki.sourceforge.net/FAQ](http://cult-thinclient.wiki.sourceforge.net/FAQ)

---

### Post by choward666 on 2007-12-26
help?

---

### Post by utahraptor2 on 2008-01-20
I solved this problem. It took me five straight hours of researching cpio's function and examining the cult.img archive, but I got it! Here's how to do it - and why it works the way it does:

After navigating in Terminal to the directory which holds the decompressed folders, run the following command:

**find * | cpio -o -Hnewc | gzip >cult.img**

the "-Hnewc" parameter suppresses some output and does something vague, but it also has limited compatibility across the board. It worked fine both ways for me in Fedora Core 7 (Blasphemy?), and I wouldn't see why it would cause any problems in Ubuntu.

Now, let's examine the command:

"*find * "*
cpio is an archive system which doesn't maintain a real directory hierarchy; as well, it by itself seems to be stripped down and unable to know what it's compressing. For this reason, you have to combine the 
"find [wildcard] print" to the effect of displaying every file and directory in your working directory.

*| cpio -o -Hnewc*
cpio archives all of the previously displayed files, and marks their directory structure. *SOMEHOW*
it compiles all of these files into a single file called "cult". I suspect it has to do with the next command:

*gzip >cult.img*
This command takes the completed output ("cult") and puts it into the archive file "cult.img", which is actually a ".gz" compressed archive renamed to the ".img" extension.

Voila!

And they say Marines are groundpounders.

Hope this helped you!

Note: mkinitramfs has absolutely nothing to do with any it...the package isn't checked against a hashing algorythm, so a small modification of the scripting has no effect on the operation of the OS. I suspect that the author of the Cult Thin Client put that in the Wiki to throw people off...but that's just me.

---

### Post by maward on 2008-04-16
You guys have helped me out quite a bit here. THANKS!

Chris, did you ever get the RDP session to login automatically?
If so, could you please explain the modifications you made?

Thanks,
Mark

---

### Post by dtmilano on 2008-04-22
Add the required rdp options (-u, -p, etc.) as showed in [cult custom usage]("http://codtech.com/wiki/index.php/CULT_classic_custom:_usage#CODTECH_Universal_Linux_Thinclient_3.0_.28rdp.29").

---

### Post by drabina on 2008-06-20
I am a Linux noob. I was able to mount the ISO file, then extract contents of cult.img file and modify the timeout settings. Now I have two questions/problems that I cannot solve. Any help would be appreciated.

1. Where do I change the default WTS server name? I need to enter my own IP for the Remote Desktop server. I would also want the RD to startup automatically.

2. When I execute the ```

find * | cpio -o -Hnewc | gzip >cult.img
``` command I get the following error ```
cpio: invalid option -- o
BusyBox v1.2.2 (2006.12.07-15:23+0000 multi-call binary
Usage: cpio -[dimtuv][F cpiofile]
```

Help!

---

