---
title: "Question about other options to download update package for Ubuntu system"
date: 2016-08-21
forum: General Help
---

### Post by patrikmellq on 2016-08-21
I ask if there is a way to downlod update package into downlod folder and then check (checksum) that the package are correct and then install them one by one.
Or is there any other options.

I ask because i been haveing a issue with Tripwire - when you update Ubuntu system - you get all kind of warning with Tripwire and i can not be sure that one warning among them has to do with that i been comprimized/hack.
So i was thinking i could download update package and check them Before install by hand - then i would know that Tripwire would only give me warnings about the updating Ubuntu system and i can clear and update Tripwire database again.

Cheers

---

### Post by howefield on 2016-08-21
Using the -d option with apt-get will download the package to /var/cache/apt/archives/ but not install it.

```
sudo apt-get install -d tripwire
```

You can then check it integrity against whatever checksum you want.

What version of Ubuntu are you using ?

---

### Post by patrikmellq on 2016-08-21
I have laptop with Ubuntu XFCE 14.04 LTS but i thinking to install Ubuntu 16.04 LTS on my gaming computer (Main Home Computer) but Before i decide to do so i want a solution how to handle updates with Tripwire.

1) How does the code look like if i want to update Ubuntu - for example (( sudo apt-get update -d )) ?
2) How do i check (( /var/cache/apt/archives/ )) to be correct with checksum or MD5 sum - is there any command for that ?
3) How do i install the package from (( /var/cache/apt/archives/ )) ? after checking that they are valid and no other comprimized software is among them ...

Many Thanks ...

---

### Post by howefield on 2016-08-21
> **patrikmellq said:**
> How does the code look like if i want to update Ubuntu - for example (( sudo apt-get update -d )) ?

Update as in upgrade to 16.04.1 ?

> How do i check (( /var/cache/apt/archives/ )) to be correct with checksum or MD5 sum - is there any command for that ?

The MD5SUM for the 64 bit version of tripwire is 
```
ebe292bfb1a04ab7a1c5f7112d171a35
```
the 32 bit MD5SUM is
```
4c23543f68e9992aabe21c44558074d6
```

Use the following command to get the MD5SUM from the package and compare the result against the above, depending on whether you have the 32 bit or 64 bit.

```
md5sum /var/cache/apt/archives//tripwire_2.4.2.2-3_amd64.deb
```

Check the file name above is correct for your machine, it will be slightly different if you have the 32 bit package.

> How do i install the package from (( /var/cache/apt/archives/ )) ? after checking that they are valid and no other comprimized software is among them ...

Just use...

```
sudo apt-get install tripwire
```

The system will recognise that you have already downloaded the package, so will simply install it.

---

### Post by patrikmellq on 2016-08-21
Thanks for the help :-)

---

### Post by howefield on 2016-08-21
You're welcome, please mark the thread as solved if you are done.

---

