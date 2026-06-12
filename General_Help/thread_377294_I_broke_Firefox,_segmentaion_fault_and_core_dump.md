---
title: "I broke Firefox, segmentaion fault and core dump"
date: 2007-03-05
forum: General Help
---

### Post by threethirty on 2007-03-05
I recently updated FireFox, and now it wont run.  Here is the terminal output...

```
three@Raptor:~$ firefox
/usr/lib/firefox/firefox-bin: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                 AllPeers initiated successfully
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Segmentation fault (core dumped)
three@Raptor:~$ 

```

it also tries to restore the last session (that's when it crashes) 

any ideas

---

### Post by 8086 on 2007-03-08
Well, since you know that Firefox crashes when trying to restore the last session, why don't you try *not* restoring the last session?

Happens all the time for me, I do not know whether it's Firefox' fault or some plugin, but I suspect that the Java VM is to blame most of the time. It has been real buggy the last 6 months. Even Azureus crashes with a Java segfault.

---

### Post by threethirty on 2007-03-15
I'd love to but it crashes before I can choose

---

### Post by aranbanjo on 2007-03-15
U2 allPeers extension ;) 

```
firefox -safe-mode
```

that's it

---

### Post by asdir on 2007-04-13
From [Beanpicks]("http://www.arunma.com/category/allpeers-crashes-firefox/"):

After installing AllPeers and using it for a few days, I had my firefox crashed giving me a core dump.

When i tried to open my firefox from my terminal, i got this.

arun@arun-desktop:~$ firefox
&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;
AllPeers initiated successfully
&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;
Segmentation fault (core dumped)

Now, will tell you how i solved this issue..

Type
arun@arun-desktop:~$ firefox -safe-mode

You will have a dialog giving a few options.

Do not load your plugins. And once your firefox is up, uninstall or disable All Peers. All Peers knows that there is a bug in there and they are already working on it.

For windows users, get inside the Mozilla Firefox folder and there you can see firefox.exe. Then stay in the Firefox folder and issue the above commands. I dont use Windows. So, if this fix did work, please do leave a comment.

---

### Post by Einheit on 2007-06-17
Thanks for the quick fix. What made this odd to diagnose was that it didn't happen immediately after installing AllPeers.

---

