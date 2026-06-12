---
title: "What happened to easy .deb install?"
date: 2016-04-27
forum: General Help
---

### Post by izznogooood on 2016-04-27
Is it just me or is Softwaresenter broken?

I clearly remember downloading different debs and just click installing (In beta). This is not working for me anymore. I have to --force install "everything"... OK for me, but what about people trying Ubuntu?

*16.04*

---

### Post by howefield on 2016-04-27
Are you talking about 16.04 specifically ?

---

### Post by izznogooood on 2016-04-27
Yes, sorry about that.

---

### Post by QDR06VV9 on 2016-04-27
Maybe the difference for myself is that I use Gdebi as default installer for the .debs.
I have never been a real user of the package managers though.(outside of synaptic)

---

### Post by howefield on 2016-04-27
Thread moved to the General Help forum.

To save typing it all out, have a [read at this thread]("http://ubuntuforums.org/showthread.php?t=2321818"), there are also others.

---

### Post by izznogooood on 2016-04-27
For the record: I was looking for a discussion around the subject, not help. The reason why i chose ubuntu is (was) the easy "click" install, and availabilities of 3rd party software being so easy. This (if intended) is a step (huge) away from that.

Unless it´s a bug, then this discussion would be pointless :)

---

### Post by oldrocker99 on 2016-04-27
From Wikipedia: "Development was ended in 2015 and in Ubuntu 16.04 LTS it was replaced with GNOME Software instead."

Gdebi is the best graphical way to install a .deb file. There's also what I usually use, which is
```
sudo dpkg -i filename.deb
```

---

### Post by izznogooood on 2016-04-27
> **oldrocker99 said:**
> ```
sudo dpkg -i filename.deb
```

Then you would have to run "sudo apt -f install" afterwords.

I will definitely give [COLOR=#000000]Gdebi a try!

IMHO this should be included in a distro like Ubuntu.[/COLOR]

---

### Post by howefield on 2016-04-27
> **izznogooood said:**
> For the record: I was looking for a discussion around the subject, not help. The reason why i chose ubuntu is (was) the easy "click" install, and availabilities of 3rd party software being so easy. This (if intended) is a step (huge) away from that.

Unless it´s a bug, then this discussion would be pointless :)

The link to the relevant bug is in the thread I have linked a few posts above.

---

### Post by oldrocker99 on 2016-04-27
From Wikipedia: "Development was ended in 2015 and in Ubuntu 16.04 LTS it was replaced with GNOME Software instead."

So, to install GNOME Software:```
sudo apt-get install gnome-software
```
The icon showed up in my System folder called "Software." It looks like the Ubuntu Software Center is gone. You can't buy software in GNOME Software as far as I can tell, but you can't with AppGrid, either.

Gdebi is the best graphical way to install a .deb file. There's also what I usually use, which is
```
sudo dpkg -i filename.deb
```

---

### Post by izznogooood on 2016-04-27
](*,)

---

### Post by cubenerd on 2016-04-28
I'm pretty sure you can still install Ubuntu Software Center from Gnome Software Center.
Afterwards, you may select to use USC as your default application to install .deb's :)

---

### Post by Frogs Hair on 2016-04-28
I see the old software-center is still available in synaptic. The new version is named ubuntu-software.

ninja'd

---

### Post by izznogooood on 2016-04-29
apparently you can "sudo apt install ./package.deb", I had no Idea ;)

[http://www.howtogeek.com/252981/how-to-install-deb-packages-without-ubuntu-software-in-ubuntu-16.04/](http://www.howtogeek.com/252981/how-to-install-deb-packages-without-ubuntu-software-in-ubuntu-16.04/)

---

### Post by Frogs Hair on 2016-04-29
Ive always used gdebi for downloaded .debs which are usually web-browsers. I think it was mentioned a few posts back. :wink:

---

### Post by howefield on 2016-04-30
> **izznogooood said:**
> [http://www.howtogeek.com/252981/how-to-install-deb-packages-without-ubuntu-software-in-ubuntu-16.04/](http://www.howtogeek.com/252981/how-to-install-deb-packages-without-ubuntu-software-in-ubuntu-16.04/)

Nice one, thanks for the link.

---

