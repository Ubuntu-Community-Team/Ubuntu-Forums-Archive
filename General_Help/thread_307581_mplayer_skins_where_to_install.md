---
title: "mplayer skins where to install?"
date: 2006-11-26
forum: General Help
---

### Post by lime4x4 on 2006-11-26
trying to install some new skins for mplayer i installed them in /usr/share/mplayer but i guess ubuntu's version of myplayer doesn't have them there

---

### Post by taurus on 2006-11-26
You can install them in ~/.mplayer/Skin...

---

### Post by kinson on 2007-03-24
I've been having some problems installling mplayer skins too :(

I unpackaged the skin.tar.bz that I downloaded from the mplayer website, and copied the folder to my ./mplayer/skins folder.

```

kinson@ubuntu:~/.mplayer/skins$ ls
iTunes-mini  WMP6
kinson@ubuntu:~/.mplayer/skins$ pwd
/home/kinson/.mplayer/skins

```

But nothing extra shows up in the mplayer skin list? Its the same if I tried copying it to the /usr/local/share/mplayer/skins (or something) directory.

If it makes any difference, I installed mplayer through automatix2.

Any help would be appreciated.

cheers,
Kinson :)

---

### Post by chek2fire on 2007-04-08
i have found a solution for the mplayer skins
first unpack the files here /usr/share/mplayer/skins then make a contact of the folder here
/home/yourname/.mplayer

---

### Post by shirilover on 2007-04-08
Try renaming one of the folder in ~/.mplayer/skins to default.

---

### Post by krussell on 2007-04-08
Hello :-)
Have you tried /usr/local/share/mplayer/Skin ? It worked for mplayer compiled from source, can't say about mplayer installed from ubuntu repository.

---

### Post by kinson on 2007-04-08
I've tried putting them in

/home/kinson/.mplayer/skins/<skin folder name>
and
/usr/local/share/mplayer/Skin/<skin folder name>

and also tried renaming the skin folder to "default", and it didn't work. 

I'm not sure whether the uppercase/lowercase matters here in the "Skin" and "skin" though.

Cheers,
Kinson

---

### Post by iborg1013 on 2007-04-11
try in

/usr/share/mplayer/skins

---

