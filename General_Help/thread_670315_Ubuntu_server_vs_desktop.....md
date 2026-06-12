---
title: "Ubuntu server vs desktop....?"
date: 2008-01-17
forum: General Help
---

### Post by vamp4life666 on 2008-01-17
I need to host 20+ simultaneously open network connection from a single machine. Can Ubuntu 7.10 desktop do that or do I need to move up to the server edition?

Michael

---

### Post by tech9 on 2008-01-17
> **vamp4life666 said:**
> I need to host 20+ simultaneously open network connection from a single machine. Can Ubuntu 7.10 desktop do that or do I need to move up to the server edition?

Michael


you need the server edition, it has a built-in dns server for assigning your 20 + clients IP addresses

---

### Post by GavinZac on 2008-01-17
server edition is the exact same as ubuntu desktop, but with pre-prepared options for installing LAMP servers, etc, and without a graphical interface by default,

You can install anything ubuntu-server has on ubuntu-desktop, and anything ubuntu-desktop has on ubuntu-server. So yes, anything you can do from a server install, you can do from a desktop install.

---

### Post by vamp4life666 on 2008-01-17
I'll give it a wirl a see how badly I can crash this box I'm working on.
Here is a question for you. The box I am building is going to have a static ip address. Should I try to configue that during install or after?

---

### Post by vamp4life666 on 2008-01-17
I am intrested in your thaughts but I am getting diffrent responses so in detail, this is what i am up to.

I am developing a rendering farm for student use.
In order to run the farm I need a machine that for all intensive purposes is a network acessible hard drive. This machine needs to be able to host images to 20+ rendering units, In that this machine must be able to support 20+ open network conections. 

For example if you modeled a picture frame sitting on a table and wanted the picture to be of you, your neighbor, spouse, pet, whatever... that image need to be on a mapped network drive. The picture must be on a netwrok drive available to all machines set for rendering, thus the image can't be stored locally.

Ideally, I will be able to configure the machine running  7.10 with a web interface so I can add the images (jpg) that need to be shared from my laptop.

Ideally when Gutsy is configured I can go to any of the win XP boxes that are set for rendering with 3ds max and simply go: map network drive and select the the Gutsy box with the nessary images on it.

Every machine on the network has a manually set IP address, to simplify the movement of data between machines on this private network. 

That is of coure the high hope.....

The way this netowrk should run (ideally) is:
A student, classmate, could walk up, connect to the network. I will copy any of the images they need that are not material defualt built into the program to this server i am trying to build, and then release their job to the render manager. They walk away, while the rendering boxes get the job done.

I hope that explains my situation better.
I am pretty computer friendly in that I have experience with OSX, XP, Vista and I have already setup and netowrked all the other machines to make this work. All that is left is to get this server up and running.

---

