---
title: "Ubuntu Software searches not showing everything"
date: 2019-02-23
forum: General Help
---

### Post by crockett98 on 2019-02-23
I'm new to Ubuntu so only have my time using Mint to go by...

When I search for packages and software that I know is in the repository it isn't showing up. If I run "sudo apt-get install ****" then it installs fine. 

Is this normal in Ubuntu? 

Namely, I couldn't find jailfire, mesa-vulkan-drivers and gramps in Ubuntu Software. Possibly a couple more (the GUI for UFW). I've noticed whatever I install using the terminal doesn't show up under the "Installed" tab and already i'm forgetting what i've installed. 

Thanks for any help!

---

### Post by Dennis N on 2019-02-23
You're correct - Ubuntu Software is not a complete store of all available packages. Many use Synaptic Package Manager for software. It's all in there.

---

### Post by The Cog on 2019-02-23
How do you search for it? Two of those three are found in my searches?
```
steve@StevesPC:~$ apt search mesa-vulkan-drivers
Sorting... Done
Full Text Search... Done
mesa-vulkan-drivers/bionic-updates 18.2.2-0ubuntu1~18.04.2 amd64
  Mesa Vulkan graphics drivers

steve@StevesPC:~$ apt search gramps
Sorting... Done
Full Text Search... Done
gramps/bionic,bionic 4.2.8~dfsg-1 all
  Genealogical research program
```

---

### Post by Impavidus on 2019-02-23
Ubuntu Software can hide some "technical items" to prevent confusion. Sometimes this causes confusion. You may like the synaptic package manager more.

---

### Post by deadflowr on 2019-02-23
Ubuntu Software does not show "Technical Packages" or command line based applications.
It shows mainly Desktop Graphical Applications.

Exceptions to this are snap and flatpak packages.
It'll show those (graphical or otherwise). As far as I've seen.

Packages that should be shown but are not might have an issue with improper or incomplete metadata that the software store relies on.
In which case you might file a bug against the package that should be showing.

---

### Post by crockett98 on 2019-02-23
Thank you for the replies! 

My first post wasn't all that clear. I'm only having problems finding stuff using Ubuntu Software. The terminal works fine. 

I guess in the future i'll just head straight to the terminal. 

I don't seem to have Synaptic installed but I remember being a bit bamboozled by it. I played around with Linux 10-12 years ago and I'm sure I remember damaging my install with Synaptic! 

I'll just use the terminal and apt-get... I'm never going back to Windows so i'll have to learn to be comfortable with it at some point! 

I know how to list installed packages on the terminal. Is there a way to list software/packages that I have installed using apt-get? 
So far the best i've found is...
[COLOR=#242729][FONT=Consolas]```
apt --installed list | grep -v automatic
```
[/FONT][/COLOR]but it seems to included all the dependencies too. [COLOR=#242729][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by deadflowr on 2019-02-23
fwiw, if you search for Firewall in Ubuntu Software does an entry for Firewall Configuration show?
That's gufw.

---

### Post by crockett98 on 2019-02-23
Yes, its there. Second from bottom on the list. 

I've just been through my terminal history and it seems Firewall Configuration is one of three that i've installed using Software. The other two being Steam and Keepass. Curl seems to be in there but I wasn't sure so used terminal for that.

---

### Post by deadflowr on 2019-02-23
Anything curl in the Ubuntu Software would most likely be snap or flatpak (if added) related.
You need to read the fine print (Details) of whatever package you want to install from Ubuntu Software.
Plenty of users have been burned by installing a snap version of some package only to realize something's wrong with it.
(Snap are isolated by design so they don't have the same level of access to your system that a normal apt package would,
some snaps do give you extra permission settings in the Ubuntu Software, but even those are usually limited)

It's easy to tell if it's a snap or flatpak package as those will show Snap Store or flathub (or whatever other flatpak repo you added) as the source.

---

### Post by crockett98 on 2019-02-23
I'll be honest... that flew straight over my head! I'm not sure what snap or flatpak is. 

I had to install curl so I could install Brave browser. 
I got the commands from the Brave website with hit a wall at the very beginning.

```
[COLOR=#333333][FONT=Menlo]curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
[/FONT][/COLOR]
[COLOR=#333333]source /etc/os-release[/COLOR]

[COLOR=#333333]echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ $UBUNTU_CODENAME main" | sudo tee /etc/apt/sources.list.d/brave-browser-release-${UBUNTU_CODENAME}.list[/COLOR]

[COLOR=#333333]sudo apt update
[/COLOR]
[COLOR=#333333][FONT=Menlo]sudo apt install brave-browser brave-keyring[/FONT][/COLOR]
``` 

To get all that to run I had to use 

```
sudo apt install curl
```


EDIT: I do understand your post now! I remember seeing two versions of certain software in the Mint Software app. One was often flatpak. I think curl was something like you said... hence, I decided to use the terminal! I thought I'd let Ubuntu work it out! :-)

---

