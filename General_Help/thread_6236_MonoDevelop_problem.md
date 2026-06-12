---
title: "MonoDevelop problem"
date: 2004-11-26
forum: General Help
---

### Post by novaburst on 2004-11-26
I tried to install MonoDevelop last night. I followed the information given in the FAQs. It seemed to install fine from Synaptic, but here is what happened when I tried to run it.

I am using Warty, by the way.

I went to the /usr/lib/MonoDevelop/bin directory and typed ./MonoDevelop.exe
It said Permission Denied.

So I typed sudo -s and then tried again. It said the same thing.

I tried to make sure I installed all the libs and everything I needed for it.

Does anyone have any suggestions? I would really like to start coding Gnome apps with this.

---

### Post by Juergen on 2004-11-26
Somewhere in the kernel-docs you can read how to register *.exe as executables, maybe you want to do this.

As a test you could do 'mono MonoDevelop.exe' but usually you should have a script /usr/bin/monodevelop. So just type 'monodevelop', it's in your path.

And there should be an entry in you menu Applications/Development...

---

### Post by novaburst on 2004-11-26
You were right, after reboot, I noticed there were a couple entries under Applications. I tried this and saw the MonoDevelop splash screen and then nothing happened. I tried it from the command line and it was giving me some kind of exception error. So I did a reinstall and tried again and bingo, it finally came up for me.

Thanks for the help!

---

