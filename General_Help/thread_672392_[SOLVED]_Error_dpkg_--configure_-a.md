---
title: "[SOLVED] Error dpkg --configure -a??"
date: 2008-01-19
forum: General Help
---

### Post by NeonOnion on 2008-01-19
So while I was trying to update my Ubuntu it gave me this message;;

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I can't figure out for the life of me what to do, can anyone help me please?
I need help in very simple terms and easy walk throughs please!

---

### Post by Lord Illidan on 2008-01-19
Seems like you shutdown or restarted in the middle of an upgrade. No problem.

Just go to Applications -> Accessories -> Terminal.

Then type : ```
sudo dpkg --configure -a
```

Press enter.

Then type in your password when prompted to. The password will not show on the screen, so make sure you type it in correctly.

---

### Post by aysiu on 2008-01-19
**Step 1**
Close whatever program you're running (Update Manager, Synaptic Package Manager, Add/Remove)

**Step 2**
[Open a terminal](http://www.psychocats.net/ubuntu/terminal)

**Step 3**
Paste this command in the terminal: ```
sudo dpkg --configure -a
```

---

### Post by NeonOnion on 2008-01-19
> **Lord Illidan said:**
> Seems like you shutdown or restarted in the middle of an upgrade. No problem.

Just go to Applications -> Accessories -> Terminal.

Then type : ```
sudo dpkg --configure -a
```

Press enter.

Then type in your password when prompted to. The password will not show on the screen, so make sure you type it in correctly.

Thank you so much! <3
So every time my screen name and :$ show up should I type in sudo dpkg --configure -a again?

---

### Post by Lord Illidan on 2008-01-19
> **NeonOnion said:**
> Thank you so much! <3
So every time my screen name and :$ show up should I type in sudo dpkg --configure -a again?

Er..I didn't get that last sentence, can you rephrase it?

>  "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


The only reason that we told you to run that command is because your upgrade or software installation was interrupted. If that error happens again, you'll know what to do.

The terminal can be used for far more interesting purposes. Take a look at ubuntuguide.org for example.

---

### Post by NeonOnion on 2008-01-19
> **Lord Illidan said:**
> Er..I didn't get that last sentence, can you rephrase it?



The only reason that we told you to run that command is because your upgrade or software installation was interrupted. If that error happens again, you'll know what to do.

The terminal can be used for far more interesting purposes. Take a look at ubuntuguide.org for example.

Sorry about that last sentence.
I figured it out anyway.

Now it's telling me that something got corrupted and I need to run sudo apt-get install -f.
So I ran that and it's now telling me that what I'm doing can't be authenticated but I can go on if I want, what should I do?

---

### Post by Lord Illidan on 2008-01-19
Can you copy and paste the exact error please?

---

### Post by NeonOnion on 2008-01-19
neononion@neononion:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
The following NEW packages will be installed:
  sun-java5-jre
The following packages will be upgraded:
  sun-java5-bin
1 upgraded, 1 newly installed, 0 to remove and 110 not upgraded.
1 not fully installed or removed.
Need to get 29.9MB of archives.
After unpacking 83.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  sun-java5-jre sun-java5-bin
Install these packages without verification [y/N]?

---

### Post by Lord Illidan on 2008-01-19
First, why are you installing sunjava5, when there's sunjava6 out?
Second, that is pretty easy to solve. Just press Y and Enter.

---

### Post by NeonOnion on 2008-01-19
> **Lord Illidan said:**
> First, why are you installing sunjava5, when there's sunjava6 out?
Second, that is pretty easy to solve. Just press Y and Enter.

Because my friend told me too?
Wow..I sound like an idiot for that.
I'm not very computer smart though..Sorry!
Thanks a lot for helping me out!

---

### Post by Lord Illidan on 2008-01-19
No problem, it's an easy error to make, but generally the latest version is better. I thought you didn't notice that there was a later version in the repositories. To fix this, open Synaptic and erase sunjava5, and install the equivalent sunjava6 packages.

(Synaptic can be opened from terminal : gksudo synaptic)
(gksudo launches applications with root ("administrator") permissions)

---

### Post by NeonOnion on 2008-01-19
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


That is what I got after I pushed yes and it all loaded.
I've tried to run "sudo- apt-get install-f" but it just repeated the Software Index is Broken.

Man-oh-man what did I do to my computer?

---

### Post by NeonOnion on 2008-01-19
> **NeonOnion said:**
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


That is what I got after I pushed yes and it all loaded.
I've tried to run "sudo- apt-get install-f" but it just repeated the Software Index is Broken.

Man-oh-man what did I do to my computer?

I'm going to start a new thread for this.

---

### Post by marca311 on 2008-07-13
The entering
sudo dpkg --configure -a
into terminal never works for me:(

---

