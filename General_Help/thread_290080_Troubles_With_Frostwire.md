---
title: "Troubles With Frostwire"
date: 2006-10-31
forum: General Help
---

### Post by dothedorky on 2006-10-31
So i'm currently operating in ubuntu 6.06 LTS (just upgraded... and wow).

I'm having troubles getting frostwire working and visible. When i click on it, in the accessories -->sound and video--> frostwire nothing pops up or opens. I tried downloading it, and nothing seems to work. 

Any ideas?

---

### Post by David Corrales on 2006-10-31
Try launching it from a terminal to get more error output.

---

### Post by hardkaare on 2006-10-31
yep you need to have jave installed and setup.

had the same problem.

run it from terminal and you can see the error.

you need to use the java chooser, and choose the correct java machine for your installation.

As far as i know there is problem more about bash and you need to change something in the frostwire startup script.

but you can find it all here in the forum.

---

### Post by DougieFresh4U on 2006-10-31
check your Sun Java 5 & Java 1.4 or 1.5

---

### Post by voodoonirvana on 2006-10-31
Im having the exact same problem (I think). When I try and run it from the terminal I get:

sam@sam-laptop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

---

### Post by DougieFresh4U on 2006-10-31
are you using dapper or edgy?

---

### Post by canadianwriterman on 2006-10-31
This was corrected with the latest version of Automatix2. If you uninstall Frostwire, then use Automatix2 to install it, it should be fine. Worked for me when I had the same problem.

---

### Post by turkenator on 2006-11-01
i dont know about other users but i always had problems with limewire/frostwire it might be some java problem or something but they just freeze and sometimes they make the whole computer freeze and u cant do anything but reset it (or in theory ssh into it) lime wire is more prone to do this frostwire ussually just freezes and u can kill its process and for me it happened in all the distros i tried so far suse/redhat/fedora/kubuntu ah well just my $0.02

---

### Post by veli on 2006-11-01
> **dothedorky said:**
> So i'm currently operating in ubuntu 6.06 LTS (just upgraded... and wow).

I'm having troubles getting frostwire working and visible. When i click on it, in the accessories -->sound and video--> frostwire nothing pops up or opens. I tried downloading it, and nothing seems to work. 

Any ideas?

Frostwire should be in Internet menu, not in Sound. If it's not visible in the menu upon install, log out-log in, and it'll be there. If not, launch Alacarte menu editor go to Internet and you'll see it ckecked. Uncheck it and check it again, this would bring Frostwire (and any other program not appearing at first) in the menu. These worked for me.

---

### Post by dothedorky on 2006-11-02
Is there by any chance, a howTo guide on the forums? I noticed that some java was missing in order to properly operate the program, but was at a loss in how to actually *get* those updates. 

I'm using aaannnd- (if it helps any) 

[I]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"[/I]

---

### Post by dothedorky on 2006-11-02
i tried going through alacarte, unchecking it and then checking it again with no success. Anyone know how to update java?

---

### Post by ninjad on 2006-11-03
if you used the extra repos to install frostwire or a deb file there was a problem with the coding for the package. to make frostwire launch right you need java and you need to change the frostwire sh file.

to fix the sh file:
```
sudo gedit /usr/bin/frostwire
```

then where it says sh runFrost.sh (should be the third line) change the first sh to bash. that made frostwire launch for me.

to install java 5:
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

you need the extra repos enabled to install java.

---

### Post by dothedorky on 2006-11-07
Removing the first sh to bash did not help in loading frostwire- i am still able to click on the icon- only nothing opens. If i go to applications-->internet-->frostwire. 

When downloading the files using your handy commands i've got:

Reading package lists... Done
Building dependency tree... Done
sun-java5-jre is already the newest version.
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

If i already have these plugins why wont frostwire just load already?](*,)

---

### Post by dothedorky on 2006-11-08
*bump*

No luck with many tweaks on Frostwire. Should I just accept defeat and move on?

---

