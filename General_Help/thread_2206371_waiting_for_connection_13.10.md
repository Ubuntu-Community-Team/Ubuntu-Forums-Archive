---
title: "waiting for connection 13.10"
date: 2014-02-18
forum: General Help
---

### Post by ricardo12 on 2014-02-18
hi guys im beginner so... i have one problem with my main pc i changed windows 7 ultimate for ubuntu but i skiped some things and now appears this message and i cant even login .... or see something just this error

---

### Post by ricardo12 on 2014-02-18
ham i tried to change to windows 7 again but i couldnt because something called ntfs and i tried to reinstall ubuntu and i couldnt too ...

---

### Post by Iowan on 2014-02-18
> **ricardo12 said:**
> ... i skiped some things and now appears this message and i cant even login .... or see something just this error
Can you be more specific about what message or error?

What happened when you tried to reinstall?

---

### Post by ricardo12 on 2014-02-18
well i tried and didnt happen nothing just get stuck like my screen turned off

about message its simply: waiting for network connection.... waiting for network connection 60 seconds 


i saw many posts before post mine and i cant solve this problem i need some topic very explicit for i need to do because i dont want and i dont need more errors.

---

### Post by spyworld on 2014-02-18
When you receive this error message:
[COLOR=#000000]waiting for network connection.... waiting for network connection 60 seconds [/COLOR]

During installation or Starting up Ubuntu?
If you receive this error message during Ubuntu installation, try to download daily build image. (Personal Opinion).
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Daily Build always include latest package.

---

### Post by ricardo12 on 2014-02-19
starting up

---

### Post by Impavidus on 2014-02-19
I once had that issue after upgrading from 10.04. It waited for 2 minutes and then continued without network. Appeared that I had to truncate the /etc/network/interfaces file to nothing more than ```
auto lo
iface lo inet loopback
```Can't say whether your problem is the same.

---

### Post by ricardo12 on 2014-02-19
i dont understand that... dont appears nothing to me i cant do updates with ctrl+alt+f2 sudo apt-get update .. maybe i need to turn on with commands my wireless but i dont know how to and i cant open ubuntu just do ctrl alt f2....

waiting up to 60 more seconds for network configuration....then it goes black screen. this is when i can do ctrl+alt+f2


i login my acc and its like im using terminal. but i cant download updates because they all fail

please if someone knows something that i can use with pen drive like change partition to NTFS to install windows again or someway to solve this problem help me pls

---

### Post by ricardo12 on 2014-02-19
> **Impavidus said:**
> I once had that issue after upgrading from 10.04. It waited for 2 minutes and then continued without network. Appeared that I had to truncate the /etc/network/interfaces file to nothing more than ```
auto lo
iface lo inet loopback
```Can't say whether your problem is the same.


can u teach me how to do that bro?

---

### Post by varunendra on 2014-02-19
> **ricardo12 said:**
> can u teach me how to do that bro?

If you can boot with the Live USB, go to the Hard Disk partition _where you have installed Ubuntu_. There, browse to the "**etc > network**" directory. There should be a file "**interfaces**" in that directory. Double-click to open it and see what are its contents.

It should contain only these two lines as Impavidus mentioned -
```
auto lo
iface lo inet loopback
```

If there are any extra lines, they need to be deleted *(any lines that 'Start' with a hash (**#**) symbol can be ignored)*.
To be able to delete extra lines, if there are any, you must open your file editor program as root, otherwise you would let you only 'Read' the file, not edit it.

To open the file as root, open your text editor with root privilege -
**press Alt-F2 > type "sudo gedit" > press 'Enter' key**.

This will open the text editor with a blank file. Ignore or close this file (but not the editor) > click "File > Open" from its menu > browse to the "interfaces" file above > open it > edit to remove the extra lines > save > close (ignore any prompts it may give about the other blank file it opened).

Note that if you are booted with a Live USB, it will contain its own version of the "interfaces" file in its root path. You have to edit (if required) the one that is on the partition where you have installed Ubuntu.

---

### Post by ricardo12 on 2014-02-19
if i use pen drive to reinstall again ubuntu this goes to black screen ... how i will do that?

---

