---
title: "[SOLVED] Two problems with Beryl"
date: 2007-06-21
forum: General Help
---

### Post by Skavenger on 2007-06-21
Hi, a few days ago I was using feisty with beryl without problems, but I had to format and I loss everething... anyway, I'm using ubuntu again, but when I reinstalled beryl, some features were gone :S. One is the wall plugin, is not in the desktop tab, and the other problem I have is with the magic lamp 1 efect, I cant set the waves to 0, after this was by default (I think), I remember magic lamp looked like  OS X, now is ugly =P

How can I fix this?

Thank you!

---

### Post by Ultra Magnus on 2007-06-21
wierd - you did a totally clean reinstall?
The wall plugin is available is a separate repository a think:

you can get it pretty easily by adding these too your /etc/apt/sources.list file

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I think its under unsupported plugins

code : sudo apt-get update

code: sudo apt-get install beryl-plugins-unsupported

I don't know why magic lamp looks different though....

---

### Post by AlexThomson_NZ on 2007-06-21
I'm not 100% sure, but I think they stopped providing the 0 option because they were violating Apple IP, anything more than one was apparently a different effect.

---

### Post by Ultra Magnus on 2007-06-22
> **AlexThomson_NZ said:**
> I'm not 100% sure, but I think they stopped providing the 0 option because they were violating Apple IP, anything more than one was apparently a different effect.

What, and apple are introducing multiple desktops - No Justice!

---

### Post by AlexThomson_NZ on 2007-06-22
Don't get me started! :(

---

### Post by Skavenger on 2007-06-22
> **Ultra Magnus said:**
> The wall plugin is available is a separate repository a think:

you can get it pretty easily by adding these too your /etc/apt/sources.list file

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I think its under unsupported plugins

code : sudo apt-get update

code: sudo apt-get install beryl-plugins-unsupported
thanks, that works!
I used [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29") to install beryl, what's the diference? because that guide does not installed me the wall plugin
> **AlexThomson_NZ said:**
> I'm not 100% sure, but I think they stopped providing the 0 option because they were violating Apple IP, anything more than one was apparently a different effect.
=(

---

### Post by AlexThomson_NZ on 2007-06-22
Hey take heart, this  is open source.  If you are comfortable with compiling beryl plugins, the change to extend the range down to 0 is beyond trivial and is just a one-byte modification :)

---

