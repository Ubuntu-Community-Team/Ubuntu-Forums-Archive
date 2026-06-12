---
title: "Howto upgrade Musecsore from 2.1.0 to 3.0?"
date: 2020-09-17
forum: General Help
---

### Post by Old Jimma on 2020-09-17
Hi Ubuntu Community:

I'm a music student and use **Musescore** to create beautiful scores, midi files, and pdfs.

The version available from the Ubuntu repos is **2.1.0.**

I need features of **Musescore**  available on version **3.0**.

How to I install that?

I went to the **Musescore**  web site and it said something about Applmage to get more recent versions. It did not work for me.

Is there a way to update a repository and then update to get **3.0**?

Thanks,
Old Jimma

---

### Post by webaake on 2020-09-17
Are you on 18.04 as said in your profile?

Why didn't the appimage file work? Any log messages about that?

Seems that Ubuntu 20.10 don't even have 3.0 version.

You might be able to compile it yourself, but that's a tall order with a steep learning curve.

---

### Post by Old Jimma on 2020-09-17
Hi Webaake:

Thanks for your reply!

After downloading the appimage file from [https://musescore.org/en/download/musescore-x86_64.AppImage]("https://musescore.org/en/download/musescore-x86_64.AppImage"), I clicked on it and got a message that says:



Could Not Display "Musescore-3.5.0-x86-64: there is no application installed for "appimage application bundle" files. Do you want to search for an application?"

When I click "yes" to the question, nothing happens.

Old Jimma

---

### Post by Old Jimma on 2020-09-17
HI webaake:

I had no idea what an appimage file was.

I found out what to do with them at: [https://askubuntu.com/questions/774490/what-is-an-appimage-how-do-i-install-it#774520]("https://askubuntu.com/questions/774490/what-is-an-appimage-how-do-i-install-it#774520")


Then, within a command window:

> chmod a+x MuseScore-3.5.0-x86_64.AppImage
> ./MuseScore-3.5.0-x86_64.AppImage

That last line (./MuseScore-3.5.0-x86_64.AppImage) starts Musescore 3.5

However, there isn't a desktop icon that I can use to use the software conveniently, and find it in "Show Applications."

Old JImma

---

### Post by ActionParsnip on 2020-09-17
Could try a PPA
[https://launchpad.net/ubuntu/+ppas?name_filter=Musescore](https://launchpad.net/ubuntu/+ppas?name_filter=Musescore)

Remember to filter the PPA for Focal, not all PPAs support all releases of Ubuntu

---

### Post by Impavidus on 2020-09-17
Ubuntu 20.04 and 20.10 have version 3.2 available from the repositories. The package is named musescore3, so that both 2.3 and 3.2 can be installed (on 20.10 at least; it seems that 20.04 only has 3.2 available). Ubuntu 18.04 only has version 2.1. That's what you get with older Ubuntu releases: they don't get the latest software. Which is for me a reason to upgrade every 6 months.

---

### Post by CatKiller on 2020-09-17
> **Old Jimma said:**
> Then, within a command window:

> chmod a+x MuseScore-3.5.0-x86_64.AppImage
> ./MuseScore-3.5.0-x86_64.AppImage

That last line (./MuseScore-3.5.0-x86_64.AppImage) starts Musescore 3.5

However, there isn't a desktop icon that I can use to use the software conveniently, and find it in "Show Applications."

Now that you've made the file executable, which is what the first command did, and which you could have done from the GUI if you'd wanted, by right-clicking and changing its Properties, you should be able to launch it by just double-clicking on it.

The launchers that are used in menus and so on are just text files with a specific syntax. You should be able to work out how to create your own by dragging and dropping a representative sample from your menu to a text editor to see how they work. .desktop files placed in ~/.local/share/applications will show up in menus. Or there are GUI tools for creating launchers if you don't want to play with text files.

---

### Post by Old Jimma on 2020-09-17
Hi ActionParsnip:

Thanks for your reply!!!

Here is what I did:

Went to the ppa: [https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore3-stable]("https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore3-stable") where the following code is located:

[PHP]
sudo add-apt-repository ppa:mscore-ubuntu/mscore3-stable
  sudo apt-get update
  sudo apt-get install musescore3
[/PHP]

**This installed the most recent MUSESCORE 3 RELEASE .**

Thanks!
Old

---

