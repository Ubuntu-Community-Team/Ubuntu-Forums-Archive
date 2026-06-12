---
title: "Thin Client Customization HELP!"
date: 2008-06-30
forum: General Help
---

### Post by techman.chan on 2008-06-30
I'm new to the whole idea of linux. It would be great if people could give me some step by step instructions instead of run this command and I don't know what to do.

What I'm looking for is to create 2 customized set of thin client images. I'm using the default right now but I don't know how to customized the look and feel of the client. What I mean by this is there some way I can control the client like a Windows 2003 group policy????

Image 1: 10 Kiosk style workstation for employee to use in the break room (only web browser can be runned).

Image 2: 200 Production workstation where employee's do work but lockdown like a school or library so our employees can't customize the systems like their own personal computers and only can run certain programs that they need to use pertaining to their job.

If you ask what kind of company need to lock down computers is that we are a call centre where agents only need to run a web browser and 1 program (program records calls and save to a file server).

Help would be great!

---

### Post by tbeehler on 2008-07-25
> **techman.chan said:**
> I'm new to the whole idea of linux. It would be great if people could give me some step by step instructions instead of run this command and I don't know what to do.

What I'm looking for is to create 2 customized set of thin client images. I'm using the default right now but I don't know how to customized the look and feel of the client. What I mean by this is there some way I can control the client like a Windows 2003 group policy????

Image 1: 10 Kiosk style workstation for employee to use in the break room (only web browser can be runned).

Image 2: 200 Production workstation where employee's do work but lockdown like a school or library so our employees can't customize the systems like their own personal computers and only can run certain programs that they need to use pertaining to their job.

If you ask what kind of company need to lock down computers is that we are a call centre where agents only need to run a web browser and 1 program (program records calls and save to a file server).

Help would be great!

Hey Techman,

I am in the exact same boat you are, only I'm using windows 2003 server for my server instead of ubuntu, but the concepts are the same.

What you want to do, is make sure that your DHCP server is set to boot a particular file image (thinstation linux has a great tool for creating one), but once you've created it and specified in it, set your clients to boot via PXE and they'll automatically go out and look for the boot image and boot accordingly.

If you want to control the clients, simply make whatever change you'd like to the boot file and the changes will propagate next time everyone reboots their machine and thus, loads the new image.

Now, the thinstation people have done a great job of making it easy to create an image, however, some of my hardware isn't supported, and thus, you may have issues there.

I'm currently experimenting with ubuntu to see what kind of fun things I can create.  I'll keep you posted.  In the mean time, let me know all the information you can and we'll see about getting you up and running asap.

---

