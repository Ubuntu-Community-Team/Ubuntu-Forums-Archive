---
title: "Ubuntun will not allow Unity 3d (12.04)"
date: 2013-01-10
forum: General Help
---

### Post by Templar00 on 2013-01-10
Hi Guys,

I'm having a little trouble with my laptop. I've been running Ubuntu since I got it 3.5 years ago, and 12.04 since it came out. Up until 2 days ago it was all fine, then when trying to do a standard update it hit a bump. There were some package problems that I traced to not having enough space. It caused some error messages and Unity 3d would not start. I've managed to reinstall those packages (linux-headers-generic 3.2.0-36.57) but still Unity 3d will not work. 

Any ideas? I'm not great in the terminal (I can cut and paste as good as the next man: but that's about all) and I don't know how to find the problem, or how to fix it. Hence asking/begging for your help!

I'm running a Toshiba Satellite A200 with 12.04. 

Cheers

---

### Post by cottfcfan on 2013-01-10
Make sure you have not got any broken packages in synaptic.
If you have run:
```
sudo apt-get -f install
```
It would also be advisable to clear out your redundant kernels, Ubuntu Tweak is a good tool for that, then update, upgrade & reboot.

---

### Post by Templar00 on 2013-01-10
Thanks - I've checked for broken packages and there are none. I've also tried the -f install command, and no joy there either. I'll give Ubuntu tweak a go though. Will let you know the result.

---

### Post by Templar00 on 2013-01-11
OK, so I used Ubuntu Tweak to clear out old Kernels, rebooted and...

No Unity.

Not 3d, not 2d, not even the launcher.

I've spent the last 6 hours with my HTC Desire trying to find out how to fix this, I've managed to upgrade to 12.10, but still no Unity. I'm back on Gnome Classic for now (ugh) because I cannot for the life of me get Unity back.

Any ideas? I'm completely stumped - I'm not great with tinkering with these machines, I'm happy to get them set up and leave them in peace normally, but that does leave me out to sea when things like this happen.

HELP!!

---

### Post by John_Swing on 2013-01-11
Hello,

You can try :

```
 sudo apt-get install --reinstall ubuntu-desktop
```

and then

```
 sudo apt-get install --reinstall unity 
```

I used this when I had a broken unity and it worked for me.

John.

---

### Post by Templar00 on 2013-01-12
Hi John,

Thanks for the advice, but it hasn't worked for me. I have just installed 12.10, but still nothing. I managed to get Gnome working, so at least I can access the internets on a screen more than 2 inches across, but I'd prefer to get Unity working again.

---

