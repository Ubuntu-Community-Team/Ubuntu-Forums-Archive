---
title: "Using Ubuntu and playing tv through firefox and the cable co. website"
date: 2023-03-21
forum: General Help
---

### Post by 01robert on 2023-03-21
I'm semi new to Ubuntu so this problem may have already been solved. I'm in the process of making Linux and Ubuntu (currently 22.04) my daily driver. So far, 99.9% of everything works very well. The one thing that isn't working is when I log onto the cable co. website and try to check a program that I set to record. After the program is recorded, if I try to  play the program it doesn't work. I set the DRM in firefox but that doesn't help. Anyone have any ideas?

---

### Post by SeijiSensei on 2023-03-22
Do you have a Windows machine available to see if it works there?

---

### Post by MAFoElffen on 2023-03-22
Or... Have you tried with a different browser such as Google Chrome? (Some times vendors make assumptions about what people are using...)

---

### Post by 01robert on 2023-03-22
I've done the same thing using  Windows 10 and it works. I haven't tried any other browser other than Firefox. I'll give that a try. Another wrinkle, so to speak, is out of habit I usually use Firefox in Incognito mode. I'll first try it without the Incognito mode. Thanks for the input.

---

### Post by SeijiSensei on 2023-03-23
Also if you have content blockers like UBlock Origin or Ghostery enabled, turn them off and try again.

---

### Post by 01robert on 2023-03-24
Well, I tried two other browsers (chromium and brave), I shut off any blockers (badger and ghostery), and I tried using all of the browers (firefox, chromium, did I spell that right?, and brave) in both standard mode and incognito mode and nothing worked. I did get an error? message from the cable co. when I was doing this.  It seemed to say that I should upgrade to the latest version of the browerser ( which I did already) and that it was compatible with IOS, Windows 7+, Firefox, and Chrome. Anyone else run into this? I installed chromium but not chrome. I've never tried chrome with a linux os.  For some reason that doesn't seem right. That may be the only alternative for this problem, minor as it is. One thing that I haven't tried is to try a virtual machine running under Ubuntu with Win10 or a mac virtual machine. Any thoughts....

---

### Post by DuckHook on 2023-03-24
I've never actually tried to do what you are doing, but here are a few ideas.

[LIST=1]
[*]Set your user agent in each browser to Windows. Broadcasters sometimes stupidly assume that Linux users are "hackers" and will default to denying access, but if they are fooled into thinking that you are using boring crippled OS, they feel "safe" and might let you go.
[*]I highly encourage you to try out Windows in a VM. I have both W10 & W11 in VMs for just such nonsense as you are experiencing now. It made no sense for me to waste time/serenity wrestling with Windows crippleware when I could run the thing jailed safely in a VM where it couldn't cause any damage.
[/LIST]

---

### Post by 01robert on 2023-03-24
Sorry, I'm a rookie. What is a user agent (I'll do some digging after I log off), and how do I set it (again, I'll do some digging on this after I log off). Also, last night I  found a VirtualBox download for Linux, from their website and downloaded it. I then fired up the terminal and typed in sudo apt-get install virtualbox-7.0 and  I received an error message of sorts that said, I think, that the file could not be found. Any thoughts? I'll do some digging on this too after  I log off. I do like the vm option like DuckHook said to take care of nonsense issues. There are a couple other os's that have some interesting things like Jails and what not, but that's way,way over my head...

---

### Post by Frogs Hair on 2023-03-24
The user agent that I know of is a browser extension.I wasn't aware it was still around, this extension was better known in the internet explorer days.
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher/)

---

### Post by DuckHook on 2023-03-24
The user agent string is what your browser uses to advertise itself as. It can be spoofed to advertise itself as a different browser, or as belonging to a different OS. Here are instructions for setting Firefox's: [https://www.whatismybrowser.com/guides/how-to-change-your-user-agent/firefox](https://www.whatismybrowser.com/guides/how-to-change-your-user-agent/firefox)

VMs are not that hard to get up and running once you are familiar with them, but there is an initial learning curve. The VM platform that I use is called KVM which is already baked into the Linux kernel. Intro is here: [https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor)

Many people do use VBox, which is slightly easier to start with, but it requires the addition of a foreign module (which I don't like). I also find KVM more stable and faster, but these are not critical issues. Ease of use is probably more important for you at this time.

---

