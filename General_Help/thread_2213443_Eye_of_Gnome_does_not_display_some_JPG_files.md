---
title: "Eye of Gnome does not display some JPG files"
date: 2014-03-26
forum: General Help
---

### Post by bach on 2014-03-26
I am running Ubuntu Gnome 13.10 and Eye of Gnome version 3.10.2. I am unable to view some JPG files using Eye of Gnome. For instance, the two files available at 

[https://dl.dropboxusercontent.com/u/2171814/dog.zip](https://dl.dropboxusercontent.com/u/2171814/dog.zip)

Here is a screenshot: [https://dl.dropboxusercontent.com/u/2171814/eog.png&#65279;](https://dl.dropboxusercontent.com/u/2171814/eog.png&#65279;)

I can view the files using other programs (for instance, okular, gwenview etc.). 

cribari@darwin3:~$ dpkg -l | grep eog
ii  eog                                    3.10.2-0ubuntu2~saucy1                  amd64        Eye of GNOME graphics viewer program
ii  eog-dbg                                3.10.2-0ubuntu2~saucy1                  amd64        Eye of GNOME graphics viewer program - debugging symbols
ii  eog-plugins                            3.10.1-1~saucy1                         amd64        set of plugins for eog

---

### Post by monkeybrain20122 on 2014-03-26
Works for me. EOG 3.8.2. Ubuntu 13.10 (Unity)
Your second link 404.

Edited: Booted into the Fedora 20 partition which runs gnome 3.10. The jpg files open in EOG 3.10.2 just fine (interesting that EOG is not even installed in F20, the default application to open image files is shotwell)

---

### Post by ajgreeny on 2014-03-26
They also open in EOG in 12.04 (EOG 3.4.2) and in EOG in 14.04 running as a VM in VirtualBox 4.3.10

---

### Post by bach on 2014-03-26
Clearly the problem is with my eog. I have already reinstalled it, but the problem remains. Is there a way for me to find out what is wrong? Interestingly, eog opens many imagens, but fails on a few (mostly full HD resolution photos). Suggestions are welcome.

---

### Post by coffeecat on 2014-03-26
I don't think this is the case for your example jpegs in the zip you posted a link to, but eog gets confused if an image file has the wrong extension - png for jpg or vice versa. Whereas better behaved image apps such as gthumb and gimp do the correct Unix thing and determine the file type from the metadata in the file header, not the filename extension.

---

### Post by bach on 2014-03-26
It seems that the problem is with xf86-video intel. See [https://bugs.freedesktop.org/show_bug.cgi?id=70527](https://bugs.freedesktop.org/show_bug.cgi?id=70527) .

---

