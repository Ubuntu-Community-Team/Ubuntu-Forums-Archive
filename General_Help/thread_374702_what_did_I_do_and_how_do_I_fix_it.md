---
title: "what did I do and how do I fix it?"
date: 2007-03-02
forum: General Help
---

### Post by violet_spectre on 2007-03-02
First of all, I'm not sure exactly what category I should post this in, so I apologize in advance if this is the wrong place.  So after installing ubuntu 6.10 about a week ago, and finally getting my wireless adapter to work, I moved on to my next problem, which was getting my screen resolution set right.  
Suffice to say that this didn't go as planned. I have an nvidia 7600gt, so I eventually found my way to this page-http://www.tuxmachines.org/node/13690, which seemed to be just what I was looking for. I ran both "sudo apt-get update" and "sudo apt-get install nvidia-glx" in the terminal, and then restarted like it told me to. This is where the problems start. upon rebooting, I get alot of odd text that I dont recognize, a strange blue screen,  and eventually end up at a command prompt. Being quite the linux newbie, i'm not really sure what to do, but after some experimentation I manage to successfully get back to a normal looking screen by typing in "sudo startx" which I remembered seeing someware online as a way to start the gui. So now I'm back in ubuntu, and, low and behold, my screen resolution is now correct! however, I seem to have messed some things up somewhere. Ubuntu is telling me that there are 138 updates to install, but when I click "install updates" I get the following message:

Failed to run /usr/sbin/synaptic '--hide main window' '--non-interactive' '--parent-window-id'  '39845891' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpoxblok' as user root

Unable to copy the user's Xauthorization file

I get a similar message when trying to access the synaptic package manager:
Failed to run /usr/sbin/synaptic as user root.
Unable to copy user's Xauthorization file.
I seem to  get similar messages for anything requiring access as root.
So what did I do , and how do I fix it?  Any help is very much appreciated.

Also, I forgot to mention that the little red shut down icon in the upper right corner no longer gives me a shut down or restart option, but only logout or switch users, which takes me back to a command prompt.

---

### Post by Kateikyoushi on 2007-03-02
Try in terminal or before starting x.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by taurus on 2007-03-02
Have you rebooted to see if X is still running?  Then, open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  You can reboot your machine with

```
sudo shutdown -r now
```
Upon reboot, you should see a GUI login screen.

---

### Post by violet_spectre on 2007-03-02
wow, thanks for the quick replies. I took a dinner break, and when I came back and booted up, ubuntu started right up, and somehow everything seems to have fixed itself. I dont know how or why, but it works now. My only concern is that in the grub bootloader (I dual boot with xp, for now anyway) their are now a bunch more entries for various versions of ubuntu, as if it creates a new one everytime I update something. Is this normal? as long as I select the top one, it works fine, just wondering if this is normal. thanks again for the quick replies.

---

### Post by taurus on 2007-03-02
Each time you upgrade a kernel, two new entries will be added to /boot/grub/menu.lst, one for the new kernel and one for the recovery mode.

---

### Post by sgstarling on 2007-03-02
How many is a 'bunch more' entries?

When I installed 6.10 then did an update, it set up a new kernel version and rescue mode for that new version.

um, it was something like this: it USED to be:

[LIST=1]
[*]Ubuntu, kernel 2.6.17-10-generic
[*]Ubuntu, kernel 2.6.17-10-generic (recovery mode)
[*]Ubuntu, memtest86+
[/LIST]

Then, after the update, when it added a new kernel version:

[LIST=1]
[*]Ubuntu, kernel 2.6.17-11-generic
[*]Ubuntu, kernel 2.6.17-11-generic (recovery mode)
[*]Ubuntu, kernel 2.6.17-10-generic
[*]Ubuntu, kernel 2.6.17-10-generic (recovery mode)
[*]Ubuntu, memtest86+
[/LIST]

Thus my grub list got bigger. Notice the top two choices are the new version now.

---

### Post by violet_spectre on 2007-03-02
ok, cool, just wanted to make sure that was normal. Thanks alot guys.

---

### Post by zhinker on 2007-04-21
I have the same thing happening to me.  Is there any way to fix that?

---

