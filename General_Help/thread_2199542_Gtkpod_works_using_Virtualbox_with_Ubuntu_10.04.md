---
title: "Gtkpod works using Virtualbox with Ubuntu 10.04"
date: 2014-01-14
forum: General Help
---

### Post by PDA1 on 2014-01-14
**_1- First, a few comments and opinions. If you don't want to read it skip to part 2 below._**

Gtkpod beyond Ubuntu 10.04 is broken. It doesn't work in Ubuntu 12.04. Period. No sense talking about. It's broken. And don't talk to me about how well iPods work with Rhythmbox, Amorak, Banshee, etc, etc, etc. All I want to do is add or remove music and videos from my iPod and GtkPod did the job perfectly in Ubuntu 10.04.

There's a supposed fix on the forum to get GtkPod to work on Ubuntu 12.04 but I've never been able to successfully implement it and have heard nothing from the guy that made it.

After WAY TOO MUCH time (over 50 hours) I've figured out how to get Gtkpod to work successfully by using virtualbox (hereinafter referred to as VB).
[U][B]
Part 2- Procedure I used to get VB Ubuntu 10.04 and GtkPod working[/B][/U]

**1 **- **Installed VB using this method** (yes, I know it's an older version)- 

[http://thedaneshproject.com/posts/how-to-install-virtualbox-on-ubuntu-12-04-lts-precise-pangolin/](http://thedaneshproject.com/posts/how-to-install-virtualbox-on-ubuntu-12-04-lts-precise-pangolin/)


**2- Get guest VB additions/extensions using this method**-

[https://sites.google.com/site/iancharestphd/aide-memoire/installingubuntu1204ltswithguestadditionsinvirtualbox](https://sites.google.com/site/iancharestphd/aide-memoire/installingubuntu1204ltswithguestadditionsinvirtualbox)

**3- Get Ubuntu 10.04 Virtual Disk Image here (I'll refer to it as VDI)**-

[http://virtualboxes.org/images/ubuntu/](http://virtualboxes.org/images/ubuntu/)

(note- on the web page scroll down to find Ubuntu 10.04- it's item number 11. Also, note the login password for the Ubuntu (once you have it running); it's- *"reverse*" (no quotes)

**4- Save the VDI**

**5- Extract the VDI** (it'll take quite a while)

**6- Start VB**

**7- Make a New VB system** (just click New in VB)

**8- Use the VDI as your disk image** (Sorry, I can't remember how I did it)

**9- Plug in your iPod** (I'm using an iPod Classic 160g)

**10- Start VB**

**11- Click on File**---->Preferences------->Extensions and add the VB extensions file

**12- Click ok once the file has been added.**

**13- Click Settings**--------->USB

[B]14- Enable both of the USB option boxes
[/B]
**15- Click on "Add filter from device" **(HOPEFULLY your iPod will be listed there) If it's not then make sure you iPod is mounted in the Host (Ubuntu 12.04) by plugging it in. If you don't see it....click on Places and it should be there. Click on the name of your iPod found in Places and that should create a Desktop icon of the iPod.

As a side note- I've not had any iPod corruption or iPod problems while my iPod was mounted in the Host (12.04) and using Ubuntu 10.04 in VB.

[B]16- close Settings and start your VB Ubuntu 10.04 
[/B]
**17-Login** using the password "reverse" for the VDI

**18- You should see your iPod mounted** and present on the Desktop with an icon. If not- go to Places and you should see it there. Click on it and that should add it to your Desktop.

**19- Install GtkPod.** Go to Ubuntu 10.04 Software Center and install Gtkpod, Libgpod & Libmp4v (pretty sure that's what the name of the file)

And like everyone usually says, "that should do it" (hopefully) and now you'll have a functional version of GtkPod working.

**20- Shared Folders.** Getting more convenient- Shared Folders (between Host and Guest)
Refer to this- [http://www.maketecheasier.com/quick-tips/access-shared-folder-virtualbox-with-ubuntu-guest/](http://www.maketecheasier.com/quick-tips/access-shared-folder-virtualbox-with-ubuntu-guest/)

** Note-** if you want to save an mp4 file from you iPod to your VB Ubuntu 10.04 using GtkPod
          - While in GtkPod.....right click on the mp4 file you want to save to your VB and provide the location where you
            want to save it (in my case- Desktop).

- when GtkPod shows you the "save" screen with the fancy looking text with file suffixes, put in the default file name format- ";%t.mp4" (no quotes). I found I couldn't save an mp4 file without that stuff.

**Note**- a technical issue I've always had with putting mp4 video files onto my iPod- any video that's longer than around 15 minutes or so will speed up around the 15 or 20 minute mark and race to the end. The only fix I have is to transcode/re-encode (or whatever they call it) any video over 15 minutes in length. To solve this problem I use FFMPEG and the following code-

$ ffmpeg -i filename.ext -vcodec libx264 -preset ultrafast -vpre ipod320 -crf 24 -aq 100  -vf scale="320:trunc(ow/a/2)*2"  *OutPutFilename.mp4*

Don't ask me what any of the FFMPEG code means- I have no idea. But it achieves the result I want.


Hope that helps.

---

