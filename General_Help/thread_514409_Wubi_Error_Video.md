---
title: "Wubi Error: Video"
date: 2007-07-31
forum: General Help
---

### Post by Time Warrior on 2007-07-31
Unfortunately I've no way that I know of to post the specific error messages however I'll endeavor to describe this as best I can.

Ububtu (the multimedia studio advanced option) installed flawlessly. So, I reboot and such and I have the options of Windows XP and Ububtu. So, I select Ubuntu.

First, I get a blank screen. But there is hard disk activity, so I wait. Then X tries to load but pukes all over the place. So I hit CTRL+ALT+F8 for more information on that, which reveals the error messages I wish I could show you all.

So, I hit CTRL+ALT+BACKSPACE to kill X. It dies but the pukes remain. So I hit CTRL+ALT+F1 and login to the prompt. The prompt is so slow that I have to keep holding down the ENTER key in order for commands to go through or for text to continue to display.

Not being able to locate a conf (or other) file to manually edit the graphics settings (I'm more used to pure Debian, new to Ubuntu) I have no way of diagnosing or attempting to correct the problem.

It seems to me as though Ubuntu doesn't quite know what to do with the graphics card. Unfortunately, I am installing this on a Dell, which is a friend of mines computer. I know the graphics cards of most proprietary systems tend to drive most Linux Distros a bit crazy.

I'm guessing the slow down / enter key being needed problems are also an end result of the graphics messing up.

The Dell is a 3GHZ Intel and has about 1GB worth of DDR Memory and a lot of hard drive space. There are two drives in 3 partitions all under NTFS.

I would like to know what I should do to rectify this issue.

I know that Wubi is very new so for all I know installing the Multimedia Studio is still untested and I just happened to miss it in the docs or some crazy thing like that.

So I'm not sure if I should try installing again with some other option (Ububtu, Xubuntu, etc..) or if theres some file i can nano or pico into, toggle a setting and have it work properly.

Thanks!

-Dave

---

### Post by ago on 2007-07-31
you may need to install the required driver (porbably ati or nvidia) and/or edit /etc/X11/xorg.conf, there are several guides on the topic. Not sure though why it is so slow, if you can find the reason it would help.

---

### Post by Time Warrior on 2007-07-31
> **ago said:**
> you may need to install the required driver (porbably ati or nvidia) and/or edit /etc/X11/xorg.conf, there are several guides on the topic. Not sure though why it is so slow, if you can find the reason it would help.

If I could find the reason I wouldn't need help. lol ... gotta love lifes "chicken and the egg" type paradoxes :-)

I'll mess with the xorg.conf and report back to you on this. I'm fairly certain you're the Author of this installer so that being the case -- despite my troubles with it -- I do give you props and I understand it's still a work in progress like most things open source. I think so far you've done a great job and I applaud you.

-Dave

---

### Post by tuxcantfly on 2007-07-31
If you're running on an nvidia card:

Ctrl-Alt-F2 to get to the prompt

login

```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

reboot

---

### Post by Time Warrior on 2007-08-01
> **tuxcantfly said:**
> If you're running on an nvidia card:

Ctrl-Alt-F2 to get to the prompt

login

```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

reboot

I'll give it a shot and report back. Thanks!

-Dave

---

### Post by Time Warrior on 2007-08-02
> **tuxcantfly said:**
> If you're running on an nvidia card:

Ctrl-Alt-F2 to get to the prompt

login

```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

reboot

Alrighty. I did exactly as instructed.

Apt-get did what it needed with no errors.
Packages were retrieved.
Packages installed.
No errors at all.

Then I reboot.
Select Ubutbu.
Same errors.

Graphics pukes. X cannot start.

The specific make and model of the machine is a Dell Dimension B110. Hopefully this helps.

-Dave

---

### Post by Time Warrior on 2007-08-07
I tried good ole regular Ubuntu and it does not have these video issues. Personally, seeing as (as far as I know, anyways) when Ubuntu boots from the image according to what your program sets up, it boots independently of Windows. Being a "real install" and all. So personally, I've got no idea as to why video would mess up using your installer and regular Ubuntu detects everything flawlessly. 

A friend of mine thinks that hal.dll is resident somehow while Ubuntu boots off the image and that it's this dll file thats screwing with things.

One suggestion I'd like to make, if it'll help matters: why not create something equal and opposite to what your doing? A Windows installer for Ubuntu. In theory, this is how it might work:

Step #1) Ubuntu is installed in its usual way
Step #2) The Windows Installer it apt-gotten or whatever other means of download / install
Step #3) The installer sets up all of the image stuff, grub and whatever else needs to be done.
Step #4) The installer asks you to reboot, and a Grub option to install Windows can be selected.
Step #5) Upon selecting it, you are asked to please insert a Windows Install Disc into the DVD / CD Drive and press a key to continue once done.
Step #6) The Windows installer from the CD does it's usual thing to install Windows, only it's forced to see only the blank image discs as opposed to the real drives in the computer
Step #7) Windows installs normally and prompts for reboot
Step #8) Grub entry for installing Windows is gone. Grub entry for Booting Windows is seen and selected.
Step #9) Second and last phase of installing Windows occurs as normal

Is this feasible?

-Dave

---

### Post by tuxcantfly on 2007-08-07
> A friend of mine thinks that hal.dll is resident somehow while Ubuntu boots off the image and that it's this dll file thats screwing with things.

I doubt a dll file could be doing anything; Ubuntu can't run dll files...

The difference is likely because the liveCD uses Ubiquity for installation, while Wubi uses d-i with a bunch of loopmounting hacks for installation. Perhaps Casper, which does the hardware detection on the liveCD, functions better at videocard detection that d-i does.

> One suggestion I'd like to make, if it'll help matters: why not create something equal and opposite to what your doing? A Windows installer for Ubuntu.

Well it sounds like a good idea, but it's a bit unfeasible, due to the closed-source nature of Windows. Since we can't modify the Windows boot or installation mechanism (closed source), how then, are we supposed to get something like this :

> Step #6) The Windows installer from the CD does it's usual thing to install Windows, only it's forced to see only the blank image discs as opposed to the real drives in the computer

to work? That could only be done by using a hypervisor, and there are plenty of high-performance hypervisors out there, like Xen and VMware ESX server, so it would be pretty pointless to try to duplicate their work.

However, if what you were aiming at were the advantages of Wubi (no CD needed for installation) without needing the loopmounted installation portions, you might want to check out UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Time Warrior on 2007-08-07
> **tuxcantfly said:**
> I doubt a dll file could be doing anything; Ubuntu can't run dll files...

The difference is likely because the liveCD uses Ubiquity for installation, while Wubi uses d-i with a bunch of loopmounting hacks for installation. Perhaps Casper, which does the hardware detection on the liveCD, functions better at videocard detection that d-i does.



Well it sounds like a good idea, but it's a bit unfeasible, due to the closed-source nature of Windows. Since we can't modify the Windows boot or installation mechanism (closed source), how then, are we supposed to get something like this :



to work? That could only be done by using a hypervisor, and there are plenty of high-performance hypervisors out there, like Xen and VMware ESX server, so it would be pretty pointless to try to duplicate their work.

However, if what you were aiming at were the advantages of Wubi (no CD needed for installation) without needing the loopmounted installation portions, you might want to check out UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Thanks for the resource list and explanations, it's appreciated. How would you get it to work? How does nLite take files from a Windows CD and create a custom install iso with Windows being closed source?

Things like Vmware, Quemu, etc... run other OSes within the primary os as a VM. I'm not suggesting this be done at all. Just as yours installs to image files, why couldn't something be made to install Windows to image files also?

Though what I'm proposing is similar to VMware it is different in the aspect that I'm not talking about a virtual machine. I'm talking about a means of installing Windows similarly to the way your installer does for Ubuntu. I'm not a programmer but nor am I novice when it comes to how various things work and why, either.

You can likely answer your own question better than I could because you are a coder, and seemingly a very good one at that.

If code from other projects would help make it possible, then that is one of the beauties of open source software. Now, it might be redundant if I was suggesting to do something that already exists. However, I have not found anything that does as I've suggested which does in my opinion, make it feasible -- even if code from other existing apps is used to make it happen.

I can see why you might think it to be somewhat redundant but I'm not sure as to why you might think it's impossible due to the closed source nature of Windows.

I do wish you to continue pointing out any holes in my logic seeing as a coder you do know better than I could. I'll do my best to keep up until theres either no more holes left, or no more idea left because there were too many holes in it. lol

-Dave

---

### Post by tuxcantfly on 2007-08-08
> Thanks for the resource list and explanations, it's appreciated. How would you get it to work? How does nLite take files from a Windows CD and create a custom install iso with Windows being closed source?

Ok, I'll correct my statement. With a few hacks, perhaps it would be possible after all, however, it would be treading legal waters. The legality of stuff like nLite and BartPE, especially in the US, is extremely questionable (technically they should have needed to consult with MS before making modifications to Windows, and they didn't, and MS definitely won't authorize something like this), so even if someone managed to get it to work, legal issues would emerge and that would hamper the adoption and usage of the program, not to mention that none of us really want to get landed in hot water for writing and distributing something like that...

---

### Post by Time Warrior on 2007-08-08
> **tuxcantfly said:**
> Ok, I'll correct my statement. With a few hacks, perhaps it would be possible after all, however, it would be treading legal waters. The legality of stuff like nLite and BartPE, especially in the US, is extremely questionable (technically they should have needed to consult with MS before making modifications to Windows, and they didn't, and MS definitely won't authorize something like this), so even if someone managed to get it to work, legal issues would emerge and that would hamper the adoption and usage of the program, not to mention that none of us really want to get landed in hot water for writing and distributing something like that...

Ah, ok. Makes sense now. Thanks!

Still not sure why the video detection is malfunctioning with Wubi, but as they say, Rome wasn't built in a day. I'm sure you guys will resolve that sooner rather than later.

-Dave

---

