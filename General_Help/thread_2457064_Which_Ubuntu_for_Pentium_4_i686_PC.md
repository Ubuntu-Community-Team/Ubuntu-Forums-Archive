---
title: "Which Ubuntu for Pentium 4 i686 PC?"
date: 2021-01-25
forum: General Help
---

### Post by dkc.com on 2021-01-25
Hi Guys,
I have a PC from the dinosaur age: Pentium 4 i686 32 bit and 1 GB RAM. It runs Windows XP smoothly but I haven't dared to connect it to the internet in a long time as the OS is not supported and quite vulnerable. But now I need to connect it to the internet for the educational activities of my child.

If possible, I want to install Ubuntu on it. Can anyone suggest to me the correct version of Ubuntu that can support this PC?

I tried older versions of Puppy Linux but couldn't boot because of some kind of I/O error and I have been using Ubuntu for a long time on my main Laptop, so Ubuntu is my choice.

All help is appreciated.

Thanks in advance.

---

### Post by ajgreeny on 2021-01-25
The last version of any of the Ubuntu family for than machine would be Lubuntu 18.04 which is the last one that had a 32 bit OS available; unfortunately it will lose support in April this year so is not a very good option for you.

32 bit systems are getting more difficult to deal with as 32 bit OSs disappear from use generally, but if you're prepared to give it a try, Debian 10 with the LXDE desktop, perhaps choosing openbox window-manager rather than LXDE at the login-screen, should run on that machine, though probably fairly slowly.

You can download the iso file for the net install [https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso](https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso) which then lets you choose which DE and packages you want to use during installation; it's not a live system but it is very easy to manage if you have used Linux in any situation before so no reason to fear it.

Debian is the basis of the Ubuntu OSs so much of what needs to be done to run the system is very like Ubuntu; it uses apt package management just the same and synaptic as the GUI package manager, which Ubuntu used to use by default as well, until the Ubuntu-Software application came along and replaced it by default in Ubuntu.

There may be other distros which could be used as well but I am now out of touch with 32 bit systems; [Distrowatch]("http://distrowatch.com/") may be worth visiting for other suggestions.

---

### Post by Impavidus on 2021-01-25
Lubuntu 18.04 is the last release in the Ubuntu family with support for 32 bit, but only has 3 months of support left. The parts it has in common with Ubuntu will be supported until 2023. There are options outside the Ubuntu family.

The I/O error you got on puppy may be caused by a hardware error. Not really surprising, given the age of that computer.

---

### Post by crip720 on 2021-01-25
Have laptop with similar specs and Lubuntu 18.04 will run on it.  It is the only laptop I have that will also boot up a Ubuntu 4.10.  With the low specs, taking it easy on it is almost needed to keep it working, only two or three tabs open in a browser and usually only one program open at a time.

---

### Post by ActionParsnip on 2021-01-25
I suggest Puppy Linux

---

### Post by CelticWarrior on 2021-01-25
> **dkc.com said:**
> Hi Guys,
I have a PC from the dinosaur age: Pentium 4 i686 32 bit and 1 GB RAM. It runs Windows XP smoothly but I haven't dared to connect it to the internet in a long time as the OS is not supported and quite vulnerable. But now I need to connect it to the internet for the educational activities of my child.


It can still be used with extreme limitations and a very narrow choices of OS and even less of desktop environments and realistic expectations. **For the educational activities of your child is NOT a realistic expectation**. Please read this recent thread where a similar situation has been discussed, paying special attention to post #4 by DuckHook that describes an hands-on experience with similar hardware a few years ago, knowing that "m[COLOR=#000000]odern OSes have just become even bigger and more resource intensive since[/COLOR]": [https://ubuntuforums.org/showthread.php?t=2457023](https://ubuntuforums.org/showthread.php?t=2457023)

---

### Post by GhX6GZMB on 2021-01-25
Lubuntu 18.04 should run well. 1 GB is marginal, but will work, unless you need to load huge documents. Forget Firefox if you need a browser, it's far too heavy. Opera will work well, but there are lots of other lightweight browsers out there.

---

### Post by CelticWarrior on 2021-01-25
> **ml9104 said:**
> Lubuntu 18.04 should run well.
Not really.
Please read the previous post and the linked thread. The point here is not installing a Linux distro and make it (barely) work, that's absolutely possible. The point here is the inadequacy for the intended purpose because the educational activities of the present include [COLOR=#000000]some video&#8209;chatting and groupware&#8209;like activities. It simply isn't realistic to think it'll work for that.[/COLOR]

---

### Post by dragonfly41 on 2021-01-25
I found [http://www.rollapp.com](http://www.rollapp.com) (remote desktop) in recent days and it seems a good option for some educational apps at reasonable price.  It is not without its issues (some app versions are dated) but you can experiment with free account one app at a time before signing up for Premium. I am trying one month of Premium. This approach takes the pressure away from your old laptop since you just need a browser.

[P.S.] Further thoughts ..
1. You will need some cloud storage option to pass files between your PC and your rollapp session. I have setup Dropbox and I believe that [this works on very old PC's]("https://help.dropbox.com/installs-integrations/desktop/system-requirements").

2. You can use local automation scripts to switch between app sessions, thus allowing multiple apps to be tried in free Starter mode. Premium mode at $7 per month does allow multiple sessions and data persistence. 

3. Another option is to try creating your own remote VM version. [I am trying this workflow.]("https://subscription.packtpub.com/book/big_data_and_business_intelligence/9781788474221/1/ch01lvl1sec15/installing-and-configuring-ubuntu-desktop-for-google-cloud-platform")

---

### Post by GhX6GZMB on 2021-01-25
> **CelticWarrior said:**
> Not really.
Please read the previous post and the linked thread. The point here is not installing a Linux distro and make it (barely) work, that's absolutely possible. The point here is the inadequacy for the intended purpose because the educational activities of the present include [COLOR=#000000]some video&#8209;chatting and groupware&#8209;like activities. It simply isn't realistic to think it'll work for that.[/COLOR]

How on earth would you know that video is involved here? There are other educational activities than "Corona offsite video teaching".

But the OP mentions nothing like this.

And my assertion that Lubuntu 18.04 will run well on limited HW stands. Been there, tried that.

---

### Post by aw1182 on 2021-01-25
You could try raspbian os (not ubuntu but debian based os I believe) which is made for raspberry pi.  Its very light and probably would run great on your computer.  Its 32 bit and I'm sure will be supported for quite some time to come.  They recently released a 64 bit version of it and its still in beta I believe.

---

### Post by CelticWarrior on 2021-01-25
> **ml9104 said:**
> How on earth would you know that video is involved here? There are other educational activities than "Corona offsite video teaching".

But the OP mentions nothing like this.

And my assertion that Lubuntu 18.04 will run well on limited HW stands. Been there, tried that.

I think you're thinking only about 1GB RAM in an Atom 32-bit from some years ago or the even older but much better DualCore or AMD eqivalent and not considering the 20+ years old single-core P4, but please share your experience, if you actually have it with this specific hardware or equivalent.
Who's been there and extensively tried that is DuckHook, someone who's experience and knowledge I trust a lot more than yours, to be honest. Quoting from [here]("https://ubuntuforums.org/showthread.php?t=2457023") (my bold):

> [COLOR=#000000]While true enough, the resulting product **must at least be functional**. My grandchildren had to home&#8209;school for a portion of the pandemic and if your clients' experience is similar to theirs, then **this involved some video&#8209;chatting and groupware&#8209;like activities**. CelticWarrior is right that **your old P4 will likely give up the ghost under that sort of load**.[/COLOR]

[COLOR=#000000]**My old P4 machine with 1GB would regularly crash or freeze with a modern GUI**, no matter what I tried in the 'buntu ecosystem. I eventually got barely passable performance out of it by installing the super lightweight distro: Bodhi. Even then, **a single running instance of Firefox maxed out the RAM**. Trying to launch **any further app resulted in disk thrashing from too much swapping**, and that old disk was painfully slow for swap. I kinda&#8209;sorta worked around that issue by using Midori which uses less resources than FF. And this was a few years ago (I no longer have that machine). **Modern OSes have just become even bigger and more resource intensive since**.[/COLOR]

[COLOR=#000000]If you are absolutely intent on rehabilitating this ancient box, then **at a minimum, you will need to beef it up to 2GB RAM**. Unfortunately, **generation 1 DDR is hard to get these days and proving to be expensive**.[/COLOR]

[COLOR=#000000]Even with enough RAM, **I'm not sure that the CPU is up to video&#8209;chatting and groupware**, but it's up to you whether you want to give it a try.[/COLOR]


And this sums it up brilliantly. And yes, of course what's implicit in the "educational activities" is exactly what DuckHook mentioned there, anyone with school age children knows that. I was personally involved in projects that provided resources for families in need. Re-purposing old desktops or laptops was in the table but such noble intentions rapidly collided with a pesky thing called reality. Much newer and better spec'ed machines than the OP's were tested and proved to be below the minimum for the tasks and/or extremely unreliable due to age, but mostly the former. In the end the solution was the cheapest 10" Android tablet imported in bulk from China and those had the additional benefit of consuming 20x less energy than any old desktop or even laptop, something that matter for poor families, a LOT.

---

### Post by guiverc on 2021-01-25
I used a 

```
hp dx6120mt (pentium 4, 3gb, winfast clone of nvidia 7600gt)
```

along with numerous pentium M laptops, atom eeepcs to test Lubuntu 18.04.5 LTS which was released in 2020-August, only a few months ago.

It runs well on that box, in fact that box also runs some other *flavors* well too, better than the pentium M laptops do anyway.  I use that box for support purposes as I don't need it for my own uses.

(I do use IBM thinkpads t43, t42p & r50p that are less powerful, less ram for specific tasks, but the form factors make more sense, and they act less like a heater during operation than the pentium 4)

The issues are with Lubuntu 18.04 LTS which I consider runs great, are as already noted by others

- Lubuntu 18.04 LTS reaches EOL on 2021-April, ie. a few months.  The base system still has two years of support, but it'll depend how you use it as to the risks involved.

- Lubuntu uses LXDE for 18.04, which uses GTK2.  I'd consider the apps you're going to use in deciding the flavor, as whilst Lubuntu/LXDE runs the best on old boxes like pentium 4/d/M, with limited RAM and specific application choices other *flavors *can run equal or actually better (Xubuntu would be my second choice; it hadn't completed it's port to GTK3 with 18.04, so was next fastest).

FYI:  That pentium 4 was also used to test 18.10, 19.04 & was bumped to 19.10 (so I could experience the full GTK3 Xubuntu/XFCE on it) though they're all EOL now.

The graphics card you have also enters the picture...

I have 2x pentium M laptops that don't like the 5.4 HWE kernel of 18.04, having no issues with 5.3 or anything earlier, so I'd opt for an ISO that installs & uses the GA kernel on those. Kubuntu is also pretty light (esp. with Qt apps), but that pentium 4's video card didn't like it so it'd not be my choice on that pentium 4 box; if using a different video card that wouldn't be an issue.

As for RAM - that p4 box had 1.5GB of ram until 19.04 reached EOL (I also had another p4 then).  Many of the pentium M laptops (as well as intel atom thingies) have 1GB which is still usable, but you have to be *particular* with how you use the machine (*so as not waste ram, ie. application choice, what is sharing the limited RAM at the same time etc*).

I still use boxes with 1GB & 1.5GB of RAM (*ibm pentium M laptops mentioned earlier*), but I use them differently when compared to my more powerful 2009 main desktop (which has 8GB).  FYI: The pentium 4 desktop outperforms the three pentium-M laptops I mentioned I still use, but I use the laptops b/c  their *form-factor is more convenient*.

---

