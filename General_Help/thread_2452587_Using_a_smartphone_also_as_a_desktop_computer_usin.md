---
title: "Using a smartphone also as a desktop computer using ubuntu?"
date: 2020-10-25
forum: General Help
---

### Post by tomsax on 2020-10-25
Has anyone had experience of getting ubuntu running from an android device.  It seems to be possible as shown here.
[https://www.androidauthority.com/install-ubuntu-on-your-android-smartphone-765408/](https://www.androidauthority.com/install-ubuntu-on-your-android-smartphone-765408/)

I also know its possible to connect an android phone to a docking station to use a monitor, keyboard and mouse with it.
[https://www.cnx-software.com/2015/08/29/connect-an-android-smartphone-or-tablet-to-a-monitor-usb-keyboard-and-mouse-easily-with-a-displaylink-docking-station/](https://www.cnx-software.com/2015/08/29/connect-an-android-smartphone-or-tablet-to-a-monitor-usb-keyboard-and-mouse-easily-with-a-displaylink-docking-station/)

I have used ubuntu a lot in the past and really like it but want to be able to use it on a phone.

Has anyone else tried to do this?

I like the idea of just being able to use my smartphone also as a desktop by using this method.  Why should we have so many computer devices in our household when a smartphone is so powerful?  

Tom

---

### Post by dino99 on 2020-10-25
Something else to read: [https://www.makeuseof.com/tag/how-to-linux-on-android/](https://www.makeuseof.com/tag/how-to-linux-on-android/)
                                               [https://tuxphones.com/2020-everything-running-linux-smartphone-guide/](https://tuxphones.com/2020-everything-running-linux-smartphone-guide/)

---

### Post by scorp123 on 2020-10-25
> **tomsax said:**
> Has anyone else tried to do this?

Samsung had a project called "Linux on DeX" which was supposed to let you run a full Ubuntu Linux session on some of their high-end devices (e.g. Note 10) when you ran their "DeX" desktop mode. But the whole project got cancelled, sadly.

In the newsletters I was subscribed to at the time these links to alternatives were passed around:

[https://www.slashgear.com/samsung-linux-on-dex-is-dead-here-are-open-source-alternatives-21596310/]("https://www.slashgear.com/samsung-linux-on-dex-is-dead-here-are-open-source-alternatives-21596310/")

I found it easier to simply use some form of remote access (e.g. TeamViewer, AnyDesk, ThinLinc, Guacamole, X2go, VNC-over-SSH, RDP ...) to a remotely running Linux desktop somewhere somehow rather than have the Linux desktop run directly on my Android device. Given there are WLAN access points everywhere (Coffee shops with Internet, train stations with public WiFi ...) and the overall 4G coverage in my country is excellent (... I'd really have to go into some remote mountain valley to find that one spot where I don't have a signal ...) I don't see why I shouldn't rely on remote connections. 

So I never explored further.

From people on the "Linux on DeX" newsletters I was subscribed to I know that "Termux" and "Userland" were projects that they found to be worth looking at, but I never tried those myself.

---

### Post by cmcanulty on 2020-10-25
Pine64 makes Linux tablets, laptops, and phones you can run many versions of Linux on and yes Ubuntu.

[https://www.pine64.org]("https://www.pine64.org")

---

### Post by grahammechanical on 2020-10-25
You are looking for something called Convergence. A few years ago I was looking forward to buying a smartphone/tablet that was running a Ubuntu desktop and that could be turned into a PC by connecting a monitor, keyboard and mouse.

Ubuntu developers were working on the OS called Ubuntu Touch. A couple of Chinese companies were producing smartphones and tablets with Ubuntu Touch installed. It seemed like Convergence was coming. Then development came to an end.

Ubuntu Touch is now being developed by a group called Ubports. If you have a Nexus 5 with a Ubports version of Ubuntu Touch installed you have some measure of convergence.

[https://ubports.com/](https://ubports.com/)

[https://ubports.com/devices/promoted-devices](https://ubports.com/devices/promoted-devices)

Regards.

---

### Post by tomsax on 2020-10-29
I managed to connect my wife's android phone to a monitor as of the second link.

But I haven't been able to install ubuntu desktop on her phone because BusyBox doesn't seem to get root access. 

I will try and persevere.

Tom

---

### Post by CatKiller on 2020-10-29
The upcoming Pro1-X from F(x)tec (silly names, I know) will have Ubuntu Touch as an option so you can use it as a convergence device. When you plug it into a monitor you can use the phone part as a touchpad. 

More details [here](https://www.forbes.com/sites/jasonevangelho/2020/10/27/this-gorgeous-new-linux-phone-ships-with-ubuntu-touch-and-lineageos/) and [here](https://www.indiegogo.com/projects/pro1-x-smartphone-functionality-choice-control#/).

The Ubuntu Phone project is why we got Mir, Unity, and snaps, but they ran out of money and had to stop before it was actually viable. It seems that it's starting to come to fruition now.

---

### Post by tomsax on 2020-10-31
> **cmcanulty said:**
> Pine64 makes Linux tablets, laptops, and phones you can run many versions of Linux on and yes Ubuntu.

[https://www.pine64.org]("https://www.pine64.org")

That looks like a great project and I see they ship to the UK.  Thanks for sharing, I will consider that.  
Tom

---

