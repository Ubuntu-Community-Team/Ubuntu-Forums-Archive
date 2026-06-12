---
title: "Questions about Livepatch"
date: 2019-10-10
forum: General Help
---

### Post by my1 on 2019-10-10
I have seen recently that Ubuntu does Livepatch, so I have a few questions:

1) does that only apply to main ubuntu or are other flavors (lubuntu, kubuntu, both bionic) also supported
2) there is a limit on how many machines you can have in that, what happens if you dont want to have that machine use Livepatch anymore, or if it dies, can you disable the livepatch for that machine remotely, in case you cannot do it on the machine itself?

Thanks already.

---

### Post by Frogs Hair on 2019-10-10
Hello and Welcome

I have the  live patch option available in software and updates on Ubuntu Budgie, but it is not available for the  non LTS release I'm using. LTS Flavors are only supported for three years.  

[https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)

---

### Post by my1 on 2019-10-10
interesting thanks. I honestly prefer KDE (or LXDE on smaller machines) so I will probably stay with Lu- and Kubuntu respectively.

also thanks for the link I was there, it sadly doesnt say anything about other flavors not about how to deal with machines you no longer wanto to use or can no longer use, there are enough ugly licensing schemes I have seen to know that this has the potential to end very badly which is why I want to know as much as I can before seriously using it.

---

### Post by TheFu on 2019-10-10
[https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)
Looks like is is part of the paid *Ubuntu Advantage* support, though I remember something about it being offered through Landscape for a limited number of systems (3?).  Yep, scroll to the bottom of that page - 3 free.  $25/yr for desktops for Advantage support.

---

### Post by Frogs Hair on 2019-10-10
There is a contact link on the web page. There is a [thread]("https://ubuntuforums.org/showthread.php?t=2407112") here also.

---

### Post by my1 on 2019-10-10
> **TheFu said:**
> [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch)
Looks like is is part of the paid *Ubuntu Advantage* support, though I remember something about it being offered through Landscape for a limited number of systems (3?).  Yep, scroll to the bottom of that page - 3 free.  $25/yr for desktops for Advantage support.
I know that much. but is it 3 specific machines ever with no way of getting them out or can you remove unused machines to free up slots, or whatever, nothing is listed there.

> **Frogs Hair said:**
> There is a contact link on the web page. There is a [thread]("https://ubuntuforums.org/showthread.php?t=2407112") here also.
well that thread is solved AND almost a year old, but the contact is something I could try, I generally use the forums first trying not to waste the time of the makers of whatever too much with questions others already know the answer for.

---

### Post by Frogs Hair on 2019-10-10
I couldn't locate any information specific to flavors other than the live patch option was added to the flavors per the bug report on the old thread I linked.

---

### Post by deadflowr on 2019-10-11
> 1) does that only apply to main ubuntu or are other flavors (lubuntu, kubuntu, both bionic) also supported
It's the kernel that matters, not the desktop.
It's more suited for servers anyway.

Ubuntu Desktop just ships with the tools to enable it through the gui which is really the only thing it has over other flavors.
Enabling through snap command line is simple, but that requires grabbing your auth token from the livepatch portal.
The main Ubuntu Desktop gui method grabs the token automatically for you.

Disabling it removes the machine token, so should be able to move to another machine.
AFAIK that's how others have done it.

---

### Post by TheFu on 2019-10-11
> **my1 said:**
> I know that much. but is it 3 specific machines ever with no way of getting them out or can you remove unused machines to free up slots, or whatever, nothing is listed there.


well that thread is solved AND almost a year old, but the contact is something I could try, I generally use the forums first trying not to waste the time of the makers of whatever too much with questions others already know the answer for.

When you are paying for support, I'd be surprised if a phone number wasn't provided to call for questions.  When I pay for support, I use the phone first. My expectations are much higher.

---

