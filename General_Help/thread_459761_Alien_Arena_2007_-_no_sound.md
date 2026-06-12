---
title: "Alien Arena 2007 - no sound"
date: 2007-05-31
forum: General Help
---

### Post by RudolfMDLT on 2007-05-31
Hi there - I recently downloaded Alien Arena 2007 - an opensource game built on the quike 2 engine.   But there is no sound in the game, and the sound setting is on "Most Compatible".

Everytime I try to change this the game freezez! O, question 2) how can I kill a process in BASH/tty1-6 when   tty7 running X has a fullscreen crashed program?

Thanks,

Rudolf

---

### Post by Sockerdrickan on 2007-06-06
Turn off other apps that uses sound



CTRL+ALT+F6

ps -e |grep alien

you get the id and

kill -9 THATID

---

### Post by trinaryouroboros on 2007-06-18
Seems like a cool free game, downloaded the linux binary and set it up at /usr/lib/games/alienarena2007

Yet, when I ran the game with ./crx I got this:

error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

Since I'm using 64-bit Ubuntu Linux, I just had to go get the XFree86-compat-libs-4.0.3-2 RPM for i386:

[http://centos.osmirror.nl/2.1/final/i386/CentOS/RPMS/XFree86-compat-libs-4.0.3-2.i386.rpm](http://centos.osmirror.nl/2.1/final/i386/CentOS/RPMS/XFree86-compat-libs-4.0.3-2.i386.rpm)

I dumped the contents to a temp directory, then did:

cd /your/temp/dir
sudo cp * /lib32

Then running ./crx worked fine (although I did get your no-sound problem)

Hope this helps someone else out there, because, not a damn thing on the web helped!

Everyone has their own solution it appears.

Also, for "No sound" issues, I tried using alsa-oss by using the command:

aoss ./crx

...but, the sound was choppy and miserable, however, the solution to that appears to be just running the game with:

./crx.sdl

Hope this helps!

---

### Post by Butthead on 2007-06-19
> **trinaryouroboros said:**
> 
Since I'm using 64-bit Ubuntu Linux, I just had to go get the XFree86-compat-libs-4.0.3-2 

Didn't they just release an x86_64 bit specific version of the game? :confused:

---

### Post by Cappy on 2007-06-19
> **trinaryouroboros said:**
> Seems like a cool free game, downloaded the linux binary and set it up at /usr/lib/games/alienarena2007

error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory!

Or you could use my program getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

like this:
```

cd /usr/bin
sudo wget -q http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs
sudo chmod +x getlibs
getlibs  /usr/lib/games/alienarena2007/whateverthebinarynameis

```

---

### Post by trinaryouroboros on 2007-06-20
> **Butthead said:**
> Didn't they just release an x86_64 bit specific version of the game? :confused:

Ah you know how it is, if there aren't Specific packages for a flavor of linux, things can get fussy.

> **Cappy said:**
> Or you could use my program getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

like this:
```

cd /usr/bin
sudo wget -q http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs
sudo chmod +x getlibs
getlibs  /usr/lib/games/alienarena2007/whateverthebinarynameis

```

...does this work the way my script works, though?

What we're doing in my script for this specific game is downloading the i386 rpm's and popping them into /lib32 - not /usr/lib - this is 64-bit Ubuntu!

If getlibs works that way as well, it's my new favorite tool!

---

### Post by Cappy on 2007-06-20
Yes, it works on AMD64 AND i386. I made the script mainly for the ease of use of getting AMD64 libraries but it is just as nice for i386 too.

---

### Post by trinaryouroboros on 2007-06-20
> **Cappy said:**
> Yes, it works on AMD64 AND i386. I made the script mainly for the ease of use of getting AMD64 libraries but it is just as nice for i386 too.

Are you freakin kidding me? That's the best news I've heard yet!

You da manz!

:KS

---

### Post by Butthead on 2007-06-22
Well, I went and downloaded the ZIP file of it (to see what all the fuss was), and after getting it extracted to the directory suggested, I get the dreaded "libXxf86dga.so.1" error file when trying to run the ./crx command. :(

And Cappy, running your "Getlibs" libraries proggie, I get a "permission denied" error message when trying to use it (even when logged in as root)? :confused:

I dunno.  Maybe my paths are wrong or something? :confused:

Anybody got any ideas? And BTW, trinaryouroboros, how did you (exactly?) extract that RPM (Redhat Package Manager) file that you recommended?

Sorry for being such a linux newbee! :rolleyes:

---

### Post by trinaryouroboros on 2007-06-22
> **Butthead said:**
> Well, I went and downloaded the ZIP file of it (to see what all the fuss was), and after getting it extracted to the directory suggested, I get the dreaded "libXxf86dga.so.1" error file when trying to run the ./crx command. :(

And Cappy, running your "Getlibs" libraries proggie, I get a "permission denied" error message when trying to use it (even when logged in as root)? :confused:

I dunno.  Maybe my paths are wrong or something? :confused:

Anybody got any ideas? And BTW, trinaryouroboros, how did you (exactly?) extract that RPM (Redhat Package Manager) file that you recommended?

Sorry for being such a linux newbee! :rolleyes:

Don't be confused, we're all linux newbies until we're professional linux admins for several years!

Ok, so that RPM file, if you double-click it...it's supposed to open "File-roller", then you can click an "Extract" button on the toolbar above. 

If file-roller's not opening for some mysterious reason, just open it by popping up a terminal and typing in:

file-roller

The window Should pop up...if it's missing, or something, I'd do:

sudo apt-get install file-roller

That'll do it.

As far as the permissions with getlibs...I'm in the dark about it, it's new to me!

I would spend some time with the creator to see what the trouble is because it's definitely worth it, but, if it's not working and you want to jump into the game - try my little script again after you're sure file-roller is happy, n stuff.

Otherwise, in the script, if you open it in a text editor - there's three wget commands that download those RPM's with the missing libraries. You can manually type that in a terminal if you wish, then all you have to do is extract those badboys (using file-roller) to some place like /home/yourname/temp/ and then:

sudo cp ~/temp/usr/lib/* /lib32
sudo cp ~/temp/usr/share/doc/*/* /usr/share/doc

That's all my silly script does, really!

P.S. - This is for the 64-BIT VERSION of Ubuntu, I really don't know if this will work for 32-bit yet.

Side note: You could also try running getlibs or my script with the sudo command.

Also, if you're getting errors or something in terminal when running the script or something, please copy and paste it here to troubleshoot further.

:D

---

### Post by Butthead on 2007-06-22
Hi trinaryouroboros,

Thanks for all the help!  Unfortunately, file-roller doesn't download for me (invalid operation).  I see that by using file-roller, you must be a Gnome user (KDE here).  Hmm, I wonder if there is a non "RPM'd" version of the above files? :confused:

Anyway, thanks for all your help!  I guess it would be wise for me to see if I can get ahold of Cappy and figure out what's the deal with me not being able to run "Getlibs."  Would seem to me to be a very easy fix for all these darn file associations ((if in fact it does work as advertised).

Maybe in three years or so (after finally figuring everything out), I'll finally get to see what the big fuss about AlienArena2007 is. :rolleyes:

And by that time you all will probably be playing AlienArena2010 on Zippy Zebra Ubuntu. :eek:

---

### Post by Cappy on 2007-06-22
Do this:
```
getlibs -32 libXxf86dga.so.1
```


Still get an error? Try this:
```

sudo chmod +x /usr/bin/getlibs
```

Now try running:
```
getlibs -32 libXxf86dga.so.1
```

---

### Post by trinaryouroboros on 2007-06-23
Sorry man, I haven't used KDE in like 10 years, practically since it's inception.

---

### Post by Butthead on 2007-06-23
> **Cappy said:**
> Do this:
```
getlibs -32 libXxf86dga.so.1
```


Still get an error? Try this:
```

sudo chmod +x /usr/bin/getlibs
```

Now try running:
```
getlibs -32 libXxf86dga.so.1
```

Hi Cappy,

Hmm, no dice. :(  I still get the error command:

./crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

when running Getlibs with the ./crx file or just trying to run ./crx by itself.  Most of these methods tell me that I do have libXxf86dga.so.1 installed already and that libraries have been linked, but still nada when trying to actually run the game.  I'm about ready to give up on it soon. :mad:

BTW - trinaryouroboros, thanks for all your help too!  Is there a way (using file roller) to compress those files you said helped you out getting AlienArena2007 to work in a form other than *.rpm (like *.zip?)? :confused:

Thanks Gentlemen! ;)

---

### Post by trinaryouroboros on 2007-06-24
Okie pokie!

You want to do the following commands in a terminal (copy/paste/stuff):

```

mkdir ~/ufoinstall
cd ~/ufoinstall
wget http://box.wyrmscape.com/share/butthead.zip

```

Makes the directory...then extract the butthead.zip in ~/ufoinstall to its own directory...using whatever Zip program you have.

```

sudo cp ~/ufoinstall/butthead/usr/lib/* /lib32
sudo cp ~/ufoinstall/butthead/usr/lib/* /usr/lib

```

Not sure what'll happen on the above, but hell, may as well try, right?

Overwrite any files if it bothers you.

```

sudo cp ~/ufoinstall/butthead/usr/doc/share/*/* /usr/doc/share

```

Above one...may not be necessary, but, what the heck.

In the following code, you'll download the .run file for UFO:AI, it's like almost 300MB, so expect a delay as you do the wget command:

```

wget http://internap.dl.sourceforge.net/sourceforge/ufoai/ufoai-2.1.1-linux_hotfix2.run
sudo chmod +x ~/ufoinstall/ufoai-2.1.1-linux_hotfix2.run
sudo ./ufoai-2.1.1-linux_hotfix2.run
sudo cp ~/ufoinstall/butthead/usr/lib/* /the/directory/you/installed/ufoai

```

Sure, why not?

Also, it may or may not be necessary to do the sudo command, but, I really don't know how you have your box set up and everything, and these specific commands don't hurt anything anyways.

```

rub-belly for: good.luck
cd /directory/ai2007/is/at
./crx.sda

```

Also, I'm gonna tell you again - IF YOU'RE GETTING ERRORS IN THE TERMINAL...AT ALL! LET ME KNOW!

Good luck!

:popcorn:

---

### Post by Cappy on 2007-06-24
Butthead, if getlibs isn't working it is probably because
1) You are running it on a script instead of a binary (that's why you got an error - I'm putting in a proper error msg for this next version)
and
2) You aren't running the newest version which supports
getlibs -32 libraryname.so

Try re-installing getlibs and post any errors that getlibs gives you if it doesn't work
```

getlibs -32 libXxf86dga.so.1
```



Don't run ```

sudo cp ~/ufoinstall/butthead/usr/lib/* /usr/lib
```
that would be bad.

---

### Post by trinaryouroboros on 2007-06-24
> **Cappy said:**
> Butthead, if getlibs isn't working it is probably because
1) You are running it on a script instead of a binary (that's why you got an error)
or
2) You aren't running the newest version which supports
getlibs -32 libraryname.so

Try re-installing getlibs and post any errors that getlibs gives you if it doesn't work


Don't run ```

sudo cp ~/ufoinstall/butthead/usr/lib/* /usr/lib
```
that would be bad.

I tested it - it's harmless. 

Those libraries aren't in /usr/lib by default, and if the 64-bit ones are ever needed I would suppose a matter of overwriting those 32-bit ones should be fine.

---

### Post by Butthead on 2007-06-24
Hi Guys,

Thanks for all your help!  Haven't tried what you have both posted yet, but I'm wondering if either of you could copy & paste the output of the $PATH command (under your terminal screen) to see if my paths are in fact correct? :confused:

(The reason why I am asking this is because I *DO* already have a lib32 directory, and I seem to remember in the distant past vaguely installing the 32 bit codecs in there once).  Would seem to me that AlienArena (I'm a linux newbee though!) should be able to find the files it needs to run (or compile?) if the path syntax is correct, right? 

Funny thing is is that I get the same "libXxf86dga.so.1" error message trying to run AlienArena2007 under Mandriva Discovery x64 (which I also have installed on a seperate H.D. on this very same computer. :confused:

The only other thing I can think is to run a "md5sum" check on my alienarena2007.zip to check for possible file corruption during download? (anyone know where to find the check string?).  Things seem to unzip readily for me though.  

If not, bah!, I'll just delete it (no biggie)! :mad:

Anyway, thanks to you for both of you help! :guitar:

---

### Post by Cappy on 2007-06-25
```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

This is what echoes if you used getlibs:
```
$ ls /usr/lib32/libXxf86dga.so.1
/usr/lib32/libXxf86dga.so.1
```

This is what echoes if trinary's thing:
```
$ ls /lib32/libXxf86dga.so.1
/lib32/libXxf86dga.so.1
```

Btw there was a bug in getlibs for retrieving this library; it was retrieving the debugging libraries instead but I fixed it yesterday.

---

### Post by trinaryouroboros on 2007-06-25
Same difference on $PATH:

```

ouroboros@w0-rm-h0-l3-ff:~$ $PATH
-bash: /home/ouroboros/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory

```

---

### Post by Butthead on 2007-06-25
Hi Cappy and trinaryboros,

Thanks to the both of you for the output of your $PATH commands, and for all the help you both have tried giving me! :guitar:

I got tired of screwing around with the game trying to make it work, so I deleted it last night in a fit of anger. :mad:

BTW I found out I did in fact have a "libXxf86dga.so.1" file the whole time in my /usr/lib directory, but couldn't figure out how to make the game see it. :confused:

Anyway, thanks again go out to the both of you for all of your help! :popcorn:

---

### Post by trinaryouroboros on 2007-06-25
"Your search - libXxf85dga - did not match any documents.

Suggestions:

    * Make sure all words are spelled correctly.
    * Try different keywords.
    * Try more general keywords."

...talk about Alien, I have no idea where to find that one, man.

:(

---

### Post by trinaryouroboros on 2007-06-25
Oh, the 86dga should be part of that package in the zip...

Else the RPM is here:

[http://linux.s390.org/download/rpm2html/libXxf86dga.so.1.html](http://linux.s390.org/download/rpm2html/libXxf86dga.so.1.html)

---

### Post by trinaryouroboros on 2007-06-25
Also...what directory...exactly...are you installing it?

---

### Post by trinaryouroboros on 2007-06-26
Cappy, something interesting:

Libraries libXxf86dga.so.1.0 and libXxf86dga.so.1.0.0 have the same soname, but, I think getlibs only will download libXxf86dga.so.1.0.0, it gives an error in regards to libXxf86dga.so.1.0 - so this might explain why the RPM would work in this specific scenario, however, it may also mean that Alien Arena 2007 is misconfigured, or something.

:(

---

### Post by Butthead on 2007-06-26
> **trinaryouroboros said:**
> Also...what directory...exactly...are you installing it?

Hi trinaryourboros,

Do you mean AlienArena2007?  If so,  /usr/lib/games/alienarena2007.

The "libXxf86dga.so.1 file is located in my /usr/lib/ directory.

BTW - (since I'm such a stupid Linux newbee), I'm assuming I didn't have to "compile" AlienArena2007 first before trying to run it, right?  Basically, just unzip it and run the ./crx command while in the AlienArena2007 directory, right? :confused:

Thanks!

---

### Post by trinaryouroboros on 2007-06-26
> **Butthead said:**
> Hi trinaryourboros,

Do you mean AlienArena2007?  If so,  /usr/lib/games/alienarena2007.

The "libXxf86dga.so.1 file is located in my /usr/lib/ directory.

BTW - (since I'm such a stupid Linux newbee), I'm assuming I didn't have to "compile" AlienArena2007 first before trying to run it, right?  Basically, just unzip it and run the ./crx command while in the AlienArena2007 directory, right? :confused:

Thanks!

Peculiar, the library I thought you required is libXxf86dga.so.1.0

If that was just a typo, and you do actually have libXxf86dga.so.1.0 in /usr/lib, just move it to /lib32 by doing:

```
sudo mv /usr/lib/libXxf86dga* /lib32
```

:KS

---

### Post by Butthead on 2007-06-27
Hi trinaryouroboros,

No, I believe the file error I always got referred to the "libXxf86dga.so.1" file (I almost have to reinstall AlienArena2007 now to make sure). :confused:

I *DID* try doing what you just suggested though (copying "libXxf86dga.so.1 from my /usr/lib directory over to /usr/lib32) and that didn't seem to make any difference in fixing the error. :(

I guess the game (and Kubuntu in general) just doesn't like me. :mad:

---

### Post by Butthead on 2007-06-27
Hmm, maybe I'll just go bug the game's creators about it to see what they have to say?

---

### Post by Cappy on 2007-06-28
> **trinaryouroboros said:**
> Libraries libXxf86dga.so.1.0 and libXxf86dga.so.1.0.0 have the same soname, but, I think getlibs only will download libXxf86dga.so.1.0.0
:(

If this actually is a problem, you would only need to 
```
ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1.0
```

Copying 64-bir libraries around and checking your PATH doesn't help at all. Look back a page for my solution.

---

### Post by Butthead on 2007-06-28
Hi Cappy and trinaryourobors,

Got it finally working! (needed some kind of *.386 file installed into the arena directory from a package someone on one of the forums here steered me to). :p

Now my question is, how exactly is this game played? :confused:

Seems the only way to get bots into a level is to drop them in thru the console (sv addbot botname), and (even after beating the bot/s fairly in frag counts), the same first level constantly loads? :(

The README file in the docs directory really doesn't tell you much either. :confused:

Did you two experience any problems playing it?

Thanks!

---

### Post by trinaryouroboros on 2007-06-28
No kidding?

Well, personally I don't play with the Bots, and, they should automatically join.

---

### Post by Butthead on 2007-06-29
Hmm, something must not be totally right on my side then? :confused:

Do you have any problems with the new maps loading?

---

### Post by KrazyPenguin on 2007-07-03
Just to note:

This game works perfectly using Mint Linux (based on Ubuntu) and the Mint Portal.

I coulnd't get sound working either with Ubuntu, but everything just works now!!!

Just click,click and play. Easy.

;-)

---

### Post by Butthead on 2007-07-04
Heh, deathmatch works acceptably now for me (using the command line to start the game) after installing it to Desktop in ancient Kubuntu Dapper Drake. :grin:

Wouldn't play more than the first level (had to drop bots into the game too) when installed to /usr/bin/ (like the README file illustrated to do). ](*,)

---

