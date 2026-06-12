---
title: "Frustrating errors with libraries since upgrading to Gutsy."
date: 2007-11-25
forum: General Help
---

### Post by Winawer on 2007-11-25
Hello,

I'm at my wit's end here.  When I used the upgrade manager to upgrade to Gutsy, the upgrade failed halfway through, complaining about a number of libraries and undefined symbols.  I'm sorry, I don't have the exact list here, but I eventually got everything to work (as it were) by following the advice in this post:  [https://answers.launchpad.net/ubuntu/+question/15384]("https://answers.launchpad.net/ubuntu/+question/15384")

Ever since then, though, I've been having sporadic problems with programs failing to open or causing me problems.  For example, VLC complains that it can't find the wxwidgets plugin (though the .so file it refers to is where it is supposed to be), and now I can't open a whole host of programs.  Random examples include:  Add/Remove Programs, Synaptic, Gimp, Gnumeric, and so on.  Started from the command line, the programs fail with this message:

```
audacity: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gimp: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gnumeric: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl

```

etc.  From poking around on google, I discovered that dpkg -S should tell me where this file came from, and when I did dpkg-S /usr/lib/libgdk-x11-2.0.so.0, I got 

```
winawer@winawer-desktop:~$ dpkg -S /usr/lib/libgdk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgdk-x11-2.0.so.0
```

I tried apt-get install --reinstall libgtk-x11-2.0, but that hasn't fixed the problem, and I don't know what to do. :confused: Can anyone help me?

EDIT:  For further information, I'm using amd64 gutsy on an Core 2 Duo system.

---

### Post by Winawer on 2007-11-25
Can **anyone** help me?  This is causing me a real headache here, and I have no idea what to do about it.

---

### Post by -grubby on 2007-11-25
I'm not sure if it would just be easier to do a clean install, your system sounds like it got borked. **Remember to back up your files!**

---

### Post by Winawer on 2007-11-25
Gah - that would be a real pain, since backing up everything that I would like to save would require more space than I have.  Any other ideas?  No gurus out there who have any idea how to help me?

---

### Post by dougfractal on 2008-02-20
I've just had a similar problem when testing openoffice2.4
> /opt/openoffice.org2.4/program/soffice.bin: symbol lookup error: 
/usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl

my fix was to download feisty version and install this way.
Only just done it and am unaware of any othe probs

sudo dpkg -i libgtk2.0-0_2.10.11-0ubuntu3_i386.deb
sudo dpkg -i libpango1.0-0_1.16.2-0ubuntu1_i386.deb


openoffice.org2.4 now runs

edit:
massive dependency prob.

I had to copy the working files to a safe place
reinstall the original gusty debs
with dpkg as i was in "apt-get -f install" only option!
overwrite the gusty libs and add the symlinks

cp /home/doug/libgtk-x11-2.0.so.0.1000.11 ./
cp /home/doug/libpangocairo-1.0.so.0.1600.2 ./
ln -sf libgtk-x11-2.0.so.0.1000.11 libgtk-x11-2.0.so.0 
ln -sf libpangocairo-1.0.so.0.1600.2 libpangocairo-1.0.so.0


fingers crossed



DO** NOT **FOLLOW THIS
As I had to repair all the changes

---

