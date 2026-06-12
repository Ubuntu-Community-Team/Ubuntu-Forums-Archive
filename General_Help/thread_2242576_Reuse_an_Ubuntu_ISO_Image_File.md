---
title: "Reuse an Ubuntu ISO Image File?"
date: 2014-09-02
forum: General Help
---

### Post by sam64 on 2014-09-02
I'm starting school tomorrow, and I want to have a working Ubuntu VM on my school laptop, so that I can ask teachers for help. Do I need to download another Ubuntu ISO, or can I copy the Ubuntu ISO already on my home computer onto a flash drive and paste and reuse it in Virtual Box on my laptop?

---

### Post by JKyleOKC on 2014-09-02
You can use it as many times as you like. I keep ISO-file copies of all my software CDs from Windows days so that I can easily install them into VBox VMs.

---

### Post by sam64 on 2014-09-02
Uh-oh. I just realized that the version of the ISO on my home computer is for operating systems with an AMD processor (my laptop has an Intel processor). Not to sound lazy, but can you give me a quick link to Ubuntu ISO downloads?

---

### Post by Bucky Ball on 2014-09-02
Um, if you have a 64bit processor, the AMD release is what you are after. Disregard whether Intel or AMD processor. Not relevant. The AMD is for ALL 64bit processors. The i386 version is for all 32bit processors. You probably have the right one. Don't panic. ;)

(PS: Yes, that is lazy. ;) Just do a search for 'get ubuntu'.)

---

### Post by JKyleOKC on 2014-09-02
As BuckyBall said, the names are quite confusing. It goes back into history: AMD came out with a 64-bit processor design first, and the name got attached to the architecture since the only 64-bit systems originally used AMD chips. Intel finally got theirs working, and there are a few slight differences, but not where it matters. The current "AMD" versions are for all 64-bit machines, while those for 32 bits are labelled as "x86" architectures.

Now if your laptop is so old as to have a 32-bit-only chip then you **would** need a different ISO file, but if it's less than about 5 years old it's almost certainly capable of 64-bit operation. The more important question would be whether it has enough RAM to support using virtual machines, or enough graphics power to handle the Unity desktop of the most recent Ubuntu versions. If it falls short in either of these you might try Xubuntu or Lubuntu, both of which get by with much less in the way of resources...

---

### Post by ibjsb4 on 2014-09-02
I don't know if you understand vBox, but if you place the iso in your "Home folder" (Host), it can be loaded direct to the guest system.

[ATTACH=CONFIG]256079[/ATTACH]

A dual core processor and 3G of ram (1G for guest) is IMO the minimal requirements.  Others have done it with less, so mileage will vary.

And like already stated, X or Lubuntu is a better choice.  Ubuntu, if you can get it running, is resource demanding.

---

### Post by sam64 on 2014-09-02
Everything has been going fine so far, but after I finished naming my VM and permitted it to restart, I'm now stuck on this:
[ATTACH=CONFIG]256083[/ATTACH]

---

### Post by oldos2er on 2014-09-02
Please start a new thread for your subsequent problem in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.

---

### Post by ibjsb4 on 2014-09-02
And post a link here to your new thread so we can keep up with you :)

---

### Post by sam64 on 2014-09-02
> **JKyleOKC said:**
> The current "AMD" versions are for all 64-bit machines, while those for 32 bits are labelled as "x86" architectures.
Thanks for the history lesson ;) I've always wondered what "x86" meant.

> **oldos2er said:**
> Please start a new thread for your subsequent problem in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.
No need :mrgreen: I guess my VM decided to work after all. So how do I mark this thread SOLVED?

---

### Post by oldos2er on 2014-09-02
Under the Thread Tools drop-down menu at the top of the page.

---

