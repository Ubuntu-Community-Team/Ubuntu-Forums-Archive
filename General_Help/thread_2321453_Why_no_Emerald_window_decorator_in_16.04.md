---
title: "Why no Emerald window decorator in 16.04?"
date: 2016-04-22
forum: General Help
---

### Post by Cavsfan on 2016-04-22
Just wondering why Emerald hasn't been released on Xenial Xerus 16.04?

Here's where it shows there's currently no package.

[https://launchpad.net/ubuntu/xenial/+source/emerald](https://launchpad.net/ubuntu/xenial/+source/emerald)

And I have Xubuntu installed but I doubt that matters. I found a work around with **/usr/bin/compiz-decorator**.

  [ATTACH=CONFIG]268529[/ATTACH]

But, it's still not Emerald.

---

### Post by Frogs Hair on 2016-04-22
Hasn't Emerald been primarily a PPA project for a while now ? I find a PPA active up to 14.04. Check Web UPD8 or Noobs Lab.

---

### Post by QDR06VV9 on 2016-04-22
> **Cavsfan said:**
> Just wondering why Emerald hasn't been released on Xenial Xerus 16.04?

Here's where it shows there's currently no package.

[https://launchpad.net/ubuntu/xenial/+source/emerald](https://launchpad.net/ubuntu/xenial/+source/emerald)

And I have Xubuntu installed but I doubt that matters. I found a work around with **/usr/bin/compiz-decorator**.

  [ATTACH=CONFIG]268529[/ATTACH]

But, it's still not Emerald.
Here is how i installed it Cavsfan: [https://blueprints.launchpad.net/~cybersec/+archive/ubuntu/panto-packages-xenial/+build/8860668](https://blueprints.launchpad.net/~cybersec/+archive/ubuntu/panto-packages-xenial/+build/8860668)
I installed all 3 .debs. 
Cheers

---

### Post by Cavsfan on 2016-04-22
> **Frogs Hair said:**
> Hasn't Emerald been primarily a PPA project for a while now ? I find a PPA active up to 14.04. Check Web UPD8 or Noobs Lab.

Yes, I believe you are correct. I've gotten if from the Noobs Lab ppa before. I see the Emerald package hasn't been hosted in Launchpad for quite some time.
I was not able to  readily find any way to get it and thought that it would be available somewhere.

> **runrickus said:**
> [QUOTE=Cavsfan;13474894]Just wondering why Emerald hasn't been released on Xenial Xerus 16.04?

Here's where it shows there's currently no package.

[https://launchpad.net/ubuntu/xenial/+source/emerald](https://launchpad.net/ubuntu/xenial/+source/emerald)

And I have Xubuntu installed but I doubt that matters. I found a work around with **/usr/bin/compiz-decorator**.

  [ATTACH=CONFIG]268529[/ATTACH]

But, it's still not Emerald.

Here is how i installed it Cavsfan: [https://blueprints.launchpad.net/~cybersec/+archive/ubuntu/panto-packages-xenial/+build/8860668](https://blueprints.launchpad.net/~cybersec/+archive/ubuntu/panto-packages-xenial/+build/8860668)
I installed all 3 .debs. 
Cheers[/QUOTE]

Thanks for that link! I'll do that! :)

---

### Post by Cavsfan on 2016-04-22
Got it done! I NEED emerald! :P

It was weird though. I tried installing the emerald .deb file with Software Center and it said it was installing but never asked for my password.
Maybe that was because there was an unmet dependency?

I then tried to install the libemeraldengine .deb file with Software Center and it did ask for my password and did install that file.
Again I tried to install the emerald .deb file with Software Center but it still wouldn't work.

So, I ended up going to the tmp directory where those 2 packages were stored and entered

```
sudo dpkg -i emerald-package
```

And that appeared to work so I entered **/usr/bin/emerald** in CCSM and logged out and it was good. 

[ATTACH=CONFIG]268534[/ATTACH]

Thanks again **runrickus**!

---

### Post by QDR06VV9 on 2016-04-22
Your Very Welcome.:D
I just made a emerald folder in my home directory and put all 3 of those .debs in there.
And went to the terminal:
```
cd emerald
sudo dpkg -i *.deb
```
Just for future visitor's
Best Regards

---

### Post by Cavsfan on 2016-04-22
> **runrickus said:**
> Your Very Welcome.:D
I just made a emerald folder in my home directory and put all 3 of those .debs in there.
And went to the terminal:
```
cd emerald
sudo dpkg -i *.deb
```
Just for future visitor's
Best Regards

Thanks I forgot about the asterisk. :D

Edit: Since I needed to just install 1 package I didn't need to use the asterisk this time.

---

