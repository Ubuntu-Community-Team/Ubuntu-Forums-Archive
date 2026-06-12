---
title: "Mounting Ubuntu Partitions via USB stick"
date: 2014-11-18
forum: General Help
---

### Post by ubupro97 on 2014-11-18
Hello, so if you dig a tiny bit in my history you'll see I have an ongoing issue with a broken Xubuntu on one of my machines (as JoshuaMiller0).

I seemingly have no way to fix the issue and I cannot figure out how to access the files stored on it. The machine also has a working version of Ubuntu on it which I can use, but I seem unable to mount the Xubuntu partition (I probably haven't attempted it right). I also conveniently set up a root password on Ubuntu and forgot it (I can probably still guess it if needed). 

I am planning to wipe my computer completely, but I want to get some files first. I created a usb wth xubuntu 14.04 LTS on it and I want to mount the two other partitions and grab some file off before installing xubuntu over the other two partitions and wiping them completely. How do I do this?

Thanks,
Joshua Miller.

[B]
Edit[/B]: On loading the USB, I found I could just open two different  "volumes" labelled "30 GB Volume" and "60 GB Volume". The two volumes  have a directory "medial/xubuntu" (note no ubuntu visible) I'm currently  looking through the files trying to identify which OS each are from.

Note that I may have stuffed up in updating Xubuntu 10.04 LTS to 12.04  LTS and there is a chance I am looking at two xubuntu versions and not  the ubuntu version. I really have no idea how to tell different ones  apart from their files.

**Edit 2:**
I have determined which is which linux distro. I appear to have access to copy things off the the Ubuntu partition (the one I already have access to), but not the Xubuntu partition. How can I gain access to this, or can I just back up my Ubuntu partition and install Xubuntu 14.04 over 12.04 so that my 12.04 files remain?

**Edit 3**:
I will need some help now. I started the 14.04 installer and ran into this message: [http://puu.sh/cVNKt/134d2bd5f8.jpg](http://puu.sh/cVNKt/134d2bd5f8.jpg)
I don't know whether unmounting will give me access to the files I need, or make them unavailable, so I am leaving it alone until further advice.

**Summary of updates:**
Using my USB with Xubu 14.04, I have located the Ubu 12.04 and Xubu 12.04 partitions, but I do not have access to copy any files on Xubu 124. I can back up everything I need from Ubu 124, and then I could possibly install Xubu 144 in replacement of Xubu 124 so that my files are kept. When I ran Xubu 144 installer, I got this [message]("http://puu.sh/cVNKt/134d2bd5f8.jpg") and I have no idea what to do so I am waiting on help.

Thanks again,
Joshua Miller.

**Edit 5**:

That was extremely unexpected. While backing up my Ubu 124 data my processor fan decided to start up, but it seems that the machine is getting very old and it starting making a loud whirling noise as the computer overheated to oblivion. I just killed the pc and it's cooling down while I inspect the issue.

---

### Post by cal1j on 2014-11-18
What does it look like when you try viewing your partitions in gparted from the live USB?

---

### Post by ubupro97 on 2014-11-18
> **cal1j said:**
> What does it look like when you try viewing your partitions in gparted from the live USB?

Gparted? Sorry, I may not have mentioned I am a complete rookie with this even though I've been using it for four-five years -_-.

---

### Post by cal1j on 2014-11-18
No problem. I am still learning and feeling stupid despite spending an absurd amount of time spent learning *NIX. Ok so boot into your system with the live USB. Run:

 ```
sudo gparted 
```

in the terminal. I'm assuming you can bring up a terminal (command line), if not I'll help you get that too. If it says gparted isn't installed, then run this:

```
sudo apt-get install gparted
```

Once installing has completed, run the first command again. The gparted window should look something like this:

[IMG]http://gparted.org/screens/gparted_1_big.png[/IMG]

Once you have it running, take a screenshot like the one above and post it. I'll see if I can help from there.

---

### Post by ubupro97 on 2014-11-18
> **cal1j said:**
> 

 ```
sudo gparted 
```


Oh yes, I remember doing this earlier when getting help from someone else around this same issue. I then got busy and by the time I was around to it the thread was locked.

I ran into some issues with my processor fan dying and all, so I will put the computer back together in the morning and get back to you (I had to remove basically every component to get to the damn thing and the back cover still won't fully come off and I can't find any more screws).

---

### Post by oldfred on 2014-11-19
If launching gui apps from terminal, use gksudo.
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

But you cannot use gparted on mounted partitions, so it is not normally installed, but is on the live installer.
And from live installer you can just launch from Unity. If any key icons show then that partition is mounted, swap usually is, and you have to unmount or with swap swap-off to unmount.

---

