---
title: "How can I keep often used programs in RAM?"
date: 2007-02-18
forum: General Help
---

### Post by chris_ds on 2007-02-18
Hi there,

I use the following programs daily:
- firefox/swiftfox
- Konueror
- Azureus
- Konsole 
- Kmail

Is there any chance to keep them in RAM when possible? I know puppy linux and co. are starting those or similar programs from RAM, but when I start them in Kubuntu they always load from hard disc (with some delay, even if I just closed them).

I installed prelink and preload from some howto's but they don't seem to work here.

Is there a prgram that will let me select the programs I want to keep in RAM?

---

### Post by kerry_s on 2007-02-18
How much ram?
Have you tried changing swappiness to 0? (/etc/sysctl.conf, add vm.swappiness=0 to the end) that will keep it in ram longer instead of moving things to swap.
Konqueror has a built in feature to always keep a instance loaded, look under performance in settings.

- Azureus  <-don't know
- Konsole  <-Try using tilda instead, then you just press a key and the terminal drops down and rolls up.
- Kmail  <-don't know

firefox put 2 entries in /etc/rc.local->

sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

Replace "user"- 3x with you name.

---

### Post by chris_ds on 2007-02-19
Thanks for reply =)

OK I only have 512MB ram, but that should be enough for those little programs.

Tilda? Never heard of that. Will check it out (but i really like my konsole).
I will look for the swappiness setting but according to ksysguard there are only 20MB used from 1024mb.

Before I test the firefox thing... What will it do? 

:popcorn:  in advance for your effort.

---

### Post by kerry_s on 2007-02-19
> **chris_ds said:**
> Thanks for reply =)

OK I only have 512MB ram, but that should be enough for those little programs.

Tilda? Never heard of that. Will check it out (but i really like my konsole).
I will look for the swappiness setting but according to ksysguard there are only 20MB used from 1024mb.

Before I test the firefox thing... What will it do? 

:popcorn:  in advance for your effort.

Tilda's a good terminal that just drops down at the press of a key and rolls up when you press the key again. You just put it in start up and it is always ready, so it's faster than any terminal. It can do tabs and is customizable.

You don't want it using swap till necessary, swap is slower it has to read that from your hard disk.

It loads firefox into cache for faster start.

---

### Post by allwin on 2007-02-19
Friendly warning.  If you set SWAPPINESS to 0, a little fellow called OOM_KILLER will come along and randomly kill processes (like Firefox).  At least that was my experience.  If a task requires more memory than is free at a particular instant, it shoots it out of the sky and does not always swap things out first to see if some room could be freed.  Not to spread FUD or anything.  However if you look around Google you will see I have lots of company.  I don't know if setting it to a low, but nonzero, value fixes things.  Default is something like 60.  It's another of many parms that doesn't do quite exactly what you want IMHO.[-X

---

### Post by kerry_s on 2007-02-19
Yeah but that is very rare and hardware dependent. Swappiness=0 is one of the most common linux tweaks out there. Thank you telling us though, i'm adding that to my list of things to check when things go wrong. :)

---

### Post by chris_ds on 2007-02-20
Thanks for the good advices. Hope they will help here =)

But is there a tool to load single programs into ram whenever possible? 
What about a ramdisk with a script that copies firefox etc. into it on every reboot? 

Maybe I should switch from azureus to ktorrent (Java is using "VM-Size:431216" and "VMRSS:132260". One of that is my physical RAM, yes?) But I think Ktorrent is a bit slow...

---

### Post by nsleiman on 2007-02-20
> **kerry_s said:**
> Tilda's a good terminal that just drops down at the press of a key and rolls up when you press the key again. You just put it in start up and it is always ready, so it's faster than any terminal. It can do tabs and is customizable.

You don't want it using swap till necessary, swap is slower it has to read that from your hard disk.

It loads firefox into cache for faster start.

by the way what Theme/Window Manager are you using? i really like it!

---

### Post by chris_ds on 2007-02-20
OK I tried the rc.local thing but I am using Swiftfox...

I found "/usr/lib/swiftfox" but there's no ".swiftfox" in my home directory just the "/home/user/.mozilla/firefox"

my rc.local now looks like this:

sudo -u user find /usr/lib/swiftfox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

---

### Post by kerry_s on 2007-02-20
> **nsleiman said:**
> by the way what Theme/Window Manager are you using? i really like it!

I use Xubuntu

The window theme is-> [http://xfce-look.org/content/show.php?content=43023](http://xfce-look.org/content/show.php?content=43023)

The gtk theme is-> [http://www.xfce-look.org/content/show.php?content=46153&PHPSESSID=e5759fd2bd45276e8dced1f6cf244139](http://www.xfce-look.org/content/show.php?content=46153&PHPSESSID=e5759fd2bd45276e8dced1f6cf244139)

---

### Post by kerry_s on 2007-02-20
> **chris_ds said:**
> OK I tried the rc.local thing but I am using Swiftfox...

I found "/usr/lib/swiftfox" but there's no ".swiftfox" in my home directory just the "/home/user/.mozilla/firefox"

my rc.local now looks like this:

sudo -u user find /usr/lib/swiftfox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &


You got to replace "user" with the name you login as, the app has to run as you so you can use them,example->

sudo -u chris find /usr/lib/swiftfox ! -type d | xargs cat > /dev/null &
sudo -u chris find /home/chris/.mozilla/firefox ! -type d | xargs cat > /dev/null  &

Swfiftfox uses the exact same folder as your firefox for settings so /home/chris/.mozilla/firefox is right.

I use swiftfox to, i just install mine differently. I download from the site and and unpack it, then i rename the swiftfox folder to firefox and replace the one in /usr/lib with the swiftfox one and copy the plugins over from the mozilla folder. I just don't like having 2 versions of firefox installed at 1 time. :)

---

### Post by chris_ds on 2007-02-22
Yes I replaced "user" with my user name. I was just scared to post it here ;-)

OK i did it like you posted it. But it still starts in 8-10 seconds. 

Maybe someone can write a tool that can load selected programs into ram :KS 
Would be pretty cool, a selective preload for Open Office, Siwftfox and everything you like!

---

### Post by ormen on 2007-02-26
> **kerry_s said:**
> How much ram?
Have you tried changing swappiness to 0? (/etc/sysctl.conf, add vm.swappiness=0 to the end) that will keep it in ram longer instead of moving things to swap.
Konqueror has a built in feature to always keep a instance loaded, look under performance in settings.

- Azureus  <-don't know
- Konsole  <-Try using tilda instead, then you just press a key and the terminal drops down and rolls up.
- Kmail  <-don't know

firefox put 2 entries in /etc/rc.local->

sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

Replace "user"- 3x with you name.

In the rc.locale file, there's a line with this content:

```
exit 0
```

Is this to be erased, put at the end, or before your addings?

/Ormen

---

