---
title: "installing programs and such..."
date: 2006-12-26
forum: General Help
---

### Post by hairmetal4ever on 2006-12-26
Much different than windows.  For some websites, Firefox needs plugins to play videos, esp. Windows Media Player *wmv types.  I downloaded the plugin it asked for and I double click and it can't open.

What's the proper procedure to install a program on Ubuntu?  Is there a good crash-course?

Also, how do I look at how much space is in my filesystem folder?

---

### Post by NeoLithium on 2006-12-26
Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) it has a nice list of options to help you set up the proper codecs to view movies, etc online; as well as a tutorial on installing certain programs.

---

### Post by bodhi.zazen on 2006-12-26
> **hairmetal4ever said:**
> Much different than windows.  For some websites, Firefox needs plugins to play videos, esp. Windows Media Player *wmv types.  I downloaded the plugin it asked for and I double click and it can't open.

What's the proper procedure to install a program on Ubuntu?  Is there a good crash-course?

Primary way is via aptitude, apt-get, or synaptic.

See here for an overview of your options:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

See NeoLithium's link for information as well as here:

Restricted formats:

	[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

	[http://www.ubuntuforums.org/showthread.php?&t=182902](http://www.ubuntuforums.org/showthread.php?&t=182902)

> Also, how do I look at how much space is in my filesystem folder?

In a terminal type:

```
df -h
```

---

### Post by hairmetal4ever on 2006-12-26
> **NeoLithium said:**
> Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) it has a nice list of options to help you set up the proper codecs to view movies, etc online; as well as a tutorial on installing certain programs.

I guess what confuses me is that I will be told "type install such and such" and I'm not even aware of the program file existing on my computer.

---

### Post by NeoLithium on 2006-12-26
Most of those that will ask you to type install, will ask for a command similar to:
```
sudo apt-get install <program name>
``` 
In which case, it will automatically find the program you requested from the Ubuntu repositories, and download/install it for you.

There's other ways as well, such as downloading debian packages; or compiling from source.  Reading through one of the guides, even just a quick scan, will reveal lots to you; and of course search the forum and ask questions.  Once you get started, it's not hard before you start to get the hang of it :)

---

### Post by hairmetal4ever on 2006-12-26
I already know much more than I did.  Thanks for your help.  I'm a whiz at hardware and competent on Windoze but this is still pretty Greek to me.

---

### Post by hairmetal4ever on 2006-12-27
Half this stuff, I do everything it said to, and I still don't have anything working right.

](*,) ](*,) ](*,) 

I tried installing WINE, by putting the info in the repository on Synaptic, selecting and "Apply" and I can't find it anywhere!!  Also installed a bunch of stuff to try and get windows media files to play.  Still, get errors when I try.

---

### Post by JohnBortion on 2006-12-27
The only way to play windows media player files I've found is with mplayer.  You have to enable multiverse in the /etc/apt/sources.list

---

### Post by hairmetal4ever on 2006-12-27
> **JohnBortion said:**
> The only way to play windows media player files I've found is with mplayer.  You have to enable multiverse in the /etc/apt/sources.list

How do I do that?

---

### Post by bodhi.zazen on 2007-01-02
> **hairmetal4ever said:**
> How do I do that?

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

