---
title: "Frets on Fire and .rar"
date: 2007-07-23
forum: General Help
---

### Post by Hickler on 2007-07-23
I have frets on fire and I got bored with the original three songs, so I downloaded a song pack. The instructions were to download the pack then unpack each song to the songs folder in frets on fire. When I try to open each song with archiver it tells me the file type (.rar) is unsupported, what should I do?

---

### Post by hessiess on 2007-07-23
7zip supports rar, and its on add remove programs

---

### Post by tbroderick on 2007-07-23
Do you have unrar installed?

---

### Post by Hickler on 2007-07-23
> **tbroderick said:**
> Do you have unrar installed?

No I don't but from what I can gather it's only a trial? In the meantime I will try 7zip. Thank you.

---

### Post by Hickler on 2007-07-23
Hmm, I downloaded and installed 7zip but when I try to open a song it still opens with archiver, where would 7zip be stored so that I can choose "Open with..."?

---

### Post by hessiess on 2007-07-23
i just instaled it but cannot find it eather, uset to use it alot on windows.

---

### Post by ZacDavis on 2007-07-23
7-zip on linux does not have a GUI.

---

### Post by hessiess on 2007-07-23
how do you use it from a cli? carnt work out the comand to start it, tryed 7zip 7-zip 7-Zip is it somthing strange

---

### Post by stchman on 2007-07-23
> **Hickler said:**
> I have frets on fire and I got bored with the original three songs, so I downloaded a song pack. The instructions were to download the pack then unpack each song to the songs folder in frets on fire. When I try to open each song with archiver it tells me the file type (.rar) is unsupported, what should I do?

Install the rar plugin

sudo apt-get install unrar

This will allow File Roller to unpack .rar archives.

---

### Post by Hickler on 2007-07-23
> **stchman said:**
> Install the rar plugin

sudo apt-get install unrar

This will allow File Roller to unpack .rar archives.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

:-/

---

### Post by distroman on 2007-07-23
Try this.
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

Add;
```
# PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo apt-get update
```

```
sudo apt-get install unrar
```

---

### Post by Hickler on 2007-07-23
Said the same thing.. but I add this
```
# PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
To the bottom of the sources page?
And also, when I enter 
```
gksudo gedit /etc/apt/sources.list
```
It says
```
(gedit:13941): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...

```

---

### Post by sr20ve on 2007-07-23
> **Hickler said:**
> I have frets on fire and I got bored with the original three songs, so I downloaded a song pack. The instructions were to download the pack then unpack each song to the songs folder in frets on fire. When I try to open each song with archiver it tells me the file type (.rar) is unsupported, what should I do?

IIRC you can still play songs in the compressed rar format in frets on fire.

---

### Post by Hickler on 2007-07-23
> **sr20ve said:**
> IIRC you can still play songs in the compressed rar format in frets on fire.

How?

---

### Post by distroman on 2007-07-23
```
sudo nano -w /etc/apt/sources.list
```

Guess you could try system > software sources

---

### Post by Hickler on 2007-07-23
> **distroman said:**
> ```
sudo nano -w /etc/apt/sources.list
```

Guess you could try system > software sources

What do you mean?

---

### Post by sr20ve on 2007-07-23
> **Hickler said:**
> How?

Just copy the rar files into your songs directory.

---

### Post by distroman on 2007-07-23
> **sr20ve said:**
> Just copy the rar files into your songs directory.
Do what he says :KS

---

### Post by Hickler on 2007-07-23
Tried it already, doesn't work. But I'll try again i suppose

---

### Post by Hickler on 2007-07-23
No, it doesn't work..

---

### Post by sr20ve on 2007-07-23
> **Hickler said:**
> No, it doesn't work..

What version of FOF? 1.2.451?

---

### Post by Hickler on 2007-07-23
> **sr20ve said:**
> What version of FOF? 1.2.451?

Yes

---

### Post by Hickler on 2007-07-23
...Is that the latest version of FOF?

---

### Post by sr20ve on 2007-07-23
> **Hickler said:**
> ...Is that the latest version of FOF?

Yeah, it is.

---

### Post by Hickler on 2007-07-23
So you can put the .rar file in your song directory and when you go to your song list in FOF it's there?

---

### Post by sr20ve on 2007-07-23
Yeah.

It's a nice way to organize all your songs, if you have hundreds of songs like I do. You can put all songs by a particular artist in a rar file. Then when you go to your song list in fof, it lists the rar as an archive and shows a suitcase icon instead of a cassette tape icon, you go into the archive and it lists all songs in that archive. Makes it easier than spending 5 minutes trying to scroll through your song list.:guitar:

---

### Post by stchman on 2007-07-23
> **Hickler said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

:-/

Enable all the software sources (main, universe, multiverse, restricted).  It is there, trust me. After that do the following:

```

sudo apt-get update
sudo apt-get -y install unrar

```

unrar is in the multiverse repository

[http://packages.ubuntu.com/feisty/utils/unrar](http://packages.ubuntu.com/feisty/utils/unrar)

---

### Post by Hickler on 2007-07-23
I will do all that but for now I've found a temporary solution, I boot to Windows and unzip them there, then copy them back. xD

---

