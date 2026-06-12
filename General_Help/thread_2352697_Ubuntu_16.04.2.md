---
title: "Ubuntu 16.04.2"
date: 2017-02-14
forum: General Help
---

### Post by Hewjr100 on 2017-02-14
Just asking, what happened to ubuntu 16.04.2 iso.  They said Friday or Monday, heard nothing since then.  Anybody have an update?

Henry

---

### Post by howefield on 2017-02-14
Looking like Thursday the 16th according to #ubuntu-release.

---

### Post by Hewjr100 on 2017-02-14
Oh boy, well Thursday it is. Thanks.

---

### Post by Hewjr100 on 2017-02-16
Well it's 9:15 pm NY time and 2:15 am Friday in London I think, can't remember who is ahead of who.  Yet I see no ubuntu 16.04.2, not even a peep as to what happened this time.  I wish Canonical would be more forthcoming with updates.  Guess I'll hit the hay and say "Hey".

Henry

---

### Post by bearlake on 2017-02-16
> **Hewjr100 said:**
> Well it's 9:15 pm NY time and 2:15 am Friday in London I think, can't remember who is ahead of who.  Yet I see no ubuntu 16.04.2, not even a peep as to what happened this time.  I wish Canonical would be more forthcoming with updates.  Guess I'll hit the hay and say "Hey".

Henry

Hmmm

Look [here]("https://lists.ubuntu.com/archives/ubuntu-release/2017-February/004036.html").

---

### Post by Kris_M on 2017-02-17
I'm on 16.04.1 . What would make me want to upgrade to 16.04.2?  Or perhaps more to the point will I need to be on 16.04.2 to upgrade to 18.04.x LTS when it comes along?

---

### Post by deadflowr on 2017-02-17
> **Kris_M said:**
> I'm on 16.04.1 . What would make me want to upgrade to 16.04.2?  Or perhaps more to the point will I need to be on 16.04.2 to upgrade to 18.04.x LTS when it comes along?

If you keep the system up-to-date, you'll get 16.04.2 whether you want it or not.
The difference being, your 16.04.2 will be basically the same as before, but updated.
(You will not get the newer hardware stack that comes with the iso install of 16.04.2.)

And you'll be at least 16.04.4 when you have the option to upgrade the release to 18.04, anyways.

My understanding though, is that users who do install the 16.042 iso will be getting the newer hardwares from each point release automatically.
(so a user who install the iso will get the stack for 17.04 when it's point release comes out this summer  (or winter, for those in the other hemisphere; and vice versa) (for 16.04.3)
and then they'll get the next one after and so on.

The initial release 1604/16.04.1 do not get newer hardware stacks as that release in seen as a good point for systems that need to be up and running with as little downtime as possible for as long as possible.
Each updated stack may or may not contain trouble, so having a single stack that you can run and depend on for the entire support period is crucial.

---

### Post by howefield on 2017-02-17
> **Hewjr100 said:**
> Well it's 9:15 pm NY time and 2:15 am Friday in London I think, can't remember who is ahead of who.  Yet I see no ubuntu 16.04.2, not even a peep as to what happened this time.  I wish Canonical would be more forthcoming with updates.  Guess I'll hit the hay and say "Hey".

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) or [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by Kris_M on 2017-02-17
> **deadflowr said:**
> If you keep the system up-to-date, you'll get 16.04.2 whether you want it or not.
The difference being, your 16.04.2 will be basically the same as before, but updated.
(You will not get the newer hardware stack that comes with the iso install of 16.04.2.)

And you'll be at least 16.04.4 when you have the option to upgrade the release to 18.04, anyways.

My understanding though, is that users who do install the 16.042 iso will be getting the newer hardwares from each point release automatically.
(so a user who install the iso will get the stack for 17.04 when it's point release comes out this summer  (or winter, for those in the other hemisphere; and vice versa) (for 16.04.3)
and then they'll get the next one after and so on.

The initial release 1604/16.04.1 do not get newer hardware stacks as that release in seen as a good point for systems that need to be up and running with as little downtime as possible for as long as possible.
Each updated stack may or may not contain trouble, so having a single stack that you can run and depend on for the entire support period is crucial.

Thanks!!!

---

### Post by Keith_Helms on 2017-02-17
If you want your 16.04/16.04.1 system to look exactly like you installed 16.04.2 from an ISO image, with a newer kernel and graphics, you can run the following command
```

sudo apt-get install --install-recommends xserver-xorg-hwe-16.04

```

---

### Post by Kris_M on 2017-02-17
> **Keith_Helms said:**
> If you want your 16.04/16.04.1 system to look exactly like you installed 16.04.2 from an ISO image, with a newer kernel and graphics, you can run the following command
```

sudo apt-get install --install-recommends xserver-xorg-hwe-16.04

```


Thanks!  Easiest update I've ever done!  Now if it could only be that easy when 18.04 comes along... :)
```
kris@kris-Z97X-UD3H:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
kris@kris-Z97X-UD3H:~$
```

---

