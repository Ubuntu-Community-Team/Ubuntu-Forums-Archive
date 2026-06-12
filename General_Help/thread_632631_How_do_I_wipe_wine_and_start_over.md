---
title: "How do I wipe wine and start over?"
date: 2007-12-05
forum: General Help
---

### Post by FoxHappy on 2007-12-05
I tried unstalling and then reinstalling through the synap package manager but everything was still there, so I tried clearing it now it won't come back.

How can I just wipe everything with wine and start over with it?

---

### Post by kebes on 2007-12-05
> **FoxHappy said:**
> I tried unstalling and then reinstalling through the synap package manager but everything was still there, so I tried clearing it now it won't come back.

How can I just wipe everything with wine and start over with it?

Uninstall Wine using the Synaptic Package Manger (as you did before). Then, delete the hidden directory called ".wine" that is in your home folder. (If you want to be safe, just move or rename that hidden folder.)

In a terminal you could do this by going:
```
cd ~
mv .wine tmp/
```
(The first command, "cd ~", just changes directory into your home folder. The second command moves the entire folder ".wine" into the folder "tmp/" that you probably have in your home folder.)

With that directory gone, all your wine settings and any Windows applications you installed in Wine will be gone. Then reinstall Wine using Synaptic (which will recreate that directory).

---

### Post by oeolycus on 2007-12-05
What's the reasoning, if you don't mind me asking?

You could try:
```
aptitude purge wine
```
If you installed from synaptic originally. (all of this can be done through synaptic too)

---

### Post by FoxHappy on 2007-12-05
> **kebes said:**
> Uninstall Wine using the Synaptic Package Manger (as you did before). Then, delete the hidden directory called ".wine" that is in your home folder. (If you want to be safe, just move or rename that hidden folder.)

In a terminal you could do this by going:
```
cd ~
mv .wine tmp/
```
(The first command, "cd ~", just changes directory into your home folder. The second command moves the entire folder ".wine" into the folder "tmp/" that you probably have in your home folder.)

With that directory gone, all your wine settings and any Windows applications you installed in Wine will be gone. Then reinstall Wine using Synaptic (which will recreate that directory).

That seems to have done the trick, thanks. For some reason also all my old wine stuff seems to have shoved itself under Applications -> Other. Nothing under that menu works, can I just delete it from the menu or is there something else I should do?


> **oeolycus said:**
> What's the reasoning, if you don't mind me asking?

You could try:
```
aptitude purge wine
```
If you installed from synaptic originally. (all of this can be done through synaptic too)

Long story short I was trying to get internet explorer to run on wine. Naturally being a M$ product it not only installed a non working IE, but also outlook express and put a buncha crap all over my virtual C drive, and that's just the kind of BS that I switched to linux to get away from. So I tried fixing by my amateur self, and it all kinda went downhill from there.

---

### Post by Anduu on 2007-12-05
> **oeolycus said:**
> What's the reasoning, if you don't mind me asking?

You could try:
```
aptitude purge wine
```
If you installed from synaptic originally. (all of this can be done through synaptic too)

Typically custom configs/files added after the installation won't get removed...the only way to be sure of a clean reinstall is to delete them manually.

---

### Post by ericesque on 2007-12-06
I accidently updated DirectX at the end of a game install.  This is the process I used to remove wine and reinstall it.  Problem was that after I reinstalled wine applications would act like they were installing, but no files would be copied to the virtual c:

it was at that point I gave up. haha!

---

### Post by kebes on 2007-12-06
> **FoxHappy said:**
> Nothing under that menu works, can I just delete it from the menu or is there something else I should do?

Yes, you can just remove those dead menu entries. (I guess when Wine uninstalls it doesn't know to remove those links that were added.)

---

