---
title: "Setting up a home server"
date: 2013-01-14
forum: General Help
---

### Post by rmcellig on 2013-01-14
I have never done this before. I saw numerous videos on Youtube and am not sure what is the best and hopefully easiest way to do this.

My computer for the server is a Dell Dimension 4500 from around 2001.

Can someone please let me know what is the best way to go regarding setting up a Linux home server?

My LAN has an iMac circa 2006, and 5 PC's running Linux and one of them running Linux as well as XP Pro.

Thanks!!!

---

### Post by matthew.parlette on 2013-01-14
I may have some ideas for you on this, but what exactly are you looking to get out of it?

When I hear home server, I mainly think of storage for media (pictures, music) and maybe streaming of that media to different devices, along with a backup solution for your data.

I can give you a run down of my conclusions on how to handle this, but it would be easier to know what you are looking to accomplish and I can gear my answers to that.

---

### Post by lykwydchykyn on 2013-01-14
In addition to what you want it to do, how do you want to interact with it?  Ubuntu server gives you only a command line by default, there are other systems that give you a browser-based interface or a traditional desktop interface if you wish.

---

### Post by rmcellig on 2013-01-14
Mainly what I am looking for is a central repository to share files over my LAN as well music sharing over my LAN. That's all I can think of for now.
A GUI interaction would be preferable for me rather than using the command line.

---

### Post by lykwydchykyn on 2013-01-14
I would recommend checking out the following, then:

- clearOS
- Zentyal
- freeNAS

All of those are great, ready-to-roll storage server boxes with friendly browser-based GUIs.

---

### Post by rmcellig on 2013-01-14
Thanks!! I will check these out. What's the difference between these and say Ubuntu server?

---

### Post by freeplant on 2013-01-15
You can try some self-hosting dropbox like service.
I think it more suits your need.

* Seafile, [http://seafile.com](http://seafile.com)
* Owncloud

---

### Post by eenofonn on 2013-01-15
not sure about the others but freenas would probably be a good move for you. since you're basically just looking to turn the machine into network attached storage (NAS) from the sounds of it.

---

### Post by lykwydchykyn on 2013-01-15
> **rmcellig said:**
> Thanks!! I will check these out. What's the difference between these and say Ubuntu server?

Ubuntu server has no GUI by default, and even if you install a desktop environment, it still has no graphical tools for configuring services and so forth.  It'll be config files & commands for the most part.

Zentyal is built on Ubuntu server, but adds a nice web-based configuration tool for services.

ClearOS is similar, but it's built on CentOS instead of Ubuntu, so the base OS is more stable and "mature" (read: older versions of software).

FreeNAS is actually built on BSD, not Linux, and is primarily focused on storage services (whereas the others target a wide variety of services, like directory authentication, proxy filtering, printing, etc).

I would check out all three and see which interface looks the most intuitive.  There's no clear right or wrong answer.

---

### Post by matthew.parlette on 2013-01-15
> **rmcellig said:**
> Mainly what I am looking for is a central repository to share files over my LAN as well music sharing over my LAN. That's all I can think of for now.
A GUI interaction would be preferable for me rather than using the command line.

Just as an example of my setup, I have ubuntu server running with samba to host my larger media to my television (by way of XBMC).

I've used dropbox for years, but now with owncloud, I can keep my pictures and music synced between all of my computers and my server in case one of them kicks the bucket. Owncloud has a web interface, and the only limit is the space you have on that server.

The client for owncloud can be rough at times, but it is fairly new and does the job.

I like using ubuntu server so I can then install a minecraft server, or teamspeak, which I've done for my friends and I.

---

### Post by eenofonn on 2013-01-15
> **matthew.parlette said:**
> Owncloud has a web interface, and the only limit is the space you have on that server.

The client for owncloud can be rough at times, but it is fairly new and does the job.


This is why I love the Forums, had never heard of owncloud before and it seems pretty awesome!

---

