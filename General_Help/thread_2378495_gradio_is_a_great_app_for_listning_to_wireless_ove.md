---
title: "gradio is a great app for listning to wireless over the Internet"
date: 2017-11-23
forum: General Help
---

### Post by Neill_R on 2017-11-23
Well sort of solved

sudo add-apt-repository ppa:ubuntu-desktop/gnome-3-26
sudo add-apt update

snap install gnome-3-26-1604
snap connect gradio:gnome-3-26-1604 gnome-3-26-1604
sudo snap connect gradio:gnome-3-26-1604 gnome-3-26-1604
gradio

or

snap run gradio &

not sure of the diffence in starting the application


gradio is a great application for listening to wireless over the Internet. However the developer has drop the repository and hence there is no more .DEB to down load
he say he only deals with flatpak and snap now. i can't get either of those to work
[URL="https://github.com/haecker-felix/gradio/wiki"]
https://github.com/haecker-felix/gradio/wiki[/URL]

I don't want to have to type snap run gradio. I want gradio in the Lubuntu menu under Sound & Video

[URL="https://github.com/haecker-felix/gradio/releases"]
https://github.com/haecker-felix/gradio/releases[/URL]

I download the version 6.0 both the zip and the tar.gz

What to do next ...

I am following 

[URL="http://ubuntuhandbook.org/index.php/2017/09/internet-radio-app-gradio-6-0-snap-ubuntu/"]http://ubuntuhandbook.org/index.php/2017/09/internet-radio-app-gradio-6-0-snap-ubuntu/

[/URL]but i get this error

~/Downloads/gradio-6.0$ sudo snap connect gradio:gnome-3-24-platform gnome-3-24:gnome-3-24-platform
**error: snap "gradio" has no plug named "gnome-3-24-platform"**

hands@hands-HP-dc5850-SFF:~/Downloads/gradio-6.0$ ^C

---

### Post by blackbird34 on 2017-11-23
Honestly, running "snap install gradio" is way easier than alternatives. I agree its annoying not to be able to do it via APT or a PPA, but Snaps aren't much harder. The .zip and .tar.gz files you downloaded are compressed source code, which you would have to compile, and that is a REAL HASSLE.

 I looked it up for you in the thread below: 

[URL="https://ubuntuforums.org/showthread.php?t=2327691"]https://ubuntuforums.org/showthread.php?t=2327691

[/URL]
> [B]
Re: lubuntu 16.04 is there support for snaps?[/B]

                                                                                                                                             Snaps will install and work on Lubuntu but as Lubuntu is a small  size (compared to Ubuntu) ISO image it does not come with a package  called snapd by default. Ubuntu & Xubuntu have snapd by default. So,  for Lubuntu the process is

```
sudo apt install snapd 
```
Then to see what snaps are available in the snap channel run

```
snap find
```


When I type "snap find gradio" I get this: 
```

nad@Incendies:~$ snap find gradio 
Name    Version  Developer      Notes  Summary
gradio  6.0.2    haecker-felix  -      A GTK3 app for finding and listening to internet radio stations
```

Then I typed "snap install gradio", and it installed. Easy.

---

### Post by Neill_R on 2017-11-23
you didn't show the final install command output see my question again  (modified)

---

### Post by ajgreeny on 2017-11-23
You could use radiotray instead of gradio.
I use radiotray and it is great; it sits in the panel as an icon and is set up by right clicking that to add URLs of radio broadcasts.

Give it a try, you may like it as I do.

---

### Post by Neill_R on 2017-11-23
Thanks but how does that help me. i used radiotray until i found gradio it was much better

---

### Post by Holger_Gehrke on 2017-11-24
The information at ubuntuhandbook.org is slightly outdated. The current version of gradio is 6.0.2 and need the snap gnome-3-2**6**-1604 not gnome-3-2**4**-1604, as stated at [https://github.com/haecker-felix/gradio/wiki/Install-Gradio](https://github.com/haecker-felix/gradio/wiki/Install-Gradio) . Once the connection between gradio and gnome is made, running gradio with 'snap run gradio' works as advertised. And on my system (XUbuntu 17.04) it does set up a menu item in the category multimedia, though I don't know at which stage this turns up (during install ? connect ? on first run ?).

My opinion: though the program **is** nice, it's not worth ~170 Megabyte (135 for gnome, 37 for gradio) of diskspace. I've run [Tiny Core Linux]("http://www.tinycorelinux.net/welcome.html") on a system with less disk space than that (128 MB disk on module). snap-packages with their 'let's pack up all dependencies into an archive' approach just seem like a terrible waste of space to me.

Holger

---

### Post by Alxl on 2017-11-24
GRadio is easy to install:

   sudo snap install gradio
    sudo snap install gnome-3-26-1604
    sudo snap connect gradio:gnome-3-26-1604 gnome-3-26-1604

---

