---
title: "Loving Lubuntu speed..  But a few errors / issues maybe? Or it could be just me :)"
date: 2021-02-22
forum: General Help
---

### Post by lovechips on 2021-02-22
Hi..  First off Im not a techie just a hobbyist who tinkers and found Ubuntu last summer after finally getting it that my old battered laptop needed some love rather than the hammering it was getting trying to run Windows 10.. and since then have tried many flavours.

I run an old Lenovo Flex 2-15 with 1.8g i3-4030U CPU and 8g 1600MHZ ram and a Nvidia GeForce 810M so since I found "Lubuntu" just last week it's on fire with speed!!!  and loving it :D

So yes most of what I "need" runs flawlessly eg Bitwig with Jack, Gimp, Inkscape, Kdenlive etc 

However..  Just two programs I "want" (not need but..) are OBS and Krita.

Now..  My old laptop has a dodgy screen..  So i run a HDMI to my 42" TV and use that as the primary monitor. Its been like that for about 4 year now.. yeah I know time to upgrade but if it still works right? :)

So my problem is this..  Both Krita and OBS I have found work flawlessly with Ubuntu and my other fave UbuntuMate..  But on Lubuntu OBS wont even fire up after it gives me some error about the Max audio buffer reached in the logs and Krita - although it fires up - all i get is some massive pics of a couple of the icons on the screen..

And as OBS didnt want to play I tried "Kazam" but that wouldn't load either..  I have FFmpg etc so I sont know whats going on there..  I'll keep looking to find a working screen recorder.

Now..  If they both worked without a hitch on the other couple of distros then Im guessing this is probably a Lubuntu thing - but just wondering if anyone else had run into problems like this?

And no..  Im not here really to ask for tech assistance on how to get these two specific programs running..  Yes I know "ask about them on their relevant program websites forums" Im just curious if anyone else has had any weird issues with Lubuntu that they didn't get with other distros due to its slimmed out nature.

I for one am certainly sticking with Lubuntu for now as it works my Bitwig Daw like a charm with only 8G ram so..  

Thanks for listening.

Sparky,

---

### Post by guiverc on 2021-02-22
First off, you haven't provided release details, so how can we know what desktop you're using?

Are you using a *legacy* Lubuntu release using LXDE?
Are you using a *modern* Lubuntu release using LXQt?

Without release details, we currently can only provide *inaccurate* details.  I can do a search for `krita` `obs-studio` etc and get details, but how do I know which relates to you?

```
guiverc@d960-ubu2:~$   rmadison krita
 krita | 1:2.4.0-0ubuntu2      | precise          | amd64, armel, armhf, i386, powerpc
 krita | 1:2.4.0-0ubuntu2.1    | precise-security | amd64, armel, armhf, i386, powerpc
 krita | 1:2.4.0-0ubuntu2.1    | precise-updates  | amd64, armel, armhf, i386, powerpc
 krita | 1:2.8.1-1-0ubuntu3    | trusty/universe  | amd64, armhf, i386, powerpc, ppc64el
 krita | 1:2.9.7-0ubuntu12     | xenial/universe  | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 krita | 1:4.0.1+dfsg-0ubuntu1 | bionic/universe  | source, amd64, i386, ppc64el, s390x
 krita | 1:4.2.9+dfsg-1        | focal/universe   | source, amd64, arm64, ppc64el, s390x
 krita | 1:4.3.0+dfsg-1build2  | groovy/universe  | source, amd64, arm64, ppc64el, riscv64, s390x
 krita | 1:4.4.2+dfsg-1        | hirsute/universe | source, amd64, arm64, ppc64el, riscv64, s390x

guiverc@d960-ubu2:~$   rmadison obs-studio
 obs-studio | 21.0.2+dfsg1-1 | bionic/universe  | source, amd64
 obs-studio | 25.0.3+dfsg1-2 | focal/universe   | source, amd64, arm64, armhf, ppc64el
 obs-studio | 26.0.2+dfsg1-1 | groovy/universe  | source, amd64, arm64, armhf, ppc64el
 obs-studio | 26.1.2+dfsg1-1 | hirsute/universe | source, amd64, arm64, armhf, ppc64el

```

I have no experience with OBS, but I've noticed no difference on Ubuntu Desktop (GNOME or Unity which are both GTK3) or Lubuntu LXDE (GTK2) or Lubuntu LXQt (Qt5), nor another desktop, *but I'm not a big user of it*, but nor can I imagine why there would be.

The base of Lubuntu is the same as other Ubuntu *flavors*, with only the desktop itself replaced by a lighter one, and the apps are chosen that share libraries & toolkits with the desktop itself (keeping the system light), however users are free to user other alternatives  (*my system is a modern Lubuntu using LXQt/Qt5 but I still use some old GNOME apps I started using in GNOME2 days; but I have the RAM to do it*)

Providing your release details at least is a start.

Are you using default packaged versions of the programs (from my search queries?) or *snap* or other packaged versions, in which case details would be helpful.

A number of you-tubers stream from Lubuntu (hey a couple are Lubuntu *developers,* so if there problems, it would be fixed pronto!).

---

### Post by lovechips on 2021-02-22
Ah..  Thanks for this and my apologies..  Im using a Lubuntu 20.04 downloaded last week onto USB. pure linux install - no dual boot etc


Firstly i tried a simple sudo apt install obs-studio which did install it..  but it wouldnt launch so then after a little search i found the following repo to try adding:
sudo add-apt-repository ppa:obsproject/obs-studio
then sudo apt install obs-studio
But same thing..


So.. Ive just done a Snap install..  And Hey that loads up! But massive icons on the HDMI.


[IMG]https://github.com/LoveChips/Lubuntu-Pics/blob/main/obs.jpg?raw=true[/IMG]


Krita was a straight sudo apt install krita 4.2.9 which on the HDMI screen also gave the massive icons.

[IMG]https://raw.githubusercontent.com/LoveChips/Lubuntu-Pics/main/Krita.jpg[/IMG]



So I have tried the snap version 4.4 which after the splash screen gives nothing at all.


To which end I have just reinstalled the original Krita version 4.2.9

(The images above are a snapshot which show my Laptop and HDMI screen as I have them linked that way..)



And to further testing..  Unplug the HDMI and reboot..  Both the versions I have on now work absolutely fine just on the laptop..

[IMG]https://github.com/LoveChips/Lubuntu-Pics/blob/main/obs%20working.jpg?raw=true[/IMG]

[IMG]https://github.com/LoveChips/Lubuntu-Pics/blob/main/krita-working.jpg?raw=true[/IMG]


But as I said on my prev post the laptop screen isn't good..  The screenshots come out fine but its help together with sellotape after a disaster some time ago the actual LCD has white spots and a crack thorugh it so not practical at all to use.. Maybe one day the Mrs will allow me cash for a new one rather than a new fridge or summin but hey :D


Anyway, summing up here ..  Now i know its the HDMI fault..  hmm..  I'll keep digging and see what I can find.


If I can get these to work on it as my primary then happy days and ten more years out of this aching laptop! :D

<EDIT>

As a sidenote I just ran another test..  Switch primary monitors so the laptop is the primary..

Well yes the programs now load straight onto the laptop screen..  but as soon as i drag them to use on the HDMI..  they go massive again.. hmmm

---

