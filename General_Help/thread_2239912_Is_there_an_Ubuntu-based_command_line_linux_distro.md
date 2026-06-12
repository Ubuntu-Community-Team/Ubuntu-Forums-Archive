---
title: "Is there an Ubuntu-based command line linux distro available?"
date: 2014-08-16
forum: General Help
---

### Post by ric_Poirier on 2014-08-16
Hi,

I just bought a new computer, but my old computer still works well (but is slow on Ubuntu). What I would like to do is the following: use my old computer as a backup for my new one, using **openssh-server**. Now, since my old computer wouldn't be used anymore in graphic mode (only in command-line mode), I was wondering if there exists a linux distro which:
[LIST]
[*]is based on Ubuntu (in which I could use **apt-get**, for instance); 
[*]is only command-line (to save on speed and weight). 
[/LIST]
If not, what do you think would be my best option?

Thank you very much,

Éric

---

### Post by JetStorm on 2014-08-16
Yes - it's called Ubuntu server.
You can find more info at this link - [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

You can also try a netinstall of Debian (what Ubuntu is based on) without a graphic environment. Package versions might be a bit older but it's using a lesser amount of system resources.

---

### Post by ric_Poirier on 2014-08-16
Thanks for your quick answer.

I just downloaded ubuntu server, but the cd won't boot on my old PC. I know that the Ubuntu version that I have on it is 32-bit, and that the ubuntu server is only available in 64-bit. Could that be a problem?

---

### Post by coffeecat on 2014-08-16
> **ric_Poirier said:**
> 
I just downloaded ubuntu server, but the cd won't boot on my old PC. I know that the Ubuntu version that I have on it is 32-bit, and that the ubuntu server is only available in 64-bit. Could that be a problem?

It depends whether your machine is 32-bit or 64-bit, of course. You can find out by running "lscpu" in the terminal. 

What is curious is that if you click on the download button in the link JetStorm posted, it unequivocally states, "64-bit only". Yet if you go to this link for all the options, both desktop and server, there is an i386 server ISO, which is 32-bit:

[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

I don't know why the main ubuntu.com site is saying that.

---

### Post by ian-weisser on 2014-08-16
Look on the Alternatives link, and you will find: [http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-server-i386.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-server-i386.iso.torrent)

---

### Post by grahammechanical on 2014-08-16
And then there is the Minimal CD. And it is minimal. Only 31MB to download the ISO image and everything else is downloaded and installed based upon our selection. We can get a full Ubuntu installation or just Linux. Or anything in between including alternative desktops. Without the server applications that come with the server editions. Unless we choose to have them.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Regards.

---

### Post by ric_Poirier on 2014-08-17
Thank you very much. Ubuntu server seems to be exactly what I am looking for!

Éric

---

