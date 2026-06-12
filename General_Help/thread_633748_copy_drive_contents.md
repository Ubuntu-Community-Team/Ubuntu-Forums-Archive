---
title: "copy drive contents"
date: 2007-12-06
forum: General Help
---

### Post by buccaneere on 2007-12-06
I tried this in another forum, and the thread quickly got jammed up with responses from people who didn't understand what I'm tryin' to do. 

So please, if you do not understand, DO NOT REPLY, or ask for a re-explanation. It clogs the thread, and I don't know enough about linux, but I can judge by the command name that it is the wrong thing to accomplish my task.

So here it is again...

[COLOR="Navy"]Two new, empty laptops; Acer 5100/vista, and HP dv 9000/vista. *All I need for this musical HDD's is music*:guitar:

I pulled the HDD from the Acer, and set it aside. I took the secondary HDD from the HP (it has 2 HDD's), put it into the Acer, and loaded ubuntu, and made a hundred or so personal settings and hardware configurations.

I want now to transfer **all** settings and ubuntu contents to the **original Acer HDD**.

So I took the HP secondary drive back out of the Acer, and put it in the PRIMARY bay of the HP, and put the original Acer into the SECONDARY bay of the HP.

So now I can mirror the ubuntu settings onto the Acer original HDD, and then put it back into the Acer. Right?

Wrong. The HP won't boot the ubuntu-loaded HDD. It's cryin' about graphical interface not startin'.


So will this work:

Leave both HDD's as they are, and boot from ubuntu liveCD. Then, execute disk copy, from the primary disk, to the secondary disk.[/COLOR]

---

### Post by HermanAB on 2007-12-06
See this: [http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

You are on the right track with booting off a CD.  That ensures that the disk drive will not be altered while the copying is in process.  That is very important, else you end up with a corrupted copy.

Cheers,

Herman

---

### Post by buccaneere on 2007-12-06
> **HermanAB said:**
> See this: [http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

You are on the right track with booting off a CD.  That ensures that the disk drive will not be altered while the copying is in process.  That is very important, else you end up with a corrupted copy.

Cheers,

Herman

Thanks there, Herman...

---

### Post by buccaneere on 2007-12-07
I DID IT!!!

Leave both HDD's as they are, and boot from ubuntu liveCD. Then, execute disk copy, from the primary disk, to the secondary disk.

I think tgalati4 got me the right code for the copy execute...

Log into rescue mode.

HTML Code:

# [HTML]cp /dev/sda /dev/sdb[/HTML]

Took about 50 minutes to execute, with no progress indicator... All of a sudden, a beep, I punched up fdisk -l, and VOILA! Replication.

Put it back into the Acer, and it's good to go!

---

