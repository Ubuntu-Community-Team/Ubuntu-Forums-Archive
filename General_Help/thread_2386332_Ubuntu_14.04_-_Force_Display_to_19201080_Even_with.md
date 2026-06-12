---
title: "Ubuntu 14.04 - Force Display to 1920*1080 Even without a Monitor"
date: 2018-03-04
forum: General Help
---

### Post by OriTheEep on 2018-03-04
I need to be able to use a PC without a monitor for a while, dropping in every now and then with a vnc client.

The problem is that booting up without a monitor gives a ludicrously low display resolution. I would like the PC to boot up with a resolution of 1920*1200 regardless of whether or not a monitor is connected.

I am using Remima as a client and Vino as a Server for vnc, should this be relevant.

If any solution will also work with 16.04, this would be useful for another machine that sometimes has its monitor hijacked for telly purposes and has a habit of crashing: this might be a UEFI problem.

The machine's monitor has yet to disappear into the land of repair shops, so experiments may still be undertaken. I am aware that this must scarcely be a rare request but, having tried one or two solutions for similar problems without success, would prefer to ask for a solution specific to these requirements. Hopefully nothing too complicated for somebody with more expertise than I can claim.

Thanks for reading this.

---

### Post by OriTheEep on 2018-03-04
Sorry, I should add that the monitor doesn't actually work except insofar as to be recognised by the OS on booting up.

---

### Post by OriTheEep on 2018-03-05
Further digging on my part has turned up something of a solution which can be found on this [page]("http://www.bictor.com/2017/08/15/installing-a-dummy-monitor/").

Following the instructions there will give a resolution of 1360x768 as well as the 1024x800 specified, at least that's what I got.

Now I would like to have a resolution of 1920x1080. Simply adding "1920x1080", using a space as a separator, at the start of the Modes line doesn't work. Anyone able to tell me what will?

---

### Post by OriTheEep on 2018-03-05
Finally found a page with [exactly what I was after]("https://gist.github.com/mangoliou/27c6c5867a95932f21ae59ad7152aa33").

Had a problem with line 9 where downloading their xorg.conf on top of the one I had created earlier (See my previous post on this topic) raised a whinge about permissions. No problem, changing to the Desktop and downloading their xorg.conf to that folder gave me the text needed to replace the text in the earlier file. That is:

[INDENT]cd Desktop

wget  [https://gist.githubusercontent.com/mangoliou/ba126832f2fb8f86cc5b956355346038/raw/b6ad063711226fdd6413189ad905943750d64fd8/xorg.conf](https://gist.githubusercontent.com/mangoliou/ba126832f2fb8f86cc5b956355346038/raw/b6ad063711226fdd6413189ad905943750d64fd8/xorg.conf)

sudo gedit /usr/share/X11/xorg.conf.d/xorg.conf

gedit xorg.conf

Clear the entire contents of the file in /usr/share/X11/xorg.conf.d

Copy the entire contents of the Desktop file, paste it into the file in /usr/share/X11/xorg.conf.d and save this.

Reboot
[/INDENT]

Display resolution now the required 1920x1080 with oodles of other resolutions available from the Display section of System Settings.

There was more on that webpage (ll 12-25) but, as I had what I wanted, I didn't pay much heed.

Despite the apparent lack of interest from other users, it did help being able to post here, go for a long walk then come back to it. Hopefully anybody with a similar level of ignorance to mine trying to get the same result will find this helpful?

---

