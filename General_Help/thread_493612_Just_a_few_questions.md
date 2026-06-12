---
title: "Just a few questions"
date: 2007-07-05
forum: General Help
---

### Post by dogdude16 on 2007-07-05
I am new to Ubuntu and Wubi but i have just a few questions.

Can i use this on my slave harddrive?
Everytime i turn my computer on do i have to pick Windows or Ubuntu or how does it work?
How much does the install take up?

---

### Post by lixy on 2007-07-06
> **dogdude16 said:**
> I am new to Ubuntu and Wubi but i have just a few questions.

Can i use this on my slave harddrive?

Sure.

> Everytime i turn my computer on do i have to pick Windows or Ubuntu or how does it work?

Technically yes. You pick which OS you wanna boot from a list. A timer is installed by default to make life easier. You can of course later change the order of OSes and the timer duration.

> How much does the install take up?

15-30mns. Depends on your machine's specs.

---

### Post by kkei08 on 2007-07-06
> **lixy said:**
> 
15-30mns. Depends on your machine's specs.

I'm gonna guess he meant hard drive space, not time to install.

15gb no? I'm new here =D

---

### Post by dogdude16 on 2007-07-06
Thanks for the response.  I want to use Wubi to install ubuntu so can i use Wubi on a second hardrive? or does it have to be my primary because i read that you uninstall it by windows add/remove programs.

---

### Post by ago on 2007-07-06
Yes you can

---

### Post by joker_bxl on 2007-07-31
I found Wubi really interesting... but:

- Can I install Ubuntu (via Wubi) in external usb drive?
- Can it boot from external drive?
- If usb hd drive is off, what happen during boot?
- Can I move Ubuntu installation on the usb hd drive to another pc... ? How? (some experiences?) :grin:

In the faq of Wubi website we can found this:
[INDENT][I][FONT="Courier New"]
Can I use my free hard disk space and install Ubuntu there?
Not at the moment, but the feature is in the pipeline[/FONT][/I][/INDENT]

What they mean?

Voilà... thx a lot for your reply!

Bye \\:D/
Dario

---

### Post by ago on 2007-07-31
> **joker_bxl said:**
> I found Wubi really interesting... but:

- Can I install Ubuntu (via Wubi) in external usb drive?
Probably yes, but it's untested, have a go and let us know. In the worst case you can uninstall

> - Can it boot from external drive?
In theory yes

> - If usb hd drive is off, what happen during boot?
That you will be able to boot into windows but not into ubuntu (assuming you installed ubuntu in the usb drive)

> - Can I move Ubuntu installation on the usb hd drive to another pc... ? How? (some experiences?) :grin:
You need to copy the wubildr* files to that machine and add a line to boot.ini

> What they mean?
Installation to a dedicated partition by formatting unpartitioned free space.

---

### Post by joker_bxl on 2007-07-31
> **ago said:**
> Probably yes, but it's untested, have a go and let us know. In the worst case you can uninstall

I'll try this solution tonight and I'll post result as soon as possible.

Ago thanx for help! :wink:

Ciao
Dario

---

### Post by joker_bxl on 2007-07-31
Last question... No way to use Ubuntu live-cd instead of download files?

---

### Post by ago on 2007-07-31
> **joker_bxl said:**
> Last question... No way to use Ubuntu live-cd instead of download files?

Only alternate ISO at the moment. When the 7.10 version is out you should be able to use the live CD or ISO.

---

### Post by joker_bxl on 2007-08-02
I've tried it with without succes... :(
Installation end and when you reboot, boot menu work fine but when I try to launch Ubuntu an error 17 is showed. Grub don't find some files...

Now the question is, it's a problem of the bios who maybe don't see usb external drive during boot time?

ps: I've read about the possibility to use an iso (alternate) for installation (I must include it in Wubi folder, it's right?) instead download it. Can you confirm please? It'll be great because download 700Mb everytime I want test somethings with Wubi is scary. [-X

---

### Post by tuxcantfly on 2007-08-03
> ps: I've read about the possibility to use an iso (alternate) for installation (I must include it in Wubi folder, it's right?) instead download it. Can you confirm please?

Yes it's possible to do that

> Installation end and when you reboot, boot menu work fine but when I try to launch Ubuntu an error 17 is showed. Grub don't find some files...

Try upgrading the grldr packages, or use the latest minefield build which has the grldr packages. Also, you might want to see this: [https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c](https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c)
> 
Now the question is, it's a problem of the bios who maybe don't see usb external drive during boot time?

Try moving the grldr files over to the internal drive.

Also, you listed that you're an OpenSUSE user. If you already have an opensuse installation on that drive, simply use Lubi [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/) instead of Wubi to do the installation; it should work better.

---

