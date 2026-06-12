---
title: "How to mount .nrg, cue/bin, .ccd etc. cd-images in Feisty Fawn?"
date: 2007-04-23
forum: General Help
---

### Post by Civean on 2007-04-23
Hi,
I finally got fed up with all XP problems and decided to switch when Feisty Fawn was released. Everything was a smooth ride, which really impressed me since last time I tried with linux I ended up rummaging around in terminal mode to get internet to work... anyhow!

The problem I have is indicated in the title, how to do this under linux? (using the loopback device doesn't work, it only supports .iso, and converting from these formats to .iso loses critical information)

Through reading around on various forums I got the tip to try out CDEmu, which supports all these formats. After installing (6 hours of hair pulling, since it's not in the repo's), I mounted my first cue/bin under linux, and voilá! It worked! But... all the mounted files are corrupted. Further reading around sent me to this thread:

[http://ubuntuforums.org/showthread.php?t=276743&highlight=cdemu]("http://ubuntuforums.org/showthread.php?t=276743&highlight=cdemu")

more specifically, these posts:

[http://ubuntuforums.org/showthread.php?t=276743&page=4&highlight=cdemu]("http://ubuntuforums.org/showthread.php?t=276743&page=4&highlight=cdemu")

This is  my exact same problem. And reading on, there is apparently no solution, CDEmu is as of now broken. So I went on, and found a new, experimental, userland CDEmu rewritten by the developers for CDEmu 0.9:

[http://www.kabelkaos.net/cdemu/]("http://www.kabelkaos.net/cdemu/")

There are however no instructions for how to install or use this program. I successfully compiled and installed 3 of the 5 packages after hours of work, but 2 eludes me to this day. (I posted the error messages in the end of the thread above)

So, here I am. I have honestly no idea how to proceed with this, and this is really a deal breaking issue for me (and many others I know). Using the original cd's is not an option, since they are quite far away from me (exchange student). Have I missed some program or some method to do this? I mean, this is one of the major functions for my computer normally, using daemon tools under WinXP. 

If this functionality existed natively under linux, I know a whole bunch of people who would switch right now...

Any help is greatly appreciated!

(System specs: plain Feisty Fawn Ubuntu, Compaq nc6000 laptop)

---

### Post by Civean on 2007-04-25
Is there really no way?

---

### Post by mskadu on 2007-04-25
though i've never tried this myself, you may want to check out the following:

[http://ubuntuforums.org/showthread.php?p=2476444](http://ubuntuforums.org/showthread.php?p=2476444)

Also, i believe you can mount ISO's directly using the mount command. For an example, see:

[http://www.bi03.co.uk/home/blog.php?id=10](http://www.bi03.co.uk/home/blog.php?id=10)

hope this helps..

---

### Post by Civean on 2007-04-25
Thank you, I will try it as soon as possible. Shame it requires KDE files, but better than nothing. Wierd that I have not found any information about it while searching around...

I was aware about the second method, doesn't work with other things than .iso....

Again, thanks!

---

### Post by cmon on 2007-04-27
I've tried to run Acetoneiso in gnome (Feisty) and it seems to work, but it wont accept bin files and that's a real set back. Civean (or anyone else) have you found some way to mount a bin file in Feisty, or is it just impossible for the time being?

---

### Post by mskadu on 2007-04-27
Until something better comes up, my suggestion is to convert these files to ISO format and mount them. Here are a few links that can help:

BIN to ISO:
[http://ubuntuforums.org/showthread.php?p=30922](http://ubuntuforums.org/showthread.php?p=30922)

or try binchunker (*apt-get install bchunk)[I]. *See [this]("http://techbycolin.com/?p=130").

[/I] 
NRG to ISO: use nrg2iso (avialable via apt-get if not already installed)

hope this helps..

---

### Post by cmon on 2007-04-27
> **mskadu said:**
> Until something better comes up, my suggestion is to convert these files to ISO format and mount them. Here are a few links that can help:

BIN to ISO:
[http://ubuntuforums.org/showthread.php?p=30922](http://ubuntuforums.org/showthread.php?p=30922)

or try binchunker (*apt-get install bchunk)[I]. *See [this]("http://techbycolin.com/?p=130").

[/I] 
NRG to ISO: use nrg2iso (avialable via apt-get if not already installed)

hope this helps..

Sweet dude!! :D That did the trick. Thanks a lot :).

---

### Post by Civean on 2007-05-02
Sorry, but it doesn't work for me, the iso format removes necessary information from the image file. So, for the time being I waiting for the new CDEmu userspace project to mature, it seems very promising.

---

### Post by mskadu on 2007-05-02
Please tell me more. What information is removed?
:popcorn:

> **Civean said:**
> Sorry, but it doesn't work for me, the iso format removes necessary information from the image file. So, for the time being I waiting for the new CDEmu userspace project to mature, it seems very promising.

---

### Post by Civean on 2007-05-19
The cloneCD and cue/bin formats are 1:1 disc copies, preserving all copyprotection data etc, which is needed if you want to circumvent DRM...  (as for me, want to load my legally purchased cd's from a harddrive instead of lugging them all around across the globe)

---

