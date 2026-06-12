---
title: "Software Center fails to download, blames internet connection"
date: 2013-06-16
forum: General Help
---

### Post by islandBilly on 2013-06-16
I know it's hard to diagnose, but on both my netbook, running 11.04, and a laptop running a live 12.04.2 I am failing to download any software from the Software Center. It says to check my internet connection, but I have no trouble getting email or loading web pages - except on THIS and other Ubuntu sites, which seem exceeding slow. Is it possible there is a problem on the servers?

I am trying to demonstrate Ubuntu for a friend on her laptop w the live 12.04 and I can't tell you how annoying it is when the Software Center doesn't work. Synaptic produced the same result. I searched the forums for comment and but mostly the Ubuntu forum never comes back or complains about the search the error message ("Failed to download Package files \n check your internet connection" - real helpful!)

I was trying to download gthumb image viewer, which is an actual Provided By Ubuntu package.

---

### Post by Impavidus on 2013-06-16
The problem with your 11.04 install can simply be explained: 11.04 has reached end of live and therefore the repositories from where the software centre downlads programs have been move away from the server. Best thing would be to install 12.04.

This doesn't explain your problem with 12.04. If internet works otherwise there may be a problem with the server. You could try using a different mirror or the main server.

---

### Post by islandBilly on 2013-06-16
I think you are mistaken. It may be that the 11.04 version will try to download a different gthumb version from the 12.04 - for instance, I downloaded the Ubuntu UP clock for 12.04, useless though it was, but could not even see it on the 11.04 machine. The Software Center is at least that smart.

The stuff is there, somehow or other, but it starts th download and then fails. I did succeed in downloading th UP-clock on the 12.04 laptop, but not gthumb or other things that may be gtk stuff.

---

### Post by varunendra on 2013-06-17
> **islandBilly said:**
> I think you are mistaken. It may be that the 11.04 version will try to download a different gthumb version from the 12.04 - for instance, I downloaded the Ubuntu UP clock for 12.04, useless though it was, but could not even see it on the 11.04 machine. The Software Center is at least that smart.

The stuff is there, somehow or other, but it starts th download and then fails. I did succeed in downloading th UP-clock on the 12.04 laptop, but not gthumb or other things that may be gtk stuff.

I have to agree with what Impavidus mentioned. For 12.04, you should try "sudo apt-get update" and/or changing servers, but for 11.04, the stuff has definitely been moved. Refer to the bottom of EOL table on this page : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
> The content of these old releases has been archived and can be accessed from [http://old-releases.ubuntu.com/releases](http://old-releases.ubuntu.com/releases).

As such, you may try changing the URLs in your sources.list file from "archive.ubuntu.com" to "old-releases.ubuntu.com". You may do that by manually editing the file (/etc/apt/sources.list) or -
```
sudo sed -i 's:archive.ubuntu:old-releases.ubuntu:' /etc/apt/sources.list
```
If you still get errors, it may help to try installing from terminal and post back exact error messages the terminal returns.

---

