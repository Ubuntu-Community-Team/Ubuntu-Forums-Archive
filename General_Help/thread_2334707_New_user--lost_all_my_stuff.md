---
title: "New user--lost all my stuff"
date: 2016-08-21
forum: General Help
---

### Post by tryst98 on 2016-08-21
So I made the leap and pledged to follow through with programming this time. I remember finding codeacademy boring so I grabbed a Ubuntu book at the bookstore today and put in the CD to try it out. Everything was going pretty well and I remember following the steps perfectly. For whatever reason (and I flipped through tons of pages that never explained) the Python packages I downloaded wouldn't do what the book said they would--that is, they wouldn't open up a text editor (or interpreter? bear with me I'm a complete newbie). The Ubuntu OS comes with gedit, but whenever I typed a command in Python it wouldn't execute. Figured it was just cause the Python package downloads weren't opening correctly because I didn't know how to do it. 

Anyway I worked on this stuff for hours but to no avail with Python. I wasn't even able to download spotify, adobe flash OR chrome. I popped out the CD and left the bookstore. When I got home I saw that Ubuntu was still running despite not having the CD in. I turned off the computer and changed the BIOS settings and boot order back to where they were initially but it still only boots Ubuntu. 

Right now I have come to terms with the fact that I probably lost all of my photos, essays, songs and precious bookmarks I had on Windows 10. My fault for not backing up I guess. Still, naturally, I'd like to know if there is a way to recover it. Even better, recover it and dual-boot (I think that's what it's called) Windows and Ubuntu with Ubuntu working well enough to download chrome, adobe spotify and maybe audible. Even better if it lets me program in Python! Pipe dreams eh..

Anyway at this point I'll take any help I can get. Kinda bummed that I can't do anything I want to on my computer haha. 

Thanks in advance~

---

### Post by HermanAB on 2016-08-21
First, turn that computer off and stop using it.  You can probably recover most of your files with a utility called photorec, which you can run off a CD.

---

### Post by tryst98 on 2016-08-21
Actually using it now. Do I download photorec on this computer or?

---

### Post by yancek on 2016-08-21
When you boot the Ubuntu DVD, you have two options.  Try without installing or Install so it doesn't install without user intervention.
Was this your own CD/DVD you brought to the book  store?  Do you still have it?  Which release is it?

If you are running Ubuntu from a CD/DVD, you can install software but it is pretty pointless because any changes you make are lost on reboot.  That's the nature of a Live CD/DVD.

If you still have the Ubuntu DVD or some other Linux, you can take a look to see if you still have your windows partitions by mounting the partitions.  Do you have a DVD?

---

### Post by Bucky Ball on 2016-08-21
Welcome. DVDs stuck to magazines we know nothing about as they generally aren't official releases but a 'tweaked' custom version by the magazine. These can have customisations we know nothing about so suggest you [download the official ISO]("http://www.ubuntu.com/download") and create a bootable disk or USB so you can get into a live session and we can see what is going on. For now, it is advisable you _[U]do not_[/U] use that hard drive you suspect is wiped.

Boot from the install media you create to a 'live' session: boot the media and when you get to the options choose 'Try Ubuntu' (NOT install Ubuntu). Once you are at a desktop, look for and launch Gparted. Do you see NTFS partitions there? Any? Do you see any partitions that are EXT anything? EXT4 for instance?

Let us know or post a screen shot of what you have there.

Unless you chose 'Install Ubuntu' or clicked the 'Install' icon on the desktop of a live session, Ubuntu would not be installed. If there is no disk in the machine and you are still running Ubuntu, then ...

What happens when you reboot the machine with the disk out??? Please remove any disks or USB dongles, reboot the machine and let us know exactly what you get and any error messages that are shown. Or if everything works exactly as expected.

---

### Post by tryst98 on 2016-08-21
Is there any way I can live chat with someone about this? I turned off the computer and mobile is hard to navigate.


I have the disc here with me but it's not in the computer. For whatever reason it began installing by itself after I hit "try Ubuntu" and it wouldn't let me cancel.

9th edition Ubuntu 16.04

I popped the CD back in. It goes straight to my Ubuntu login. Won't allow me to choose windows or Ubuntu but picks for me

[http://i.imgur.com/0ocCfWg.jpg](http://i.imgur.com/0ocCfWg.jpg)
^when I type in gparted

I've been turning it on and off so often that now it's just a black screen. It did that the last few times but only for a couple of seconds or a minute or two max. It's been 5 minutes <.>

---

### Post by Bucky Ball on 2016-08-22
Please click the 'open' icon in Gparted and post a screen shot of what that shows. 

Also, boot into Ubuntu, open a terminal (I think you'll find it with a search in Dash?), and type this in. You will be asked for your password and it will be invisible when you type it. That is normal.

```
sudo update-grub
```

Reboot the machine and tap the shift key. That should bring up a list of installed operating systems for you to choose from. If it doesn't, reboot and try escape (it is a different key depending on how Ubuntu is installed). When you see that list, is Windows by any chance there?

Restarting the machine repeatedly is not going to achieve anything positive. Better to just figure out what's going on.

---

### Post by tryst98 on 2016-08-22
[IMG]https://ubuntuforums.org/webkit-fake-url://c03b6a81-923e-4cbe-b930-df140b7eff06/imagejpeg[/IMG]
I typed the command in the terminal and when I restarted the computer and tapped shift the screen turned black. After about 15 mins I pressed the start button (though the light indicated the computer was on) and the monitor turned on and showed my login for Ubuntu.

by now I just want to work with this. I would like to download Adobe flash but it won't let me. I choose APT for Ubuntu 10.04+, then launch and ok. After I hit "download now" I get a message that says "sorry, Ubuntu 16.04 has experienced an internal error. If you notice further problems, try restarting the computer"

---

