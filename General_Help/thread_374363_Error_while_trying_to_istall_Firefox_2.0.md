---
title: "Error while trying to istall Firefox 2.0"
date: 2007-03-02
forum: General Help
---

### Post by lsutiger on 2007-03-02
I am tryng to install Firefox 2.0.0.2. I created a folder named download where I am keeping all of my downloaded files. 
I open up terminal. Change directory to download. and I type this:
```
sudo tar -C /opt -x -z -v -f firefox-2.0.0.2.tar.gz
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```
So I created a directory named opt:
```
complexity@complexity-laptop:~/download$ dir
acer_acpi-0.3                installnewfirefox.sh
acer_acpi-0.3.tar.gz         jre1.5.0_11
chris_tatiana02_17_mpeg.mpg  jre-1_5_0_11-linux-i586.bin
firefox-2.0.0.2.tar.gz       opt
Firefox_wallpaper.png        
```
As you can see the directory is there, but I am still getting the error.
Any suggestions?

---

### Post by taurus on 2007-03-02
The opt is in your $HOME directory but you want to unpack it to /opt so you need to create it first.

```
sudo mkdir /opt
```

---

### Post by lsutiger on 2007-03-02
ok I have the .tar file in the home directory and a folder named opt in the home directory, but I get the same message....```
complexity@complexity-laptop:/home$ sudo tar -C /opt -x -z -v -f firefox-2.0.0.2.tar.gz
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```
when I do a directory listing:
```
complexity@complexity-laptop:/home$ ls
complexity  firefox-2.0.0.2.tar.gz  opt

```

---

### Post by taurus on 2007-03-02
Where do you want to unpack firefox-2.0.0.2.tar.gz?

---

### Post by lsutiger on 2007-03-02
Well I am following [this script]("http://lamparder320.googlepages.com/firefox2.txt"). so I am guessing the /opt directory.

---

### Post by taurus on 2007-03-02
```
sudo mkdir /opt
sudo cp firefox-2.0.0.2.tar.gz  /opt
cd /opt
sudo tar xvzf firefox-2.0.0.2.tar.gz
```

---

### Post by lsutiger on 2007-03-02
I apreciate all of  you help. I can't gt it to work correctly. I am going to post everthing from the terminal.```
complexity@complexity-laptop:~$ dir
coding   download  Examples                firefox-2.0.0.2.tar.gz.asc  Programs
Desktop  error     firefox-2.0.0.2.tar.gz  Firefox_wallpaper.png       text
complexity@complexity-laptop:~$ cd ..
complexity@complexity-laptop:/home$ dir
complexity  firefox-2.0.0.2.tar.gz  opt
complexity@complexity-laptop:/home$ sudo cp firefox-2.0.0.2.tar.gz  /opt
complexity@complexity-laptop:/home$ cd /opt
bash: cd: /opt: Not a directory
complexity@complexity-laptop:/home$ mkdir opt
mkdir: cannot create directory `opt': File exists
complexity@complexity-laptop:/home$ cd/opt
bash: cd/opt: No such file or directory
complexity@complexity-laptop:/home$ cd opt
complexity@complexity-laptop:/home/opt$ sudo tar xvzf firefox-2.0.0.2.tar.gz
tar: firefox-2.0.0.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
complexity@complexity-laptop:/home/opt$ ls
complexity@complexity-laptop:/home/opt$

```

I am not getting it! The directory is already there but when I copy the file and go to the directory, it does not exist!

---

### Post by taurus on 2007-03-02
Please look at my previous post again.

```

**[COLOR="Red"]sudo    mkdir    /opt[/COLOR]**
sudo    cp     firefox-2.0.0.2.tar.gz     /opt
cd       /opt
sudo    tar    xvzf    firefox-2.0.0.2.tar.gz

```

---

### Post by lsutiger on 2007-03-02
Well, if you look back at the script I linked to, that is what I followed and I got through it. But it definately muffed something up.
Now when I try to start firefox, I get a popup that states: Error - Could not launch Application
Details: Failed to execute child process "firefox" (no such file or directory.

Ouch!

---

### Post by DJ_Peng on 2007-03-03
I hate to break this to you, but I'm not sure you need a script to install Firefox 2.0.0.2. I know I didn't. Simply download it from the Mozilla website, extract it to the folder of your choosing (you can do this within Nautilus with a couple of mouse clicks), and run the ```
firefox
``` file that's in the resulting folder. You can change any or all of your launchers to run that file, so it's easy to run.

---

### Post by Maestro23 on 2007-03-03
Even better, FF 2.0.0.2 was included in the last update.  It's in the repositories now.

---

### Post by lsutiger on 2007-03-03
Wow! You wouldn't have know it by all the posts on How To Install firefox 2.0, [like this]("http://www.psychocats.net/ubuntu/firefox"), and [this]("http://lamparder320.googlepages.com/firefox2.txt"), and [this]("https://help.ubuntu.com/community/FirefoxNewVersion"). All of this misinformation can really confuse someone. Especially the oe hosted by Ubuntu Documentation.
Thanx!

---

### Post by Maestro23 on 2007-03-03
Enjoy and Good luck.

---

### Post by DJ_Peng on 2007-03-03
Yeah, lsutiger, that really dumsquizzles me. There's still the issue of some media plugins running it the way I suggested, but Automatix seems to fix that with little to no problem, at least not for me. I've thought about documenting how I got the Mozilla build installed, but I'm not so sure it won't just muddy up the waters even more than they already are.

@Maestro23:
I saw that, but I for one will stick with the Mozilla builds. The repository was updated in less than a week this time, but using their build seems to break, or at least damage, the ability to update plugins.

---

### Post by Maestro23 on 2007-03-03
> **DJ_Peng said:**
> Yeah, lsutiger, that really dumsquizzles me. There's still the issue of some media plugins running it the way I suggested, but Automatix seems to fix that with little to no problem, at least not for me. I've thought about documenting how I got the Mozilla build installed, but I'm not so sure it won't just muddy up the waters even more than they already are.

@Maestro23:
I saw that, but I for one will stick with the Mozilla builds. The repository was updated in less than a week this time, but using their build seems to break, or at least damage, the ability to update plugins.

Cool man.  Whatever works for ya. :)

---

