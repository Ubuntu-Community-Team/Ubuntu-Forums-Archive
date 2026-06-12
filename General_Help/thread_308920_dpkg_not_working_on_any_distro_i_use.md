---
title: "dpkg not working on any distro i use"
date: 2006-11-28
forum: General Help
---

### Post by HokeyFry on 2006-11-28
in the past few days i have installed several distros of ubuntu on my laptop. I started with breezy, upgraded to dapper, reinstalled to edgy, then reinstalled to breezy again. the reason i did all this was because dpkg does not work on any distro i use. for example, if i try to install vlc thru dpkg this is what happens:

```

alexander@d47-69-99-55:/media/REDFLASH/vlcpackages$ sudo dpkg -i vlc_0.8.4-svn2$
Password:
dpkg-deb: unexpected end of file in version number in vlc_0.8.4-svn20050920-3+h$
dpkg: error processing vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb

```

this happens with any deb package i try to install

thanks in advance for any help

---

### Post by ~LoKe on 2006-11-28
Hm...not sure, but try..

```
sudo apt-get clean
sudo apt-get -f install
```

---

### Post by bettlebrox on 2006-11-29
Do any of the other package management tools work? 
Does this happen with every .deb file or just with the vlc deb file?

---

### Post by CatKiller on 2006-11-29
Is there any reason you don't just use ```
sudo aptitude install vlc
``` or Synaptic?

You might find [this page]("http://monkeyblog.org/ubuntu/installing/") edifying.

---

### Post by HokeyFry on 2006-11-29
i dont use those because i am having trouble getting my usb internet working, so i dont have internet till i get a new lan cord.

also, this happens with all deb packages, not just vlc. i used that as an example.

---

### Post by bettlebrox on 2006-11-29
Maybe the files your trying to install are corrupted? How did you download them?

---

### Post by CatKiller on 2006-11-29
> **HokeyFry said:**
> i dont use those because i am having trouble getting my usb internet working, so i dont have internet till i get a new lan cord.

also, this happens with all deb packages, not just vlc. i used that as an example.

Fair enough. Is it possible you've got unmet dependencies problems? For example, [this page]("http://packages.ubuntu.com/edgy/graphics/vlc") lists the dependencies of the Edgy VLC package - you can download the Ubuntu packages from that site too. It's possible that those dependencies have unmet dependencies. Usually Synaptic would sort all of that out for you but if you use dpkg you need to work it out for yourself. If you've put all the deb files in the same directory, you can use ```
sudo dpkg -i *.deb
``` to install all of them. Also, I believe that if you put the files in /var/cache/apt/archives/ you can use Synaptic to install them without downloading them, and hopefully that will tell you which packages, if any, are missing.

---

### Post by HokeyFry on 2006-12-01
didnt mean to post my bad

---

### Post by HokeyFry on 2006-12-01
well, first, ive used this cd before, and i had no troubles. 

second, dpkg doesnt even begin to detect dependencies... im heading to my dads today ill try whatever Loke said to so with apt-get clean and -f install.

if that doesnt work ill try doing an online upgrade to dapper to see if that fixes anything. if not, ill download a new CD image and try doing one last fresh install, maybe even consider building dpkg from source if thats possible.

---

### Post by CatKiller on 2006-12-01
> **HokeyFry said:**
> 
second, dpkg doesnt even begin to detect dependencies... 

That's right. I think I said that too. I don't think it's supposed to. The front-ends (Synaptic, apt-get, aptitude, Adept) do though, so if you want to know which dependencies you've not taken account of, use one of those instead.

Unless I've misunderstood what you've said, which is always possible.

---

### Post by HokeyFry on 2006-12-01
my bad i worded that wrong. i meant it doesnt even get as far as saying what additional packages i need to install on the system, thats what i meant.


also, i believe this is an issue with dpkg itelf, not with the packages im installing. does anyone know where i can get the source for dpkg, and how would i install it (i still dont understand how to use 'make' very well

---

### Post by CatKiller on 2006-12-02
Is it always the same error message - "dpkg-deb: unexpected end of file in version number"? I can't really imagine what that would mean other than a bad download/burn. Some drives just don't like particular media burned with other particular drives, especially if it's -RW. There is something called **lintian** that is supposed to check .debs for common errors, but I've never gone anywhere near that deep to know what it is capable of or how to use it.

You could potentially get the source for the Breezy version of dpkg from [here]("http://packages.ubuntu.com/breezy/source/dpkg"), but I don't know how you'd install it and I really don't think that's your problem.

I also don't think that dpkg ever tries to say what additional packages you need to install. I'd imagine that it just fails with some kind of cryptic error message.

---

### Post by bettlebrox on 2006-12-03
It seems unlikely that dpkg is broken, it is more likey that the CD is faulty, or the CD drive on your Dad's system is faulty. Try accessing the CD then looking at the output from dmesg to see if the OS is spitting out any error messages about the drive.

---

### Post by HokeyFry on 2006-12-04
well i do remember some kind of wierd error i got when installing it, something about a 'cpufreq' failing (like 3 times during the installation). 

i dont know what that means thuogh.

---

### Post by bettlebrox on 2006-12-05
cpufreq is a module (driver) for Processors with throttling (or stepping) like the Pentium Mobile processors. What processor do you have? 

Can you get this system on the Net at all? You could try and see if you apt-get install some small file and that would tell us if the package management is fecked or not. ;)

---

### Post by HokeyFry on 2006-12-06
Pretty sure its a pentium III. Ill check when i get home.


yeah i can get it on the net but not till at least thursday. also, to check if the Edgy CD is corrupt i am installing it on another computer and will test dpkg, though i did not see the errors i got when installing it on the laptop. ill get back with the status later today.

---

### Post by riven0 on 2006-12-07
I had the same problem with dpkg. But I did something stupid - ran cleanlinks with sudo access. It ended up deleting some perl directories and some other stuff with dpkg. :rolleyes: :sigh:

Anyway, the only way I got it fix was to download the newest [dpkg package from Debian]("http://packages.debian.org/unstable/admin/dpkg") and run sudo dpkg -i dpkg_1.13.24_i386.deb 

That about fixed it. Still have some problems with perl, but I'm getting it ironed out. Once dpkg is acting right, it's easy to fix everything else.

---

### Post by HokeyFry on 2006-12-07
if dpkg isnt working right, how would i use it to reinstall itself?

also, it determined that it is not the cd, as i used the CD to install on another desktop, and used dpkg to install mp3 support. maybe my laptop just has some type of weird issue, i dunno. ill reinstall later today or tomorrow, if that doesnt work, ill attempt to compile it from source and see if that helps

---

### Post by riven0 on 2006-12-07
I really can't explain it, HokeyFry. dpkg was broken for me, too, and yet I got it installed. Maybe I was just lucky. :-D 
In either case, if you still have problems after the re-install, there is the source file listed on the bottom of that same page. Sometimes it's the last resort.

---

### Post by HokeyFry on 2006-12-12
argh! i figured out the problem and its not dpkg. umm it appears that some files in the ubuntu package search really are corrupted, as i just installed mp3 support using dpkg, while installing unrar gave me the wierd error. I dont know if this bug is known or not but where can i report this?

---

