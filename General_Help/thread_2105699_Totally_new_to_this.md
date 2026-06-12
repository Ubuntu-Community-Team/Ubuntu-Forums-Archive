---
title: "Totally new to this"
date: 2013-01-16
forum: General Help
---

### Post by guyver13 on 2013-01-16
Hello people ):P

Im using a Panasonic toughbook, originally shipped with XP, but has Windows 7 installed

Ive been toying with the idea of trying Ubuntu, BUT

why is so stupidly difficult to install it??? :mad:

All i want to do is try it on a live CD environment

Ive searched so many websites and found nothing but barriers designed to make me want to stick with windows

Ive downloaded Ubuntu 12.10, Ive installed it onto a USB stick, BUT, my laptop doesnt have a USB boot up in the bios. Ive looked at burning a CD, but some sites say CDs wont hold the programme and a DVD must be used, I dont have a DVD writer. If i CAN indeed use a CD, how do i do it, the only thing i can find online is " Put Ubuntu onto disc, boot from disc and your away"

What exactly do i put onto CD?
Do i need to unzip the files first, or put the iso straight onto disc?
The more basic the better ;)

Please help 
please
pretty please
etc etc etc :lolflag:

---

### Post by hydn79 on 2013-01-16
You can try [http://lubuntu.net/](http://lubuntu.net/) it's small enough for CD. The core of Lubuntu is based on Linux and Ubuntu .

---

### Post by ibjsb4 on 2013-01-16
Download Ubuntu 12.04, it fits on a CD and has the option to try it out.  12.04 is LTS, meaning it has long term support (5 years).

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Just be aware it will run slower because its not on your HDD.

---

### Post by ibjsb4 on 2013-01-16
> **hydn79 said:**
> You can try [http://lubuntu.net/](http://lubuntu.net/) it's small enough for CD. The core of Lubuntu is based on Linux and Ubuntu .

hydn79 has a good point, Ubuntu may be too heavy for your machine.  
What are you machine specs (cpu, ram, video)?

---

### Post by chadk5utc on 2013-01-16
> **guyver13 said:**
> Hello people ):P

Im using a Panasonic toughbook, originally shipped with XP, but has Windows 7 installed

Ive been toying with the idea of trying Ubuntu, BUT

why is so stupidly difficult to install it??? :mad:

All i want to do is try it on a live CD environment

Ive searched so many websites and found nothing but barriers designed to make me want to stick with windows

Ive downloaded Ubuntu 12.10, Ive installed it onto a USB stick, BUT, my laptop doesnt have a USB boot up in the bios. Ive looked at burning a CD, but some sites say CDs wont hold the programme and a DVD must be used, I dont have a DVD writer. If i CAN indeed use a CD, how do i do it, the only thing i can find online is " Put Ubuntu onto disc, boot from disc and your away"

What exactly do i put onto CD?
Do i need to unzip the files first, or put the iso straight onto disc?
The more basic the better ;)

Please help 
please
pretty please
etc etc etc :lolflag:

If you have a cd burner yes use the burn image to disc option and just select the appropriate iso and burn it. If not you should be able to install it to usb and boot check your bios boot order to see if it sees the usb drive?? The only reason a CD wont hold the info is if the file size exceeds that of the average CD which is about 700MB

---

### Post by guyver13 on 2013-01-16
> **ibjsb4 said:**
> hydn79 has a good point, Ubuntu may be too heavy for your machine.  
What are you machine specs (cpu, ram, video)?


Pentium M processor 1500mhz 1.5ghz
1280mb ram
32 bit OS

new to Windows 7 so cant find any other info, (second hand laptop)

---

### Post by Mark Phelps on 2013-01-16
> **chadk5utc said:**
> If you have a cd burner yes use the burn image to disc option and just select the appropriate iso and burn it. 
Ubuntu 12.10 is TOO BIG to fit on a CD -- which is why a DVD burner is needed -- which the OP already said they did not have.

> If not you should be able to install it to usb and boot check your bios boot order to see if it sees the usb drive?? 
The OP already said in their original message that they can NOT boot from USB.

> The only reason a CD wont hold the info is if the file size exceeds that of the average CD which is about 700MB OK ... but Canonical mentioned long before releasing 12.10 that they would NOT be sizing the releases to fit on CDs anymore.

---

### Post by ibjsb4 on 2013-01-16
> **guyver13 said:**
> Pentium M processor 1500mhz 1.5ghz
1280mb ram
32 bit OS

new to Windows 7 so cant find any other info, (second hand laptop)

Ubuntu should be ok on those specs.  

Between Ubuntu and Lubuntu is Xubuntu.  Not as many bells and whistles as Ubuntu, but more than Lubuntu.  A nice middle ground and I have installed Xubuntu on machines with lower specs than yours with excellent results.

I think your cpu supports The 32 bit pae kernel, so you should be good to go.

---

### Post by guyver13 on 2013-01-16
> **ibjsb4 said:**
> Ubuntu should be ok on those specs.  

Between Ubuntu and Lubuntu is Xubuntu.  Not as many bells and whistles as Ubuntu, but more than Lubuntu.  A nice middle ground and I have installed Xubuntu on machines with lower specs than yours with excellent results.

I think your cpu supports The 32 bit pae kernel, so you should be good to go.

Ok cool, how do I get it up and running then?
The sites I've looked at all seem to assume that I already have a CD with it on, they mention nothing about what exactly I should have installed on the CD. Do I need to unzip or not. Burning the CD should be easy.

---

### Post by MG&amp;TL on 2013-01-16
> **guyver13 said:**
> Ok cool, how do I get it up and running then?
The sites I've looked at all seem to assume that I already have a CD with it on, they mention nothing about what exactly I should have installed on the CD. Do I need to unzip or not. Burning the CD should be easy.

Nope, don't unzip, the file is a disk image. [http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

---

### Post by ibjsb4 on 2013-01-16
Any other questions, or are you good to go?

---

### Post by guyver13 on 2013-01-17
> **MG&TL said:**
> Nope, don't unzip, the file is a disk image. [http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)


Nice one, this is the type of info i was after, nice and simple to understand

BUT

I still cant get it to work ARGHHHHHHH :mad::mad::mad:

for some reason my cd writer is only running at 48x and keeps throwing out errors

so im left with 2 choices

Is it possible to just install unbutu off the internet as a full install?
if not ill need to reinstall XP and get the cd writer working as it should

---

### Post by MG&amp;TL on 2013-01-18
Have you got a USB? You can use those, usually far more reliably, instead of a CD. 

There is [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi) , but there are limitations to that method. Performance won't be as good, and you are limited to 30GB, for instance.

---

