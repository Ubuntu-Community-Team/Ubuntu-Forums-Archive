---
title: "Sources list problem/can't access it"
date: 2014-07-14
forum: General Help
---

### Post by DougieFresh4U on 2014-07-14
Fresh 14.04 install. tried to do first update and terminal spits out:
[HTML]sudo apt-get update
[sudo] password for dougie: 
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdcss.list (dist parse)
E: The list of sources could not be read.
[/HTML]
and
[HTML]$ /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied
[/HTML]
It's beena long long time since I have had to do any 'tinkering'with my installs.
Would be glad for some help in fixing. 
Thanks

---

### Post by Bashing-om on 2014-07-14
DougieFresh4U; Hello;

Let's examine the error and what the package manager advises:
> 
E: Malformed line 1 in source list /etc/apt/[color=red]sources.list.d[/color]/[color=green]libdvdcss.list[/color] (dist parse)

Which tells us to look in the 3rd party directory "sources.list.d" and in particular the file "libdvdcss.list".

So let's do so:
```

cat /etc/apt/sources.list.d/libdvdcss.list

``` to see what the error is. Once seen then open up your favorite text editor ( with administrative authority - gksudo ) to that file and make the correction we have seen that is required.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by DougieFresh4U on 2014-07-14
[HTML]cat /etc/apt/sources.list.d/libdvdcss.list
to see what the error is. Once seen then open up your favorite text editor ( with administrative authority - gksudo ) to that file and make the correction we have seen that is required.[/HTML]
thanks, getting this:
[B]deb [ftp://ftp.videolan.org/pub/debian/stable](ftp://ftp.videolan.org/pub/debian/stable) trusty
[/B]

---

### Post by Bashing-om on 2014-07-14
DougieFresh4U; unk uh,

Does not compute.
The command "cat" is short for concatenate which only has to do with showing the contents of a file.
so copy and paste this into your terminal:
```

cat /etc/apt/sources.list.d/libdvdcss.list

```
for instance, an out put for one of my sources in that directory:
```

sysop@1404mini:~$ cat /etc/apt/sources.list.d/google-chrome.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main # re-enabled 06Jul2014 on upgrade to trusty

```
sysop@1404mini:~$
Post that output - between code tags -  back to us for our inspection.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by DougieFresh4U on 2014-07-14
Sorry, been a long time for code tags
Here is what I get:
```
[dougie:/home/dougie] $ cat /etc/apt/sources.list.d/libdvdcss.list
deb ftp://ftp.videolan.org/pub/debian/stable trusty
[dougie:/home/dougie] $
```

---

### Post by Bashing-om on 2014-07-14
DougieFresh4U; Hummmm

Humm, when you do in the browser address bar:
```

ftp://ftp.videolan.org/pub/debian/stable

```
note there is no listing for "trusty" The last field in your URL. That lends credence to that source as being invalid.

Now, videolan.org is the home page for the media player 'vlc'. Is there a real real need for you to go to the PPA for this utility ? -if that is your goal - 'vlc' is directly available in the software repository. Introducing later versions into a stable system can mess up the dependency tree of installed files.

Would not the better course be to remove that source and acquire 'vlc' -stable and compliant - from the software repository.
(that too "might" be another bag of worms)

[INDENT][INDENT]what to do, oh what
[INDENT][INDENT][INDENT][INDENT]to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DougieFresh4U on 2014-07-14
Have gone and rebuilt sources list via terminal commands.
Seems to be working and updating.
Just hope that upon reboot I am not left with a 'borked' install!

---

### Post by Bashing-om on 2014-07-14
DougieFresh4U; Great !

To see what the package manager thinks, after update/upgrade is completed:
```

sudo apt-get -f install
dpkg -C

```
If these run clean, you are home free.

[INDENT][INDENT]hey, 
[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DougieFresh4U on 2014-07-14
> **Bashing-om said:**
> DougieFresh4U; Great !

To see what the package manager thinks, after update/upgrade is completed:
```

sudo apt-get -f install
dpkg -C

```
If these run clean, you are home free.

[INDENT][INDENT]hey, 
[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
Thanks, all seems good now. Haven't rebooted yet but I'm about to try:p

---

