---
title: "lshw isn't working..."
date: 2008-06-23
forum: General Help
---

### Post by wilson47 on 2008-06-23
Hello,

I was just looking around, and tried the command: ```
sudo lshw 
```
and it would just print ```
PCI (sysfs)
```, and stay there. After about five minutes of nothing, I closed the terminal. 

I run Ubuntu 8.04. Any help would be much appreciated, or, is there another command to find all my system info?

Thanks,
Glen

---

### Post by Kevbert on 2008-06-23
Interesting.  It seems to work for me when I use either 'sudo' or not (there's a short delay of about 1 second).  You could try:
```
lspci -v | less
```
to show all pci connected devices and 
```
lsusb -v | less
```
for all usb devices.

---

### Post by wilson47 on 2008-06-23
It works if I don't use *sudo*, but it insists that you don't get all (correct?) information. That is why I tried using sudo, but without any success.

Both of those commands worked. They provided all info only using sudo.

Any ideas?

---

### Post by cariboo on 2008-06-23
Are you having any other problems with sudo. Check /etc/hosts it should look something like this:

```
127.0.0.1	localhost
127.0.1.1	intrepid
```

In your case interpid would be replace with your hostname. There should be nothing after hostname.

If you don't know your hostname in a terminal type:

```
hostname
```

Jim

---

### Post by Kevbert on 2008-06-23
Another command to try is 
```
lshal
```
which lists all devices the hardware abstraction layer knows about, but apparently, not necessarily, all hardware on your system.  Sorry if this sounds a bit woolly but I'm quoting 'The Official Ubuntu Book'.  What devices do you have which aren't being displayed by each of the commands ?

---

### Post by wilson47 on 2008-06-23
After inspecting that, I get the result
```
127.0.0.1 localhost
127.0.1.1 dell-desktop.example.com dell-desktop
```
and my hostname is just dell-desktop.

So I thus altered to read 
```
127.0.0.1 localhost
127.0.1.1 dell-desktop
```.

Still nothing... 

I have been having sudo issues in general though. For instance, I was unable to get permission to run the ./configure script when compiling a program from source. I only got it to work after using ```
chmod 777
``` which I have read is not really reccomended.

---

### Post by wilson47 on 2008-06-23
I was just trying to use the command, mostly out of curiosity. It just rather bothered me that such a (seemingly) basic command was giving me problems. 

Those commands seem to work just fine! Thanks for all your help. 

But still no lshw... I just have seen this command used in lots of posts I have been going through, and would like to resolve the issue if I ever run into problems and need it.

---

### Post by VMC on 2008-06-23
This is one of the reasons I read and try to help. You find commands you either forgot about or undiscovered. I don't recall using lshw. I'm sure this has nothing to do with it, but here is my outputs of:

```
locate lshw
```

/usr/bin/lshw
/usr/share/app-install/desktop/lshw-gtk.desktop
/usr/share/app-install/icons/lshw-gtk.xpm
/usr/share/doc/lshw
/usr/share/doc/lshw/changelog.Debian.gz
/usr/share/doc/lshw/copyright
/usr/share/man/man1/lshw.1.gz
/var/lib/dpkg/info/lshw.list
/var/lib/dpkg/info/lshw.md5sums
```
whereis lshw
```

lshw: /usr/bin/lshw /usr/share/man/man1/lshw.1.gz

---

### Post by wilson47 on 2008-06-23
I have the same output after those commands. I guess that is a good start!

I tried the *sudo lshw* after a fresh start, and still no luck...

---

### Post by wilson47 on 2008-06-24
Still no luck. Help anyone???

---

### Post by mc4man on 2008-06-24
try this and then look in your home folder for the html file
```
 sudo lshw -html > hardware.html

```

---

### Post by wilson47 on 2008-06-24
It sadly just sits at 
```
glen@dell-desktop:~$  sudo lshw -html > hardware.html
[sudo] password for glen: 
PCI (sysfs)  


```
and doesn't do anything...

It works without sudo. I can post it if that would help.

---

### Post by mc4man on 2008-06-24
So sudo works for everything else? (as far as you know)
 typical stuff like sudo apt-get update

---

### Post by wilson47 on 2008-06-24
It works for apt-get update. I have been having trouble with permission elsewhere though... For instance, I was trying to compile a program from source, and sudo ```
./configure
``` wouldn't work no matter where I unpacked, until I ran ```
chmod 777 -R <Program's Folder>
``` which, from what I have read, shouldn't need to be done? 

So I think it may be a sudo problem...

---

### Post by mc4man on 2008-06-24
> So I think it may be a sudo problem...
in an odd sort of way
I was thinking if you could find a relationship between 'things' you can't do with sudo it may lead somewhere. I don't see any from the two you've mentioned/found so far.  

Off topic - you usually wouldn't use sudo in compiling for configuring, the typical would be ./configure, make,  make install. That doesn't mean you couldn't, just that you shouldn't.

Are you running the Dell version of Hardy?

---

### Post by VMC on 2008-06-24
You haven't supplied a password to sudo correct? On all other commands that require sudo you need to supply your password, yes?

I was thinking that maybe something in group got messed up. I also traced the output of a few of those directories but didn't find much.There is a web page for that command. Its here: [http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)
They do have open tickets but nothing like what do described.

That Host file usually effects other commands. I'm surprised you haven't had problems with that before now.

---

### Post by wilson47 on 2008-06-25
I'm on a Dell 1420 Laptop which had Gutsy on it. Then I updated to Hardy not too long ago. 

With the ./configure thing, it wouldn't work without sudo, so my first instinct was just to try with sudo, but no luck...

And when I run ```
sudo lshw
``` I do give it my password, and then it hangs. Was that what you meant VMC? And thank you for that link! I'm going to go through there to see what I can find.

---

### Post by zoobave on 2008-10-02
I am also getting the same problem. Any solutions?

---

### Post by wilson47 on 2008-12-23
My solution was a fresh install to 8.10. Maybe not the most practical, but it definitely works now!

---

