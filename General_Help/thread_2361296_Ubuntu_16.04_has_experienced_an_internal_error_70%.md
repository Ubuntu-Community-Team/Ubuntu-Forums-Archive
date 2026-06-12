---
title: "Ubuntu 16.04 has experienced an internal error 70% done from a good dvd install disc"
date: 2017-05-15
forum: General Help
---

### Post by FernandoRueda on 2017-05-15
as the photo indicates, this happens for no real reason. I'm installing this on:
-pentium 3 laptop 700/850mhz
-512MB ram
-8mb video
-10gb HD
-DVD-rw drive
-media dvd-rw burnt at 2x for the installation disc.

I read something about some architechture that needs to be added but even so that guy didn't have luck.
I suppose this is a common error what can be the solution?[ATTACH=CONFIG]275122[/ATTACH]

---

### Post by Bucky Ball on 2017-05-15
It would help if you hit the button that says 'Details' on that error screen and tell us what they are or post a pic. 

Incidentally, to post pics, hit 'Go Advanced' or 'Adv Reply' and use the paperclip icon there.

While system requirements might say that Ubuntu will theoretically run on that machine, you are probably not going to get a good experience with a P3 and 512 RAM. I would STRONGLY advice you to try a lighter flavour; Xubuntu (my choice) or Lubuntu if that doesn't work (lightest).

Even if you can get Ubuntu running, it will probably be boringly slow and not a lot of fun to use. Good luck.

PS: Just noticed your 10Gb hard drive! No. Go with Xubuntu or Lubuntu. I would forget Ubuntu 16.04 LTS on this machine personally.

I wouldn't know if your specs have got anything to do with why you're getting your error (could be running out of disk space while trying to install as some needs to be used that will be cleaned again later, but maybe you don't have enough for that), but thought I'd give some general observations before you waste too much time with this. Try one of the others and see if you get the same issue.

Also, when you are booting from the DVD, are you trying 'Try Ubuntu'? Please do and see what result you get running a 'live' session directly from the DVD. Works ok?

---

### Post by FernandoRueda on 2017-05-15
> **Bucky Ball said:**
> It would help if you hit the button that says 'Details' on that error screen and tell us what they are or post a pic. 

Incidentally, to post pics, hit 'Go Advanced' or 'Adv Reply' and use the paperclip icon there.

While system requirements might say that Ubuntu will theoretically run on that machine, you are probably not going to get a good experience with a P3 and 512 RAM. I would STRONGLY advice you to try a lighter flavour; Xubuntu (my choice) or Lubuntu if that doesn't work (lightest).

Even if you can get Ubuntu running, it will probably be boringly slow and not a lot of fun to use. Good luck.

PS: Just noticed your 10Gb hard drive! No. Go with Xubuntu or Lubuntu. I would forget Ubuntu 16.04 LTS on this machine personally.
It's **Xubuntu 16.04 with xfce** but says ubuntu on the error page, I used a previous version of xubuntu before last year and it was cool so I should be good. I will post details if need be. I just hit continue and the thing finished. and I can run live from the dvd disc up to the desktop screen.

---

### Post by Bucky Ball on 2017-05-15
> **FernandoRueda said:**
> ... I used a previous version of xubuntu before last year and it was cool ...

Don't take that as ANY indication this one will be 'cool'. Each new release is usually more resource hungry, takes up more space and generally has other differences which may not be obvious. What was the previous version? 10.04? Different beast and lighter.

Please state from the start which release and FLAVOUR you are trying to install to avoid confusion. Yes, it might say 'Ubuntu error'. Wouldn't make any diff which flavour you were installing. They all run the same Ubuntu kernel, but not all flavours are going to throw errors for the same reason.

And still waiting on the details of that error, as requested in my last post. :)

(PS: I never use anything but Xubuntu-core myself. You might give that a go if the resource appetite of 16.04 is your issue.)

---

### Post by FernandoRueda on 2017-05-15
> **Bucky Ball said:**
> Don't take that as ANY indication this one will be 'cool'. Each new release is usually more resource hungry, takes up more space and generally has other differences which may not be obvious. What was the previous version? 10.04? Different beast and lighter.

Please state from the start which release and FLAVOUR you are trying to install to avoid confusion. Yes, it might say 'Ubuntu error'. Wouldn't make any diff which flavour you were installing. They all run the same Ubuntu kernel, but not all flavours are going to throw errors for the same reason.

And still waiting on the details of that error, as requested in my last post. :)

(PS: I never use anything but Xubuntu-core myself. You might give that a go if the resource appetite of 16.04 is your issue.)
I mentioned it was xubuntu 16.04 with xfce. I'm gonna read about the xubuntu-core right now.

---

### Post by FernandoRueda on 2017-05-15
I have a pentium 3 850mhz 512mb and 8mb video. I just finished installing xubuntu xfce 16.04 and checked to download updates while installing so it should be ready to work, yet when I run firefox it crashes instantly. my network card is running very slow too but there is no firmware non-free stuff here and I don't know if that would be any help as the internet works slow but fine. I have no web browser that I know of on it atm. I tried Opera but same thing.

EDIT:
Post merged.

---

### Post by Bucky Ball on 2017-05-15
> **FernandoRueda said:**
> I mentioned it was xubuntu 16.04 with xfce. I'm gonna read about the xubuntu-core right now.

Before my first post? Actually, no, you didn't. ;)

> **FernandoRueda said:**
> as the photo indicates, this happens for no real reason. I'm installing this on:
-pentium 3 laptop 700/850mhz
-512MB ram
-8mb video
-10gb HD
-DVD-rw drive
-media dvd-rw burnt at 2x for the installation disc.

I read something about some architechture that needs to be added but even so that guy didn't have luck.
I suppose this is a common error what can be the solution?[ATTACH=CONFIG]275122[/ATTACH]

The title of your thread also says 'Ubuntu' and not 'Xubuntu'. Looking at the picture again, yes, looks like Xubuntu. :)

I used to use the minimal install and build it up to what Xubuntu-core is. Now I just start with Xubuntu core. Much lighter and only what you want/need. Perfect for that dinky machine of yours. [URL="https://xubuntu.org/news/introducing-xubuntu-core/"]

Here's the link[/URL] if you haven't already found it. Community ISOs at the bottom of the page, although you can install it using the Ubuntu minimal ISO. I'm running Xubuntu-core 16.04 LTS, but Unit193's page with the ISOs has the annoying habit of only offering the current, newest release and 'disappearing' the last. In that instance, Xubuntu-core 16.04 LTS can be installed with the mini.iso method.

Easiest way to do that is to install using the [16.04 LTS Ubuntu mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") (this only installs the Ubuntu kernel which all the flavours use), reboot after install, login. You will be in a giant terminal (CLI). Issue this:

```
xubuntu-core^
```

Let it roll. When that's cooked you should be rebooting to an xfce desktop, looking like Xubuntu, but with no apps. I generally open a terminal and install Firefox and a package manager to easily install apps I want (my defaults rather than Ubuntu/Xubuntu's).

```
sudo apt install firefox synaptic
```

Good to go. Anyway, I love X-core (obviously), hope it works for you. There is also a Lubuntu-core (and a Ubuntu-core I believe).

(PS: Did you 'check the disk for defects? Check the md5sum to make sure the burn was ok? Tried the disk on another machine that does have good specs to see if it runs a live session ok?)

---

### Post by mörgæs on 2017-05-15
The new Firefox demands SSE2 which a Pentium 3 does not have. More here:
[https://ubuntuforums.org/showthread.php?t=2359242](https://ubuntuforums.org/showthread.php?t=2359242)

Time to try other browsers. Links2 is a favourite of mine for news browsing, for example. It takes some time to get used to but I think it's worth the effort.

EDIT:
Post merged.

---

### Post by ajgreeny on 2017-05-15
Thread merged.

Please do not create threads about the same problem; it is confusing to all and dilutes the forum's ability to help you and others.

---

