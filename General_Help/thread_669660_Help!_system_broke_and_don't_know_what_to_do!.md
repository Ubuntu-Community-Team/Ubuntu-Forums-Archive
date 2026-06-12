---
title: "Help! system broke and don't know what to do!"
date: 2008-01-16
forum: General Help
---

### Post by toMeloos on 2008-01-16
Don't know what happened but my system seems broke. It's up and running and I can use the desktop environment but commands from the terminal don't work anymore. I don't know what could have caused it but I cannot update using apt, use nano, etc.

Running a 'sudo apt-get upgrade' results in the following error (sorry for the Dutch in there):

```

Ophalen:29 http://nl.archive.ubuntu.com gutsy-updates/universe python-avahi 0.6.20-2ubuntu3.1 [29,9kB]
12,1MB opgehaald in 15s (797kB/s)                                              
Extraheren van sjablonen uit pakketten: 100%
Voorconfigureren van pakketten...
/bin/rm: 2: &#65533;&#393;&#1993;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;: not found
/bin/rm: 2: &#65533;&#65533;1&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;N=w&#65533;a&#65533;VSP&#65533;-S&#65533;&#832;[&#65533;&#65533;[ø-&#832;9&#65533;u&#65533;&#65533;&#65533;1&#65533;&#65533;[^&#65533;SQRV&#65533;&#65533;1&#589;A8&#9508;ø‰ÈH^ZY[Ã: &#9532;&#9146;&#9500; °&#9146;&#9508;&#9532;&#9229;
/&#9225;&#9227;&#9532;/&#9148;&#9492;: 2: 1ÒŠˆI@Cù&#9516;ñ&#9618;ÃSQRVW‰Æ‰ßŠŠ8Ø&#9508;FGIù&#9516;í¸_^ZY[Ã¸_^ZY[ÃQSP1À°°1Û³‰áÍ€Y[YÃQSP1À°°1Û³‰áÍ€X[YÃQSP1À°°1Û³‰áÍ€X[YÃQSP1À°°1Û³‰áÍ€Y[YÃRQSP1À°°1Û³
                                                                         ‰áÍ€X[YZÃRQSP1À°°1Û³
             ‰áÍ€X[YZÃQSP1À°°1Û³‰áÍ€X[YÃSQRV1ö¸@èÈþÿÿ=&#9500;‰ÆSQ¸·‰ó¹@Í€Y[‰ð^ZY[Ã/&#9229;&#9226;&#9524;/&#9252;&#9229;&#9474;SQRVWP01ÿ¸2èˆþÿÿ‰Æ=&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-5&#65533;ÈSQR&#65533;&#65533;&#1785;B&#65533;&#832;ZY[=&#65533;&#65533;&#65533;&#65533;tG&#65533;&#65533;f&#65533;f&#65533;F&#65533;F&#65533;&#65533;&#832;&#65533;F
                                                                               SQR&#65533;7&#65533;&#1273;&#65533;&#65533;&#832;ZY[=u&#65533;&#65533;-S&#65533;&#65533;&#832;[&#65533;&#65533;_^ZY[&#65533;SQRVW&#65533;
                                      X&#65533;Á&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;SQR&#65533;&#65533;&#65533;&#65533;&#832;ZY[&#65533;&#65533;SQ&#65533;0&#65533;&#65533;&#65533;&#832;Y[_^ZY[&#65533;: not found
/bin/rm: 2: ELF: not found
/bin/rm: 2: &#65533;&#393;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
/bin/rm: 1: Syntax error: word unexpected (expecting ")")
dpkg: fout bij afhandelen van /var/cache/apt/archives/findutils_4.2.31-1ubuntu2.1_amd64.deb (--unpack):
 subproces rm cleanup gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/findutils_4.2.31-1ubuntu2.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I get a same kind of error when I run a 'sudo nano'. When running a normal 'nano' command I get an error saying 'cannot execute a binary file' (roughly translated from Dutch).

Can anyone tell me what's going on with my system? I don't get it and I'm scared of turning it off because i'm too afraid it won't start properly anymore...

---

### Post by mathisdermaler on 2008-01-16
Obviously a lot of your files are corrupt.  My advice would be to give your system up for lost.  

Buy a new hard drive of the right type for your computer, then turn it off and take out your current hard drive.  Put in the new hard drive and install ubuntu on it fresh.  Then put your old drive back in as a secondary drive, and copy all the files you want to save to the new installation.  After that check your system to try to prevent this from happening again (failing hard disk maybe?)

---

### Post by toMeloos on 2008-01-20
What I don't understand is that I can still run just about anything in the X session that's still running. Only exception so far seems to be synaptic, but that actually runs commands in a terminal. Anything in the terminal doesn't seem to work anymore. This makes me wonder wheater I'm actually facing a lot of corrupt files or if this problem is limited and fixable without reinstalling.

p.s. I'm running Ubuntu Gutsy AMD64 with software raid 1.

---

### Post by fjgaude on 2008-01-20
That error code of 1 coming out points to likely a bad sector on your hard drive. Raid1, eh?

You could try repairing the drives, one at a time from a live CD using this command:

```
sudo e2fsck -C0 -p -f -v /dev/sd[nn]
```

Using whatever your two drives are named.

Trust you know how to use a live CD to repair, access the two drives. You should never use such a command on a mounted drive, BTW.

Let us know how you make out.

---

### Post by toMeloos on 2008-01-22
Booted the alternate installation cd in text installation mode, immediately switched to the console and ran the e2fsck command stated above on all /dev/sd** devices. They all pass the test perfectly. No bad sectors.

System won't boot correctly anymore. Kernel boots but several services can't start because several basic programs (like rm) won't work. Guess I have to reinstall the operating system. Still very curious what could have caused this though!?!

---

### Post by fjgaude on 2008-01-23
Sorry I don't have anymore suggestions...

Good luck, but do let us know how you make out.

---

### Post by toMeloos on 2008-01-23
Couldn't figure it out so I reinstalled the whole system.

---

