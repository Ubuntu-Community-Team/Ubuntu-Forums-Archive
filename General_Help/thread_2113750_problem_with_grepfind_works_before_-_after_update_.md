---
title: "problem with grep/find works before - after update - problem"
date: 2013-02-08
forum: General Help
---

### Post by rnerwein on 2013-02-08
hi
i think that's a tread for the devolpment. i don't no why. my problem is that is was this command 100 of times and it still works like it's defined.
but i run it again (got about - i think 3 updates in the last 4 days). now when i run this command in my home directory "~" i always get the ouput:
grep: Ungültige Option -- »&#65533;«
Aufruf: grep [OPTION]&#8230; MUSTER [DATEI]&#8230;
Rufen Sie »grep --help« auf, um weitere Informationen zu erhalten.
i try to translate it: grep: unknow option (that's a lie)
--> look at the uptput !
i now how to call grep and let us bet it's a mo****** about your .gfs (by the side this hassle me in some more situations)
the command i showned works in every directory - without my home :-((   help.
oh yes - i tryed to run the command as super-user --> id -a gives me when i run " su -": uid=0(root) gid=0(root) Gruppen=0(root)
when i run "sudo /bin/bash": -->uid=0(root) gid=0(root) Gruppen=0(root) (the same)
this is a big problem for me - i am no "mouse freak" - please think about your implemention of your fu*** .gfs. when the problem is
between my ears (what i don't belive) give me an anserwer please.
 grep -inH 'find_anithing' `find . -type f`
running with id: uid=0(root) gid=0(root) Gruppen=0(root)
: find: "./.gvfs": Keine Berechtigung -> no permission ???
grep: Ungültige Option -- »&#65533;«
Aufruf: grep [OPTION]&#8230; MUSTER [DATEI]&#8230;
Rufen Sie »grep --help« auf, um weitere Informationen zu erhalten.
as a hint: i think the problem is in the commands - but i cant't find the return-code why.
cheers

---

### Post by schragge on 2013-02-08
Please care to elaborate with some examples of what is wrong.

---

### Post by rnerwein on 2013-02-08
> **schragge said:**
> Please care to elaborate with some examples of what is wrong.
hi guy
that's a nice answer: Please care to elaborate with some examples of what is wrong.
but i think i am to stupid to understand what you mean with your post. that's not a example it is reality.
cheers

---

### Post by schragge on 2013-02-08
> **rnerwein said:**
> grep -inH 'find_anithing' `find . -type f`Easy, man (or should I say "sachte" :)?). Look at the time of my post then you understand what I meant. Anyway, what ```
grep -inHr -e 'find_anything' .
``` gives you? I suppose it's not *grep*'s fault. Something in the output of *find* makes *grep* think it's an option, and not a file name. I think that you have a file somewhere in your home directory named, say [COLOR=green]*Grönemeyer -Ö.mp3*[/COLOR], i.e. having a space-dash sequence in its name. Try
```
grep -inH -e 'find_anything' -- `find . type f`
```To find the "offending" file, try ```
find -name '* -*'
``` By the way, invoking *find* from *grep*'s command line as you did can give weird results if you have some files with unusual characters in their names. Better use either
```

find some/dir -type f -print0 | xargs -0 grep -inHe 'find_anything' --

```or
```

find some/dir -type f -exec grep -inHe 'find_anything' -- {} +

```
Alternatively, you can invoke *grep* with the -r option as I did above. It's a GNU extension.

---

### Post by rnerwein on 2013-02-14
> **schragge said:**
> Easy, man (or should I say "sachte" :)?). Look at the time of my post then you understand what I meant. Anyway, what ```
grep -inHr -e 'find_anything' .
``` gives you? I suppose it's not *grep*'s fault. Something in the output of *find* makes *grep* think it's an option, and not a file name. I think that you have a file somewhere in your home directory named, say [COLOR=green]*Grönemeyer -Ö.mp3*[/COLOR], i.e. having a space-dash sequence in its name. Try
```
grep -inH -e 'find_anything' -- `find . type f`
```To find the "offending" file, try ```
find -name '* -*'
``` By the way, invoking *find* from *grep*'s command line as you did can give weird results if you have some files with unusual characters in their names. Better use either
```

find some/dir -type f -print0 | xargs -0 grep -inHe 'find_anything' --

```or
```

find some/dir -type f -exec grep -inHe 'find_anything' -- {} \+

```Alternatively, you can invoke *grep* with the -r option as I did above. It's a GNU extension.
hi sragge
thanks for your reply - you are online just now - but:
the grep and find combinations results in:
first: find: "./.gvfs": Keine Berechtigung (by the side - i am running this as a super user !)
thats the output of different combinations of grep and find:

grep: lseek fehlgeschlagen: Nicht erlaubter Seek
grep: &#3619;&#3623;&#3617;&#3648;&#3614;&#3621;&#3591;: Datei oder Verzeichnis nicht gefunden
grep: &#3648;&#3614;&#3639;&#3656;&#3629;&#3619;&#3633;&#3585;.&#3648;&#3614;&#3639;&#3656;&#3629;&#3594;&#3637;&#3623;&#3636;&#3605;.mp3: Datei oder Verzeichnis nicht gefunden
grep: ./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629;: Datei oder Verzeichnis nicht gefunden
grep: &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3: Datei oder Verzeichnis nicht gefunden
grep: ./Musik/brennen/&#3648;&#3614;&#3621;&#3591;&#3609;&#3634;&#3591;&#3615;&#3657;&#3634;: Datei oder Verzeichnis nicht gefunden
grep: lseek fehlgeschlagen: Nicht erlaubter Seek
grep: iJigg.com.mp3: Datei oder Verzeichnis nicht gefunden
grep: ./Musik/brennen/02-&#3652;&#3617;&#3656;&#3627;&#3621;&#3656;&#3629;&#3649;&#3605;&#3656;&#3619;&#3633;&#3585;&#3592;&#3619;&#3636;&#3591;: Datei oder Verzeichnis nicht gefunden
what i learned again  - told me every time my students - a computer is a high speed idiot !.
what everybody (me too) is to think about exception handling !.
cheers 
and have fun (oh thats thai language which cause the problem)

---

### Post by schragge on 2013-02-14
The problem is not so the Thai language by itself as the spaces. For example, > **rnerwein said:**
> grep: ./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629;: Datei oder Verzeichnis nicht gefunden
grep: &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3: Datei oder Verzeichnis nicht gefunden This means that you have a file named
[color=green]./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3[/color]
```
grep anything `find -name '&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3'`
```
is the same as
```

grep anything ./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3

``` Do you see the problem now?

---

### Post by rnerwein on 2013-02-14
> **schragge said:**
> The problem is not so the Thai language by itself as the spaces. For example,  This means that you have a file named
[COLOR=green]./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3[/COLOR]
```
grep anything `find -name '&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3'`
```is the same as
```

grep anything ./Musik/brennen/&#3588;&#3623;&#3634;&#3617;&#3629;&#3656;&#3629;&#3609;&#3649;&#3629; &#3610;&#3629;&#3618;&#3614;&#3637;&#3594;&#3648;&#3617;&#3588;&#3648;&#3585;&#3629;&#3619;&#3660;.mp3

``` Do you see the problem now?
hi sragge
oh yeah i see the problem - see my private message about "execption handling"
cheers
;)

---

### Post by steeldriver on 2013-02-14
> **rnerwein said:**
> 
the grep and find combinations results in:
first: find: "./.gvfs": Keine Berechtigung (by the side - i am running this as a super user !)


AFAIK, the .gvfs user mount point  has always been created [FONT=Courier New]drwx------[/FONT] (it's a feature of the fuse filesystem, I think) so they are not readable by anyone other than the owner. Running 'find' as super user does not circumvent that.

[https://bugzilla.gnome.org/show_bug.cgi?id=534284](https://bugzilla.gnome.org/show_bug.cgi?id=534284)

---

### Post by rnerwein on 2013-02-14
> **steeldriver said:**
> AFAIK, the .gvfs user mount point  has always been created [FONT=Courier New]drwx------[/FONT] (it's a feature of the fuse filesystem, I think) so they are not readable by anyone other than the owner. Running 'find' as super user does not circumvent that.

[https://bugzilla.gnome.org/show_bug.cgi?id=534284](https://bugzilla.gnome.org/show_bug.cgi?id=534284)
hi steeldriver
i know that - but have a look here:

hi that's the output of: ls -la
d?????????  ? ?     ?         ?            ? .gvfs
for me a strange behavior !

that's my grep - combined with find:
grep -inH 'blablu' `find . -type f`

and this command results in:
root@tschang:~ 15:05-> grep -inH 'blablu' `find . -type f`
find: "./.gvfs": Keine Berechtigung (means access denied)
grep: Ungültige Option -- »&#65533;«
in english: grep was called with an illegal option ( for sure not !!!)
this hapen only when the command cross my home-directory.
ah - nobody have the same (and for my scripts it is a big problem) problem ?
Aufruf: grep [OPTION]… MUSTER [DATEI]…
Rufen Sie »grep --help« auf, um weitere Informationen zu erhalten.
root@tschang:~ 15:09-> id -a
uid=0(root) gid=1000(richi) Gruppen=0(root),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),1000(richi)

even the same result (before the UID was set with my own C-program to keep my environment)
root@tschang:/home/richi# grep -inH 'blablu' `find . -type f`
find: "./.gvfs": Keine Berechtigung
grep: Ungültige Option -- »&#65533;« 
Aufruf: grep [OPTION]… MUSTER [DATEI]…
Rufen Sie »grep --help« auf, um weitere Informationen zu erhalten.
root@tschang:/home/richi# id -a
uid=0(root) gid=0(root) Gruppen=0(root),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),1000(richi)

as you see - i run this command with full root-access. there must be some combination of bits in the .gvfs that make the grep or find confuesed .(got a similar problem with an ethernt-driver long time ago - driver got a combination of bit tell him - hey that's a timeout wait 30 seconds :P. 
normaly this post will be a thread - but i know to exclude the .gvfs. but it should be interesting to find the reason. try it in your home and if you ain't get the same result as i than i think it is a very interesting problem which can hapen ervery where.
ciao

---

### Post by schragge on 2013-02-14
Again, the grep error [COLOR=red]grep: Ungültige Option[/COLOR] has nothing to do with *.gvfs/*

Try this
```

touch '/tmp/x -Q'
grep -inH 'blabla' `find /tmp -type f`

```
You're mixing three different, completely unrelated issues here.
[LIST=1]
[*]*grep* choking on unquoted file names with spaces and other unusual characters. 
[*]*~/.gvfs* not being read accessible even by root. It's not a bug, see [thread=791693]this thread[/thread]. 
[*]*ls -l ~/.gvfs* giving question marks. This is LP bug #[lpbug]212789[/lpbug]. 
[/LIST]

---

