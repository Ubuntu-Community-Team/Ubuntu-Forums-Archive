---
title: "How do you create a torrent file w/default Gnome client ?"
date: 2007-07-24
forum: General Help
---

### Post by Sweet Spot on 2007-07-24
I'm using BitTorrent to download stuff just fine. But do I need to download any other binaries in order to create a .torrent file ?  I really want to get my ratio up on Oink's, so this would help. I'd really like to do it only w/the default Gnome Bittorrent client, please. GUI method not necessary, but if I'm going to use the terminal, can someone please refer me to either a copy/paste for exact instructions or a tutorial somewhere ?

Doug

---

### Post by Sweet Spot on 2007-07-25
Bump.

---

### Post by Sweet Spot on 2007-08-09
I really still need the answer to this, if anybody can please help I'd really appreciate it.

---

### Post by apetresc on 2007-08-09
You can use "btmakemetafile", one of the core files for BitTorrent. Type ```
man btmakemetafile
``` at a terminal to see how to use it.

You don't need to install any extra software to do this; if you have the Gnome client, you have this.

---

### Post by Sweet Spot on 2007-08-09
Thanks. So if I'm understanding the manual instructions correctly, I have to type btmakefile "location of file"
         btmakefile "announce address"

Is this correct, or do I have the formatting wrong ? I'll give it a shot in a lil while. 

doug

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> Thanks. So if I'm understanding the manual instructions correctly, I have to type btmakefile "location of file"
         btmakefile "announce address"

Is this correct, or do I have the formatting wrong ? I'll give it a shot in a lil while. 

doug
Close. You only type btmakemetafile once, firstly; you just give it two or more parameters at once. Also, you put the announce address FIRST, *then* the file path. Thirdly, it is "btmakemetafile" not "btmakefile". And lastly, you can optionally specify some extra options that are documented in the manpage, but those are optional.

So a working call might look like: ```
btmakemetafile http://url.to.tracker.com/announce /path/to/file
```

---

### Post by Sweet Spot on 2007-08-09
Sweet. Thank you so much. Going to try in just a minute. This seems easier than I thought it was going to be ! *crosses nubby lil' fingers*

doug

---

### Post by Sweet Spot on 2007-08-09
Ok, tried it and got this:

> bash: syntax error near unexpected token `('
Here's what I tried to upload (I'm going to mask certain things )

```
btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/**********/Artist - Album (Vinyl LP & B-Sides)
```I copied the directory address straight from Nautilus, so don't see why there should be any errors. What do you make of that ?

Do you think it's because I'm attempting to upload a directory and not files directly ?



Edit:  Ok, tried it again, this time removing the ( )  but this time I get >  
error: Too many args - 0 max.

With this: ```
btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/********/Radiohead  Hail To The Thief
```

Reason I'm upping this btw is because not everybody has a turntable, and would like to hear the vinyl version. (well, people on a specific forum)

---

### Post by apetresc on 2007-08-09
The problem is that you are not escaping the spaces properly. Notice how you have spaces in the filename -- how is the program supposed to know whether it is one filename or a lot of files with smaller filenames? It can't -- you need to tell it :)

That is easily done. Before each space, simply add the "\" character (make sure it's a forward slash, not a backslash, or it will think you're giving it a directory path). Then it'll know that the space is part of the filename, and take it all as one. Good luck!

---

### Post by Sweet Spot on 2007-08-09
Ugh. It's always something. I'm being told that I should install Sam:

>  [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) /home/*****/Radiohead \ Hail To The Thief /Radiohead\  Hail To The Thief Vinyl LP & B Sides
[1] 8100
bash: [http://tpb.tracker.thepiratebay.org/announce:](http://tpb.tracker.thepiratebay.org/announce:) No such file or directory
The program 'B' is currently not installed.  You can install it by typing:
sudo apt-get install sam
Make sure you have the 'universe' component enabled
bash: B: command not found
[1]+  Exit 127                [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) /home/********/Radiohead \ Hail To The Thief /Radiohead\  Hail To The Thief Vinyl LP
*******@*******-desktop:~$ sudo apt-get install sam



So  naturally, I installed Sam and got this:

> /Radiohead\  Hail To The Thief Vinyl LP & B Sides
[1] 8166
bash: [http://tpb.tracker.thepiratebay.org/announce:](http://tpb.tracker.thepiratebay.org/announce:) No such file or directory
B: No pipe "/tmp/.sam.*******.:0" to sam.
[1]+  Exit 127                [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) /home/*******/Radiohead \ Hail To The Thief /Radiohead\  Hail To The Thief Vinyl LP

---

### Post by apetresc on 2007-08-09
Nono, you did it wrong. You have to escape every single space (and every single round bracket). You want this line:
```
btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/**********/Artist\ -\ Album\ \(Vinyl\ LP\ &\ B-Sides\)
```

What happened is, because you didn't escape right, it thought "B" was a command name (it shouldn't be), which belongs to the package 'sam'. 'sam' actually has nothing to do with this, you can remove it now if you want to.

---

### Post by g2g591 on 2007-08-09
you didn't escape all the spaces.

---

### Post by Sweet Spot on 2007-08-09
DOH !!!! In the process of installing Sam, I think it may have uninstalled other things. Is there a command I can use to see everything that happened in my prior commands ? 

Secondly, if the directory is this: [quote]/home/********/Radiohead  Hail To The Thief /Radiohead  Hail To The Thief Vinyl LP & B Sides[/quote 

Then I should make it this? :/home/********/Radiohead\  Hail To The Thief\ /Radiohead\  Hail\ To\ The\ Thief\ Vinyl\ LP\ &\ B \Sides

? Or do I not put the slash after the first instance of Thief ?*getting confused a bit*

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> DOH !!!! In the process of installing Sam, I think it may have uninstalled other things. Is there a command I can use to see everything that happened in my prior commands ? 
It shouldn't have. "sam" is just a text editor.

> **Sweet Spot said:**
> Secondly, if the directory is this: > /home/********/Radiohead  Hail To The Thief /Radiohead  Hail To The Thief Vinyl LP & B Sides

Then I should make it this? :/home/********/Radiohead\  Hail To The Thief\ /Radiohead\  Hail\ To\ The\ Thief\ Vinyl\ LP\ &\ B \Sides

? Or do I not put the slash after the first instance of Thief ?*getting confused a bit*
No, you have to put a "\" before *every single space and/or bracket and or ampersand (&) and/or any other character that has a significance to the shell*. You should make it: ```
/home/********/Radiohead\Hail\ To\ The\ Thief/Radiohead\ Hail\ To\ The\ Thief\ Vinyl\ LP\ \&\ B\ Sides
```

EDIT: Sorry, fixed a bug in my own escaping. That's a lot of spaces in that filename :o

---

### Post by Sweet Spot on 2007-08-09
I'm so sorry for this hassle, but really do appreciate your help in this matter. Look, I cut/pasted the files in the first directory and deleted the other, so now the main directory is:

```
/home/*******/Radiohead  Hail To The Thief 
```which should translate to: /home/*******/Radiohead  \Hail \To \The \Thief

Correct ? 

I've tried several variations now, and this is the latest I get: > btmakemetafile [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) /home/***/Radiohead\ Hail\ To\ The\ Thief 
Traceback (most recent call last):
  File "/usr/bin/btmakemetafile", line 154, in <module>
    comment = config['comment'], target = config['target'])
  File "/usr/bin/btmakemetafile", line 45, in make_meta_file
    info = makeinfo(file, piece_length, flag, progress, progress_percent)
  File "/usr/bin/btmakemetafile", line 107, in makeinfo
    size = getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/**/http:/tpb.tracker.thepiratebay.org/announce'


---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> I'm so sorry for this hassle, but really do appreciate your help in this matter. Look, I cut/pasted the files in the first directory and deleted the other, so now the main directory is:

```
/home/*******/Radiohead  Hail To The Thief 
```which should translate to: /home/*******/Radiohead  \Hail \To \The \Thief

Correct ? 

No. The slashes come before the character they escape (the space in this case). It translates to:```
/home/*******/Radiohead\ \ Hail\ To\ The\ Thief
```
Did you intentionally have TWO consecutive spaces in that filename (after Radiohead)? If so, you need to add a slash like I just did. I didn't do it in the one above because I didn't realize you had two consecutive spaces.

---

### Post by Sweet Spot on 2007-08-09
I'm about to give up here. I'm doing this right now: ](*,)

No, I didn't put an extra space in there. I'm copying directly from the directory address which is in Nautilus. I'm still getting the error:

> btmakemetafile [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) /home/******/Radiohead\ \ Hail\ To\ The\ Thief 
Traceback (most recent call last):
  File "/usr/bin/btmakemetafile", line 154, in <module>
    comment = config['comment'], target = config['target'])
  File "/usr/bin/btmakemetafile", line 45, in make_meta_file
    info = makeinfo(file, piece_length, flag, progress, progress_percent)
  File "/usr/bin/btmakemetafile", line 107, in makeinfo
    size = getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/*****/http:/tpb.tracker.thepiratebay.org/announce'


I've now renamed the folder so it only has one space between Radiohead and Hail. still the same crap though.

---

### Post by apetresc on 2007-08-09
Weird. What is the output of ```
ls ~
```
(That's a tilde ~ not a minus sign -)

---

### Post by Sweet Spot on 2007-08-09
> **AdrianP said:**
> Weird. What is the output of ```
ls ~
```(That's a tilde ~ not a minus sign -)

Part of the output (would rather not display all) is: > Radiohead Hail To The Thief 

As I said above in my edit, I renamed the folder to have only one space between Radiohead and Hail. I'm not sure of what's going on here.

---

### Post by apetresc on 2007-08-09
Oh! Well if you've edited it to have only one space now, then it is just:
```
btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/*******/Radiohead\ Hail\ To\ The\ Thief
```

I didn't see your edit the first time around.

BTW, I assume you're not actually writing "*****" for your user directory :P

---

### Post by Sweet Spot on 2007-08-09
> **AdrianP said:**
> Oh! Well if you've edited it to have only one space now, then it is just:
```
btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/*******/Radiohead\ Hail\ To\ The\ Thief
```I didn't see your edit the first time around.

BTW, I assume you're not actually writing "*****" for your user directory :P

I actually compensated in the command line for the deleted space, but it's still the same. Even when I CD to the directory, it tels me that it doesn't exist. Unless I'm CD'ng wrong of course. 

I did exactly this: (but with my username of course) ```
 btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/********/Radiohead\ Hail\ To\ The\ Thief
Traceback (most recent call last):
  File "/usr/bin/btmakemetafile", line 154, in <module>
    comment = config['comment'], target = config['target'])
  File "/usr/bin/btmakemetafile", line 45, in make_meta_file
    info = makeinfo(file, piece_length, flag, progress, progress_percent)
  File "/usr/bin/btmakemetafile", line 107, in makeinfo
    size = getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/********/http:/tpb.tracker.thepiratebay.org/announce'

```

---

### Post by apetresc on 2007-08-09
Hm, judging from the error message, your copy of btmakemetafile seems to want the parameters in the opposite order of mine. Try swapping the two parameters and see what happens.

Everything else is correct, and on my machine that line works perfectly (I just teseted it with a dummy directory named that)

---

### Post by Sweet Spot on 2007-08-09
if only it were that easy, I guess. No dice:

> btmakemetafile /home/*******/Radiohead\ Hail\ To\ The\ Thief [http://tpb.tracker.thepiratebay.org/announce](http://tpb.tracker.thepiratebay.org/announce) 
Traceback (most recent call last):
  File "/usr/bin/btmakemetafile", line 154, in <module>
    comment = config['comment'], target = config['target'])
  File "/usr/bin/btmakemetafile", line 45, in make_meta_file
    info = makeinfo(file, piece_length, flag, progress, progress_percent)
  File "/usr/bin/btmakemetafile", line 107, in makeinfo
    size = getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/*******/Radiohead Hail To The Thief'


Am I cursed ?

---

### Post by apetresc on 2007-08-09
Sorry, I'm fresh out of ideas :( I tried it on my computer and it worked like a charm:
```
adrian@rootbeer:~$ mkdir Radiohead\ Hail\ To\ The\ Thief
adrian@rootbeer:~$ cp wtf1.png Radiohead\ Hail\ To\ The\ Thief
adrian@rootbeer:~$ btmakemetafile http://tpb.tracker.thepiratebay.org/announce /home/adrian/Radiohead\ Hail\ To\ The\ Thief
adrian@rootbeer:~$ ls Radiohead\ Hail\ To\ The\ Thief*
Radiohead Hail To The Thief.torrent

Radiohead Hail To The Thief:
```
As you can see, my .torrent file was created no problem...

Perhaps as a last resort you could install Azureus? It has features for this sort of thing too.

---

### Post by Sweet Spot on 2007-08-09
Wow. This is hardly even fair. How is it that it won't recognize the actual directory ? That is bizarre. I'd really rather not install another program for this. How depressing. I thank you very much for your efforts though. you really tried. 

doug

I even tried:   >  mkdir Radiohead\ Hail\ To\ The\ Thief
*******@********-desktop:~$ cp wtf1.png Radiohead\ Hail\ To\ The\ Thief
cp: cannot stat `wtf1.png': No such file or directory


---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> 
I even tried:

Er, that's not going to work. That line copies the image file "wtf1.png" to the radiohead directory. I did that so that the directory would have something in it to make a torrent *of*. It was just a random file. Unless you have a file in your home directory called wtf1.png, it's not going to work :P

Choose some other random file in your home directory and try it.

What I find interesting is that you were able to create the directory "Radiohead\ Hail\ To\ The\ Thief"... I thought it was already there for you? Or did you do this in some other directory besides your home one?

---

### Post by Sweet Spot on 2007-08-09
It is interesting, I guess. I was able to recreate the directory, and they are sitting next to each other as I'm looking. They're identical.  Would I be able I wonder, to copy the files over to the newly created dir and have it work from there ? Hmm..


edit: Guess not.  :(   What the hell is going on with this thing ? Does anyone else have a clue as to what my problem is ?

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> It is interesting, I guess. I was able to recreate the directory, and they are sitting next to each other as I'm looking. They're identical.  Would I be able I wonder, to copy the files over to the newly created dir and have it work from there ? Hmm..

Hmm, okay, that in itself is a problem -- that should be impossible. There must be some slight difference. This is probably what was causing your problem. You may have some strange sort of metacharacter in there that isn't getting transmitted properly.

Can you show me your "ls ~" output again? Or a screenshot of the two folders?

---

### Post by zachtib on 2007-08-09
as of our new release, Deluge supports torrent creation via an included plugin, it's even got a gui

---

### Post by Sweet Spot on 2007-08-09
> **AdrianP said:**
> Hmm, okay, that in itself is a problem -- that should be impossible. There must be some slight difference. This is probably what was causing your problem. You may have some strange sort of metacharacter in there that isn't getting transmitted properly.

Can you show me your "ls ~" output again? Or a screenshot of the two folders?

It doesn't matter anymore. I deleted the original and now all that exists is the new one that I created. However, I'll try and create another one along side it:  Well, now it WON'T let me, saying that it already exists. which it did before, as well. I swear, I'm not going crazy here. They looked identical. As they should have since I copy/pasted the directory. 

Here's what you asked for btw:  > -desktop:~$ ls ~
1- All Stuff  Desktop  Radiohead Hail To The Thief  Random Text Files

---

### Post by Sweet Spot on 2007-08-09
> **zachtib said:**
> as of our new release, Deluge supports torrent creation via an included plugin, it's even got a gui


Is Deluge native to Gnome ?  And if so, is it something I'd have to compile ? I don't see it in the repos.  And how stable is it ?

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> It doesn't matter anymore. I deleted the original and now all that exists is the new one that I created. However, I'll try and create another one along side it:  Well, now it WON'T let me, saying that it already exists. which it did before, as well. I swear, I'm not going crazy here. They looked identical. As they should have since I copy/pasted the directory. 
That is absolutely *bizarre*. I wish we could recreate that but I guess we can't. Okay, try running the btmakemetafile script again, with both orders of parameters and see what happens.

> Is Deluge native to Gnome ?
I'm not the Deluge developer, but yes, yes it is. More info here: [http://deluge-torrent.org/](http://deluge-torrent.org/)

It appears to be very similar to Ktorrent, which I love.

---

### Post by Sweet Spot on 2007-08-09
?Stupid question. Do I actually have to list what the files are inside of teh Hail To The Thief directory ?

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> ?Stupid question. Do I actually have to list what the files are inside of teh Hail To The Thief directory ?

Nope, just a path to the directory works equally well. It worked for me.

---

### Post by Sweet Spot on 2007-08-09
Wait, I didn't delete it. I put it in the trash. Check this out, I put it back: Hold on a sec, editing the pic

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> Wait, I didn't delete it. I put it in the trash. Check this out, I put it back: Hold on a sec, editing the pic
Whaaaaat the heeeck. That is some black magic there. I have no idea how/why that could happen.

(I already saw the pic ;))

---

### Post by Sweet Spot on 2007-08-09
Tell me about it ! I guess I have more problems than just not being able to upload a torrent. I thought that you weren't able to have file names or directories with the same exact name/case in Linux ? 

I think I AM cursed ! :shock::-#

---

### Post by apetresc on 2007-08-09
> **Sweet Spot said:**
> Tell me about it ! I guess I have more problems than just not being able to upload a torrent. I thought that you weren't able to have file names or directories with the same exact name/case in Linux ?
Correct, it shouldn't be possible :(
```
adrian@rootbeer:~$ mkdir test
adrian@rootbeer:~$ mkdir test
mkdir: cannot create directory `test': File exists
```
I'm at a loss to explain it. Sorry :(

---

### Post by Sweet Spot on 2007-08-09
Tried both variations. Got nada, zip, zilch, the big ZERO.

---

### Post by Sweet Spot on 2007-08-09
I have installed Deluge, and it seems to be a very nice program. I have actually managed to create a torrent file, but I'm not sure if it's actually seeding. I don't see any activity yet. All the necessary ports are open, and the announce is listed as "OK" but no activity. Then again, the people who said they'd be downloading haven't said whether or not they've tried yet. 

It's better than nothing though.

---

