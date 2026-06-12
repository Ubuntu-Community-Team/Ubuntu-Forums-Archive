---
title: "Photoshop CS2, Wine, Almost There"
date: 2006-10-12
forum: General Help
---

### Post by computergee on 2006-10-12
I am very close to getting Photoshop to run, but I get the following message when photoshop starts up:

You are not allowed to continue because your account does not have the proper privileges. Please login using an account with administrator privileges and try again.

I read that running chmod +w -R on the Adobe folder, in wines drive_c, but that does not work. Anybody have any ideas? I beleive its a permissions issue, but I have no idea how to solve it.

If anyone needs any help getting as far as I have gotten, just ask and I'll try to help.

---

### Post by kuja on 2006-10-12
How about doing a sudo chown -R $USER:$USER on the drive_c and ~/.wine?

---

### Post by computergee on 2006-10-12
Same thing :(, thanks anyways.

---

### Post by kuja on 2006-10-12
Just a note, you may be wasting your time: [http://appdb.winehq.org/appview.php?iVersionId=2631](http://appdb.winehq.org/appview.php?iVersionId=2631)

---

### Post by computergee on 2006-10-12
People have gotten it to work, I followed this tutorial, the actual site is down. But basicly you copy some registry files, the files from a windows partition. People have reported success. Some people have had this problem, but they solved it with " chmod +w -R", but that did not work with me.

[http://digg.com/linux_unix/HOW_TO_Adobe_Photoshop_CS2_on_Ubuntu_10_steps](http://digg.com/linux_unix/HOW_TO_Adobe_Photoshop_CS2_on_Ubuntu_10_steps)

---

### Post by c0rrupt3d_fate on 2006-10-12
meh, I just use gimp :-k

---

### Post by skyshock21 on 2006-10-13
> **c0rrupt3d_fate said:**
> meh, I just use gimp :-k

That's the easy way out.  :p 

We've almost got a working tutorial for how to run Photoshop CS2 on Linux.  Then you don't have to use Gimp anymore, unless you just really really like it.  ](*,)

---

### Post by Littleweseth on 2006-10-13
> **skyshock21 said:**
> That's the easy way out.  :p 

We've almost got a working tutorial for how to run Photoshop CS2 on Linux.  Then you don't have to use Gimp anymore, unless you just really really like it.  ](*,)

Note the use of the phrasing 'have to use GIMP'. With due regard to the developers, Photoshop > The GIMP for nearly everything.

I'm very interested in finding out how to make PS CS2 run.

In any case : Are you sure that the origin of that error message is actually based in linux? I don't know much, but it sounds like it's talking about *windows* privileges.

---

### Post by whizbaby on 2006-10-13
I only want to ask (half-off-topic): anybody of you tried gimpshop?
[http://www.gimpshop.net/](http://www.gimpshop.net/)

---

### Post by jcrnan on 2006-10-13
whizbaby: Ive tried it and its better then gimp but it does NOT compare to Photoshop. Gimp has large technical limitations, gimpshop only changes the gui.

---

### Post by PriceChild on 2006-10-13
> **Littleweseth said:**
> I don't know much, but it sounds like it's talking about *windows* privileges.I'd agree with that... Personally i would try getting windows to emulate it in an environment other than XP, such as 2000

---

### Post by Littleweseth on 2006-10-13
Out of curiosity : why not run photoshop (and dreamweaver, plus what ever else you want) in a virtual machine? It strikes me as a much more elegant and fuss-free solution.

---

### Post by computergee on 2006-10-13
No luck running it as windows 2000.

There are some things gimp just wont do, that photoshop does. I've been running photoshop in a virtual system for awhile now, but running it through wine would be more convienent to me. I may just redo ubuntu and try edgey soon, hopefully it will work on a clean install.

---

### Post by skyshock21 on 2006-10-15
> **Littleweseth said:**
> Out of curiosity : why not run photoshop (and dreamweaver, plus what ever else you want) in a virtual machine? It strikes me as a much more elegant and fuss-free solution.

Because unless you're on a system running Xen that allows for hardware virtualization (limited subset of CPU's), you're going to see a serious performance hit because of the virtualization layer's overhead.  With WINE you can run it at near close to native speeds.

---

### Post by closeyourwindows on 2006-10-15
I got photoshop CS running with wine .92
All the later versions would not work for me and I just dont upgrade wine.  but it works on my PIII laptop just fine.

---

### Post by kuja on 2006-10-15
closeyourwindows, if I remember right, CS will work and CS2 will not. 

As per virtualization, it works more or less flawlessly, though there is the added overhead. I tried it out for a while for the sake of experimentation, and found the performance of most things to be acceptable, with the exception of, of course, 3d hardware acceleration :(

Hardware virtualization seems to be only available on newer cpu's; though, I've read that on the Core2's it may actually be even slower than the software virtualization. The document arguing that was written by vmware, so I assume it has some truth in it.

---

### Post by Littleweseth on 2006-10-16
kuja : Can you specify 'newer CPUs'?

---

### Post by kuja on 2006-10-16
The AMD AM2's, the Intel CD and C2D processors.

---

