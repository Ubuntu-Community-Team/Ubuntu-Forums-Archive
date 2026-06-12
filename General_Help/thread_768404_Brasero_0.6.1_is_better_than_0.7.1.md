---
title: "Brasero 0.6.1 is better than 0.7.1?"
date: 2008-04-26
forum: General Help
---

### Post by chunchengch on 2008-04-26
In gutsy, I used default Brasero 0.6.1 to blank or to burn disc without any problem, one day, I downloaded Brasero 0.7.1 from getdeb, I supposed it was newer, so it will be better than 0.6.1, but I was wrong, then I switched back to the default one.

In hardy, I find the default is Brasero 0.7.1, and unfortunately, it is still unusable, I can not burn or blank disk, while the same disc can be easily blanked and the same ISO image can be easily burnt in Nero Linux, I am really disappointed in Brasero 0.7.1.

---

### Post by olskar on 2008-04-26
I agree with you sadly..

---

### Post by FredB on 2008-04-26
Well I can burn anything I want with brasero 0.7.1... Not a single problem here. Am I the only one ?

---

### Post by chunchengch on 2008-04-28
Brasero 0.6.1 is not allowed to be installed in Hardy because of dependency problem, so I give Brasero 0.7.1 another try, I use a new blank DVD+R disc to burn ubuntu-8.04-desktop-i386.iso , well, Brasero 0.7.1 detects the blank disc and confirms it can be recorded (screenshopt 1), but then it pops out a stupid error message "Insufficient space on media" (screenshopt 2), I check the Session log (screenshopt 3) but don't know what the problem is?

Can anyone fix the problem? thanks a lot!


screenshopt 1  
[ATTACH]67670[/ATTACH] 

screenshopt 2 
[ATTACH]67671[/ATTACH]

screenshopt 3
[ATTACH]67672[/ATTACH]

---

### Post by pelle.k on 2008-05-14
> Can anyone fix the problem? thanks a lot!
Sure can. I think, anyway ;)
This is a .deb repackaged (nothing else) in 8.04 "hardy heron", from the original 7.10 "gutsy gibbon" deb source package. Works for me anyway! Hope you'll find it useful.

**[http://download.tuxfamily.org/pandora/temp/brasero_0.6.1-0ubuntu1hardy1_i386.deb](http://download.tuxfamily.org/pandora/temp/brasero_0.6.1-0ubuntu1hardy1_i386.deb)**
Install it with
```
 sudo dpkg -i brasero_0.6.1-0ubuntu1hardy1_i386.deb
```
**You need to "hold" the package from getting updated as well**
```
echo "brasero hold" | sudo dpkg --set-selections

```
if you need to remove the "hold" in the future
```
echo "brasero install" | sudo dpkg --set-selections

```






[COLOR="orange"]This is how i did it (if you want to compile it yourself);
1. download the source package from [http://packages.ubuntu.com/gutsy/brasero](http://packages.ubuntu.com/gutsy/brasero)
```
dget http://archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_0.6.1-0ubuntu1.dsc
```
2. unpack it
```
dpkg-source -x brasero_0.6.1-0ubuntu1.dsc
```
3. bump the changelog, and give it a new revision (0ubuntu1hardy1) using nano (ctrl+x to save and quit).
```
cd brasero-0.6.1/debian/; dch -i
```
4. build it
```
cd ..; sudo apt-get build-dep brasero; sudo dpkg-buildpackage -rfakeroot
```

I used pbuilder instead of dpkg-buildpackage, but that's another story. You may need some development tools installed if you want to compile yourself though.[/COLOR]

---

### Post by chunchengch on 2008-05-15
pelle.k,

Thanks for your information, but I don't want to use Brasero for the time being, because Nero Linux works much better than Brasero.

---

### Post by kosmo on 2008-05-16
I think this is some kernel problem:confused:.

---

### Post by kpkeerthi on 2008-05-16
Report this as bug here [http://bugzilla.gnome.org/buglist.cgi?product=brasero&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=UNCONFIRMED&version=0.7.1](http://bugzilla.gnome.org/buglist.cgi?product=brasero&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=UNCONFIRMED&version=0.7.1)

The devs are pretty responsive.

---

### Post by pelle.k on 2008-05-16
I have the same problem using brasero 0.7.1 in mandriva 2008.1, so this is a brasero bug, it's nothing wrong with the packaging (ubuntu).

BTW, this is really OT but chunchengch, can i please ask you what gtk theme you are using? (looks really nice) :)

---

### Post by chunchengch on 2008-05-16
> **pelle.k said:**
> ... what gtk theme you are using? (looks really nice) :)

That is Azel, one of the themes I like the most, you can find it here [http://www.gnome-look.org/content/show.php/Azel?content=76898](http://www.gnome-look.org/content/show.php/Azel?content=76898)

---

### Post by pelle.k on 2008-05-16
Ah... Thanks!

---

