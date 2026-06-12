---
title: "Netflix on a 64-bit system."
date: 2013-01-23
forum: General Help
---

### Post by DivingHawk on 2013-01-23
Is there any way to run the commands from this video on a 64-bit system? I've heard rumors but nothing I've tried works. Surely somebody knows a way to make Netflix run on a 64 bit.

[http://www.youtube.com/watch?v=Tfte5su5DIA](http://www.youtube.com/watch?v=Tfte5su5DIA)

---

### Post by Nburnes on 2013-01-23
> **DivingHawk said:**
> Is there any way to run the commands from this video on a 64-bit system? I've heard rumors but nothing I've tried works. Surely somebody knows a way to make Netflix run on a 64 bit.

[http://www.youtube.com/watch?v=Tfte5su5DIA](http://www.youtube.com/watch?v=Tfte5su5DIA)

Works fine for me on 13.04 x64

Do ```

sudo apt-add-repository ppa:ehoover/compholio

sudo apt-get update

sudo apt-get install netflix-desktop
```

Then it wouldn't start so I had to 
```
rm -Rf ~/.netflix-desktop
```

and it runs great

All from here: [http://www.iheartubuntu.com/](http://www.iheartubuntu.com/)

---

### Post by DivingHawk on 2013-01-23
That last line of code doesn't appear to do anything for me. I can't find netflix anywhere in the dash home.

---

### Post by Nburnes on 2013-01-23
> **DivingHawk said:**
> That last line of code doesn't appear to do anything for me. I can't find netflix anywhere in the dash home.

Well, what are you running? 

As I said it is working fine for me and is found in my Dash. It was found in my Dash but clicking it would do nothing, until I did that final rm -rf command. Now have it pinned to the Unity Launcher. (Watching some "As Seen on TV" show right now).

---

### Post by DivingHawk on 2013-01-23
I'm running Quantal Quetzal. When I give the command to install Netflix it says 

"The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-compholio (>= 1.5.19~quantal1) but it is not installable
E: Unable to correct problems, you have held broken packages."

---

### Post by Nburnes on 2013-01-23
> **DivingHawk said:**
> I'm running Quantal Quetzal. When I give the command to install Netflix it says 

"The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-compholio (>= 1.5.19~quantal1) but it is not installable
E: Unable to correct problems, you have held broken packages."

From reading here: [https://bugs.launchpad.net/netflix-desktop/+bug/1101783](https://bugs.launchpad.net/netflix-desktop/+bug/1101783)

It seems you do not have Multi-Arch enabled. 

From ehoover (person who made it)
> It is most likely that your problem is that you don't have Multi-Arch enabled and you're working on a 64-bit machine. Please try running the following command:
dpkg --print-foreign-architectures
If it does not output "i386" then that means that "Multi-Arch" support is disabled. You can enable Multi-Arch by:
* Ubuntu 12.10:
sudo dpkg --add-architecture i386 && sudo apt-get update
* Ubuntu 12.04:
echo "foreign-architecture i386" | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch && sudo apt-get update

---

### Post by DivingHawk on 2013-01-23
That did it! Thanks!

---

### Post by chewyboy000 on 2013-01-23
Thank you [Nburnes]("http://ubuntuforums.org/member.php?u=856545")

---

