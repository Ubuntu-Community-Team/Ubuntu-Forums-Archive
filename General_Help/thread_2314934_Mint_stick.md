---
title: "Mint stick"
date: 2016-02-24
forum: General Help
---

### Post by loug28 on 2016-02-24
hi guys! 

I'm trying to install the linux mint tool, minstick version 1.2.6 onto my Xubuntu 15.10 machine. when i use gdebi I get told that a dependency is unsatisfiable. and that dependency is udisks. so i

```
sudo apt-get install udisks
```


and I get
```

Package udisks is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'udisks' has no installation candidate

```

And I don't now what to do. I prefer the mint tools over anything else. heck, i want to move back to linux mint! 

Anyone that can help will have my internal love and thanks

---

### Post by deadflowr on 2016-02-25
udisks on Ubuntu only goes up to 15.04.
15.10 and newer now uses udisks2

[udisks]("http://packages.ubuntu.com/search?keywords=udisks")

[udisks2]("http://packages.ubuntu.com/search?keywords=udisks2")

I'm not sure udisks can be installed on 15.10.
As I have not check to see if dependencies can be satisfied, or if the needed dependencies will break anything.

**Mint's current release 17.X is based on Ubuntu 14.04,
so it would make sense that mint stick is built from that.
To run on something similar to that.

As if any of that helps or make sense...

---

### Post by loug28 on 2016-02-25
> **deadflowr said:**
> udisks on Ubuntu only goes up to 15.04.
15.10 and newer now uses udisks2

[udisks]("http://packages.ubuntu.com/search?keywords=udisks")

[udisks2]("http://packages.ubuntu.com/search?keywords=udisks2")

I'm not sure udisks can be installed on 15.10.
As I have not check to see if dependencies can be satisfied, or if the needed dependencies will break anything.

I can tell you it can not, hence my original post. thank you though. 

> **Mint's current release 17.X is based on Ubuntu 14.04,
so it would make sense that mint stick is built from that.
To run on something similar to that.

I at no point questioned the why. I asked for help on the how. as in how to get it wrong or what I can do. UNetbootin doesn't want to work and neither does live-usb-creator

> As if any of that helps or make sense...

it makes sense. it doesn't help but I can thank you anyway.

**Edit: also as I see you're a mod, I apologize if my wording came across as rude. Not my intention. I was intending to be to the point.**

---

### Post by sudodus on 2016-02-25
You can try ***mkusb*** according to the following link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Install it from the PPA into Xubuntu with the following commands,

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

Edit: If you have problems, maybe the iso file is bad. Please check it with md5sum: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by loug28 on 2016-02-25
> **sudodus said:**
> You can try ***mkusb*** according to the following link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Install it from the PPA into Xubuntu with the following commands,

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

I thank you

>  Edit: If you have problems, maybe the iso file is bad. Please check it with md5sum: [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

I've considered that too and I always redownload it after deleting the old, and restarting the machine. But I thank you for that site. I hope i don't mess anything up. ;)

---

### Post by loug28 on 2016-02-25
> **sudodus said:**
> You can try ***mkusb*** according to the following link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Install it from the PPA into Xubuntu with the following commands,

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

Edit: If you have problems, maybe the iso file is bad. Please check it with md5sum: [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

I thank you! this helped!

---

### Post by sudodus on 2016-02-25
You are welcome :-)

---

