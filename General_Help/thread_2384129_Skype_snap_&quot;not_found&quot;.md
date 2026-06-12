---
title: "Skype snap &quot;not found&quot;"
date: 2018-02-02
forum: General Help
---

### Post by barjunk on 2018-02-02
I was excited to learn yesterday that Skype had a snap!

However, when I use the command:

snap install --classic skype


It comes back with "Skype not found".

Is this because I have to do something else?

I was able to install minetest and it worked as expected.

Is it possibly because I'm using a 32 bit machine?

Thanks for any guidance.

Mike B.

---

### Post by Frogs Hair on 2018-02-02
Try the following.  ```
sudo snap install skype --classic
```

---

### Post by deadflowr on 2018-02-02
> Is it possibly because I'm using a 32 bit machine?
Yes.
As far as I know skype has only been 64-bit on linux for some time.
I don't think snap package changes that.
[https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skype-32-bit-linux/f0a01b8e-3b71-44be-a8a9-b7d89ebeb0c1?auth=1]("https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skype-32-bit-linux/f0a01b8e-3b71-44be-a8a9-b7d89ebeb0c1?auth=1")

---

### Post by barjunk on 2018-02-03
This did not help.   When I do a 'snap list' , with or without sudo, I only see: node-red, mumble, supertuxkart, get-iplayer, inkscape, minetest, offlineimap.

Are there such things as "repositories"?

If so, how would I use an alternate one if such a thing exists?

---

### Post by barjunk on 2018-02-03
> **deadflowr said:**
> Yes.
As far as I know skype has only been 64-bit on linux for some time.
I don't think snap package changes that.
[https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skype-32-bit-linux/f0a01b8e-3b71-44be-a8a9-b7d89ebeb0c1?auth=1](https://answers.microsoft.com/en-us/skype/forum/skype_linux-skype_startms-skype_installms/skype-32-bit-linux/f0a01b8e-3b71-44be-a8a9-b7d89ebeb0c1?auth=1)

Maybe the snap developers might respond with something to that effect.

On the other hand, there probably aren't that many folks using older 32bit hardware.

Thanks for the link.

---

### Post by deadflowr on 2018-02-03
> Maybe the snap developers might respond with something to that effect.
The snap developer is skype and microsoft, fwiw

> Are there such things as "repositories"?


I guess in theory there can be other snap repos, but currently I only know of Ubuntu snap store, which you are connected to already.

As far as I know snaps follow the same architecture designs of regular packages.
Where you would be able to run a 32-bit snap, with ease, on a 64-bit system, but not in reverse.
Likewise where you can install 32-bit applications on a 64-bit version of Ubuntu, but you cannot run 64-bit applications on a 32-bit version of Ubuntu.

---

### Post by cruzer001 on 2018-02-03
> Are there such things as "repositories"?

You can install Synaptic Package Manager to access the repostories.

```
sudo apt install synaptic
```

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://www.lifewire.com/guide-to-synaptic-package-manager-2205707](https://www.lifewire.com/guide-to-synaptic-package-manager-2205707)

But there sill will not be a 32bit skype.

---

### Post by deadflowr on 2018-02-03
Something far far far outside the box would be try the Windows version for 32-bit
(they still build a 32-bit Windows version for Windows 7, but this requires an updated Windows Internet Explorer browser version 11, from what I read)
and see if you can get it to work in [WINE]("https://help.ubuntu.com/community/Wine").

That's way out in left field, and an unknown if it'll even work.
But probably the best shot at getting anything skype functional on linux 32-bit.

---

