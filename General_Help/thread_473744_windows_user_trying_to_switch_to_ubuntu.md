---
title: "windows user trying to switch to ubuntu"
date: 2007-06-14
forum: General Help
---

### Post by hops33n on 2007-06-14
Gotta a couple of questions here, what im trying to do is use my ubuntu 7.04 laptop instead of xp for network admin and daily use.   Just trying to figure out what programs I should use.

What kinda security software should I use ie malware and firewall, is antivir and firestarter good choices?  Some of my friends say you dont need antivirus software, but I like to feel cozy.

How about something like Hyperterminal and putty for console admin, does linux have something like this?

Can ubuntu play window media and quicktime movies by default or do I need something extra?

Can someone show me how to make and run a script the will change the ip address information?  From dhcp to static and static back to dhcp.

Does linux offer some kinda wifi scanner like netstumbler?

Is there some kinda pdf creator, adobe that you can convert a doc to pdf by printing it?

Last one, I ended up deleting my gnome network manager for wifi off the panel, how in the world do I get that back up there?

Thanks in advance.

---

### Post by jasonlfunk on 2007-06-14
> **hops33n said:**
> 
What kinda security software should I use ie malware and firewall, is antivir and firestarter good choices?  Some of my friends say you dont need antivirus software, but I like to feel cozy.

I use firestarter, it works well. Seriously, the only reason you would need a virus scanner is if you had access to windows shares or mounted a windows drive. I don't use one so I cannot recommend one.

> 
How about something like Hyperterminal and putty for console admin, does linux have something like this?

What exactly are you wanting? Something that will store telnet or ssh sessions?

> 
Can ubuntu play window media and quicktime movies by default or do I need something extra?
Follow the instructions here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> Can someone show me how to make and run a script the will change the ip address information? From dhcp to static and static back to dhcp.
It would just be a matter for replacing the text in a file and restarting a service, you can do it with a bash script. More information can be found here: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)
> 
Does linux offer some kinda wifi scanner like netstumbler?
Perhaps something like:
GTKWifi: [http://ubuntuforums.org/showthread.php?t=113715](http://ubuntuforums.org/showthread.php?t=113715)
or
SWScanner: [http://www.swscanner.org/en](http://www.swscanner.org/en) 

> 
Is there some kinda pdf creator, adobe that you can convert a doc to pdf by printing it?
I just read this in LifeHacker :) [http://www.arsgeek.com/?p=1720](http://www.arsgeek.com/?p=1720)

> 
Last one, I ended up deleting my gnome network manager for wifi off the panel, how in the world do I get that back up there?
I'm not at my Ubuntu machine now so I don't know for sure, but if you right click the panel and click "Add to Panel" it may be in the list there.

---

### Post by buuntuu! on 2007-06-14
welcome!

if you insist on a firewall install firestarter which is only the frontend for iptables that is watching over you by default.

clamav is the antivir of my choice, though i only scan files i pass along to windows-users ;)
 no need for antivir on linux :)

there is hardly any multimediasupport by default as there are no proprietary codecs included in the distro. you can fix this easily reading up [here]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29#head-e8e18f028625a9fec498bb3d38cc284460a51a1d")

openoffice exports to pdf

rightclick the panel > add to panel > create new starter > type "networkmanager" as command and choose an icon.

whoa, what a marathon!

EDIT: and too slow as well!!

---

### Post by trippinnik on 2007-06-14
looks like they got you covered on most of the points.  as to terminal connections,  if you have ssh setup on the server already (putty is an ssh client) you can type ssh (ip address or server name) at the terminal prompt.

---

### Post by jfinkels on 2007-06-14
> **hops33n said:**
> Gotta a couple of questions here, what im trying to do is use my ubuntu 7.04 laptop instead of xp for network admin and daily use.   Just trying to figure out what programs I should use.

What kinda security software should I use ie malware and firewall, is antivir and firestarter good choices?  Some of my friends say you dont need antivirus software, but I like to feel cozy.

We don't have malware, adware, viruses, etc. Installing firestarter is simple, if you really want to do it.
> 
How about something like Hyperterminal and putty for console admin, does linux have something like this?

The terminal is integral part of the Linux environment. Things like putty were created based on Unix-like system standards. For us, all you have to do is go to the terminal, type "ssh" and the ip address and you're in. Simple as that. Everything is built in, or a few words typing away.
> 
Can ubuntu play window media and quicktime movies by default or do I need something extra?

You will probably need something extra, or you can download VLC player, which should work with pretty much any format you give it. There's a version for Windows, go check it out for yourself. Here's some info on restricted formats in Ubuntu: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
> 
Can someone show me how to make and run a script the will change the ip address information?  From dhcp to static and static back to dhcp.

Make a new thread and someone can show you. It will be very easy.
> 
Does linux offer some kinda wifi scanner like netstumbler?

Ubuntu 7.04 Feisty Fawn comes with one. You can also install others from the software repositories. Very simple.
> 
Is there some kinda pdf creator, adobe that you can convert a doc to pdf by printing it?

Yes, see above poster.
> 
Last one, I ended up deleting my gnome network manager for wifi off the panel, how in the world do I get that back up there?

Thanks in advance.

See above poster.

---

### Post by calraith on 2007-06-14
You can configure CUPS (the Common Unix Printing System) to print to PDF, so you can print PDF's from any application, not just OpenOffice and whatever else explicitly includes PDF conversion.  Google for CUPS PDF and I'm sure you'll find buttloads of howto's (like [this one]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/") or [this one]("http://ubuntuforums.org/showthread.php?t=188860")).

There's also a package called "pdfedit" that makes a pretty good replacement for Adobe Acrobat Professional, and will let you modify and save changes to PDF's.  You should find it in the Synaptic Package Manager if you have the Universe repositories enabled.

A quick Google search showed me a GUI way of [enabling the Universe repositories]("http://monkeyblog.org/ubuntu/installing/") through Synaptic.  The instructions are specifically for an older version of Ubuntu, but I'd imagine they still apply.  (I'm a console kind of guy myself, so I don't have firsthand experience.)

---

### Post by hops33n on 2007-06-14
Well I sure appreciate the help everyone, I'll try to start implementing some of this stuff.  About the hyperterminal deal, I use that for serial console connections to cisco routers and switches, is this too a part of linux?  I just figured I would need a special program for setting the baud, flow control, parity..... Again, thanks you all.

---

### Post by calraith on 2007-06-14
For antivirus, I'm fond of clamav as well.  I just found something interesting in the repos -- clamfs.  Apparently it's a userspace filesystem which basically provides on-access scanning using the clamav daemon.  It doesn't appear to be terribly mature in its integration with Ubuntu yet.  Installation requires installing clamfs from the repos, copying /usr/share/doc/clamfs/clamfs-sample.xml to /etc/clamfs.xml, salting /etc/clamfs.xml heavily to taste, and then running "clamfs /etc/clamfs.xml."  Maybe if one of you guys who has a triple-foam sausage vanilla cream spaghetti latte with cinnamon sprinkles gets bored, you wouldn't mind writing up a friendly, more verbose howto?

---

### Post by calraith on 2007-06-14
> **hops33n said:**
> Well I sure appreciate the help everyone, I'll try to start implementing some of this stuff.  About the hyperterminal deal, I use that for serial console connections to cisco routers and switches, is this too a part of linux?  I just figured I would need a special program for setting the baud, flow control, parity..... Again, thanks you all.

[CuteCom]("http://www.lockergnome.com/nexus/linux/2004/12/08/replacing-hyperterminal-on-linux/"), [minicom and ckermit]("http://osdir.com/ml/linux.redhat.release.valhalla/2003-02/msg00008.html") seem to be the terminal apps of choice for ubergeeks such as yourself.  ;)  They're all available in the apt repositories through Synaptic.

---

